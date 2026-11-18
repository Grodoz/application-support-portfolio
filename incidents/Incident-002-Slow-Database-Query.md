# Incident 002 - Severe Database Performance Degradation Caused by Inefficient SQL Query

## Incident Information

Incident ID: INC-002

Severity: High

Status: Resolved

Environment: Production

Application: Volunteer Management System

Date Opened: 2026-11-19

Date Resolved: 2026-11-19

---

## Portfolio Disclaimer

This incident report is a simulated troubleshooting exercise created for professional portfolio purposes.

The scenario, application, users, logs, database records, timelines, and technical artifacts are fictional and intended solely to demonstrate:

- Application Support
- SQL Troubleshooting
- Performance Analysis
- Root Cause Investigation
- Technical Documentation

No confidential, proprietary, or employer-owned information has been used.

---

# Executive Summary

Users reported unusually slow response times while accessing the Volunteer Participation Dashboard.

Page load times increased from approximately 2 seconds to more than 20 seconds.

Investigation revealed a reporting query performing a full table scan against a rapidly growing participation_history table containing over 2 million records.

A targeted index was implemented, reducing query execution time by more than 95 percent and restoring normal system performance.

---

# Business Impact

## User Impact

- Dashboard response times exceeded acceptable thresholds
- Volunteer coordinators were unable to generate reports efficiently
- Users experienced application timeouts during peak periods

## Business Impact

- Increased support requests
- Delayed operational reporting
- Decreased productivity for volunteer coordinators
- Potential loss of confidence in system reliability

---

# Initial Symptoms

## User Reports

```text
"The volunteer dashboard takes forever to load."

"Participation reports are timing out."

"The system worked fine last month."
```

## Monitoring Alert

```text
ALERT ID: DB-PERF-101

Average Query Duration: 22.4 seconds
Alert Threshold: 5.0 seconds

Severity: HIGH
```

## Performance Metrics

```text
Dashboard Load Time

Normal: 2.1 seconds
Current: 23.4 seconds

Database CPU

Normal: 35%
Current: 94%
```

---

# Investigation Timeline

## 08:15 AM

Incident assigned to Application Support.

## 08:20 AM

Issue reproduced successfully.

Navigation Path:

```text
Dashboard
  ↓
Volunteer Reports
  ↓
Participation Summary
```
x
Observed Result:

```text
23-second page load time
```

---

## 08:25 AM

Application infrastructure reviewed.

Application Server Statistics:

```text
Status: Healthy

CPU Usage: 28%

Memory Utilization: 51%

Disk Utilization: 44%
```

No infrastructure concerns identified.

---

## 08:30 AM

Network connectivity validated.

```text
Latency: Normal

Packet Loss: None

Bandwidth Utilization: Normal
```

No network issues identified.

---

## 08:35 AM

Database monitoring reviewed.

```text
Database CPU: 94%

Database Memory: 88%

Database Availability: Healthy
```

Database performance became primary focus.

---

# Log Analysis

## Application Log

File: application.log

```text
2026-11-19 08:22:31 INFO

Participation Report Requested

User:
coordinator@test.org

Report:
Volunteer Participation Dashboard
```

```text
2026-11-19 08:22:54 WARN

Query execution exceeded threshold.

Execution Time: 22398 ms

Threshold: 5000 ms
```

```text
2026-11-19 08:22:54 WARN

Performance degradation detected.
```

Observations:

- Application functioning normally
- Long-running database queries detected
- No application crashes observed

---

## Database Log

File: database.log

```text
2026-11-19 08:22:31

LONG-RUNNING QUERY DETECTED

Query Duration:
22398 ms

Database:
VolunteerVMS_Prod
```

```text
2026-11-19 08:22:32

CPU WARNING

Current CPU:
94%

Threshold:
80%
```

Observation:

Performance issue appears isolated to a database query.

---

# SQL Investigation

## Problem Query

```sql
SELECT
    volunteer_id,
    COUNT(*) AS total_events,
    SUM(hours_s*rved) AS total_hours
FROM particip*tion_history
GROUP BY volunteer_id*ORDER BY total_hours DESC;
```

---

# Execution Statistics

