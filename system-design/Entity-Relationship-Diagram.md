# Entity Relationship Diagram (ERD)

## Volunteer Management System (VMS)

Version: 1.0

Author: Richard Broyles

Date: November 2026

Status: Portfolio Demonstration Project

---

## Portfolio Disclaimer

> [!IMPORTANT]
> This Entity Relationship Diagram (ERD) and supporting documentation were created for portfolio purposes.
>
> The entities, attributes, relationships, data structures, and business rules described in this document are fictional and are intended solely to demonstrate:
>
> - Systems Analysis
> - Data Modeling
> - Database Design
> - Business Analysis
> - Requirements Analysis
> - Technical Documentation
>
> No proprietary, confidential, or employer-owned information has been used.

---

# Purpose

This document defines the logical data model for the Volunteer Management System.

The objectives are to:

- Identify business entities
- Define relationships between entities
- Support application development
- Enable reporting and analytics
- Improve data quality
- Support future scalability

---

# Entity Relationship Overview

```text
VOLUNTEER
     |
     | 1:M
     |
     v
VOLUNTEER_REGISTRATION
     ^
     |
     | M:1
     |
EVENT
     |
     | 1:M
     |
     v
ATTENDANCE
     |
     | M:1
     |
VOLUNTEER

VOLUNTEER
     |
     | 1:M
     |
     v
VOLUNTEER_SKILL

VOLUNTEER
     |
     | 1:M
     |
     v
VOLUNTEER_AVAILABILITY

USER_ACCOUNT
     |
     | 1:1
     |
VOLUNTEER
```

---

# High-Level ERD

```text
+------------------+
| USER_ACCOUNT     |
+------------------+
| account_id PK    |
| username         |
| password_hash    |
| account_status   |
| role_id FK       |
+------------------+
          |
          | 1:1
          |
          v
+------------------+
| VOLUNTEER        |
+------------------+
| volunteer_id PK  |
| first_name       |
| last_name        |
| email_address    |
| phone_number     |
+------------------+
          |
          | 1:M
          |
          +----------------------+
          |                      |
          v                      v

+------------------+     +----------------------+
| VOLUNTEER_SKILL  |     | VOLUNTEER_AVAILABILITY|
+------------------+     +----------------------+
| skill_id PK      |     | availability_id PK   |
| volunteer_id FK  |     | volunteer_id FK      |
| skill_name       |     | available_date       |
+------------------+     +----------------------+

          |
          | M:M
          |
          v

+---------------------------+
| VOLUNTEER_REGISTRATION    |
+---------------------------+
| registration_id PK        |
| volunteer_id FK           |
| event_id FK               |
| status                    |
+---------------------------+
           ^
           |
           |
+------------------+
| EVENT            |
+------------------+
| event_id PK      |
| event_name       |
| event_date       |
| capacity         |
+------------------+
           |
           | 1:M
           |
           v

+------------------+
| ATTENDANCE       |
+------------------+
| attendance_id PK |
| event_id FK      |
| volunteer_id FK  |
| hours_served     |
+------------------+
```

---

# Entity: USER_ACCOUNT

## Description

Stores authentication and authorization information.

## Primary Key

```text
account_id
```

## Attributes

| Column | Description |
|----------|------------|
| account_id | Unique account identifier |
| username | Login username |
| password_hash | Encrypted password |
| account_status | Active, Locked, Disabled |
| role_id | Security role |
| last_login_date | Most recent login |

## Business Rules

- Username must be unique.
- Passwords must be encrypted.
- Locked accounts cannot authenticate.

---

# Entity: VOLUNTEER

## Description

Stores volunteer demographic information.

## Primary Key

```text
volunteer_id
```

## Attributes

| Column | Description |
|----------|------------|
| volunteer_id | Unique volunteer ID |
| first_name | Volunteer first name |
| last_name | Volunteer last name |
| email_address | Email address |
| phone_number | Contact phone |
| city | Residence city |
| state | Residence state |
| registration_date | Join date |

## Business Rules

- Email address must be unique.
- One volunteer may have only one profile.
- Volunteer profile required before event registration.

---

# Entity: VOLUNTEER_SKILL

## Description

Stores volunteer skills and qualifications.

## Primary Key

```text
skill_id
```

## Foreign Keys

```text
volunteer_id
```

## Attributes

| Column | Description |
|----------|------------|
| skill_id | Unique skill ID |
| volunteer_id | Volunteer relationship |
| skill_name | Skill description |
| skill_level | Beginner, Intermediate, Advanced |

