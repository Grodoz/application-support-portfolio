# Process Flows

## Volunteer Management System (VMS)

Version: 1.0

Author: Richard Broyles

Date: November 2026

Status: Portfolio Demonstration Project

---

## Portfolio Disclaimer

> [!IMPORTANT]
> This document contains fictional business process flows created for portfolio purposes.
>
> The organization, workflows, users, and business processes described herein are intended solely to demonstrate:
>
> - Business Analysis
> - Systems Analysis
> - Process Modeling
> - Requirements Documentation
> - Workflow Optimization
> - Technical Communication
>
> No proprietary, confidential, or employer-owned information has been used.

---

# Purpose

This document defines the current-state and future-state business processes for the Volunteer Management System.

The goals of these process flows are to:

- Document how work is currently performed
- Identify inefficiencies and risks
- Define the desired future process
- Support system requirements
- Guide solution design

---

# Process Flow 1 - Volunteer Registration

## Current State

### Challenges

- Paper forms
- Manual data entry
- Delayed communications
- Duplicate records
- High administrative workload

### Workflow

```text
Volunteer Completes Paper Form
               |
               v
Coordinator Receives Form
               |
               v
Coordinator Reviews Information
               |
               v
Coordinator Enters Data Into Spreadsheet
               |
               v
Coordinator Saves Volunteer Record
               |
               v
Coordinator Sends Email Confirmation
               |
               v
Volunteer Added To Active List
```

### Pain Points

1. Manual data entry
2. Duplicate volunteer records
3. Lost paperwork
4. Delayed confirmation emails
5. Limited reporting capability

---

## Future State

### Workflow

```text
Volunteer Completes Online Registration
               |
               v
System Validates Required Fields
               |
               v
Email Address Verified
               |
               v
Volunteer Record Created
               |
               v
Confirmation Email Sent
               |
               v
Volunteer Account Activated
```

### Benefits

- Reduced manual effort
- Faster registration
- Improved data accuracy
- Automatic communications
- Better reporting

---

# Process Flow 2 - Volunteer Event Registration

## Current State

### Workflow

```text
Volunteer Receives Event Email
               |
               v
Volunteer Replies By Email
               |
               v
Coordinator Reviews Response
               |
               v
Coordinator Updates Spreadsheet
               |
               v
Coordinator Confirms Registration
```

### Issues

- Multiple spreadsheets
- Registration conflicts
- Manual tracking
- Scheduling errors

---

## Future State

### Workflow

```text
Volunteer Logs Into System
               |
               v
Volunteer Browses Available Events
               |
               v
Volunteer Selects Event
               |
               v
System Checks Capacity
               |
      +--------+--------+
      |                 |
      v                 v
Space Available     Event Full
      |                 |
      v                 v
Registration      Waitlist Option
Created                |
      |                |
      +--------+-------+
               |
               v
Confirmation Sent
```

### Benefits

- Real-time registration
- Automatic capacity management
- Waitlist support
- Improved user experience

---

# Process Flow 3 - Attendance Tracking

## Current State

### Workflow

```text
Volunteer Arrives At Event
               |
               v
Signs Paper Attendance Sheet
               |
               v
Coordinator Collects Sheet
               |
               v
Attendance Entered Into Spreadsheet
               |
               v
Reports Updated Manually
```

### Issues

- Lost sign-in sheets
- Manual entry errors
- Delayed reporting
- Inconsistent attendance records

---

## Future State

### Workflow

```text
Volunteer Arrives At Event
               |
               v
Coordinator Opens Attendance Screen
               |
               v
Volunteer Marked Present
               |
               v
Hours Recorded
               |
               v
Volunteer History Updated
               |
               v
Reporting Updated Automatically
```

### Benefits

- Real-time attendance data
- Improved reporting accuracy
- Reduced administration

---

# Process Flow 4 - Volunteer Availability Management

## Current State

### Workflow

```text
Coordinator Emails Volunteer
               |
               v
Volunteer Replies With Availability
               |
               v
Coordinator Reviews Email
               |
               v
Spreadsheet Updated Manually
               |
               v
Schedule Created
```

### Issues

- Outdated schedules
- Missing responses
- Scheduling conflicts

---

## Future State

### Workflow

```text
Volunteer Logs In
               |
               v
Updates Availability Calendar
               |
               v
System Stores Availability
               |
               v
Coordinator Reviews Availability
               |
               v
Volunteer Assigned To Event
```

### Benefits

- Accurate availability
- Reduced scheduling effort
- Fewer schedule conflicts

---

# Process Flow 5 - Event Cancellation

## Current State

### Workflow

```text
Coordinator Cancels Event
               |
               v
Creates Email Distribution
               |
               v
Manually Sends Notification
               |
               v
Waits For Volunteer Responses
```

### Issues

- Delayed notifications
- Missed communications
- Volunteer confusion

---

## Future State

### Workflow

```text
Coordinator Cancels Event
               |
               v
Event Status Updated
               |
               v
Notification Triggered
               |
               v
All Registered Volunteers Notified
               |
               v
Audit Log Updated
```

### Benefits

- Faster communication
- Consistent notifications
- Improved auditability

---

# Process Flow 6 - Reporting

## Current State

### Workflow

```text
Coordinator Requests Report
               |
               v
Opens Multiple Spreadsheets
               |
               v
Manually Combines Data
               |
               v
Creates Report
               |
               v
Distributes Report
```

### Issues

- Time-consuming
- Error-prone
- Data inconsistencies

---

## Future State

### Workflow

```text
Coordinator Opens Dashboard
               |
               v
Selects Report Type
               |
               v
System Generates Report
               |
               v
Coordinator Reviews Results
               |
               v
Report Exported
```

### Benefits

- Faster report generation
- Improved accuracy
- Consistent metrics

---

# End-to-End Future State Workflow

```text
Volunteer Registration
           |
           v
Profile Creation
           |
           v
Availability Management
           |
           v
Event Registration
           |
           v
Attendance Tracking
           |
           v
Hours Recording
           |
           v
Reporting And Analytics
```

---

# Process Improvement Summary

| Area | Current State | Future State |
|--------|--------------|-------------|
| Registration | Manual | Automated |
| Scheduling | Spreadsheet-Based | System Driven |
| Attendance | Paper Forms | Digital Tracking |
| Availability | Email Driven | Self-Service |
| Notifications | Manual | Automated |
| Reporting | Manual Compilation | Real-Time Dashboards |

---

# Business Benefits

## Operational Benefits

- Reduced administrative effort
- Faster volunteer onboarding
- Improved attendance tracking
- Automated communications

## Data Benefits

- Improved data quality
- Reduced duplicate records
- Consistent reporting

## User Benefits

- Better volunteer experience
- Faster registration
- Self-service capabilities

---

# Skills Demonstrated

- Business Process Analysis
- Current-State Analysis
- Future-State Design
- Workflow Documentation
- Requirements Analysis
- Systems Analysis
- Process Improvement
- Solution Design
- Stakeholder Communication
- Technical Documentation