## Before Optimization

```text
Execution T*me:
22.4 seconds

Rows Examined:
2*187,445

Rows Returned:
12,341

Database CPU:
94%

Logical Reads:
1,4*0,000
```

---

# Execution Plan Analysis

Execution Plan Findings

```text
Operation:
TABLE SCAN

Table:
participation_history

Estimated Cost:
89%
```

Observation:

The database was scanning the entire table.

No index existed on volunteer id.
---

# Database Growth Analysis

Table Record Count:

```sql
SELECT COUNT(*)
FROM participation_history;
```

Result:

```text
2,187,445 records
```

Historical Growth:

```text
January 2026 :  850,000

June 2026   : 1,350,000

November 2026: 2,187,445
```

Finding:

The table more than doubled in size within one year.

---

# Root Cause Analysis

## Root Cause

A frequently executed dashboard query *as performing* a full table scan because no index existed on the volunteer_id column.

As the dataset grew, performance degraded significantly.

---

## Contributing Factors

1. Rapid growth in participation_history records
2. Lack of query performance monitoring
3. Missing indexing strategy
4. No performance testing against production-sized data.

---

# Resolution

## Create Supporting Index

```sql
CREATE INDEX IX_PARTICIPATION_HISTORY_VOLUNTEER
ON participation_history (volunteer_id);
```

---

##*Update Statistics

```sql
UPDATE STATISTICS participation_history;
```

---

## Retest Query

```sql
SELECT
    volunteer_id,
    COUNT(*) AS total_events,
    SUM(hours_served) AS total_hours
FROM participation_history
GROUP BY volunteer_id
OR*ER BY total_hours DESC;
```

---

# Performance Improvements

## Before Optimization

```text
Query Execution Time:
22.4 seconds

Database CPU:
94%
```

## After Optimization
```text
Query Execution Time:
0.8 seconds

Database CPU:
37%
```

## Improvement Summary

```text
Execution Time Improvement:
96%

CPU Reduction:
57%

Logical Reads Reduction:
96.9%
```

---

# Validation Testing

## Test 1

Generate Volunteer Participation Dashboard

Result:
```text
PASS
```

---

## Test 2

Search Volunteer History

Result:

```text
PASS
```

---

## Test 3

Export Volunteer Report

Result:

```text
PASS
```

---

## Test 4

Concurrent Dashboard Access

20 simultateous users tested.

Result:

```text
PASS
```

---

# Monitoring Enhancements

New alert thresholds implemented:

```text
Slow Query Threshold:
5 seconds

Database CPU Threshold:
80%

Table Scan Alert:
Enabled

Long Running Query Alert:
Enabled
```

New dashboard metrics added:

```text
Top 10 Longest Running Queries

Average Query Duration

Database CPU Utilization

Missing Index Recommendations
```

---
# Engineer Investigation Notes

```text
08:15 AM - Incident assigned
08:20 AM - Issue reproduced

08:2* AM - Infrastructure validated

08*30 AM - Database CPU spike identified

08:40 AM - Slow query isolated

08:50 AM - Execution plan reviewed

09:00 AM - Missing index identified

09:12 AM - Index created

09:20 AM - Statistics updated

09:25 AM - Query retested

09:30 AM - Performance restored

09:40 AM - Incident closed
```

---

# Corrective Actions

1. Create supporting database index
2. Update database statistics
3. Validate application functionality
4. Document findings

Status: Complete

---

# Preventive Actions

1. Quarterly index review process
2. Automated slow-query monitoring
3. Annual performance testing
4. Database growth tracking
5. Monthly performance reporting

Status: Open

---

# Lessons Learned

- Database growth can significantly impact application performance.
- High-frequency queries should be reviewed regularly.
- Indexing strategy must evolve with data volume.
- Monitoring should detect degradation before users report issues.
- Production-sized datasets should be included in performance testing.

---

# Skills Demonstrated

- Application Support
- SQL Troubleshooting
- Database Performance Analysis
- Query Optimization
- Root Cause Analysis
- Incident Management
- Log Analysis
- Execution Plan Review
- Database Monitoring
- Performance Testing
- Technical Documentation
- Production Support
