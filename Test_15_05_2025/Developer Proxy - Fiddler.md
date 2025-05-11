# <u>Developer Proxy - Fiddler</u>

Fiddler ist ein **HTTP/HTTPS-Proxy-Tool**, das Webverkehr analysiert, debuggt und manipuliert.
Es funktioniert als **Man-in-the-Middle (MitM)**-Proxy zwischen deinem Browser (oder einer App) und dem Internet.


# <u>Entschlüsselung von HTTPS-Traffic</u>
Um HTTPS-Anfragen entschlüsseln zu können, gibt sich Fiddler gegenüber dem Browser als der Zielserver aus.  
Dazu installiert Fiddler ein eigenes **Root-Zertifikat** im Betriebssystem, wodurch es legitim TLS-Zertifikate für beliebige Domains (z. B. `google.com`) erzeugen kann.

Der Browser glaubt, er kommuniziert direkt mit `google.com`, während die Verbindung tatsächlich zu Fiddler geht.  
Fiddler baut im Hintergrund eine eigene Verbindung zum echten Zielserver auf, leitet die Anfragen des Browsers dorthin weiter und gibt die Antworten des Servers wiederum an den Browser zurück.