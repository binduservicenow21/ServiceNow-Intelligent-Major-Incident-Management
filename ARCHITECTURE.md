# Intelligent Major Incident Management
# Technical Architecture Document
 # 1. Project Information
    Item                                     Details

Project                                     Intelligent Major Incident Management

Platform                                    ServiceNow Australia Release

Application                                  Intelligent Major Incident Management

Application Type                              Scoped Application
     
Environment                                    Personal Developer Instance

Technology                                    JavaScript, GlideRecord, GlideDateTime

Automation                                   Business Rules, Flow Designer, Scheduled Scripts

Reporting                                    Platform Analytics / Dashboards
    
# 2. Architecture Overview
The application automates the major incident lifecycle through the following components:

  1. Major Incident creation.
  2. Declaration validation.
  3. Manager approval.
  4. SLA calculation and monitoring.
  5. Response acknowledgement.
  6. Multi-level escalation.
  7. Event-driven notifications.
  8. Operational dashboard reporting.
# 3. Application Data Model
# Major Incident Table
Technical table name:

x_78515_intellig_0_major_incident

Key fields:

Field                               Purpose

Short Description               Brief incident summary

Description                    Detailed incident information

Priority                       Incident priority

Impact                        Business impact

Urgency                       Business urgency

State                        Major incident lifecycle state

Major Incident Manager        Responsible manager

Assignment Group                 Support team

Assigned To                    Assigned technician

Related Incident                 Associated incident

Business Service                Affected business service

Affected Users                 Number of impacted users

Approval                        Manager approval status

Response Due                    Response SLA deadline

Resolution Due                  Resolution SLA deadline      

SLA Status                    Current SLA status

Response Breached              Response breach indicator

Resolution Breached            Resolution breach indicator

Response Acknowledged          Response acknowledgement flag

Response Acknowledged At      Acknowledgement timestamp

Escalation Level              Current escalation level

Escalated At                 Last escalation timestamp

Resolution Notes              Resolution details

Root Cause                        Identified root cause



# 4. Business Rules
 # MIM Declaration Validation
  . Executes before insert and update.
  . Validates mandatory declaration information.
  . Allows only P1 and P2 for major incident acceptance.
  . Prevents invalid impact and urgency combinations.
  . Aborts invalid record updates.
# MIM Calculate SLA
  . Executes before insert and update.
  . Reads the selected priority.
  . Calculates response and resolution deadlines.
  . Updates SLA status.
  . Initializes breach flags for new records.
# MIM SLA Escalation
  . Supports escalation-related record processing.
  . Escalation processing is primarily handled by the scheduled SLA monitor.
# 5. Flow Designer – Approval Workflow
Flow name: MIM - Major Incident Approval

# Trigger:

 . Table: Major Incident
 .  Trigger: Record Updated
 . Conditions: State = Accepted and Approval = Not Yet Requested.
# Workflow:

  . Request approval from Major Incident Manager.
  . Wait for approval response.
  . If approved, retain Accepted state.
 . If rejected, change state to Rejected.
# 6. SLA Management
Configured project SLA targets:

Priority                           Response                  Resolution
 
P1 - Critical                      5 minutes                 1 hour

P2 - High                         15 minutes                4 hours

P3 - Moderate                     30 minutes                8 hours
 
P4 - Low                          60 minutes                24 hours
 
Response acknowledgement is performed through a custom UI Action named Acknowledge Response.

# 7. Scheduled SLA Monitoring
Scheduled Script Execution:

MIM - SLA Breach Monitor

Execution interval: Every 5 minutes.

# Responsibilities:

. Checks response SLA deadlines.
. Checks resolution SLA deadlines.
. Identifies breached SLA records.
. Updates breach indicators.
. Determines escalation level.
. Generates escalation events.
. Saves updates without triggering unnecessary Business Rule recalculation.
# 8. Escalation Management
Level                       Responsible Team

Level 1                     Team Lead

Level 2                     Major Incident Manager

Level 3                      IT Management

# Escalation conditions:

  . Level 1: Response SLA breach.
  . Level 2: Response remains unacknowledged 15 minutes after Level 1, provided the resolution SLA has not breached.
  . Level 3: Resolution SLA breach.
# 9. Event-Driven Notifications
Event name:

x_78515_intellig_0.mim.escalation

Event parameters:

 . Parameter 1: Escalation level.
 . Parameter 2: Major incident short description.
Three email notification configurations:

 . MIM - Level 1 Escalation
 . MIM - Level 2 Escalation
 . MIM - Level 3 Escalation
Note: Event generation and notification configuration were tested.
Actual outbound email delivery was not validated because outbound email is disabled in the PDI.

# 10. Dashboard and Reporting
Dashboard:

GlobalTech Major Incident Management Dashboard

# Reports:
MIM - Incidents by State.
MIM - Incidents by Priority.
MIM - SLA Breach Summary.
MIM - Escalation Levels Overview.
MIM - Open Major Incidents.
MIM - Incidents by Assignment Group.
# 11. Functional Testing
The following functional scenarios were tested:

Test Scenario                             Result

Major Incident creation                  Passed

Declaration validation                    Passed

Manager approval                         Passed

Approval rejection                      Passed

SLA calculation                        Passed

Response acknowledgement              Passed    

Response breach detection            Passed

Resolution breach detection         Passed

Level 1 escalation                 Passed

Level 2 escalation                 Passed

Level 3 escalation                Passed

Event generation                 Passed

Dashboard visualization             Passed

Actual email delivery            Not verified – PDI restriction

# 12. Business Benefits
Improves major incident declaration consistency.
Reduces manual approval effort.
Provides automated SLA deadline monitoring.
Supports timely escalation.
Improves operational visibility.
Helps IT teams coordinate critical incident response.
# 13. Future Enhancements
Integrate Major Incident Management with the Incident table.
Implement automated incident communication.
Configure dedicated escalation recipient groups.
Integrate Microsoft Teams or collaboration tools.
Introduce AI-based major incident classification and summarization.
Implement advanced performance and SLA trend analytics.
# 14. Conclusion
The Intelligent Major Incident Management application demonstrates the use of ServiceNow scoped application development, server-side scripting, Flow Designer, scheduled automation, event-driven notifications, and operational reporting to improve the management of critical IT incidents.

# Project Type: ServiceNow Developer Portfolio Project.




