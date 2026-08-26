# Website TBH GmbH

Einseitige Website der TBH GmbH — Technisches Büro für Elektrotechnik,
Satzäcker 25, A-2752 Wöllersdorf.

Die gesamte Seite steckt in einer einzigen Datei: `index.html`.
Schriften, Grafiken und Skripte sind eingebettet, es gibt keine
Abhängigkeiten und keinen Build-Schritt. Zum Ansehen genügt es, die
Datei im Browser zu öffnen.

## Im Browser bearbeiten

Auf der Repo-Seite auf GitHub die Taste `.` drücken — das öffnet den
Editor github.dev direkt im Browser. Alternativ in der Adresszeile
`github.com` durch `github.dev` ersetzen.

Dort `index.html` öffnen, ändern, links unter „Source Control“ eine
kurze Beschreibung eintippen und auf „Commit & Push“ klicken. Das
funktioniert von jedem Gerät mit Browser und GitHub-Login.

## Aufbau der Datei

| Bereich | Wo |
|---|---|
| Farben, Schriften, Layout | `<style>` am Dateianfang |
| Kopfzeile und Navigation | `<header class="site">` |
| Startseite | `<main id="top">` mit den Abschnitten `hero`, `leistungen`, `ueber-uns`, `referenzen`, `kontakt` |
| Impressum | `<div id="page-impressum">` |
| Datenschutzerklärung | `<div id="page-datenschutz">` |
| Fußzeile mit Kontaktdaten | `<footer class="site">` |
| Skripte | `<script>`-Blöcke am Dateiende |

Impressum und Datenschutz sind eigene Seiten: Ein kleiner Router blendet
über `#impressum` bzw. `#datenschutz` die Startseite aus.

## Offene Punkte vor dem Livegang

- **GitHub-Plan klären.** GitHub Pages läuft aus einem privaten
  Repository nur mit kostenpflichtigem Konto (GitHub Pro oder Team).
  Kostenlose Alternative wäre, das Repository öffentlich zu machen —
  dann ist aber die gesamte Commit-Historie öffentlich einsehbar und
  gehört vorher durchgesehen.
- **Datenschutzvereinbarung mit GitHub (DPA) annehmen.** Die
  Datenschutzerklärung setzt sie bereits als bestehend voraus.
- **Nachprüfen, dass GitHub Pages keine Cookies setzt.** Der Text sagt
  ausdrücklich „keine Cookies“ zu. Für statisch ausgelieferte Seiten
  trifft das zu, ist vor dem Livegang aber einmal im Browser zu
  kontrollieren (Entwicklerwerkzeuge → Anwendung → Cookies).
- **Gewerbebehörde** im Impressum gegen den Gewerbeschein prüfen —
  eingetragen ist die Bezirkshauptmannschaft Wiener Neustadt.
- **Kontaktformular**: Es öffnet derzeit das E-Mail-Programm des
  Besuchers, es gibt keinen Serverversand. Für echten Versand ist die
  Stelle im Skript markiert. Kommt ein Backend dazu, muss der Absatz
  „Kontaktaufnahme“ mitwachsen.
- Rechtstexte vor der Veröffentlichung von der WKO-Rechtsberatung prüfen
  lassen.

## Veröffentlichen

Geplant ist **GitHub Pages**; Wix hält nur die Domain. Der Vorteil:
jeder Commit aus github.dev geht automatisch live, der Ablauf
„von überall im Browser bearbeiten“ bleibt also erhalten.

Noch nicht aktiv. Die Schritte in der Reihenfolge:

1. **Pages einschalten** — im Repository unter Settings → Pages als
   Quelle Branch und Ordner `/` wählen. `index.html` liegt bereits im
   Wurzelverzeichnis, es braucht keinen Build-Schritt. Die Seite ist
   danach unter `tbh-stefan.github.io/homepage` erreichbar.
2. **Erst danach die Domain umstellen.** Solange Schritt 1 nicht läuft,
   nichts am DNS ändern.
3. **DNS beim Domain-Inhaber setzen.** Für `www.tbh.co.at` genügt ein
   CNAME auf `tbh-stefan.github.io`. Für die nackte Domain
   `tbh.co.at` sind stattdessen vier A-Records nötig:
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`,
   `185.199.111.153`.
4. **`CNAME`-Datei anlegen** — eine Datei namens `CNAME` im
   Wurzelverzeichnis, Inhalt ist die gewünschte Adresse (eine Zeile,
   z. B. `www.tbh.co.at`). Sinnvoll erst, wenn das DNS steht: sobald
   die Datei existiert, leitet GitHub die `github.io`-Adresse auf die
   eigene Domain um.
5. **HTTPS erzwingen** — in den Pages-Einstellungen „Enforce HTTPS“
   aktivieren, sobald das Zertifikat ausgestellt ist.

**Achtung bei den bestehenden Einträgen:** Unter `tbh.co.at` läuft
bereits die E-Mail (`office@tbh.co.at`) und möglicherweise eine
bestehende Seite. Die MX-Records dürfen dabei nicht angetastet werden,
sonst steht die Firmen-E-Mail. Im Zweifel zuerst nur `www` umstellen
und die nackte Domain unverändert lassen.
