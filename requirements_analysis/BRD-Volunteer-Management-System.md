# Business Requirements Document (BRD)

# Volunteer Management System (VMS)

Version: 1.0
Author: Richard Broyles
Date: November 2026
Status: Portfolio Demonstration Project

---

## Portfolio Disclaimer
This document is a fictional business requirements document created for portfolio purposes.

This document is intended to demonstrate requirements gathering, systems analysis, business analysis, documentation, and solution design skills commonly used in enterprise software projects.

---

# 1. Executive Summary
The Volunteer Management System (VMS) is a web-based application designed to help nonprofit organizations recruit, manage, schedule, communicate with, and track volunteers.

The current volunteer management process relies on spreadsheets, email communications, paper forms, and manual scheduling activities.  These manual processes result in data inconsistencies, scheduling conflicts, communication challenges, and limited reporting capabilities.

The proposed system will centralize volunteer information and automate key processes including registration, scheduling, communication, attendance tracking, and reporting.

---

# 2. Business Problem Statement
The organization currently faces several operational challenges:

- Volunteer information is stored across multiple spreadsheets.
- Event coordinators manually schedule volunteers.
- Volunteer availability is difficult to track.
- Attendance records are inconsistent.
- Reporting requires significant manual effort.
- Email communications are time-consuming.
- There is no centrailized repository for volunteer history.

These challenges increase administrative workload and reduce organizational efficiency.

---

# 3. Business Objectives
The proposed system will:

### Objective 1
Reduce the time spent managing volunteer records.

### Objective 2
Improve visibility into volunteer participation.

### Objective 3
Reduce scheduling conflicts.

### Objective 4
Improve volunteer communication.

### Objective 5
Provide accurate reporting and analytics.

### Objective 6
Create a centralized volunteer database.

---

# 4. Scope

## In Scope

- Volunteer registration
- Volunteer profile management
- Event management
- Volunteer scheduling
- Attendance tracking
- Email Notifications
- Reporting and dashboards
- User authentication
- Administrative functions

## Out of Scope
- Payroll Processing
- Background check integration
- Donation processing
- Accounting functionality
- Mobile application (Phase 1)

---

# 5. Stakeholders

| Stakeholder | Responsibility |
|-------------|----------------|
| Volunteers | Register and participate in events |
| Volunteer Coordinators | Schedule volunteers and monitor participation |
| Event Managers | Create and manage events |
| Executive Leadership | Review reports and organizational metrics |
| System Administrators | Manage application configuration and security |
| IT Support Staff | Maintain system availability |

---

# 6. Current State Analysis

## Current Process

### Volunteer Registration

1. Volunteer submits paper form.
2. Staff manually enters information into spreadsheet.
3. Coordinator reviews application.
4. Volunteer receives confirmation email.

### Event Scheduling

1. Coordinator creates volunteer schedule.
2. Schedule distributed through email.
3. Volunteers reply manually.
4. Coordinator updates spreadsheet.

### Attendance Tracking

1. Volunteers sign paper attendance sheet.
2. Staff manually enters attendance into spreadsheet.
3. Reports generated manually.

---

# 7. Future State Vision
The Volunteer Management System will provide:

- Online registration
- Automated scheduling
- Real-time attendance tracking
- Volunteer self-service portal
- Email notifications
- Reporting dashboard
- Searchable volunteer database

---

# 8. Assumptions

- Volunteers have internet access.
- Email addresses are available for communication.
- Organization will provide system administrators.
- User training will be provided.
- Existing volunteer data can be imported.

---

# 9. Constraints
- Limited nonprofit budget.
- System must support modern web browsers.
- User interface should require minimal training.
- Sensitive volunteer information must be protected.

---

# 10. Functional Requirements

## User Management

### FR-001
System shall allow volunteers to create accounts.

### FR-002
System shall require unique email addresses for registration.

### FR-003
System shall allow users to reset passwords.

### FR-004
System shall support role-based access control.

Roles include:
- Volunteer
- Coordinator
- Administrator

---

## Volunteer Profiles

### FR-005
System shall maintain volunteer contact information.

### FR-006
System shall track volunteer skills.

### FR-007
System shall track volunteer interests.

### FR-008
System shall track volunteer availability.

---

## Event Management

### FR-009
Coordinators shall create events.

### FR-010
Events shall include:

- Name
- Description
- Date
- Start Time
- End Time
- Location
- Volunteer Capacity

### FR-011
System shall allow event updates.

### FR-012
System shall support event cancellation.

---

## Scheduling

### FR-013
Volunteers shall view available events.

### FR-014
Volunteers shall register for events.

### FR-015
System shall prevent overbooking.

### FR-016
System shall maintain waiting lists.

---

## Attendance Tracking

### FR-017
Cooridinators shall record attendance.

### FR-018
System shall record volunteer hours.

### FR-019
System shall maintain attendance history.

---

## Notifications

### FR-020
System shall send registration confirmation emails.

### FR-021
System shall send event reminders.

### FR-022
System shall notify volunteers of cancellations.

### FR-023
System shall notify volunteers of schedule changes.

---

## Reporting

### FR-024
System shall produce volunteer participation reports.

### FR-025
System shall provide event attendance reports.

### FR-026
System shall report volunteer hours.

### FR-027
System shall export reports to CSV format.

---

# 11. Non-functional Requirements

## Performance

### NFR-001
System shall support 1,000 concurrent users.

### NFR-002
Search results shall return within 3 seconds.

### NFR-003
Page load times shall not exceed 2 seconds under normal operating conditions.

---

## Security

### NFR-004
Passwords shall be encrypted.

### NFR-005
Users shall only access authorized data.

### NFR-006
All traffic shall use HTTPS.

---

## Availability

### NFR-007
System shall be available 99.99% of the time.

---

## Usability

### NFR-008
System shall support modern web browsers.

### NFR-009
New volunteers shall be able to complete registration without training.

---

# 12. Success Metrics

| Metric | Target |
|----------|----------|
| Volunteer Registration Completion Rate | 90% |
| Scheduling Time Reduction | 50% |
| Attendance Tracking Accuracy | 95% |
| Report Preparation Time Reduction | 75% |
| Volunteer Satisfaction Rating | 4.5/5 |

---

# 13. Risks

| Risk | Impact | Mitigation |
|--------|--------|--------|
| Low User Adoption | High | Provide training and commuication |
| Data Migration Issues | Medium | Conduct validation testing |
| Email Delivery Problems | Medium | Implement monitoring |
| Budget Constraints | High | Deliver functionality in phases |

---

# 14. Approval

This document serves as a baseline business requirements for the Volunteer Management System project.

Future requirements changes shall follow the orgainzation's change management process.

---

# Skills Demonstrated
- Business Requirements Analysis
- Systems Analysis
- Stakeholder Analysis
- Functional Requirements Definitions
- Non-functional Requirements Definition
- Business Process Documentation
- Scope Definition
- Requirements Documentation
- Solution Planning
- Technical Communication
