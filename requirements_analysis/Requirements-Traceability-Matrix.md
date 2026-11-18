# Requirements Traceability Matrix (RTM)

# Volunteer Management System (VMS)

Version 1.0

Author: Richard Broyles

Date: November 2026

Status: Portfolio Demonstration Project

---

## Portfolio Disclaimer
This Requirements Traceability Matrix was created for portfolio purposes to demonstrate business analysis, systems analysis, requirements management, testing alignment, and software lifecycle traceability skills.

The requirements, user stories, test cases, and business processes contained in this document are fictional and do not represent any actual company, project, or employer.

---

# Purpose

The Requirements Traceability Matrix (RTM) ensures that:

- Every business requirement is addressed by one or more user stories.
- Every user story can be tested.
- Project stakeholders can verify requirements coverage.
- Defects and changes can be properly analyzed for impact.

---

# Traceability Overview
```text
Business Requirement
        ↓
User Story
        ↓
Test Case
        ↓
Test Result
```

---

# Traceability Matrix

| Requirement ID | Business Requirement | User Story ID | Test Case ID | Status |
|----------------|----------------------|---------------|--------------|--------|
| FR-001 | Volunteer account creation | US-001 | TC-001 | Covered |
| FR-002 | Unique email validation | US-001 | TC-002 | Covered |
| FR-003 | Password reset | US-003 | TC-003 | Covered |
| FR-004 | Role-based security | US-020 | TC-004 | Covered |
| FR-005 | Maintain contact information | US-004 | TC-005 | Covered |
| FR-006 | Maintain volunteer skills | US-005 | TC-006 | Covered |
| FR-007 | Maintain volunteer interests | US-005 | TC-007 | Covered |
| FR-008 | Manage volunteer availability | US-006 | TC-008 | Covered |
| FR-009 | Create event | US-007 | TC-009 | Covered |
| FR-010 | Event details management | US-007 | TC-010 | Covered |
| FR-011 | Modify event | US-008 | TC-011 | Covered |
| FR-012 | Cancel event | US-009 | TC-012 | Covered |
| FR-013 | View available events | US-010 | TC-013 | Covered |
| FR-014 | Register for event | US-011 | TC-014 | Covered |
| FR-015 | Prevent overbooking | US-011 | TC-015 | Covered |
| FR-016 | Support waitlist | US-012 | TC-016 | Covered |
| FR-017 | Record attendance | US-013 | TC-017 | Covered |
| FR-018 | Record volunteer hours | US-014 | TC-018 | Covered |
| FR-019 | Maintain attendance history | US-013 | TC-019 | Covered |
| FR-020 | Registration confirmation email | US-015 | TC-020 | Covered |
| FR-021 | Event reminder notification | US-015 | TC-021 | Covered |
| FR-022 | Cancellation notification | US-009 | TC-022 | Covered |
| FR-023 | Schedule change notification | US-016 | TC-023 | Covered |
| FR-024 | Participation reporting | US-017 | TC-024 | Covered |
| FR-025 | Attendance reporting | US-018 | TC-025 | Covered |
| FR-026 | Volunteer hours reporting | US-017 | TC-026 | Covered |
| FR-027 | Export reports to CSV | US-019 | TC-027 | Covered |

---

# Test Case Summary

| Test Case ID | Description |
|--------------|-------------|
| TC-001 | Verify volunteer account creation |
| TC-002 | Verify unique email validation |
| TC-003 | Verify password reset workflow |
| TC-004 | Verify role-based access controls |
| TC-005 | Verify profile updates |
| TC-006 | Verify volunteer skills maintenance |
| TC-007 | Verify volunteer interests maintenance |
| TC-008 | Verify volunteer availability updates |
| TC-009 | Verify new event creation |
| TC-010 | Verify event detail management |
| TC-011 | Verify event modification process |
| TC-012 | Verify event cancellation process |
| TC-013 | Verify event search and viewing |
| TC-014 | Verify volunteer event registration |
| TC-015 | Verify overbooking prevention |
| TC-016 | Verify waitlist functionality |
| TC-017 | Verify attendance recording |
| TC-018 | Verify volunteer hours tracking |
| TC-019 | Verify attendance history retention |
| TC-020 | Verify registration confirmation email |
| TC-021 | Verify reminder notifications |
| TC-022 | Verify cancellation notifications |
| TC-023 | Verify schedule change notifications |
| TC-024 | Verify participation reporting |
| TC-025 | Verify attendance dashboard |
| TC-026 | Verify volunteer hours report |
| TC-027 | Verify CSV export functionality |

---

# Coverage Analysis

## Functional Requirement Coverage

| Area | Requirements | Covered |
|--------|-------------|---------|
| User Registration | 4 | Yes |
| Volunteer Profiles | 4 | Yes |
| Event Management | 4 | Yes |
| Scheduling | 4 | Yes |
| Attendance Tracking | 3 | Yes |
| Notifications | 4 | Yes |
| Reporting | 4 | Yes |

Overall Coverage: 100%

---

# Requirements Change Impact Example

## Example Change Request

**Change Request ID:** CR-001

### Description

Allow volunteers to register multiple availability time ranges for a single day.

### Impact Analysis

Affected Business Requirement:

```text
FR-008
```

Affected User Story:

```text
US-006
```

Affected Test Cases:

```text
TC-008
```

Affected System Modules:

```text
Volunteer Profile
Scheduling Engine
Coordinator Dashboard
```

### Risk Level

Medium

### Recommended Action

Update user story, revise scheduling logic, and create additional test cases prior to deployment.

---

# Traceability Benefits

The RTM provides:

- Complete requirement coverage visibility
- Verification that all requirements are tested
- Impact analysis for future changes
- Improved stakeholder communication
- Reduced risk of missed requirements
- Audit and compliance support

---

# Skills Demonstrated

- Requirements Traceability
- Business Analysis
- Systems Analysis
- Requirements Management
- Test Planning
- Change Impact Analysis
- Software Development Lifecycle (SDLC)
- Quality Assurance Planning
- Stakeholder Communication
- Documentation Management
