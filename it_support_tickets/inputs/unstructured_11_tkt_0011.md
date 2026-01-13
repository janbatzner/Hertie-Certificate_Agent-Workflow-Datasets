# EMAIL THREAD — INTERNAL IT SUPPORT

---

**Thread ID:** MTH-2024-0117-0933  
**Related Ticket:** TKT-2024-0011

---

## EMAIL 1 — Initial Report

**From:** Martin Braun <m.braun@stadtverwaltung.de>  
**To:** Kolleginnen Kulturamt <kulturamt-team@stadtverwaltung.de>  
**Date:** January 17, 2024, 09:15  
**Subject:** Komisches Sicherheitsproblem im Browser

---

Hallo zusammen,

hat jemand von euch auch diese merkwürdigen Sicherheitswarnungen im Browser wenn ihr auf unsere internen Seiten geht? Bei mir zeigt Chrome seit gestern immer diese rote Warnung "Ihre Verbindung ist nicht privat" an.

Das passiert bei der Zeiterfassung, dem Intranet und sogar bei der Urlaubsplanung-Seite. Ich dachte erst, ich hätte was falsch gemacht, aber eigentlich habe ich nichts verändert.

Kann ich die Seiten trotzdem benutzen oder ist das gefährlich?

Gruß,
Martin

---

## EMAIL 2 — Colleague Response

**From:** Petra Vogel <p.vogel@stadtverwaltung.de>  
**To:** Kolleginnen Kulturamt <kulturamt-team@stadtverwaltung.de>  
**Date:** January 17, 2024, 09:28  
**Subject:** RE: Komisches Sicherheitsproblem im Browser

---

Hi Martin,

bei mir funktioniert alles ganz normal. Keine Warnungen oder so. Ich benutze aber Firefox, vielleicht liegt es daran?

Hast du schon mal den Cache gelöscht? Das hilft manchmal bei Browser-Problemen.

Gruß,
Petra

---

## EMAIL 3 — Another Colleague

**From:** Klaus Hartmann <k.hartmann@stadtverwaltung.de>  
**To:** Kolleginnen Kulturamt <kulturamt-team@stadtverwaltung.de>  
**Date:** January 17, 2024, 09:41  
**Subject:** RE: Komisches Sicherheitsproblem im Browser

---

Moin,

ich hab auch Chrome und bei mir geht alles. Vielleicht ist auf deinem Rechner irgendwas nicht aktuell?

Die IT wäre da wohl der richtige Ansprechpartner. Die Nummer ist 9026-4000 oder per Mail it-helpdesk@stadtverwaltung.de

Klaus

---

## EMAIL 4 — Martin's Follow-up

**From:** Martin Braun <m.braun@stadtverwaltung.de>  
**To:** Kolleginnen Kulturamt <kulturamt-team@stadtverwaltung.de>  
**Date:** January 17, 2024, 09:58  
**Subject:** RE: Komisches Sicherheitsproblem im Browser

---

Danke euch beiden!

Cache habe ich gerade gelöscht — leider keine Änderung. Die Warnung zeigt immer noch:

```
Ihre Verbindung ist nicht privat
NET::ERR_CERT_AUTHORITY_INVALID
```

Habe es auch im Edge probiert, gleiche Warnung dort. Also liegt es wohl nicht an Chrome selbst.

Ich werde jetzt mal die IT anschreiben. Hoffentlich ist das kein ernstes Sicherheitsproblem...

Martin

---

## EMAIL 5 — Ticket Request to IT

**From:** Martin Braun <m.braun@stadtverwaltung.de>  
**To:** IT-Helpdesk <it-helpdesk@stadtverwaltung.de>  
**CC:** Abteilungsleitung Kulturamt <leitung-kultur@stadtverwaltung.de>  
**Date:** January 17, 2024, 10:33  
**Subject:** Sicherheitswarnungen bei allen internen Webseiten — Dringend

---

Sehr geehrte Damen und Herren vom IT-Support,

