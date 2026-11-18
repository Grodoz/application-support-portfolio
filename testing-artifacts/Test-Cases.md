# Test Cases

# Volunteer Management System (VMS)

Version: 1.0

Author: Richard Broyles

Date: November 2026

Status: Portfolio Demonstration Project

---

## Portfolio Disclaimer

This test case document was created for portfolio purposes to demonstrate software testing, requirements validation, quality assurance planning, and systems analysis skills.

The system, requirements, workflows, and test cases described in this document are fictional and are not associated with any current or former employer.

---

# Purpose

This document defines the test cases used to validate the Volunteer Management System against its business requirements and user stories.

These test cases support:

- Functional Testing
- Regression Testing
- User Acceptance Testing (UAT)
- Requirements Validation

---

# Test Environment

## Environment

```text
Environment: Test
Application Version: 1.0
Database: VolunteerVMS_Test
Browser: Chrome Latest
```

## Test Data

```text
Volunteer User:
volunteer@test.org

Coordinator User:
coordinator@test.org

Administrator User:
admin@test.org
```

---

# Registration Test Cases

---

## TC-001

### Test Name

Volunteer Account Creation

### Related Requirement

FR-001

### Related User Story

US-001

### Preconditions

User is not currently registered.

### Test Steps

1. Navigate to Registration page.
2. Enter required information.
3. Click Register.

### Expected Result

- Account created successfully.
- Confirmation message displayed.
- Confirmation email generated.

### Priority

High

### Status

Pass

---

## TC-002

### Test Name

Duplicate Email Validation

### Related Requirement

FR-002

### Related User Story

US-001

### Preconditions

Existing account already uses email.

### Test Steps

1. Open Registration page.
2. Enter existing email address.
3. Submit registration.

### Expected Result

- Registration fails.
- User receives validation message.
- No duplicate account created.

### Priority

High

### Status

Pass

---

## TC-003

### Test Name

Password Reset Workflow

### Related Requirement

FR-003

### Related User Story

US-003

### Preconditions

Existing volunteer account exists.

### Test Steps

1. Select Forgot Password.
2. Enter registered email.
3. Open reset email.
4. Reset password.
5. Log in.

### Expected Result

- Password reset succeeds.
- User successfully logs in.

### Priority

High

### Status

Pass

---

# Security Test Cases

---

## TC-004

### Test Name

Role-Based Access Validation

### Related Requirement

FR-004

### Related User Story

US-020

### Preconditions

Volunteer account exists.

### Test Steps

1. Log in as Volunteer.
2. Attempt to access Admin page.

### Expected Result

- Access denied.
- Security event logged.

### Priority

High

### Status

Pass

---

# Volunteer Profile Test Cases

---

## TC-005

### Test Name

Update Volunteer Contact Information

### Related Requirement

FR-005

### Related User Story

US-004

### Test Steps

1. Log in.
2. Open Profile.
3. Update phone number.
4. Save changes.

### Expected Result

- Information saved successfully.
- Updated values visible.

### Priority

High

### Status

Pass

---

## TC-006

### Test Name

Update Volunteer Skills

### Related Requirement

FR-006

### Related User Story

US-005

### Test Steps

1. Open volunteer profile.
2. Add skill.
3. Save profile.

### Expected Result

- Skill saved successfully.
- Skill appears in profile.

### Priority

Medium

### Status

Pass

---

## TC-007

### Test Name

Update Volunteer Interests

### Related Requirement

FR-007

### Related User Story

US-005

### Test Steps

1. Edit interests.
2. Save profile.

### Expected Result

- Interests updated successfully.

### Priority

Medium

### Status

Pass

---

## TC-008

### Test Name

Manage Volunteer Availability

### Related Requirement

FR-008

### Related User Story

US-006

### Test Steps

1. Open availability calendar.
2. Select available dates.
3. Save changes.

### Expected Result

- Availability updated successfully.
- Coordinator can view availability.

### Priority

High

### Status

Pass

---

# Event Management Test Cases

---

## TC-009

### Test Name

Create Event

### Related Requirement

FR-009

### Related User Story

US-007

### Test Steps

1. Log in as Coordinator.
2. Create new event.
3. Save event.

### Expected Result

- Event created successfully.
- Event visible in event list.

### Priority

High

### Status

Pass

---

## TC-010

### Test Name

Update Event Details

### Related Requirement

FR-010

### Related User Story

US-008

### Test Steps

1. Select existing event.
2. Modify location.
3. Save changes.

### Expected Result

- Event updated successfully.
- Updated location displayed.

### Priority

Medium

### Status

Pass

---

## TC-011

### Test Name

Modify Existing Event

### Related Requirement

FR-011

### Related User Story

US-008

### Test Steps

1. Open event.
2. Edit event information.
3. Save.

### Expected Result

- Event reflects modifications.

### Priority

Medium

### Status

Pass

---

## TC-012

### Test Name

Cancel Event

### Related Requirement

FR-012

### Related User Story

US-009

### Test Steps

1. Open event.
2. Select Cancel Event.
3. Confirm cancellation.

