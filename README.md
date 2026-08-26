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

- **Auftragsverarbeitungsvertrag mit Wix** abschließen bzw. den in den
  Wix-Nutzungsbedingungen enthaltenen DPA aktiv annehmen. Die
  Datenschutzerklärung setzt ihn bereits als bestehend voraus.
- **Cookie-Banner in Wix aktivieren.** Die Datenschutzerklärung sagt zu,
  dass nicht notwendige Cookies und Wix Analytics nur nach Einwilligung
  laufen. Ohne aktivierten Consent-Dialog stimmt diese Zusage nicht.
- **Wix-Unterauftragsverarbeiter** gegen die aktuelle Liste von Wix
  prüfen. Im Text stehen Israel (Angemessenheitsbeschluss 2011/61/EU)
  und Standardvertragsklauseln für die übrigen Drittstaaten.
- **Gewerbebehörde** im Impressum gegen den Gewerbeschein prüfen —
  eingetragen ist die Bezirkshauptmannschaft Wiener Neustadt.
- **Kontaktformular**: Es öffnet derzeit das E-Mail-Programm des
  Besuchers, es gibt keinen Serverversand. Für echten Versand ist die
  Stelle im Skript markiert. Kommt ein Backend dazu, muss der Absatz
  „Kontaktaufnahme“ mitwachsen.
- Rechtstexte vor der Veröffentlichung von der WKO-Rechtsberatung prüfen
  lassen.

## Veröffentlichen

Noch nicht aktiv — und mit Wix als Hoster ist der Weg nicht trivial:

Wix ist ein Baukasten, kein Webspace. Eine fertige `index.html` lässt
sich dort **nicht** als Startseite hochladen. Realistische Wege:

1. **Seite im Wix-Editor nachbauen.** Diese Datei dient dann als
   Vorlage für Layout, Texte und Farben. Die Rechtstexte lassen sich
   direkt übernehmen.
2. **Wix nur für die Domain nutzen**, die Seite selbst woanders
   ausliefern (GitHub Pages, Netlify, Cloudflare Pages, klassischer
   AT-Hoster) und `tbh.co.at` dorthin zeigen lassen. Dann stimmen die
   Wix-Angaben in der Datenschutzerklärung nicht mehr — der Abschnitt
   „Hosting & technischer Betrieb“ muss auf den tatsächlichen Anbieter
   umgeschrieben werden.
3. **Wix-HTML-Einbettung.** Die Seite läuft in einem iframe innerhalb
   einer Wix-Seite. Technisch möglich, aber schlecht für Suchmaschinen
   und die Adresszeile — nicht empfohlen.

Für GitHub Pages (Weg 2): unter Settings → Pages den Branch auswählen;
`index.html` liegt bereits im Wurzelverzeichnis. Bei einem privaten
Repository setzt Pages ein kostenpflichtiges GitHub-Konto voraus.
