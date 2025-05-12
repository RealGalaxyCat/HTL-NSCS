# <u>HTTP - Hypertext Transfer Protocol</u>

Mit diesem kann man **Inhalte**, die **in HTML erstellt oder eingebettet** sind, übertragen. (z.B. Multimediainhalte wie Videos)

**<u>Allgemeines</u>**
- zustandslos
- Zuordnung von **Statusinformationen** (Formulare, Warenkörbe, ...) erfolgt durch **Cookies**

**<u>Ports</u>:**
Standard: 80, alternativ: 8080
verschlüsselt (HTTPS): 443

**<u>Versionen:</u>**
- **HTTP/1.0**
	- Bei jeder Anfrage wird eine neue TCP-Verbindung aufgebaut
- **HTTP/1.1**
	- Bestehende TCP-Verbindungen können zum "Nachladen" von Daten verwendet werden
	- höhere Übertragungsgeschwindigkeit, geringere Netzlast
	- ermöglicht WebDAV
- **HTTP/2**
	- in einer TCP-Verbindung können mehrere Webseiten-Elemente simultan übertragen werden
	- kürzere Ladezeiten
	- Push-Funktion: Daten können ohne vorherige Anforderung an den Client (z.B. Browser) geschickt werden
- **HTTP/3 QUIC**
	- nutzt **UDP** anstatt TCP

---

# <u>1. HTTP-Methoden</u>

| Name | Beschreibung |
| --- | --- |
| GET | Anforderung einer Datei |
| POST | Daten an den Server senden |
| PUT | Senden einer Datei |
| DELETE | Löschen einer Datei |
| HEAD | Anforderung der Headers, ohne eigentlichem Inhalt, zum Überprüfen ob Datei in Cache noch aktuell ist |

---

# <u>2. HTTP Status Codes</u>
Anhand der ersten Ziffer kann man erkennen, ob die Anfrage erfolgreich war oder nicht

| Ziffer | Erfolg | Beschreibung | Beispielszenario |
| --- | --- | --- | --- |
| 1xx | ✅ | Informationen || 
| 2xx | ✅ | Anfrage war erfolgreich ||
| 3xx | ✅ | Redirects, Änderungen, Rückfragen | z.B. Anfrage wird von ``http://...`` auf ``https://...`` umgeleitet |
| 4xx | ❌ | fehlerhafte Anfrage ||
| 5xx | ❌ | Fehler im Bereich des Servers | z.B. Server startet gerade erst, hat sich aufgehängt,... |


| Status Code | Text | Beschreibung |
| --- | --- | --- |
| 101 | Switching Protocols | Protokollwechsel (Zustimmung durch den Server)
| 102 | Processing | Bei längerer Bearbeitungsdauer, damit Time-Out verhindert wird |
| 200 | OK | Daten werden nun übermittelt |
| 301 | Moved Permanently | Browser wiederholt die Anfrage, diesmal an die URL im ``Location`` Header der Antwort |
| 304 | Not Modified | Inhalt hat sich seit der letzten Anfrage nicht geändert |
| 400 | Bad Request | Syntax-Fehler in der Anfrage |
| 401 | Unauthorized | Fehlende/Falsche Authentifizierung (z.B. Username/Passwort) |
| 403 | Forbidden | Falsche Authentifizierung |
| 404 | Not Found | Ressource existiert nicht |
| 500 | Internal Server Error | allgemeine Fehlermeldung für alle kritischen Fehler welche innerhalb des Servers auftreten |
| 503 | Service Unavailable | Wartungsarbeiten, Server startet gerade erst, ... |

---

# <u>3. HTTP Headers</u>

|Name|verpflichtend|in Anfrage erlaubt|in Antwort erlaubt|Beschreibung|
|---|---|---|---|---|
|Host|✅|✅|❌|Gibt die Domain des Zielservers an (z. B. `example.com`).|
|Content-Type|❌|✅|✅|Typ der gesendeten Daten (z. B. `application/json`, `text/html`).|
|Content-Encoding|❌|✅|✅|Gibt an, wie der Anfrage-Inhalt codiert wurde (z. B. `gzip`).|
|Content-Length|❌|✅|✅|Gibt die Länge des Haupt-Inhaltes in Bytes an, nur verwenden wenn dieser vorhanden ist|
|Accept|❌|✅|❌|Gibt an, welche MIME-Typen der Client akzeptiert (z. B. `text/html`, `*/*`).|
|Accept-Encoding|❌|✅|❌|Gibt an, welche Komprimierungsmethoden akzeptiert werden (z. B. `gzip`, `br`).|
|Accept-Language|❌|✅|❌|Gibt die bevorzugten Sprachen an (z. B. `de-DE`, `en-US`).|
|Authorization|❌|✅|❌|Wird zur Authentifizierung verwendet (z. B. `Basic ...`).|
|Referer|❌|✅|❌|Seite, auf welcher der Link eingebettet war.|

---


# <u>4. Webbrowser und Sicherheit</u>
- Programme und Plugins **aktuell halten**
- Browser so einstellen, dass er **keinen Verlauf und Cache erstellt**
- Browser so einstellen, dass er **keine Formulardaten speichert**
- **Keine Cookies** von **Drittanbietern** zulassen
- **Kein Speichern von Kennwörtern** im Browser (sehr unsicher)


# <u>5. Basic Auth</u>

- Bei **Basic Auth** werden **Benutzername und Passwort Base64-codiert** und im **`Authorization`-Header** der HTTP-Anfrage mitgeschickt.  
	❗Dies ist **keine sichere Methode**, da **Base64 lediglich eine Kodierung**, aber **keine Verschlüsselung** ist.  
- Zudem können HTTP-Header unterwegs von **Zwischensystemen (z. B. Reverse-Proxys, Firewalls)** mitgelesen werden – selbst wenn diese **keinen Zugriff auf sensible Daten** haben sollten.
- Nutzername und Passwort wird bei jeder Anfrage mitgeschickt