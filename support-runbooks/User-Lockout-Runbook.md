# User Lockout Runbook

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
> The systems, users, security controls, logs, account lockout rules, monitoring alerts, and troubleshooting procedures described in this document are intended solely to demonstrate:
>
> - Application Support
> - Identity and Access Management
> - User Account Administration
> - Incident Response
> - Root Cause Analysis
> - Technical Documentation
>
> No proprietary, confidential, or employer-owned information has been used.

---

# Purpose

This runbook provides Application Support personnel with a standardized process for investigating and resolving user account lockouts.

The goals are to:

- Restore user access quickly
- Protect system security
- Determine root cause
- Prevent recurring lockouts
- Improve user experience

---

# Incident Classification

| Severity | Description |
|-----------|-------------|
| SEV-1 | All users unable to authenticate |
| SEV-2 | Multiple users affected |
| SEV-3 | Single user affected |
| SEV-4 | Self-service password reset issue |

---

# Symptoms

Users may report:

- Unable to log in
- Account locked message
- Password reset not working
- Authentication failures
- Unexpected access denial

Common user messages:

```text
Your account has been locked.

Please contact support.
```

```text
Maximum login attempts exceeded.
```

```text
Account temporarily disabled.
```

```text
Authentication failed.
```

---

# Initial Response Procedure

## Step 1 - Gather Information

Collect the following:

```text
Username

Email Address

Date and Time of Lockout

Last Successful Login

Error Message Received

Device Used

Location
```

Example:

```text
Username:
john.smith

Email:
john.smith@email.org

Error:
Account locked due to excessive login attempts
```

---

# Step 2 - Determine Scope

Questions to Ask

```text
Is only one user affected?

Are multiple users affected?

Did the issue occur after a password change?

Did the issue begin following a deployment?

Were there recent security changes?
```

If multiple users are affected:

```text
Escalate to SEV-2 investigation.
```

---

# User Lockout Decision Tree

```text
User Cannot Login
        |
        v
Account Locked?
        |
    +---+---+
    |       |
   Yes      No
    |       |
    v       v
Review     Investigate
Lockout    Authentication
Events     Failures
    |
    v
Determine Root Cause
    |
    v
Unlock Account
    |
    v
Validate Access
```

---

# Step 3 - Verify Account Status

## Database Validation

Example Query

```sql
SELECT
    username,
    account_status,
    failed_login_count,
    last_failed_login,
    lockout_timestamp
FROM users
WHERE username = 'john.smith';
```

Expected Output

```text
Username: john.smith

Account Status: LOCKED

Failed Login Count: 5

Lockout Timestamp:
2026-11-15 08:44:13
```

---

# Step 4 - Review Authentication Logs

File:

```text
authentication.log
```

Example Lockout Event

```text
2026-11-15 08:44:13 WARN

Authentication Failure

Username:
john.smith

Failed Attempt:
5

Result:
ACCOUNT_LOCKED
```

---

## Verify Failed Login Attempts

```text
Attempt 1 - Incorrect Password

Attempt 2 - Incorrect Password

Attempt 3 - Incorrect Password

Attempt 4 - Incorrect Password

Attempt 5 - Incorrect Password

Account Locked
```

---

# Step 5 - Identify Root Cause

## Root Cause 1

### Forgotten Password

Indicators

```text
Multiple failed login attempts.

No suspicious activity.
```

Resolution

```text
Reset password.

Unlock account.
```

---

## Root Cause 2

### Password Recently Changed

Indicators

```text
User updated password.

Mobile device still using old credentials.
```

Resolution

```text
Update credentials on all devices.
```

---

## Root Cause 3

### Browser Autofill Issue

Indicators

```text
Stored password differs from current password.
```

Resolution

```text
Clear stored credentials.

Retry login.
```

---

## Root Cause 4

### Mobile Device Authentication Loop

Indicators

```text
Repeated login attempts from mobile application.
```

