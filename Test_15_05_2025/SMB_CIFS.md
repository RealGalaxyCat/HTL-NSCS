# <u>1. SMB/CIFS</u>
=> Netzwerkprotokoll
**SMB =** ``Server Message Block`` => Allgemeine Name des Protokolls
**CIFS =** ``Common Internet File System`` => spezifische Implementierung von SMB 1.0

**Aufgaben:**
- Ressourcen, z.B. **Dateien und Drucker** über das Netzwerk **freigeben**.
- Ermöglicht eine **zentrale Benutzerverwaltung (Domänen-Prinzip)**

| Version | Verschlüsselt | Beschreibung |
| --- | --- | --- |
| **SMB 1.0 (CIFS)** | ❌ | veraltet, unsicher |
| **SMB 2.0/2.1** | ❌ | schneller, effizienter |
| **SMB 3.0/3.1.1** | ✅ | moderne Version, Komprimierung und<br> Performance-Verbesserungen |


# <u>2. net</u>
Wird genutzt um einen freien Netzwerkbuchstaben mit einem freigegebenen Netzwerkordner zu verbinden. (Windows)

**Allgemein:**
```
                IP oder Domain    Pfad (z.B. \Daten\Software\...)
						 |          |
net use <Laufwerk>: \\<Server>\<Freigabe> /user:<Benutzername> <Passwort>
										  \_____________________________/
													optional
```


Beispiel verbinden von Z: im **lokalem Netzwerk**:
```
net use Z: \\192.168.0.10\Daten
```

Beispiel verbinden von Z: mit **externem Server**:
```
net use Z: \\domain.com\Daten
```


**Entfernen** der **Laufwerkzuweisung**:
```
net use Z: /delete
```