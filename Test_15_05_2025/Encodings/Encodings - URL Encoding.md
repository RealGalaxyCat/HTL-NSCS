
# URL-Encoding (Percent-Encoding)

**Was ist URL-Encoding?**
- **URL Encoding** (auch **Percent-Encoding** genannt) ist ein Verfahren, um **bestimmte Zeichen in URLs in ein standardisiertes Format umzuwandeln**, sodass sie korrekt und sicher über das Internet übertragen werden können.
    
- Das betrifft vor allem **Sonderzeichen**, **Leerzeichen**, **Umlaute** oder **reservierte Zeichen**, die in URLs eine spezielle Bedeutung haben oder nicht erlaubt sind.
    

**Warum ist URL-Encoding nötig?**
- Eine URL darf nur bestimmte Zeichen enthalten:
    - **Nicht reservierte Zeichen** (dürfen direkt verwendet werden):  
        `A–Z, a–z`, `0–9`, `- . _ ~`
        
    - **Reservierte Zeichen** (haben spezielle Funktionen in der URL):  
        `: / ? # [ ] @ ! $ & ' ( ) * + , ; =`  
        → Diese dürfen **nur dann verwendet werden**, wenn ihre spezielle Bedeutung auch wirklich gemeint ist.  
        → Wenn man sie z.B. **als Teil eines Dateinamens** verwenden will, **müssen sie encodiert werden.**
        

---

**Wie funktioniert URL-Encoding?**

- Jedes zu kodierende Zeichen wird durch ein **Prozentzeichen (`%`)**, gefolgt von **zwei Hexadezimalstellen**, ersetzt, die den **ASCII-Wert** des Zeichens darstellen.  
    → Zum Beispiel:
    - Leerzeichen: `" "` → `%20` (weil ein Leerzeichen den ASCII-Wert 32 hat = 20 in Hex)
        

---

**Beispiel – URL mit Leerzeichen:**

- Eine URL wie:  
    `htlstp.ac.at/files/HTL Informationen.pdf`  
    würde **nicht korrekt funktionieren**, da das Leerzeichen (`" "`) als **Trennzeichen** interpretiert wird.
    
- **Korrekt encodiert:**  
    `htlstp.ac.at/files/HTL%20Informationen.pdf`  
    → Jetzt wird der komplette Pfad als gültige URL erkannt.

---


**Zusammenfassung (vereinfacht):**
- URL-Encoding macht Zeichen sicher übertragbar.
- Nicht erlaubte oder mehrdeutige Zeichen werden in `%XX`-Form geschrieben.
    