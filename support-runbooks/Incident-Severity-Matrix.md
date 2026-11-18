# Incident Severity Matrix

## Volunteer Management System (VMS)

Version: 1.0

Author: Richard Broyles

Date: November 2026

Status: Portfolio Demonstration Project

---

## Portfolio Disclaimer

> [!IMPORTANT]
> This runbook is a fictional operational support document created for portfolio purposes.
>
> The incident classifications, escalation procedures, business impacts, service levels, and response expectations described in this document are fictional and intended solely to demonstrate:
>
> - Incident Management
> - Production Support
> - IT Operations
> - Service Management
> - Application Support
> - Technical Documentation
>
> No proprietary, confidential, or employer-owned information has been used.

---

# Purpose

This document defines the severity classification process used by Application Support, Technical Support, Operations, and Engineering teams when responding to production incidents.

The goals of this matrix are to:

- Establish consistent incident prioritization
- Improve communication during incidents
- Standardize escalation procedures
- Reduce Mean Time to Resolution (MTTR)
- Improve service availability

---

# Incident Classification Overview

Incidents are classified according to:

1. Business Impact
2. User Impact
3. System Availability
4. Data Integrity Risk
5. Regulatory or Security Risk

Severity levels range from:

```text
Severity 1 (Critical)

Severity 2 (High)

Severity 3 (Medium)

Severity 4 (Low)
```

---

# Severity Matrix

| Severity | Business Impact | User Impact | Response Time |
|----------|----------------|-------------|---------------|
| SEV-1 | Critical Business Impact | All Users Affected | 15 Minutes |
| SEV-2 | Significant Impact | Multiple Users Affected | 30 Minutes |
| SEV-3 | Moderate Impact | Limited Users Affected | 4 Hours |
| SEV-4 | Minor Impact | Individual User | Next Business Day |

---

# SEV-1 Critical Incident

## Definition

Complete loss of a critical business service.

Business operations cannot continue.

Immediate action required.

---

## Examples

### Application Outage

```text
Volunteer Management System unavailable.
```

### Authentication Failure

```text
All users unable to log in.
```

### Database Outage

```text
Production database unavailable.
```

### Security Incident

```text
Unauthorized access to sensitive data.
```

### Data Corruption

```text
Production records being altered or deleted.
```

---

## User Impact

```text
All users impacted.

No workaround available.
```

---

## Response Requirements

### Initial Response

```text
15 Minutes
```

### Escalation

Immediate

### Incident Bridge

Required

### Executive Notification

Required

---

## Example

```text
Database server offline.

All application functionality unavailable.

Severity = SEV-1
```

---

# SEV-2 High Incident

## Definition

Major business functionality unavailable.

Business operations significantly impacted.

Workarounds may exist.

---

## Examples

### API Timeout Failures

```text
Volunteer registrations failing.
```

### Reporting Failure

```text
Operational reporting unavailable.
```

### Performance Degradation

```text
Application extremely slow.
```

### Third-Party Integration Failure

```text
Email notification service unavailable.
```

### Large Group Impact

```text
Multiple departments affected.
```

---

## User Impact

```text
Many users affected.

Limited workaround available.
```

---

## Response Requirements

### Initial Response

```text
30 Minutes
```

### Escalation

Support Manager

### Incident Bridge

Optional

### Executive Notification

As Needed

---

## Example

```text
API response times exceed 30 seconds.

Volunteer registration failing intermittently.

Severity = SEV-2
```

---

# SEV-3 Medium Incident

## Definition

Partial service degradation.

Business operations continue with limited disruption.

Reasonable workaround available.

---

## Examples

### Reporting Delays

```text
Dashboard loads slowly.
```

### Minor Integration Issues

```text
Some email notifications delayed.
```

### Limited Functional Defect

```text
Certain reports exporting incorrectly.
```

### Data Quality Issue

```text
Duplicate volunteer records detected.
```

---

## User Impact

```text
Small group of users affected.

Business operations continue.
```

---

## Response Requirements

### Initial Response

```text
4 Hours
```

### Escalation

Team Lead

