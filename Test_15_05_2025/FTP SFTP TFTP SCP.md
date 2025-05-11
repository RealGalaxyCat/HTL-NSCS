# <u>FTP/SFTP/TFTP/SCP</u>

**Übersicht:**

|Merkmal|**FTP**|**SFTP**|**TFTP**|**SCP**|
|---|---|---|---|---|
|**Abkürzung**|File Transfer Protocol|SSH File Transfer Protocol|Trivial File Transfer Protocol|Secure Copy Protocol|
|**Port**|**TCP 21** (Daten: TCP 20 oder zufällig)|**TCP 22**|**UDP 69**|**TCP 22**|
|**Verschlüsselt**|❌|✅ (SSH)|❌|✅ (SSH)|
|**Funktionalität**|Hoch-/Download, Verzeichnisnavigation|Vollwertiger Dateizugriff über SSH|Nur einfaches Datei-Übertragen|Nur Kopieren von Dateien|
|**Probleme**|\<siehe unten>|Durch SSH-Verschlüsselung bei vielen kleinen Dateien sehr langsam|Keine Authentifizierung/Verschlüsselung|Veraltet (Sicherheitslücken)|

# <u>1. FTP</u>
Ermöglicht den Aufbau einer **unverschlüsselten Verbindung** zur Übertragung von Dateien.
Es wird immer **eine** Kontrollverbindung benötigt. **Für jede** angeforderte **Datei** wird eine **neue Datenverbindung geöffnet**.


### <u>1.1. Kontrollverbindung (Aktiv und Passiv)</u>

- **Client → Server: Port 21 (TCP)**  
    Der Client stellt eine Verbindung zum Server auf Port 21 her, um FTP-Befehle zu senden.
 - Dient zur **Authentifizierung und Steuerung** der Sitzung.    
- Die Verbindung bleibt **dauerhaft** während der gesamten FTP-Sitzung bestehen.

---

### <u>1.2. Datenverbindung (Aktiver Modus)</u>
- **Client öffnet** einen zufälligen Port **>1023** und teilt diesen dem Server mit.
- **Server verbindet sich aktiv** von **Port 20 (TCP)** zu diesem Client-Port.
- ❗**Nachteil:** Oft durch **Client-Firewalls blockiert**, da der Server eine eingehende Verbindung aufbaut.

### <u>1.2. Datenverbindung (Passiver Modus)</u>
- **Server öffnet** einen zufälligen Port **>1023** und teilt diesen dem Client mit.
- **Client verbindet sich aktiv** von einem eigenen Port **>1023** zu diesem Server-Port.
- ❗**Nachteil: Firewall/NAT** beim Server muss **große Portbereiche freigeben**, da für jede Datenverbindung ein neuer Port benötigt wird