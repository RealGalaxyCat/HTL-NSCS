
# <u>1. Mail Flow</u>



# <u>2. Mail Aufbau</u>


# <u>3. Sicherheit</u>
- Aufgrund eines **Scores** wird ermittelt, ob eine E-Mail **erlaubt, markiert oder blockiert** wird.
- **Maluspunkte erhöhen** den **Score**, **Bonuspunkte verringern** ihn.
- Je weniger Punkte eine EMail erhält, desto legitimer ist sie (meistens).


**Was passiert mit Spam?**
- Mails werden als Spam markiert (Bearbeitet) und/oder in einen "Spam" Ordner verschoben
- Mails werden **niemals automatisch am Server gelöscht**
	- **Ausnahme:** EMail ist ganz sicher schädlich, z.B. EXE als Anhang
	- ZIP Dateien mit Passwort kommen oft in Quarantäne


**Whitelist (Allowlist)**
- Zugelassene Domains, höhere Priorität als Blacklist

**Blacklist (Denylist)**
- Verbotene Domains
- kann auch Legitime EMail Anbieter (Provider) enthalten von welchen aus Spam geschickt wurde (z.B. gehackte Accounts)
- Wird meist als "Remote Block list" verwendet - lokal wäre auch möglich, allerdings umständlich


### 3.1 Fehler / Verzögerungsmechanismen
Fehler können unter anderem verwendet werden um Spammer / Bots zu verlangsamen.

<u>**[1] Temporäre Fehler**</u>
- z.B. wenn Server überlastet ist
- Zustellung **soll später erneut versucht werden**


<u>**[2] Permanente Fehler**</u>
- z.B. Fehler im EMail-Aufbau, nicht existente Empfänger-Adresse
- **direktes Blockieren** bei:
	- **Blacklisted IPs/Domains/Malware**


<u>**[3] Greylisting**</u>
- E-Mails beim **ersten Zustellversuch temporär ablehnen**
- Legitime Server versuchen die Zustellung der EMail nach einiger Zeit erneut → EMail wird dann angenommen
- Spammer geben oft nach **einem** Versuch auf


<u>**[4] Tarpitting**</u>
- absichtlich **längere Antwortzeiten**, um Spam-Mail-Versand zu verlangsamen
- kann einfach durch Multithreading umgangen werden


# <u>4. Begriffe</u>

MUA - Mail User Agent<br>
MSA - Mail Submission Agent<br>
MTA - Mail Transfer Agent<br>
MPA - Mail Processing Agent<br>

**IMAPS (Internet Message Access Protocol Secure)** - Port 993 - SSL verschlüsselt<br>
**POP3S (Post Office Protocol 3 Secure)** - Port 995 - SSL verschlüsselt<br>

<br>

**CC (Carbon Copy)**
- Jeder Empfänger sieht wer noch im CC ist

<br>

**BCC (Blind Carbon Copy)**
- Nur der Sender sieht die Adressen welche im BCC stehen


# POP3 vs IMAP4
POP3 löscht Nachrichten vom Server nach dem abrufen, IMAP nicht.