### Incident Bridge

Not Required

### Executive Notification

Not Required

---

## Example

```text
Volunteer participation report incorrect.

Workaround available.

Severity = SEV-3
```

---

# SEV-4 Low Incident

## Definition

Minimal business impact.

No operational disruption.

Cosmetic or informational issue.

---

## Examples

### UI Display Issue

```text
Text alignment problem.
```

### Spelling Error

```text
Typographical error.
```

### Minor Report Formatting

```text
Date displayed incorrectly.
```

### Enhancement Request

```text
Additional export feature requested.
```

---

## User Impact

```text
Individual user or small group impacted.

No interruption to business operations.
```

---

## Response Requirements

### Initial Response

```text
Next Business Day
```

### Escalation

Not Required

### Incident Bridge

Not Required

### Executive Notification

Not Required

---

## Example

```text
Minor formatting issue within dashboard.

Severity = SEV-4
```

---

# Data Integrity Severity Rules

Any issue involving data integrity should be evaluated separately.

| Condition | Minimum Severity |
|------------|----------------|
| Duplicate Records | SEV-3 |
| Missing Records | SEV-2 |
| Corrupted Data | SEV-2 |
| Mass Data Loss | SEV-1 |
| Unauthorized Data Access | SEV-1 |

---

# Security Severity Rules

| Condition | Minimum Severity |
|------------|----------------|
| Failed Login Spike | SEV-2 |
| Privilege Escalation | SEV-1 |
| Unauthorized Data Exposure | SEV-1 |
| Malware Detection | SEV-1 |
| Vulnerability Discovery | SEV-2 |

---

# Performance Severity Rules

| Condition | Severity |
|------------|---------|
| Response Time 2x Normal | SEV-4 |
| Response Time 5x Normal | SEV-3 |
| Response Time 10x Normal | SEV-2 |
| System Unusable | SEV-1 |

---

# Escalation Matrix

| Severity | Escalation Target |
|----------|------------------|
| SEV-1 | Application Support Manager, DBA, Operations Manager, Executive Leadership |
| SEV-2 | Application Support Manager, Operations Team |
| SEV-3 | Team Lead |
| SEV-4 | Assigned Support Engineer |

---

# Communication Requirements

| Severity | Update Frequency |
|----------|----------------|
| SEV-1 | Every 30 Minutes |
| SEV-2 | Every 1 Hour |
| SEV-3 | Every 4 Hours |
| SEV-4 | Daily |

---

# Sample Incident Classifications

## Incident 001 - Authentication Failure

```text
All users unable to log in.

Business Impact:
Critical

Severity:
SEV-1
```

---

## Incident 002 - Slow Database Query

```text
Dashboard response time exceeds 20 seconds.

Business Impact:
High

Severity:
SEV-2
```

---

## Incident 003 - Duplicate Volunteer Records

```text
Reporting inaccuracies detected.

Business Impact:
Moderate

Severity:
SEV-3
```

---

## Incident 004 - API Timeout

```text
Registrations intermittently failing.

Business Impact:
High

Severity:
SEV-2
```

---

# Incident Lifecycle

```text
Incident Identified
        |
        v
Severity Assigned
        |
        v
Investigation Started
        |
        v
Root Cause Identified
        |
        v
Resolution Implemented
        |
        v
Validation Completed
        |
        v
Incident Closed
        |
        v
Post-Incident Review
```

---

# Success Metrics

Support teams should track:

- Incident Volume
- Mean Time to Detection (MTTD)
- Mean Time to Resolution (MTTR)
- Escalation Rate
- Reopened Incidents
- Service Availability
- SLA Compliance

---

# Lessons Learned Template

```text
Was the incident severity assigned correctly?

Was escalation performed appropriately?

Were communications timely?

Were response objectives met?

How can future incidents be handled more effectively?
```

---

# Skills Demonstrated

- Incident Management
- Production Support
- IT Service Management
- Operations Support
- Escalation Management
- Root Cause Analysis
- Risk Assessment
- Service Restoration
- Technical Documentation
- Systems Operations
- SLA Management
- Application Support
