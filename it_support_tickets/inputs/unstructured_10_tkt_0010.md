# IT SUPPORT TICKET — DETAILED CASE FILE

---

## TICKET HEADER

```
╔════════════════════════════════════════════════════════════════╗
║  TICKET ID: TKT-2024-0010                                      ║
║  STATUS: CLOSED                                                ║
║  CREATED: 2024-01-17 07:55:19                                 ║
║  CLOSED: 2024-01-17 11:48:32                                  ║
╚════════════════════════════════════════════════════════════════╝
```

---

## SUBMITTER INFORMATION

| Field | Value |
|-------|-------|
| Name | Sabine Keller |
| Email | s.keller@stadtverwaltung.de |
| Phone | +49 30 9026 3123 |
| Department | Schulamt |
| Location | Schulamt Pankow |

---

## ISSUE SUMMARY

**Title:** Cannot send emails with attachments

**Category:** Email  
**Priority:** Medium

---

## USER'S DESCRIPTION

> Outlook allows me to send regular emails fine but any email with attachment fails. Error message: 'The operation failed. An object could not be found.' Attachments are normal PDFs and Word docs under 5MB.

---

## TECHNICAL DETAILS PROVIDED

The user provided the following diagnostic information:

- **Error behavior:** Occurs immediately when clicking Send
- **Outlook version:** 2019 (16.0.10396.20029)
- **PST file size:** 8.2GB
- **Email account type:** Exchange
- **File types tested:** PDF, DOCX, XLSX — all fail
- **Receiving attachments:** Works fine

---

## ENVIRONMENT

| Component | Details |
|-----------|---------|
| Operating System | Windows 10 Pro |
| Primary Software | Outlook 2019 |
| Hardware | Lenovo ThinkPad T14 |
| IP Address | 192.168.10.221 |

---

## TROUBLESHOOTING LOG

### Step 1: Initial Remote Diagnosis

**Technician:** Sarah Klein  
**Time:** 10:37:15

Connected remotely to user's workstation. Verified issue reproducible:

```
Test 1: Send email without attachment → SUCCESS
Test 2: Send email with small PNG (50KB) → FAILED
Test 3: Send email with PDF (2MB) → FAILED
Error: "The operation failed. An object could not be found."
```

### Step 2: Outlook Diagnostics

Checked Outlook configuration and logs:

- OST/PST file size: 8.2GB (within limits but large)
- Outlook profile: Single profile, no corruption indicators
- Add-ins: Disabled all third-party add-ins → Problem persists
- Safe mode test: `outlook.exe /safe` → Problem persists

### Step 3: PST File Analysis

Ran Microsoft Support and Recovery Assistant (SaRA):

```
Results:
- Email send/receive: PARTIAL FAILURE
- Calendar sync: OK
- Contacts: OK
- Attachment handling: FAILED
```

**Diagnosis:** Possible PST file corruption

### Step 4: PST Repair

Executed Inbox Repair Tool (ScanPST.exe):

```
Location: C:\Program Files\Microsoft Office\root\Office16\SCANPST.EXE
File scanned: C:\Users\skeller\Documents\Outlook Files\skeller.pst

Results:
- Errors found in file: YES
- Repair status: Minor corruption fixed
- Backup created: skeller.pst.bak
```

### Step 5: Profile Rebuild

After repair, rebuilt Outlook profile:

1. Created new Outlook profile
2. Re-added Exchange account
3. Allowed OST to resynchronize
4. Tested attachment sending → **SUCCESS**

---

## RESOLUTION

| Metric | Value |
|--------|-------|
| Time to First Response | 2.7 hours |
| Total Resolution Time | 3.9 hours |
| Escalated | No |
| Recurring Issue | No |
| User Satisfaction Rating | 4/5 |

**Resolution Notes:**

PST file corruption identified. Ran ScanPST.exe repair tool. Minor corruption fixed. Outlook profile rebuilt. Attachment sending now functional.

---

## USER CONFIRMATION

```
From: Sabine Keller
To: IT-Support
Date: 2024-01-17 11:52:04
Subject: RE: Ticket TKT-2024-0010 - Resolved

Hallo Frau Klein,

vielen Dank für die schnelle Hilfe! Das Versenden von Anhängen 
funktioniert jetzt wieder einwandfrei.

Beste Grüße,
Sabine Keller
```

---

## TICKET CLOSURE

**Closed by:** Sarah Klein  
**Date:** January 17, 2024  
**Time:** 11:48:32

**Knowledge Base Article Created:** KB-2024-0089 — "Outlook Attachment Failures Due to PST Corruption"

---

*End of case file*

