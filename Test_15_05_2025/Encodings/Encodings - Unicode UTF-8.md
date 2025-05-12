- **Unicode Encoding** beschreibt, **wie die Unicode-Zeichen (wie z.B. `ä`, `你`, `✓`) intern in Bytes gespeichert werden**, damit Computer sie speichern, übertragen oder anzeigen können.
- Computer speichern nur **Bytes (0 bis 255)**, da es jedoch mehr als 96.000 Unicode Zeichen gibt, kann nicht jedes davon mit nur einem Byte dargestellt werden.

---

### Was ist Unicode?

Unicode ist ein **Standard**, der **jedem Zeichen weltweit** (z.B. Buchstaben, Emojis, chinesische Schriftzeichen) eine **eindeutige Nummer** zuweist, den sogenannten **Codepunkt** (z.B. `U+00E4` für `ä` oder `U+1F600` für 😀).

---

### Wichtige Unicode-Encoding-Formate:
(UTF-8 ist wichtig für Test)

|Encoding|Bit pro Zeichen|
|---|---|
|**UTF-8**|**8 oder 16 Bit**|
|**UTF-16**|16 oder 32 Bit|
|**UTF-32**|Immer 32 Bit|