seit gestern erhalte ich in meinem Browser (Google Chrome, aber auch Edge zeigt das gleiche) bei allen internen Webseiten der Stadtverwaltung Sicherheitswarnungen.

**Betroffene Seiten:**
- Intranet-Portal
- Zeiterfassungssystem
- Urlaubsplanungs-Tool
- Dokumentenablage

**Fehlermeldung:**
"Ihre Verbindung ist nicht privat"
Fehlercode: NET::ERR_CERT_AUTHORITY_INVALID

**Was ich bereits versucht habe:**
- Browser-Cache gelöscht
- Anderen Browser getestet (Edge) — gleiches Problem
- Kollegen im selben Büro gefragt — bei ihnen funktioniert alles

Das Zertifikat scheint gültig zu sein (läuft bis 30.06.2025 laut Browser-Info), aber irgendwas mit der Zertifikatskette stimmt nicht.

Ich kann aktuell nur arbeiten, wenn ich jedes Mal auf "Erweitert" → "Trotzdem fortfahren" klicke, was natürlich nicht sicher ist.

**Technische Details:**
- Rechner: Dell Latitude 7420
- Betriebssystem: Windows 10 Pro  
- Browser: Chrome 121 / Edge
- Meine IP: 192.168.10.267

Können Sie sich das bitte anschauen?

Mit freundlichen Grüßen,

Martin Braun  
Kulturamt Treptow  
Tel: +49 30 9026 3345

---

## TICKET CREATED

**Ticket ID:** TKT-2024-0011  
**Priority:** Low  
**Category:** Software  
**Assigned To:** Michael Koch  
**Status:** Open

---

## EMAIL 6 — IT Response

**From:** IT-Helpdesk <it-helpdesk@stadtverwaltung.de>  
**To:** Martin Braun <m.braun@stadtverwaltung.de>  
**Date:** January 17, 2024, 15:42  
**Subject:** RE: Sicherheitswarnungen bei allen internen Webseiten — Dringend [TKT-2024-0011]

---

Sehr geehrter Herr Braun,

vielen Dank für Ihre detaillierte Meldung.

Wir haben die Ursache identifiziert: Das Root-Zertifikat unserer internen Zertifizierungsstelle (Internal CA) ist auf Ihrem Computer abgelaufen. Dieses Zertifikat wird normalerweise automatisch über die Gruppenrichtlinien (GPO) aktualisiert, aber in Ihrem Fall scheint das Update nicht durchgekommen zu sein.

**Lösung:**
Wir haben das aktuelle Root-Zertifikat per GPO erneut an Ihren Computer gepusht. Bitte starten Sie Ihren Computer einmal neu. Danach sollten alle internen Seiten wieder ohne Warnung erreichbar sein.

Falls das Problem nach dem Neustart weiterhin besteht, löschen Sie bitte einmal den Browser-Cache erneut.

Mit freundlichen Grüßen,

Michael Koch  
IT-Abteilung  
Stadtverwaltung Berlin

---

## EMAIL 7 — Resolution Confirmation

**From:** Martin Braun <m.braun@stadtverwaltung.de>  
**To:** IT-Helpdesk <it-helpdesk@stadtverwaltung.de>  
**Date:** January 17, 2024, 16:54  
**Subject:** RE: Sicherheitswarnungen bei allen internen Webseiten — Dringend [TKT-2024-0011]

---

Hallo Herr Koch,

perfekt, nach dem Neustart funktioniert alles wieder!

Alle internen Seiten sind jetzt ohne Warnung erreichbar. Vielen Dank für die schnelle Lösung.

Beste Grüße,
Martin Braun

---

## RESOLUTION

**Status:** CLOSED  
**Resolution Time:** 6.2 hours  
**User Satisfaction Rating:** 5/5  
**Root Cause:** Internal CA root certificate expired on user's machine  
**Action Taken:** Pushed updated root certificate via GPO, browser cache cleared

---

*End of email thread*

