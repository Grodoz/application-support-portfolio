# User Stories

# Volunteer Management System (VMS)

Version: 1.0

Author: Richard Broyles

Date: November 2026

Status: Portfolio Demonstration Project

---

## Portfolio Disclaimer
These user stories were created for portfolio purposes to demonstrate business analysis, system analysis, Agile requirements gathering, and backing development skills.

The system, organization, users, business processes, and requirements described in this document are fictional and do not contain confidential, proprietary, or employer-owned information.

---

# Purpose

This document translates the business requirements defined in the Volunteer Management System BRD into actionable user stories suitable for Agile development planning.

---

# User Roles

- Volunteer
- Volunteer Coordinator
- Event Manager
- System Administrator
- Executive Leadership

---

# Epic 1 - User Registration and Authentication

## US-001 Volunteer Registration

**As a** Volunteer
**I want to** create a user account
**So that** I can participate in volunteer activities.

### Acceptance Criteria

- User can provide name, email, and password.
- Email must be unique.
- System validates required fields.
- User receives registration confirmation.
- User account is created successfully.

### Priority
High

### Story Points
5

---

### US-002 User Login

**As a** Volunteer
**I want to** log into the system
**So that** I can access volunteer opportunities.

### Acceptance Criteria
- User enters email and password.
- System validates credentials.
- Successful login redirects user to dashboard.
- Failed login displays error message.
- System logs authentication activity.

### Priority
High

### Story Points
3

---

## US-003 Password Reset

**As a** Volunteer
**I want to** reset my password
**So that** I can regain access to my account.

### Acceptance Criteria
- User can request password reset.
- Reset link is sent via email.
- Reset link expires after defined period.
- User can set a new password.

### Priority
High

### Story Points
5

---

# Epic 2 - Volunteer Profile Management

## US-004 Update Volunteer Profile

**As a** Volunteer
**I want to** update my profile informaiton
**So that** my information remains accurate.

### Acceptance Criteria

- User can edit personal information.
- User can update phone number.
- User can update address.
- User can save profile changes.

### Priority
High

### Story Points
3

---

## US-005 Maintain Skills and Interests

**As a** Volunteer
**I want to** maintain my skills and interests
**So that** coordinators can assign me to appropriate events.

### Acceptance Criteria

- User can add skills.
- User can edit skills.
- User can update interests.
- Changes are immediately saved.

### Priority
Medium

### Story Points
3

---

## US-006 Manage Availability

**As a** Volunteer
**I want to** indicate my availability
**So that** coordinators can schedule me appropriately.

### Acceptance Criteria

- User can select available dates.
- User can update availability.
- Availability information is visible to coordinators.

### Priority
High

### Story Points
5

---

# Epic 3 - Event Management

## US-007 Create Event

**As an** Event Manager
**I want to** create volunteer events
**So that** volunteers can register.

### Acceptance Criteria
- Event manager enters event information.
- Event includes date and location.
- Event includes volunteer capacity.
- Event becomes visible after publishing.

### Priority
High

### Story Points
8

---

## US-008 Edit Event

**As an** Event Manager
**I want to** modify event details
**So that** event information remains accurate.

### Acceptance Criteria
- Event information can be updated.
- Registered volunteers receive notifications.
- Changes are logged.

### Priority
Medium

### Story Points
5

---

## US-009 Cancel Event

**As an** Event Manager
**I want to** cancel an event
**So that** volunteers are informed of changes.

### Acceptance Criteria
- Event status changes to Cancelled.
- Volunteers receive notification.
- Registration is closed.

### Priority
Medium

### Story Points 
3

---

## US-010 Browse Available Events

**As a** Volunteer
**I want to** view available events
**So that** I can choose where to volunteer.

### Acceptance Criteria
- Events display in a list.
- User can search events.
- User can filter events by date.
- Event details are viewable.

### Priority
High

### Story Points
5

---

