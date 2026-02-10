PERFORMANCE INSIGHT DOC 
DOCUMENT CONTROL 
• DOCUMENT ID: PRI-NAWY-CRM-DB 
• VERSION: 1.0 
• DATE: DECEMBER 7,2025 
• AUTHOR: MEYER HAMDI 
• STATUES: PROPOSAL  
• STAKEHOLDERS: SALES AGENTS, SALES MANAGERS, DIRECTORS, HEAD 
OF SALES, PM’S  
1.EXECUTIVE SUMMARY 
• 1.1 Problem 
o The lake of the visibility of the performance of the sales person 
depends on the positive actions for the leads after rotation  
o Where is the stage that the sales stuck on it?  
• 1.2 Proposed Solution 
o A new "Performance Insight" dashboard module that provides 
two weighted metrics  
▪ error Rate (What percentage of my progressed leads 
convert elsewhere?) 
▪ success rate Conversion Rate (How effective am I at 
advancing reassigned leads?) 
• 1.3 expected impact 
o 30-50% reduction in time spent manually tracking lead outcomes 
o 15-25% reduction in number of leads that we lose and closing 
outside the organization  
2.Problem statement 
• 2.1 current situation 
o NAWY's CRM provides descriptive analytics (Overview I & II) 
showing historical performance but lacks performance insights 
for skill development. The sales process follows +10 defined 
stages, and leads are frequently rotated between agents based on 
performance rules. 
• 2.2 core problem 
o "Sales agents cannot systematically identify which specific funnel 
stages need improvement because they lack visibility into 
percentage of leads that convert to positive stages after rotation." 
• 2.3 Evidence of the problem 
o Manual Workarounds Exist: Agents regularly ask managers 
about rotated leads 
o Delayed Feedback: Learning opportunities come too late for 
behavior change 
o Privacy Concerns: Detailed performance visibility across 
hierarchy 
• 2.4 affected users  
User Role 
Impact 
Level 
Primary Pain Point 
Sales Agent 
High 
Cannot self-diagnose funnel weaknesses 
Sales Manager 
Medium 
Inefficient coaching due to incomplete data 
Team Leader 
Medium 
Cannot identify team-wide patterns 
Head of Sales 
Low 
Lacks cross-zone conversion analytics 
3.proposed solutions 
• 3.1 solution overview  
o A new dashboard module ("Overview III") that calculates and 
displays two weighted performance metrics based on existing 
CRM data and rules. 
• 3.2 core metrics 
o Error rate  
▪ Er  = (Σ Weighted Positive Actions on leads that later 
progressed elsewhere) ÷ (Σ All Weighted Positive Actions) × 
100 
• Agent takes 100 positive actions (weighted total: 250) 
20 of those leads later progress with other agents 
(weighted value: 60)OLR = 60 ÷ 250 × 100 = 24% 
o Success rate 
▪ Sr  = (Number of reassigned leads advanced by ≥1 positive 
action)  ÷  (Total reassigned leads received)  × 100 
▪ Sr = your fresh lead you closed ÷  total fresh leads you 
received * 100 
• Agent receives 50 reassigned leads Successfully 
advances 30 of them  
• SR= 30 ÷ 50 × 100 = 60% 
4.Technical Implementation 
• 4.1 data requirements 
o The CRM already tracks: 
▪ Lead assignment history with timestamps 
▪ Status change history with agent attribution 
▪ Positive action definitions and weights 
▪ Rotation/reassignment events 
• 4.2 Relationship needed(don’t trust me on this relationship haha) 
Lead → [Owner History] → [Status Changes] →[Subsequent Owners] → [Status Changes] 
↑                                               
Agent A                           
↑                             
Positive Action          
↑                                          
Agent B                     
↑ 
Positive Action 
5.user stories requirement  
• 5.1 user stories  
o As a sales agent I want to  
▪ See my Opportunity Loss Rate segmented by sales stage 
▪ Identify which specific status transitions have the highest 
error  
▪ Receive alerts when my metrics deviate significantly from 
baselines 
o As a sales manager I want  
▪ View team-level Opportunity Loss Rates by stage 
▪ Identify agents needing in the sales process  
▪ Track improvement in metrics over time 
▪ Export reports for performance reviews 
• 5.2 functional requirement  
o Export and report  
▪ Export metrics to PDF/Excel for performance reviews 
▪ Schedule automated report delivery 
▪ API access for integration with external dashboards 
o Dashboard display  
▪ Display both (er) and (sr) as primary metrics 
▪ Show trend arrows (improving/declining) 
▪ Allow filtering by date range (default: current quarter) 
▪ Enable drill-down by sales stage 
o Stage analysis view  
▪ Display funnel visualization with leakage percentages at 
each stage 
▪ Show "Top 3 Leakage Stages" for quick insight 
▪ Provide comparison to team/zone averages 
• 5.3 non-functional requirement  
o Security  
▪ Role-based access control (RBAC) following sales hierarchy 
▪ Data isolation between sales zones where required 
▪ Audit logging for all metric calculations 
6.risk analysis  
• 6.1 High risk: culture resistance 
o  Description: Agents may perceive metrics as punitive rather than 
developmental 
o Probability: Medium-High 
o Impact: High 
o Mitigation: 
▪ Phase 1: Manager-only access for coaching context 
▪ Clear communication: "Diagnostic tool, not report card" 
▪ Training emphasizing growth mindset 
• 6.2 Medium risk: data gaming  
o Description: Agents might manipulate status changes to improve 
metrics 
o Probability: Medium 
o Impact: Medium 
o Mitigation: 
▪ Use weighted system (existing NAWY weights) 
▪ Manager oversight and validation 
• 6.3 Medium Risk: Technical Complexity 
o Description: Lead lineage tracking across multiple rotations is 
complex 
o Probability: Medium 
o Impact: Medium 
o Mitigation: 
▪ Start with simple attribution (last positive action) 
▪ Iterative complexity increase 
▪ Thorough testing with historical data 
▪ Clear rollback plan 
• 6.4 Low Risk: Performance Impact 
o Description: Additional calculations may slow CRM performance 
o Probability: Low 
o Impact: Low 
o Mitigation: 
▪ Asynchronous calculation during off-peak hours 
▪ Database indexing optimization 
▪ Caching of calculated metrics 
7. Dependencies 
• CRM Data Integrity: Requires accurate status change tracking 
• Weight System Consistency: Depends on existing NAWY action weights 
• Training Resources: Need for proper feature introduction 
8.pros and cons  
• 8.1 Pros 
o For Sales Agents: 
▪ Targeted Self-Improvement: Precise identification of weak 
funnel stages 
▪ Objective Feedback: Data-driven insights vs. subjective 
manager opinions 
▪ Reduced Admin Time: Eliminates manual lead tracking 
(est. 3-5 hours/week) 
▪ Competitive Motivation: Healthy comparison with team 
benchmarks 
▪ Career Development: Clear path for skill improvement 
o For Sales Management: 
▪ Efficient Coaching: Data identifies exactly who needs help 
with what 
▪ Performance Transparency: Objective metrics for reviews 
and promotions 
▪ Resource Allocation: Identify team strengths/weaknesses 
for optimal assignment 
▪ Predictive Analytics: Early warning for declining 
performance trends 
o For the Organization: 
▪ Increased Conversion Rates: Estimated 5-15% 
improvement through targeted coaching 
▪ Data Asset Utilization: Leverages existing CRM data for 
new insights 
▪ Reduced Turnover: Clear development path increases agent 
satisfaction 
▪ Competitive Advantage: Advanced analytics capability in 
real estate CRM 
▪ Scalable Coaching: Consistent feedback across all teams 
and zones 
• 8.2 Cons 
o Implementation Challenges: 
▪ Development Cost: Estimated 200-300 engineering hours 
▪ Training Overhead: Requires training for 100+ sales staff 
▪ Change Management: Resistance to new performance 
visibility 
o Cultural Risks: 
▪ Unhealthy Competition: Potential for toxic rivalry between 
agents 
▪ Metric Fixation: Agents might focus on metrics rather than 
customer relationships 
9. Alternative Solutions Considered 
• 9.1 Do Nothing 
o Pros: No cost, no disruption 
o Cons: Missed improvement opportunity, continued inefficiency 
• 9.2 Enhanced Manager Reports 
o Pros: Lower cost, uses existing processes 
o Cons: Still manual, inconsistent, not scalable 
• 9.3 Simple Notification System 
o Pros: Low technical complexity, immediate alerts 
o Cons: Lacks analytical depth, could create alert fatigue 
10. Success Criteria & Measurement 
•  Quantitative Success Metrics 
o Adoption Rate: >70% of agents using dashboard weekly by 
Month 3 
o Time Savings: Reduction of ≥2 hours/week in manual tracking 
o Performance Improvement: 10% reduction in average (er) within 
6 months 
o Data Quality: >95% accuracy in metric calculations (validated 
sample) 
o System Performance: <3 second dashboard load time for 95% of 
requests 
11. Appendices 
• 11.1 Wireframe  
 
 
• 11.2 Jira usage  
 
 
 
12.Document Approval 
• Author: MEYER HAMDI  
THANK YOU  
