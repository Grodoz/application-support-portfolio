# Incident 004 - Intermittent API Timeouts Impacting Volunteer Registration

## Incident Information

| Field | Value |
|---------|---------|
| Incident ID | INC-004 |
| Severity | High |
| Status | Resolved |
| Environment | Production |
| Application | Volunteer Management System |
| Date Opened | 2026-12-03 |
| Date Resolved | 2026-12-03 |

---

## Portfolio Disclaimer

> [!IMPORTANT]
> This incident report is a simulated troubleshooting exercise created for professional portfolio purposes.
>
> The application, infrastructure, users, logs, monitoring alerts, and technical details described in this document are fictional and intended solely to demonstrate:
>
> - Application Support
> - API Troubleshooting
> - Incident Management
> - Root Cause Analysis
> - Performance Analysis
> - Monitoring and Alerting
> - Technical Documentation
>
> No confidential, proprietary, or employer-owned information has been used.

---

## Executive Summary

Multiple users reported intermittent failures while registering for volunteer events.

Some users received timeout errors, while others experienced long wait times before receiving responses.

Investigation determined that the Volunteer Registration API was waiting on a third-party email notification service before returning a response to the user.

During periods of increased registration volume, the email service experienced latency spikes that caused API requests to exceed the application timeout threshold.

The notification process was moved to an asynchronous queue, restoring normal application performance and eliminating timeout errors.

---

## Business Impact

### User Impact

- Volunteers unable to complete registrations.
- Registration confirmations delayed.
- Users submitted duplicate requests.
- Increased user frustration and support calls.

### Business Impact

- Event sign-up participation reduced.
- Duplicate registrations created.
- Support workload increased.
- Potential loss of volunteer engagement.

---

## Initial Symptoms

### User Reports

```text
"Registration just spins and never finishes."

"I clicked Register and got an error."

"I tried three times before it worked."

"I received multiple confirmation emails."
```

### Monitoring Alert

```text
ALERT ID: API-204

Service:
Volunteer Registration API

Metric:
Response Time

Current Value:
32.4 Seconds

Threshold:
5 Seconds

Severity:
HIGH
```

---

## Investigation Timeline

### 09:05 AM

Incident assigned to Application Support.

### 09:10 AM

Issue successfully reproduced.

### 09:15 AM

Application server health reviewed.

### 09:20 AM

Database performance reviewed.

### 09:30 AM

API logs analyzed.

### 09:40 AM

Third-party integration investigated.

### 09:50 AM

Root cause identified.

### 10:20 AM

Mitigation deployed.

### 10:45 AM

Performance validated.

### 11:00 AM

Incident closed.

---

## Application Health Review

### Application Server Metrics

```text
Application Availability:
100%

CPU:
34%

Memory:
52%

Disk Utilization:
41%
```

### Observation

No resource constraints detected.

---

## Database Review

### Database Health

```text
Database Status:
Online

CPU:
38%

Average Query Time:
180 ms

Failed Connections:
0
```

### Observation

Database was operating normally.

---

## API Monitoring Review

### Registration Endpoint Performance

```text
Endpoint

POST /api/volunteers/register
```

### Response Metrics

| Metric | Normal | Current |
|----------|----------|----------|
| Average Response Time | 850 ms | 32.4 sec |
| Error Rate | 0.3% | 14.8% |
| Request Volume | 450/hr | 470/hr |
| Timeout Count | 0 | 67 |

### Observation

Response times dramatically exceeded expected thresholds.

---

## Application Log Analysis

### File: application.log

```text
2026-12-03 09:06:11 INFO

Registration request received

Volunteer ID:
Pending

Request ID:
REQ-99172
```

```text
2026-12-03 09:06:11 INFO

Invoking notification service
```

```text
2026-12-03 09:06:41 ERROR

Request timeout exceeded

Maximum Timeout:
30 seconds

Request ID:
REQ-99172
```

---

## API Gateway Logs

### File: api-gateway.log

```text
2026-12-03 09:06:41

HTTP 504 Gateway Timeout

Endpoint:
/api/volunteers/register

Duration:
30001 ms
```

---

## Error Frequency Analysis

### Last 60 Minutes

```text
Successful Registrations:
403

Failed Registrations:
67

Timeout Errors:
67
```

### Observation

Failure pattern appeared specific to timeout events.

---

## Integration Analysis

### Registration Workflow

