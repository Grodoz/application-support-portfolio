# Incident 003 - Duplicate Volunteer Records Causing Reporting Inaccuracies

## Incident Information

| Field | Value |
|---------|---------|
| Incident ID | INC-003 |
| Severity | High |
| Status | Resolved |
| Environment | Production |
| Application | Volunteer Management System |
| Date Opened | 2026-11-24 |
| Date Resolved | 2026-11-24 |

---

## Portfolio Disclaimer

> [!IMPORTANT]
> This incident report is a simulated troubleshooting exercise created for professional portfolio purposes.
>
> The scenario, application, users, logs, database records, timelines, SQL queries, and technical artifacts are fictional and intended solely to demonstrate:
>
> - Application Support
> - Data Analysis
> - SQL Troubleshooting
> - Root Cause Investigation
> - Production Support
> - Incident Management
> - Technical Documentation
>
> No confidential, proprietary, or employer-owned information has been used.

---

## Executive Summary

Volunteer coordinators reported discrepancies in attendance reports and volunteer participation metrics.

Several volunteers appeared multiple times in system reports despite representing the same individual.

Investigation revealed duplicate volunteer records were being created when the registration API received repeated submissions due to temporary network latency.

The database lacked a uniqueness constraint on volunteer email addresses, allowing duplicate records to be created under certain conditions.

Database cleanup activities were performed and validation rules were implemented to prevent recurrence.

---

## Business Impact

### User Impact

- Volunteer participation reports inaccurate.
- Attendance totals overstated.
- Volunteer hours duplicated.
- Coordinators unable to trust reporting data.

### Business Impact

- Reporting inaccuracies.
- Reduced confidence in system data.
- Additional administrative effort.
- Risk of incorrect operational decisions.

---

## Initial Symptoms

### User Reports

```text
"Volunteer counts seem unusually high."

"The same volunteer appears multiple times."

"Attendance reports do not match sign-in records."
```

---

## Monitoring Observations

### Data Quality Dashboard Alert

```text
Alert ID: DQ-101

Alert Type: Duplicate Volunteer Records

Current Value: 112

Threshold: 10

Severity: HIGH
```

---

## Investigation Timeline

### 08:00 AM

Incident assigned to Application Support.

### 08:10 AM

Issue reproduced using reporting dashboard.

**Observation**

Several volunteers appeared multiple times with identical names and email addresses.

### 08:20 AM

Initial database investigation started.

### 08:30 AM

Duplicate records confirmed.

### 08:45 AM

API logs reviewed.

### 09:00 AM

Root cause identified.

### 09:15 AM

Data correction plan approved.

### 09:40 AM

Records merged and corrected.

### 10:00 AM

Validation testing completed.

### 10:15 AM

Incident closed.

---

## Database Investigation

### Initial Query

```sql
SELECT
    email_address,
    COUNT(*)
FROM volunteers
GROUP BY email_address
HAVING COUNT(*) > 1;
```

### Results

| Email Address | Duplicate Count |
|---------------|-----------------|
| john.smith@email.org | 2 |
| mary.jones@email.org | 3 |
| donna.adams@email.org | 2 |

### Observation

Multiple volunteer records existed for the same email address.

---

## Data Analysis

### Sample Volunteer Records

| Volunteer ID | First Name | Last Name | Email Address |
|--------------|------------|-----------|--------------|
| 1045 | John | Smith | john.smith@email.org |
| 1188 | John | Smith | john.smith@email.org |

### Observation

Identical volunteer information existed in separate records.

---

## Application Log Review

### File: application.log

```text
2026-11-24 07:54:02 INFO

Registration Request Received

Email: john.smith@email.org

Request ID: REG-44018
```

```text
2026-11-24 07:54:03 INFO

Registration Saved Successfully

Volunteer ID: 1045
```

```text
2026-11-24 07:54:08 INFO

Registration Request Received

Email: john.smith@email.org

Request ID: REG-44022
```

```text
2026-11-24 07:54:09 INFO

Registration Saved Successfully

Volunteer ID: 1188
```
