# IT SECURITY INCIDENT REPORT

---

## ALERT — PHISHING ATTEMPT DETECTED

**Classification:** HIGH PRIORITY  
**Incident ID:** SEC-2024-0006  
**Related Ticket:** TKT-2024-0006

---

### REPORTING PARTY

| Field | Information |
|-------|-------------|
| Name | Stefan Richter |
| Email | s.richter@stadtverwaltung.de |
| Phone | +49 30 9026 2134 |
| Department | IT-Abteilung |
| Location | IT-Zentrum Tempelhof |

---

### INCIDENT TIMELINE

**Date of Report:** January 16, 2024  
**Time:** 08:15:27  
**Discovery Method:** User self-reported

---

### INCIDENT DESCRIPTION

The reporting party received a suspicious email that appeared to be from the organization's director. The email requested immediate action to open an attached invoice.

#### Email Details

**Subject Line:**  
`URGENT: Unpaid Invoice Immediate Action Required`

**Sender Address:**  
`direktor@stadtverwaltungg.de`

⚠️ **Note the extra 'g' in the domain name** — this is a classic typosquatting technique.

**Attachment:**  
`Rechnung_2024.pdf.exe`

⚠️ **Double extension detected** — the file masquerades as a PDF but is actually an executable file.

---

### TECHNICAL ANALYSIS

The IT Security team performed analysis on the suspicious email:

#### Email Header Analysis

```
Return-Path: <bounce@mail-relay.suspicious.ru>
Received: from mail-relay.suspicious.ru (185.220.101.47)
X-Originating-IP: [185.220.101.47]
Authentication-Results: 
  spf=fail (sender IP is 185.220.101.47)
  dkim=none
  dmarc=fail action=quarantine
```

**Originating IP:** 185.220.101.47  
**Geolocation:** Romania  
**SPF Check:** ❌ FAILED  
**DKIM:** ❌ NOT PRESENT  
**DMARC:** ❌ FAILED

#### Attachment Analysis

The attachment was submitted to the sandbox environment for analysis:

- **File Type:** Windows PE Executable (disguised as PDF)
- **File Size:** 847 KB
- **SHA256:** `[REDACTED FOR SECURITY]`
- **Malware Classification:** Trojan.GenericKD (Information Stealer)
- **Behavior:** Attempts to harvest credentials and establish C2 connection

---

### ACTIONS TAKEN

1. ✅ Email quarantined immediately
2. ✅ Sender address blacklisted at mail gateway
3. ✅ Originating IP blocked at firewall
4. ✅ Domain `stadtverwaltungg.de` added to blocklist
5. ✅ Full scan of reporting user's workstation — **NO COMPROMISE DETECTED**
6. ✅ Security awareness reminder distributed to all staff

---

### EMAIL SENT TO ALL STAFF

> **Subject: Sicherheitswarnung — Phishing-Angriff**
>
> Liebe Kolleginnen und Kollegen,
>
> heute wurde ein Phishing-Versuch gemeldet. Bitte öffnen Sie KEINE E-Mails mit dem Betreff "URGENT: Unpaid Invoice" und löschen Sie diese sofort.
>
> Bei Fragen wenden Sie sich bitte an die IT-Abteilung.

---

### RESOLUTION

**Status:** CLOSED  
**Resolution Time:** 1.1 hours  
**Escalated:** Yes (to IT Security Officer)  
**User Satisfaction:** 5/5

The user correctly identified and reported the phishing attempt without opening the attachment. Commendation recommended for security awareness.

---

**Assigned Technician:** Michael Koch  
**Reviewed by:** IT Security Officer  
**Date Closed:** January 16, 2024

