# ServiceNow-Intelligent-Major-Incident-Management
A ServiceNow scoped application that automates Major Incident declaration, manager approvals, SLA monitoring, multi-level escalations, event-driven notifications, and operational dashboards.

# Intelligent Major Incident Management – ServiceNow
  # Project Overview
Intelligent Major Incident Management is a custom ServiceNow scoped application designed to streamline the major incident management lifecycle.

The application automates major incident declaration validation, manager approvals, SLA monitoring, multi-level escalations, event-driven notifications, and operational dashboards.

# Business Objectives
Improve major incident response time.
Automate major incident declaration and approval.
Monitor response and resolution SLAs.
Escalate incidents based on SLA breaches.
Provide operational visibility through dashboards.
# Technologies Used
ServiceNow Platform – Australia Release
ServiceNow Studio / Scoped Application
JavaScript
GlideRecord and GlideDateTime
Business Rules
Flow Designer
UI Actions
Scheduled Script Execution
Event Management and Email Notifications
Platform Analytics / Dashboards
# Key Features
  # 1. Major Incident Declaration
Custom Major Incident table.
Automatic record numbering.
Declaration validation using Business Rules.
Priority, impact, and urgency validation.
  # 2. Manager Approval
Flow Designer approval workflow.
Major Incident Manager approval.
Approved and rejected declaration paths.
  # 3. SLA Management
Priority                               Response Target     Resolution Target  

P1 – Critical                           5 minutes            1 hour

P2 – High                                15 minutes          4 hours

P3 – Moderate                            30 minutes           8 hours

P4 – Low                                 60 minutes            24 hours

. Automatic SLA deadline calculation.
. Response acknowledgement.
. Response and resolution breach detection.
  # 4. Multi-Level Escalation
    . Level 1 – Team Lead
    .  Level 2 – Major Incident Manager
    .  Level 3 – IT Management
Escalation events are generated when the configured escalation conditions are met.

# 5. Email Notifications
   . Event-driven notification configuration.
   . Separate notification templates for escalation levels.
   . Notification conditions based on escalation level.
Note: Actual outbound email delivery was not validated because outbound email is disabled in the PDI.

# 6. Operational Dashboard
  # Dashboard reports include:

   . Major Incidents by State
   . Major Incidents by Priority
   . SLA Breach Summary
   . Escalation Levels Overview
    . Open Major Incidents
   . Incidents by Assignment Group
# Testing
The following functional areas were tested:

  . Major Incident creation.
  . Declaration validation.
  . Manager approval and rejection.
  . SLA deadline calculation.
  . Response acknowledgement.
  . Response and resolution breach detection.
   .  Level 1, Level 2, and Level 3 escalations.
  . Event generation.
  . Dashboard visualization.
# Business Value
This application provides a structured approach to major incident handling by reducing manual intervention, improving SLA visibility, supporting timely escalation,
and helping IT teams coordinate critical incident resolution.

# Author
ServiceNow Developer Portfolio Project

# Application: Intelligent Major Incident Management
# Platform: ServiceNow Australia Release
# Environment: Personal Developer Instance (PDI)



