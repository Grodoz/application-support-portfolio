# Bug Reports

# Volunteer Management System (VMS)

Version: 1.0

Author: Richard Broyles

Date: November 2026

Status: Portfolio Demonstration Project

---

## Portfolio Disclaimer

These bug reports were created for portfolio purposes to demonstrate software testing, defect analysis, troubleshooting, root-cause analysis, and quality assurance documentation skills.

The system, defects, users, environments, and resolution activities described in this document are fictional and are not associated with any actual organization.

---

# Purpose

This document contains sample defect reports identified during testing of the Volunteer Management System.

The intent is to demonstrate:

- Defect documentation
- Issue reproduction
- Root cause investigation
- Defect prioritization
- Communication of testing results

---

# Severity Definitions

| Severity | Description |
|-----------|-------------|
| Critical | System unavailable or major business process blocked |
| High | Significant functionality impacted |
| Medium | Feature partially impacted |
| Low | Cosmetic or minor usability issue |

---

# Priority Definitions

| Priority | Description |
|-----------|-------------|
| P1 | Fix immediately |
| P2 | Fix in current release |
| P3 | Fix in future release |
| P4 | Enhancement consideration |

---

# BUG-001

## Title

Volunteer Registration Fails for Phone Numbers Containing Parentheses

### Severity

Medium

### Priority

P2

### Module

Volunteer Registration

### Environment

Test

### Steps to Reproduce

1. Open Registration Page.
2. Enter required information.
3. Enter phone number `(501) 555-1212`.
4. Submit registration.

### Expected Result

Volunteer account created successfully.

### Actual Result

Validation error displayed.

### Root Cause Analysis

Validation regular expression only accepted numeric digits.

### Resolution

Updated validation logic to support common U.S. phone number formats.

### Status

Resolved

---

# BUG-002

## Title

Duplicate Event Registrations Allowed

### Severity

High

### Priority

P1

### Module

Event Registration

### Environment

Test

### Steps to Reproduce

1. Log in as Volunteer.
2. Register for event.
3. Refresh page.
4. Submit registration again.

### Expected Result

Only one registration should exist.

### Actual Result

Multiple registrations created.

### Root Cause Analysis

Database uniqueness validation not implemented.

### Resolution

Added registration uniqueness constraint.

### Status

Resolved

---

# BUG-003

## Title

Coordinator Dashboard Loading Slowly

### Severity

Medium

### Priority

P2

### Module

Reporting Dashboard

### Environment

Test

### Symptoms

Dashboard required approximately 15 seconds to load.

### Investigation

Query execution plans reviewed.

### Root Cause Analysis

Missing index on participation_history table.

### Resolution

Database index created.

### Performance Results

Before Fix:

```text
15.2 seconds
```

After Fix:

```text
1.3 seconds
```

### Status

Resolved

---

# BUG-004

## Title

CSV Export Generates Blank File

### Severity

High

### Priority

P1

### Module

Reporting

### Environment

Test

### Steps to Reproduce

1. Generate participation report.
2. Select Export CSV.

### Expected Result

CSV file generated.

### Actual Result

Blank file downloaded.

### Root Cause Analysis

Export service writing incorrect dataset reference.

### Resolution

Updated export service mapping.

### Status

Resolved

---

# BUG-005

## Title

Volunteer Hours Not Updating After Attendance Submission

### Severity

High

### Priority

P1

### Module

Attendance Tracking

### Environment

Test

### Steps to Reproduce

1. Record attendance.
2. Enter volunteer hours.
3. Save.

### Expected Result

Volunteer profile updated.

### Actual Result

Hours remain unchanged.

### Root Cause Analysis

Attendance service failed to update profile aggregate.

### Resolution

Added missing update operation.

### Status

Resolved

---

# BUG-006

## Title

Password Reset Link Remains Active After Use

### Severity

Critical

### Priority

P1

### Module

Authentication

### Environment

Test

### Steps to Reproduce

1. Request password reset.
2. Use reset link.
3. Reuse same link.

### Expected Result

Link should expire.

### Actual Result

Link remains valid.

### Security Impact

Potential unauthorized account access.

### Root Cause Analysis

Token invalidation process missing.

### Resolution

Token destroyed immediately after successful reset.

### Status

Resolved

---

# BUG-007

## Title

Canceled Events Continue Appearing as Available

### Severity

Medium

### Priority

P2

### Module

Events

### Environment

Test

### Steps to Reproduce

1. Cancel event.
2. View events catalog.

### Expected Result

Canceled event hidden.

### Actual Result

Canceled event visible.

### Root Cause Analysis

Catalog query ignored event status.

### Resolution

Added status filter.

### Status

Resolved

---

# BUG-008

## Title

Attendance Dashboard Displays Incorrect Volunteer Totals

### Severity

High

### Priority

P1

### Module

Executive Dashboard

### Environment

Test

### Symptoms

Dashboard count exceeded actual attendance records.

### Investigation

Compared dashboard calculations to database records.

### Root Cause Analysis

Duplicate participation records included in calculation.

### Resolution

Distinct count logic implemented.

### Status

Resolved

---

# BUG-009

## Title

Waitlist Notification Sent Multiple Times

### Severity

Medium

### Priority

P2

### Module

Notification Service

### Environment

Test

### Steps to Reproduce

1. Open event slot.
2. Execute waitlist promotion job.

### Expected Result

Single notification delivered.

### Actual Result

Multiple notifications delivered.

### Root Cause Analysis

Notification retry process lacked duplicate check.

### Resolution

Added notification tracking table.

### Status

Resolved

---

# BUG-010

## Title

Unauthorized Volunteer Access to Coordinator Dashboard

### Severity

Critical

### Priority

P1

### Module

Security

### Environment

Test

### Steps to Reproduce

1. Log in as Volunteer.
2. Navigate directly to coordinator URL.

### Expected Result

Access denied.

### Actual Result

Dashboard loads successfully.

### Security Impact

Unauthorized access to sensitive volunteer information.

### Root Cause Analysis

Role validation missing at controller level.

### Resolution

Implemented centralized authorization middleware.

### Status

Resolved

---

# Defect Metrics Summary

| Metric | Count |
|----------|----------|
| Total Defects | 10 |
| Critical | 2 |
| High | 4 |
| Medium | 4 |
| Low | 0 |
| Open | 0 |
| Resolved | 10 |

---

# Defects by Functional Area

| Area | Defects |
|--------|---------|
| Authentication | 1 |
| Security | 1 |
| Event Management | 2 |
| Reporting | 2 |
| Attendance Tracking | 2 |
| Notifications | 1 |
| Registration | 1 |

---

# Lessons Learned

- Security testing must be included in every release cycle.
- Database indexing should be reviewed during performance testing.
- Role-based access controls require both UI and server-side validation.
- Export functionality requires dedicated regression testing.
- Automated testing should include duplicate transaction scenarios.

---

# Skills Demonstrated

- Defect Reporting
- Root Cause Analysis
- Functional Testing
- Security Testing
- Performance Testing
- Regression Testing
- SQL Investigation
- Risk Assessment
- Troubleshooting
- Quality Assurance
- Software Development Lifecycle
- Technical Documentation
