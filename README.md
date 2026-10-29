# seitenschwung-website

Die Website von seitenschwung: https://seitenschwung.com

Statische Seite in `public/`, ausgeliefert von nginx im Container. Jeder Push auf `main` läuft durch die
gemeinsame Pipeline aus `seitenschwung/template` (Checks, gehärteter Docker-Test, Browser-Tests) und wird danach
auf Coolify deployt. Impressum und Datenschutz erzeugt die Pipeline aus `legal.json`.

Lokal ansehen:

```bash
python3 -m http.server -d public 8080
```

`public/index.html` wird im Design-Arbeitsordner aus `.werkstatt/template-himmel.html` gebaut und hierher kopiert.
