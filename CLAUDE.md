# Morse Code – Projektkontext

Morse-Code-Lern-, Sende- und Erkennungs-App.

## Tech-Stack

- Eine einzelne `index.html` (Markup, CSS, JS inline) – kein Framework, kein Bundler, kein npm-Build.
- `manifest.json` + `sw.js` für PWA/Offline-Fähigkeit.
- Persistenz über `localStorage` (Präfix `morse_`).

## Ziel / Ausblick

Perspektivisch soll die App über einen **Capacitor-Wrapper** als iOS-App verpackt werden. Kein natives SwiftUI vorerst – die Web-App bleibt die einzige Implementierung.

## Wichtige Einschränkungen

- `getUserMedia` (Kamera/Mikrofon, für Dekoder und Taschenlampe) braucht **HTTPS oder localhost**. Über `file://` oder unverschlüsseltes HTTP bleiben diese Features blockiert.
- **iOS Safari unterstützt kein `torch`/Taschenlampe** über Web-APIs – dort nur Bildschirm-Blitz nutzbar. Nur Android Chrome unterstützt Torch.
- Beim lokalen Testen immer über einen simplen HTTP-Server starten (z. B. `python3 -m http.server`), nicht die Datei direkt im Browser öffnen.

## Code-Konventionen

- UI-Texte und Kommentare auf **Deutsch**.
- Dunkles Farbschema über CSS-Variablen: `--bg`, `--green`, `--amber`, `--danger` (siehe `:root` in `index.html`).
- Morsebaum-Logik steckt im `TREE`-Objekt.
- Koch-Methode-Reihenfolge steckt im `KOCH`-Array.
- Keine externen Libraries einführen – Ziel bleibt eine einzige, selbsterklärende, offline-fähige Datei.
- Änderungen an `index.html` sollten den Cache-Namen (`CACHE` in `sw.js`) hochzählen, damit Nutzer die neue Version erhalten.

## Testen

Änderungen an der Baum-Logik (`TREE`, `MAP`) immer gegen **alle 26 Buchstaben** testen. `node --check index.html` reicht nicht (kein reines JS) – Skript-Inhalt ggf. extrahieren und mit `node --check` auf Syntaxfehler prüfen. Für Verhalten notfalls headless mit `jsdom` testen.
