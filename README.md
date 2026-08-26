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

- **Hosting-Provider** in der Datenschutzerklärung eintragen (steht dort
  als einziger Platzhalter). Mit dem Provider ist ein
  Auftragsverarbeitungsvertrag nach Art. 28 DSGVO nötig.
- **Gewerbebehörde** im Impressum gegen den Gewerbeschein prüfen —
  eingetragen ist die Bezirkshauptmannschaft Wiener Neustadt.
- **Kontaktformular**: Es öffnet derzeit das E-Mail-Programm des
  Besuchers, es gibt keinen Serverversand. Für echten Versand ist die
  Stelle im Skript markiert.
- Der Abschnitt „Cookies und Reichweitenmessung“ sagt zu, dass die Seite
  keine Cookies, kein Tracking und keine externen Dienste einbindet. Das
  stimmt für den jetzigen Stand — sobald ein Formular-Backend, Google
  Fonts, eine Karte oder Statistik dazukommt, muss der Absatz mitwachsen.
- Rechtstexte vor der Veröffentlichung von der WKO-Rechtsberatung prüfen
  lassen.

## Veröffentlichen

Noch nicht aktiv. Für GitHub Pages: unter Settings → Pages den Branch
auswählen; `index.html` liegt bereits im Wurzelverzeichnis. Bei einem
privaten Repository setzt Pages ein kostenpflichtiges GitHub-Konto
voraus.
