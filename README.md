# Morse Code

Eine Progressive Web App zum Lernen, Senden und Erkennen von Morse-Code – direkt im Browser.

## Bereiche

- **Baum** – interaktiver Morsebaum mit Impuls-Tasten (Punkt/Strich), zum Erklopfen von Zeichen entlang der Baumstruktur.
- **Senden** – wandelt Text in Morse-Code um und gibt ihn per Ton und Bildschirm-Blitz aus.
- **Lernen** – Quiz nach der Koch-Methode (schrittweise wachsender Zeichensatz, Hören → Zeichen und Zeichen → Klopfen).
- **Lesen** – Dekoder, der Morse-Signale live über Mikrofon oder Kamera-Blinklicht erkennt.

## Hinweise

- Kamera- und Mikrofon-Features (`getUserMedia`) funktionieren nur in einem sicheren Kontext: **HTTPS** oder `localhost`.
- Die Taschenlampen-Ausgabe (Torch) hängt von Gerät und Browser ab (u. a. Android Chrome und ausgewählte iOS-Versionen) und erfordert eine Kamera-Freigabe. Ist sie nicht verfügbar, wird automatisch auf Bildschirm-Blitz zurückgefallen.
- Reines **Vanilla JS/HTML/CSS** – kein Build-Prozess, keine Abhängigkeiten, keine Frameworks.

## Lokal starten

```bash
python3 -m http.server 8080
# http://localhost:8080 im Browser öffnen
```

Die App ist als PWA installierbar und läuft dank Service Worker (`sw.js`) anschließend offline.