## Business Rules

- One volunteer may have many skills.
- Skills support event assignments.

---

# Entity: VOLUNTEER_AVAILABILITY

## Description

Stores volunteer availability information.

## Primary Key

```text
availability_id
```

## Foreign Key

```text
volunteer_id
```

## Attributes

| Column | Description |
|----------|------------|
| availability_id | Record identifier |
| volunteer_id | Associated volunteer |
| available_date | Available date |
| start_time | Start time |
| end_time | End time |

## Business Rules

- Multiple availability records allowed.
- Availability drives scheduling decisions.

---

# Entity: EVENT

## Description

Stores volunteer events.

## Primary Key

```text
event_id
```

## Attributes

| Column | Description |
|----------|------------|
| event_id | Event identifier |
| event_name | Event title |
| event_description | Description |
| event_date | Event date |
| location | Event location |
| maximum_capacity | Volunteer limit |
| event_status | Scheduled, Completed, Cancelled |

## Business Rules

- Events may have multiple volunteers.
- Capacity limits registrations.
- Cancelled events prevent new registrations.

---

# Entity: VOLUNTEER_REGISTRATION

## Description

Associates volunteers with events.

This is a junction table supporting a many-to-many relationship.

## Primary Key

```text
registration_id
```

## Foreign Keys

```text
volunteer_id

event_id
```

## Attributes

| Column | Description |
|----------|------------|
| registration_id | Registration identifier |
| volunteer_id | Volunteer registration |
| event_id | Event assignment |
| registration_date | Signup date |
| registration_status | Registered, Waitlisted, Cancelled |

## Business Rules

- One volunteer can register for many events.
- One event can have many volunteers.
- Duplicate registrations prohibited.

---

# Entity: ATTENDANCE

## Description

Tracks volunteer participation and service hours.

## Primary Key

```text
attendance_id
```

## Foreign Keys

```text
event_id

volunteer_id
```

## Attributes

| Column | Description |
|----------|------------|
| attendance_id | Attendance record |
| event_id | Related event |
| volunteer_id | Related volunteer |
| attendance_status | Present, Absent |
| hours_served | Volunteer hours |
| attendance_date | Event participation date |

## Business Rules

- Attendance only recorded for registered volunteers.
- Hours served must be greater than zero.
- Attendance records support reporting.

---

# Entity: ROLE

## Description

Stores application security roles.

## Primary Key

```text
role_id
```

## Attributes

| Column | Description |
|----------|------------|
| role_id | Role identifier |
| role_name | Role name |
| description | Security definition |

## Example Roles

```text
Volunteer

Coordinator

Administrator
```

---

# Relationship Summary

| Parent Entity | Relationship | Child Entity |
|---------------|-------------|--------------|
| USER_ACCOUNT | 1:1 | VOLUNTEER |
| VOLUNTEER | 1:M | VOLUNTEER_SKILL |
| VOLUNTEER | 1:M | VOLUNTEER_AVAILABILITY |
| VOLUNTEER | 1:M | VOLUNTEER_REGISTRATION |
| EVENT | 1:M | VOLUNTEER_REGISTRATION |
| EVENT | 1:M | ATTENDANCE |
| VOLUNTEER | 1:M | ATTENDANCE |
| ROLE | 1:M | USER_ACCOUNT |

---

# Data Integrity Controls

## Uniqueness Constraints

```text
VOLUNTEER.email_address

USER_ACCOUNT.username
```

## Referential Integrity

```text
Attendance requires valid Volunteer.

Attendance requires valid Event.

Registration requires valid Volunteer.

Registration requires valid Event.
```

## Validation Rules

```text
Hours Served > 0

Email Format Validation

Capacity Not Exceeded

No Duplicate Registrations
```

---

# Reporting Support

This model supports:

- Volunteer Participation Reports
- Attendance Reports
- Volunteer Hours Reports
- Event Capacity Reports
- Volunteer Skill Reports
- Availability Reports

---

# Example Business Questions Supported

```text
How many hours has a volunteer served?

Which events have the highest attendance?

Which volunteers possess CPR certification?

Which events are approaching capacity?

Which volunteers are available next weekend?
```

---

# Skills Demonstrated

- Data Modeling
- Entity Relationship Design
- Database Design
- Systems Analysis
- Business Analysis
- Relational Database Concepts
- Data Integrity Design
- Requirements Analysis
- Solution Architecture
- Technical Documentation
