# <u>HTTP Anfragen/Aufbau/Params/Multipart</u>

# <u>1. Beispiel Anfragen</u>

**Beispiel GET Anfrage:**
```http
Methode URL Endpoint HTTP Version
\_____/ \__________/ \__________/
 |         |         |
 |         |         |
GET /index.html HTTP/1.1
Host: www.beispielseite.de                            \
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) |
Accept: text/html,application/xhtml+xml               |
Accept-Language: de-DE,de;q=0.9                       | Headers
Accept-Encoding: gzip                                 |
Referer: https://www.google.de/                       /

❗Kein Haupt-Content (Body) vorhanden

```

**Beispiel POST Anfrage:**
```http
POST /login HTTP/1.1
Host: beispielseite.de
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)
Accept: application/json
Accept-Language: de-DE,de;q=0.9
Content-Type: application/json
Content-Length: 49

{                             \
  "username": "max",          |
  "password": "geheim123"     | Enthält einen Body (Datentyp im Content-Type Header festgelegt)
}                             /

```


---

# <u>2. Beispiel Antwort</u>

```http
HTTP/1.1 200 OK         - HTTP Version, Status Code, Text
Date: Sat, 10 May 2025 12:00:00 GMT
Server: nginx
Content-Type: text/html; charset=UTF-8
Content-Length: 1234

<!doctype html><html><body>Hello World</body></html>
```


---

# <u>3. Übertragen von Parametern</u>

### 1. Query-Parameter (GET)
```http
GET /search?q=chatgpt&lang=de HTTP/1.1
Host: example.com
...
```
❗**Kann mitgelesen werden, URL wird in Server-Logs gespeichert, nicht für Sensitive Daten wie Passwörter!**

### 2. Im Body (POST - Formulardaten)
```http
POST /login HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded    ❗Teilt dem Empfänger mit, dass die Parameter im Body sind
Content-Length: 29
...

username=max&password=geheim123
...
```
❗Sicher mit HTTPS, jedoch nicht mit HTTP

---

# <u>4. Teile der Anfragen</u>

| Methode    | enthält Headers | kann Query enthalten | hat Body | kann Parameter im Body enthalten |
| ---------- | --------------- | -------------------- | -------- | -------------------------------- |
| **GET**    | ✅               | ✅                    | ❌        | ❌                                |
| **POST**   | ✅               | ✅                    | ✅        | ✅                                |
| **PUT**    | ✅               | ✅                    | ✅        | ✅                                |
| **DELETE** | ✅               | ✅                    | ❌        | ❌                                |
| **HEAD**   | ✅               | ✅                    | ❌        | ❌                                |

---

# <u>5. Multipart</u>
`multipart` erlaubt es, **mehrere Felder** (z. B. Text und Datei) **in einer einzigen HTTP-Anfrage** zu übertragen.
- Jedes Feld ist durch eine **Boundary** getrennt, welche im **ersten Content-Type Header** festgelegt wird.
- Jedes Feld kann **eigene Headers** sowie einen **Body** haben.

**Beispiel:**
```http
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary12345

------WebKitFormBoundary12345
Content-Type: text/html              \
                                      | Feld 1
<html>Hallo Welt</html>              /
------WebKitFormBoundary12345
Content-Disposition: form-data; name="datei"; filename="bild.jpg"     \
Content-Type: image/jpeg                                               | Feld 2
                                                                      /
[BINÄRDATEN]
------WebKitFormBoundary12345--
```