### Expected Result

- Event status becomes Cancelled.
- Participants notified.

### Priority

Medium

### Status

Pass

---

# Scheduling Test Cases

---

## TC-013

### Test Name

Browse Available Events

### Related Requirement

FR-013

### Related User Story

US-010

### Test Steps

1. Log in.
2. View event catalog.

### Expected Result

- Upcoming events displayed.

### Priority

High

### Status

Pass

---

## TC-014

### Test Name

Volunteer Event Registration

### Related Requirement

FR-014

### Related User Story

US-011

### Test Steps

1. Select event.
2. Click Register.

### Expected Result

- Registration completed.
- Confirmation email sent.

### Priority

High

### Status

Pass

---

## TC-015

### Test Name

Prevent Event Overbooking

### Related Requirement

FR-015

### Related User Story

US-011

### Test Steps

1. Fill event to capacity.
2. Attempt one additional registration.

### Expected Result

- Registration denied.
- Waitlist option presented.

### Priority

High

### Status

Pass

---

## TC-016

### Test Name

Waitlist Functionality

### Related Requirement

FR-016

### Related User Story

US-012

### Test Steps

1. Select full event.
2. Join waitlist.

### Expected Result

- User added to waitlist.
- Waitlist position displayed.

### Priority

Medium

### Status

Pass

---

# Attendance Test Cases

---

## TC-017

### Test Name

Record Volunteer Attendance

### Related Requirement

FR-017

### Related User Story

US-013

### Test Steps

1. Open attendance roster.
2. Mark attendee Present.
3. Save roster.

### Expected Result

- Attendance record saved.

### Priority

High

### Status

Pass

---

## TC-018

### Test Name

Track Volunteer Hours

### Related Requirement

FR-018

### Related User Story

US-014

### Test Steps

1. Open attendance screen.
2. Enter volunteer hours.
3. Save record.

### Expected Result

- Volunteer hours stored correctly.

### Priority

High

### Status

Pass

---

## TC-019

### Test Name

Attendance History Retention

### Related Requirement

FR-019

### Related User Story

US-013

### Test Steps

1. Open volunteer profile.
2. View attendance history.

### Expected Result

- Historical attendance records displayed.

### Priority

Medium

### Status

Pass

---

# Notification Test Cases

---

## TC-020

### Test Name

Registration Confirmation Email

### Related Requirement

FR-020

### Related User Story

US-015

### Test Steps

1. Complete registration.
2. Check email inbox.

### Expected Result

- Confirmation email received.

### Priority

Medium

### Status

Pass

---

## TC-021

### Test Name

Event Reminder Notification

### Related Requirement

FR-021

### Related User Story

US-015

### Test Steps

1. Schedule reminder process.
2. Execute notification job.

### Expected Result

- Reminder message delivered.

### Priority

Medium

### Status

Pass

---

## TC-022

### Test Name

Event Cancellation Notification

### Related Requirement

FR-022

### Related User Story

US-009

### Test Steps

1. Cancel event.
2. Review notifications.

### Expected Result

- Cancellation message received.

### Priority

Medium

### Status

Pass

---

## TC-023

### Test Name

Schedule Change Notification

### Related Requirement

FR-023

### Related User Story

US-016

### Test Steps

1. Update event schedule.
2. Verify notification delivery.

### Expected Result

- Updated schedule email sent.

### Priority

Medium

### Status

Pass

---

# Reporting Test Cases

---

## TC-024

### Test Name

Volunteer Participation Report

### Related Requirement

FR-024

### Related User Story

US-017

### Test Steps

1. Open reporting dashboard.
2. Generate participation report.

### Expected Result

- Participation report displayed.

### Priority

Medium

### Status

Pass

---

## TC-025

### Test Name

Attendance Dashboard

### Related Requirement

FR-025

### Related User Story

US-018

### Test Steps

1. Open executive dashboard.

### Expected Result

- Attendance metrics displayed.

### Priority

Medium

### Status

Pass

---

## TC-026

### Test Name

Volunteer Hours Report

### Related Requirement

FR-026

### Related User Story

US-017

### Test Steps

1. Generate hours report.

### Expected Result

- Volunteer hours accurately reported.

### Priority

Medium

### Status

Pass

---

## TC-027

### Test Name

CSV Export

### Related Requirement

FR-027

### Related User Story

US-019

### Test Steps

1. Generate report.
2. Export to CSV.

### Expected Result

- CSV file downloaded successfully.
- Data matches report output.

### Priority

Low

### Status

Pass

---

# Test Execution Summary

| Metric | Value |
|----------|----------|
| Total Test Cases | 27 |
| Passed | 27 |
| Failed | 0 |
| Blocked | 0 |
| Execution Rate | 100% |

---

# Skills Demonstrated

- Test Planning
- Functional Testing
- Requirements Validation
- User Acceptance Testing
- Regression Testing
- Test Case Design
- Quality Assurance
- Traceability Support
- Defect Prevention
- Systems Analysis
- Software Development Lifecycle (SDLC)
