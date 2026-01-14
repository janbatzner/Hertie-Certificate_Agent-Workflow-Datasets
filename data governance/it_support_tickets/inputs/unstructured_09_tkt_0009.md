# TECHNICAL INVESTIGATION REPORT

---

## Account Lockout Analysis

**Ticket Reference:** TKT-2024-0009  
**Investigation Date:** January 16-17, 2024  
**Investigator:** Michael Koch, IT Security

---

## USER INFORMATION

| Field | Value |
|-------|-------|
| User | Robert Neumann |
| Email | r.neumann@stadtverwaltung.de |
| Phone | +49 30 9026 2789 |
| Department | Personalamt |
| Location | Personalamt Kreuzberg |
| Workstation | Dell OptiPlex 5090 |
| User IP | 192.168.10.145 |

---

## PROBLEM STATEMENT

User reports repeated account lockouts occurring every few hours. The user must contact the helpdesk to unlock the account each time, causing significant work disruption. Password was changed yesterday, but the problem persists.

---

## INVESTIGATION DETAILS

### Initial Assessment

**Priority:** High  
**Time Received:** January 16, 2024, 14:27:51  
**First Response:** January 16, 2024, 16:14:23  
**Time to First Response:** 1.8 hours

### Active Directory Policy Review

```
Account Lockout Threshold: 5 failed attempts
Account Lockout Duration: 30 minutes
Reset Account Lockout Counter: 30 minutes
```

### Security Event Log Analysis

Extracted failed login attempts from Domain Controller logs:

```
Event ID: 4771 - Kerberos pre-authentication failed
Account: r.neumann
Client Address: 192.168.10.234
Failure Code: 0x18 (Bad password)

Timestamps:
- 2024-01-16 08:12:44
- 2024-01-16 08:12:45
- 2024-01-16 08:12:46
- 2024-01-16 08:12:47
- 2024-01-16 08:12:48
>>> ACCOUNT LOCKED <<<

[Pattern repeats approximately every 2 hours]
```

### Key Finding

**ANOMALY DETECTED:**

The failed login attempts are originating from IP address **192.168.10.234**, which is **NOT** the user's workstation (192.168.10.145).

This suggests another device or service is attempting to authenticate with old/incorrect credentials.

---

## ROOT CAUSE INVESTIGATION

### Device Identification

IP 192.168.10.234 resolved to: `conference-room-pc-kr.stadtverwaltung.local`

This is a shared computer in the Personalamt conference room.

### Credential Manager Audit

Upon examination of the user's primary workstation:

**Windows Credential Manager findings:**

```
Credential Type: Windows Credentials
Target: \\fileserver02\hr_documents
Username: STADT\r.neumann
Stored: 2023-09-15
>>> OLD PASSWORD STORED <<<
```

### Mobile Device Investigation

The user also has a corporate mobile device (iPhone 13) configured for email access.

**ActiveSync logs show:**

```
Device ID: ApplXXXXXXXX
Last Sync Attempt: 2024-01-16 14:25:00
Authentication: FAILED
Reason: Invalid credentials
```

The mobile device still had the old password cached.

---

## REMEDIATION STEPS

1. ✅ Cleared stored credentials from Windows Credential Manager on user workstation
2. ✅ Removed old credentials from conference room PC (192.168.10.234)
3. ✅ Updated password on user's mobile device
4. ✅ Performed network-wide scan for other devices with cached credentials
5. ✅ Unlocked account after remediation

---

## RESOLUTION

**Status:** CLOSED  
**Total Resolution Time:** 8.3 hours  
**User Satisfaction:** 3/5 (user frustrated by extended disruption)

**Resolution Notes:**

Found old credential stored in Windows Credential Manager from previous file share. Also mobile device with outdated password. Cleared credentials and updated mobile device. No further lockouts reported.

### Recommendations for Future

- Implement automated alerts for repeated lockouts from non-primary devices
- Consider extending password change grace period for cached credentials
- Document all user devices at onboarding for credential management

---

**Case Closed:** January 17, 2024  
**Technician:** Michael Koch