```text
User Registration Request
       |
       v
Volunteer API
       |
       v
Database Save
       |
       v
Email Notification Service
       |
       v
Response Returned To User
```

### Observation

API waited for email delivery before returning a response.

---

## Third-Party Notification Logs

### File: email-service.log

```text
2026-12-03 09:05:52

Message Submitted

Processing Time:
21.8 seconds
```

```text
2026-12-03 09:06:17

Message Submitted

Processing Time:
24.3 seconds
```

```text
2026-12-03 09:06:33

Message Submitted

Processing Time:
28.7 seconds
```

### Observation

Email service latency increased significantly.

---

## Root Cause Analysis

### Primary Root Cause

The Volunteer Registration API performed synchronous notification processing.

The API waited for the email notification provider to complete processing before returning a response.

When email processing slowed, API requests exceeded the 30-second timeout threshold.

---

## Contributing Factors

### Factor 1

Synchronous notification processing.

### Factor 2

No retry queue architecture.

### Factor 3

No circuit breaker protection.

### Factor 4

Insufficient monitoring of third-party service latency.

---

## Resolution

### Previous Workflow

```text
User Request
    ↓
Save Volunteer
    ↓
Send Email
    ↓
Wait
    ↓
Return Response
```

---

### Updated Workflow

```text
User Request
    ↓
Save Volunteer
    ↓
Write Message To Queue
    ↓
Return Response
    ↓
Background Worker Sends Email
```

---

## Mitigation Actions

1. Notification processing moved to asynchronous queue.
2. Background worker implemented.
3. API timeout monitoring enhanced.
4. Additional alerting configured.
5. Dashboard updated with third-party latency metrics.

---

## Validation Testing

### Test 1

Volunteer Registration

Expected Result:

```text
Registration completed successfully.
```

Result:

```text
PASS
```

---

### Test 2

Confirmation Email

Expected Result:

```text
Email delivered.
```

Result:

```text
PASS
```

---

### Test 3

500 Concurrent Registrations

Expected Result:

```text
No timeout failures.
```

Result:

```text
PASS
```

---

### Test 4

Email Service Delay Simulation

Expected Result:

```text
Registration succeeds despite email delay.
```

Result:

```text
PASS
```

---

## Performance Improvements

### Before Resolution

```text
Average Response Time:
32.4 seconds

Error Rate:
14.8%

Timeout Errors:
67
```

### After Resolution

```text
Average Response Time:
0.72 seconds

Error Rate:
0.2%

Timeout Errors:
0
```

---

## Monitoring Enhancements

### New Alerts

```text
API Response Time > 5 seconds

API Error Rate > 5%

Third-Party Latency > 10 seconds

Message Queue Backlog > 500 Messages
```

### New Dashboard Metrics

```text
Average API Response Time

HTTP 5xx Rate

Queue Length

Email Processing Time

Timeout Error Count
```

---

## Engineer Investigation Notes

```text
09:05 AM - Incident assigned

09:10 AM - Issue reproduced

09:15 AM - Application review completed

09:20 AM - Database review completed

09:30 AM - API logs analyzed

09:40 AM - Integration bottleneck identified

09:50 AM - Root cause confirmed

10:20 AM - Queue solution implemented

10:45 AM - Validation testing completed

11:00 AM - Incident resolved
```

---

## Corrective Actions

| Action | Owner | Status |
|----------|----------|----------|
| Implement asynchronous processing | Development Team | Complete |
| Add API latency monitoring | Operations Team | Complete |
| Configure timeout alerts | Monitoring Team | Complete |
| Update architecture documentation | Support Team | Complete |

---

## Preventive Actions

| Action | Owner | Status |
|----------|----------|----------|
| Quarterly integration review | Architecture Team | Open |
| Third-party SLA monitoring | Operations Team | Open |
| Load testing before releases | QA Team | Open |
| Queue health monitoring | Operations Team | Open |

---

## Lessons Learned

- User-facing APIs should not depend on slow external services.
- Third-party integrations require dedicated monitoring.
- Asynchronous processing improves resiliency.
- Latency issues can manifest as application failures.
- Observability is critical for identifying integration bottlenecks.

---

## Skills Demonstrated

- Application Support
- API Troubleshooting
- Root Cause Analysis
- Performance Analysis
- Monitoring and Alerting
- Log Analysis
- Systems Thinking
- Incident Management
- Service Integration Analysis
- Technical Documentation
- Production Support
- Problem Resolution
