# Website TBH GmbH

Einseitige Website der TBH GmbH — Technisches Büro für Elektrotechnik,
Satzäcker 25, A-2752 Wöllersdorf.

Die gesamte Seite steckt in einer einzigen Datei: `index.html`.
Schriften, Grafiken und Skripte sind eingebettet, es gibt keine
Abhängigkeiten und keinen Build-Schritt. Zum Ansehen genügt es, die
Datei im Browser zu öffnen.

## Kompatibilität

Die Seite ist bewusst konservativ gebaut, damit sie auch auf älteren
Geräten und Browsern funktioniert:

- Vollständige Dokumentstruktur mit `<!DOCTYPE html>`, `<html lang="de">`
  und `<meta charset="utf-8">`. Ohne Doctype liefen Browser im
  Kompatibilitätsmodus („Quirks Mode“) und rechneten nach alten Regeln.
- Das JavaScript kommt ohne moderne Sprachfeatures aus — nur `var` und
  klassische Funktionen, keine Pfeilfunktionen, keine Klassen.
- Das CSS beschränkt sich auf Grid, `clamp()` und Custom Properties.
  Neuere Selektoren wie `:has()` stehen ausschließlich in einem
  `@supports`-Block; fehlt die Unterstützung, bleibt die Seite nutzbar.
- Impressum und Datenschutz funktionieren auch ohne JavaScript, siehe
  den Hinweis unter „Aufbau der Datei“.
- `prefers-reduced-motion` schaltet die Animationen ab.

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
| Titel, Beschreibung, Vorschaubild-Angaben | `<head>` am Dateianfang |
| Farben, Schriften, Layout | `<style>` im `<head>` |
| Kopfzeile und Navigation | `<header class="site">` |
| Startseite | `<main id="top">` mit den Abschnitten `hero`, `leistungen`, `ueber-uns`, `referenzen`, `kontakt` |
| Impressum | `<div id="impressum">` |
| Datenschutzerklärung | `<div id="datenschutz">` |
| Fußzeile mit Kontaktdaten | `<footer class="site">` |
| Skripte | `<script>`-Blöcke am Dateiende |

Impressum und Datenschutz sind eigene Seiten: Ein kleiner Router blendet
über `#impressum` bzw. `#datenschutz` die Startseite aus.

**Wichtig beim Umbenennen:** Die IDs `impressum` und `datenschutz`
müssen genau so heißen wie die Anker in den Links. Nur dann greift die
CSS-Rückfallebene über `:target`, die die Rechtsseiten auch ohne
JavaScript erreichbar hält — sonst zeigt der Browser bei abgeschaltetem
JavaScript nur die Startseite, und das Impressum wäre entgegen § 5 ECG
nicht aufrufbar.

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

Die Zieladresse ist **`www.tbh.co.at`**. Sie steht in der Datei
`CNAME` im Wurzelverzeichnis — GitHub liest sie beim Einschalten von
Pages aus und trägt die Domain automatisch ein.

Weil die Datei bereits vorhanden ist, gehört das DNS **zuerst**
gesetzt. Sonst zeigt Pages sofort auf eine Adresse, die noch nirgends
hinführt. Die Schritte in dieser Reihenfolge:

1. **DNS beim Domain-Inhaber setzen** — ein CNAME-Eintrag für die
   Subdomain `www` auf `tbh-stefan.github.io.` (mit Punkt am Ende).
   Kein A-Record, kein AAAA-Record für `www`.
2. **Pages einschalten** — im Repository unter Settings → Pages als
   Quelle Branch und Ordner `/` wählen. `index.html` liegt bereits im
   Wurzelverzeichnis, es braucht keinen Build-Schritt. Die Domain aus
   `CNAME` erscheint dort automatisch unter „Custom domain“.
3. **Zertifikat abwarten** — GitHub stellt es selbst aus, das dauert
   von ein paar Minuten bis zu einer Stunde. Solange kann eine
   Zertifikatswarnung erscheinen, das ist normal.
4. **HTTPS erzwingen** — in den Pages-Einstellungen „Enforce HTTPS“
   aktivieren, sobald das Zertifikat steht.

**Achtung bei den bestehenden Einträgen:** Unter `tbh.co.at` läuft die
Firmen-E-Mail (`office@tbh.co.at`). Angetastet wird nur die Subdomain
`www` — die MX-Records der Hauptdomain bleiben unverändert, sonst steht
die E-Mail.

Die nackte Domain `tbh.co.at` zeigt danach noch nicht auf die Seite;
wer sie ohne `www` eintippt, landet weiterhin beim alten Ziel. Wenn das
später auch umgestellt werden soll, braucht die Hauptdomain vier
A-Records auf `185.199.108.153`, `185.199.109.153`, `185.199.110.153`
und `185.199.111.153` — GitHub leitet dann selbst auf `www` um.
