# Business Requirements Document (BRD)
  # Intelligent Major Incident Management – ServiceNow
  # 1. Introduction
     The Intelligent Major Incident Management application is designed to streamline and 
     automate the management of critical IT incidents using the ServiceNow platform.

     The solution provides structured major incident declaration, approval workflows, SLA monitoring, escalation management, 
     and operational reporting.

# 2. Business Problem
  Organizations may face challenges managing critical IT incidents, including:

 . Delays in identifying and declaring major incidents.
 . Manual approval processes.
 . Difficulty tracking response and resolution deadlines.
 . Delayed escalation to management.
 .  Limited visibility into major incident performance.
 . The proposed application addresses these challenges through automated workflows and centralized monitoring.

# 3. Project Objectives
  . Standardize major incident declaration.
  . Automate manager approval.
  . Monitor response and resolution SLAs.
  . Trigger escalation based on predefined conditions.
  . Improve operational visibility through dashboards.
  . Reduce manual administrative effort.
# 4. Stakeholders
 Stakeholder                    Responsibility

Employee                        Reports IT issues

Service Desk                   Reviews and manages incidents

Major Incident Manager          Approves major incident declarations

Team Lead                       Handles Level 1 escalation

IT Management                  Handles Level 3 escalation

IT Support Teams              Investigate and resolve incidents

# 5. Functional Requirements
 # FR-01: Major Incident Creation
The system shall allow authorized users to create major incident records.

 # FR-02: Declaration Validation
The system shall validate mandatory fields and declaration conditions before accepting a major incident.

 # FR-03: Manager Approval
The system shall initiate an approval request to the Major Incident Manager.

 # FR-04: Approval Processing
The system shall update the major incident according to the manager’s approval decision.

 # FR-05: SLA Calculation
The system shall calculate response and resolution deadlines based on priority.

 # FR-06: Response Acknowledgement
The system shall allow users to acknowledge the response through a dedicated UI Action.

 # FR-07: SLA Breach Monitoring
The system shall periodically check response and resolution deadlines.

 # FR-08: Escalation Management
The system shall support three escalation levels based on configured SLA conditions.

 # FR-09: Event Notifications
The system shall generate escalation events and support corresponding email notification configurations.

 # FR-10: Dashboard Reporting
The system shall provide operational reports for major incident status, priority, SLA breaches, escalation levels, and assignment groups.

# 6. SLA Business Requirements
Priority                  Response Target               Resolution Target

P1 - Critical              5 minutes                        1 hour

P2 - High                 15 minutes                     4 hours

P3 - Moderate             30 minutes                    8 hours

P4 - Low                 60 minutes                   24 hours

These are project-defined targets for demonstration purposes.

# 7. Escalation Requirements
Level                          Escalation Condition                       Responsible Team

Level 1                         Response SLA breached                       Team Lead

Level 2             Response remains unacknowledged 15 minutes after Level 1,  Major Incident Manager
                    without a resolution breach
Level 3                         Resolution SLA breached                          IT Management

# 8. Approval Requirements
Approval shall be requested from the assigned Major Incident Manager.
The approval decision shall be recorded.
Approved declarations shall remain in Accepted state.
Rejected declarations shall move to Rejected state.
# 9. Non-Functional Requirements
Security: Access shall be controlled through roles and permissions.
Reliability: Automation shall process eligible records consistently.
Maintainability: Business logic shall be organized into appropriate ServiceNow components.
Usability: Users shall have a clear interface for managing major incidents.
Performance: Scheduled monitoring shall process records efficiently.
# 10. Acceptance Criteria
The project shall be considered functionally acceptable when:

Major incident records can be created.
Declaration validation works.
Approval and rejection paths work.
SLA deadlines are calculated correctly.
Response acknowledgement works.
Response and resolution breaches are detected.
All three escalation levels are tested.
Escalation events are generated.
Dashboard reports display the configured data.
Actual email delivery is outside the validated acceptance scope because outbound email is disabled in the PDI.

# 11. Expected Business Benefits
Faster and more consistent major incident handling.
Improved accountability.
Better SLA visibility.
Structured escalation management.
Improved operational reporting.
Reduced manual intervention.
# 12. Conclusion
This project demonstrates how ServiceNow can be configured and customized to support a structured major incident management process through workflow automation, scripting, SLA monitoring, event generation, and analytics.