Example Log

```text
Device:
Android

Attempts:
42

Duration:
7 Minutes
```

Resolution

```text
Remove saved credentials.

Reauthenticate device.
```

---

## Root Cause 5

### Security Attack

Indicators

```text
Multiple failed attempts

Unknown IP Address

Multiple accounts targeted
```

Resolution

```text
Escalate to Security Team immediately.
```

Minimum Severity

```text
SEV-2
```

---

# Step 6 - Unlock Account

## Administrative Action

Example SQL

```sql
UPDATE users
SET
    account_status = 'ACTIVE',
    failed_login_count = 0,
    lockout_timestamp = NULL
WHERE username = 'john.smith';
```

---

## Verification Query

```sql
SELECT
    username,
    account_status
FROM users
WHERE username = 'john.smith';
```

Expected Result

```text
Account Status:
ACTIVE
```

---

# Step 7 - Validate Login

Testing Procedure

```text
1. User enters username.
2. User enters password.
3. Authentication request submitted.
```

Expected Result

```text
Login Successful
```

---

# Monitoring and Alerting

## Failed Login Threshold

Alert Trigger

```text
25 failed logins
within 5 minutes
```

Severity

```text
HIGH
```

---

## Account Lockout Threshold

Alert Trigger

```text
10 lockouts
within 15 minutes
```

Severity

```text
HIGH
```

---

## Security Alert

Alert Trigger

```text
Lockouts affecting
multiple user accounts
```

Severity

```text
CRITICAL
```

---

# Common Support Scenarios

## Scenario 1

Forgot Password

Severity

```text
SEV-3
```

Resolution Time Target

```text
15 Minutes
```

---

## Scenario 2

Password Change Not Updated

Severity

```text
SEV-3
```

Resolution Time Target

```text
15 Minutes
```

---

## Scenario 3

Authentication Service Failure

Severity

```text
SEV-1
```

Resolution Time Target

```text
Immediate
```

---

## Scenario 4

Potential Brute Force Attack

Severity

```text
SEV-2
```

Resolution Time Target

```text
30 Minutes
```

---

# Escalation Matrix

| Condition | Escalation Team |
|------------|----------------|
| Single User Lockout | Application Support |
| Multiple User Lockouts | Support Manager |
| Authentication System Failure | Operations Team |
| Suspected Security Event | Security Team |
| Database Authentication Failure | DBA Team |

---

# Resolution Validation Checklist

## Account Status

Expected Result

```text
ACTIVE
```

Status

```text
PASS
```

---

## Failed Login Counter Reset

Expected Result

```text
0
```

Status

```text
PASS
```

---

## Successful Login Test

Expected Result

```text
User authenticated
```

Status

```text
PASS
```

---

## No Active Alerts

Expected Result

```text
No alerts generated
```

Status

```text
PASS
```

---

# Post-Incident Documentation

Capture:

```text
Incident Number

Affected User

Root Cause

Resolution Steps

Duration

Follow-Up Actions
```

Example

```text
Incident ID:
INC-005

Affected User:
john.smith

Root Cause:
Password changed,
mobile device retained old credentials

Resolution:
Removed stored credentials
and unlocked account

Resolution Time:
12 Minutes
```

---

# Lessons Learned Template

```text
What caused the lockout?

Could monitoring have detected it earlier?

Was the resolution process followed?

Is additional training needed?

Should monitoring rules be updated?
```

---

# Preventive Actions

1. Enable self-service password reset.
2. Implement user notification before lockout.
3. Provide password expiration reminders.
4. Monitor repeated failed login attempts.
5. Conduct periodic authentication reviews.

---

# Skills Demonstrated

- Application Support
- Identity and Access Management
- Authentication Troubleshooting
- Incident Management
- SQL Investigation
- Log Analysis
- Root Cause Analysis
- Security Awareness
- User Administration
- Production Support
- Monitoring and Alerting
- Technical Documentation
