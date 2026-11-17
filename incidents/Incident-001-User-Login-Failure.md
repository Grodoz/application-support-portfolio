# Incident 001 - Widespread User Login Failures Following Deployment

## Incident Information

|Field|Value|
|-------- |-------- |
| Incident ID | INC-001 |
| Severity | High |
| Status | Resolved |
| Environment | Production |
| Application | Healthcare Enrollment Portal |
| Date Opened | 2026-11-17 |
| Date Resolved | 2026-11-17|

---

# Executive Summary
Following a weekend application deployment, users began reporting authentication failures when attempting to access the Healthcare Enrollment Portal.

Investigation determined the application was operating normally, database systems were available, and user records remined intact.  A review of authentication logs revealed a mismatch between the password hashing algorithm used by the newly deployed authentication service and the password hashes stored in the production database.

The authentication service was rolled back to the previous version, restoring access to all affected users.

---

#Business Impact

## User Impact
- Users unable to access the healthcare enrollment portal
- Delayed enrollment activity
- Increased support call volume
- Interrupted access to self-service functionality

## Business Impact
- Potential enrollment processing delays
- Increased workload for support personnel
- Elevated operational risk during enrollment period
- Reduced customer satisfaction

---

# Initial Symptoms

## User Reports

Users reported receiving the following message after login attempts:

```text
Invalid Username or Password
```

## Monitoring Status

| Component | Status |
|----------- | ----------|
| Application Servers | Healthy |
| Database Servers | Healthy |
| Network Connectivity | Healthy |
| REST APIs | Healthy |
| Infrastructure Monitoring | No Alerts |

---

# Investigation Timeline

## 08:10 AM - Incident Reported

Service Desk escalated multiple authentication failures impacting production users.

---

## 08:15 AM - Scope Assessment

Questions investigated:
- Is the issue isolated to one user?
- Is the issue isolated to one region?
- Did the issue begin after a recent deployment?

### Findings

- Multiple user affected
- Multiple locations affected
- Issue began shortly after weekend release

### Conclusion

Likely application-related issue rather than isolated user error.

---

## 08:20 AM - Infrastrucutre Verification

### Web Server Check

```text
Server Status: RUNNING
CPU Usage: 22%
Memory Usage: 48%
Disk Space Available: 61%
```

### Database Health Check

```sql
SELECT status
FROM system_health;
```

**RESULT**
```text
ONLINE
```

### Conclusion

Infrastructure operating normally.

---

