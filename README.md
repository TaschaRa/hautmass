# Hautmaß — Abschlussprojekt Woche 8

Natascha Rampp · September 2026

**Live:** https://taschara.github.io/hautmass/

> **Alles auf dieser Seite ist erfunden.** Die Hautmaß GmbH gibt es nicht, ebenso wenig die
> fünf Filialen, ihre Adressen und die Kundenstimmen. Die Telefonnummern stammen aus den
> Bereichen, die die Bundesnetzagentur für Film- und Fernsehproduktionen reserviert hat —
> dort ist niemand erreichbar. Das Produktbild wurde mit einer Bild-KI erstellt. Die
> Wirkstoffangaben sind eine beispielhafte Auswahl und keine geprüfte Herstellungsrezeptur.

---

## Worum es geht

Hautmaß ist ein erfundenes Gesichtsserum, das erst nach einer Hautanalyse in der Filiale
gemischt wird. Gemessen werden Feuchtigkeit und Talgproduktion, dazu kommen Fragen zur
Empfindlichkeit. Jeder Wirkstoff steht mit seiner Konzentration auf der Flasche.

Kernbotschaft: *Mit Hautmaß kaufst du deine Pflege nicht mehr auf Verdacht.*
Claim: *Erst messen, dann mischen.*

## Die Dateien

| Datei | Inhalt |
| --- | --- |
| `index.html` | Startseite, elf Abschnitte |
| `fragen.html` | Häufige Fragen, zehn Stück, aufklappbar |
| `kontakt.html` | Formular für die Terminanfrage |
| `anfrage.html` | Bestätigung nach dem Absenden |
| `flasche.jpg` | Produktbild, 1500 × 1000 Pixel, mit KI erstellt |
| `logo.png` | Logo, dunkle Fassung |
| `logo-weiss.png` | Logo, helle Fassung für die Fußzeile |

Alle Dateien liegen im selben Ordner. Im Code steht nur der kurze Name, kein Pfad.
Jede HTML-Datei trägt ihr Aussehen selbst im `<style>`-Block — es gibt bewusst keine
gemeinsame CSS-Datei, damit keine Seite von einer anderen abhängt.

## Gestaltung

Fließtext 18 Pixel, Zeilenhöhe 1,6, Textspalte 600 Pixel
(rund 70 Zeichen), Absatzabstand 40 Pixel, alle Abstände Vielfache von acht, am Handy
16 Pixel Seitenrand. Eine Schrift (Jost, mit Ersatzliste). Genau zwei Knöpfe auf der
Startseite, beide „Termin buchen".

Farben: Tiefblau `#12283F`, Text `#16202B`, helle Fläche `#EDF1F4`, Akzent `#0B7D72` auf
hellem und `#35C4B0` auf dunklem Grund. Alle Kombinationen auf Kontrast gemessen, der
schwächste Wert liegt bei 5,0 zu 1.

Die Seite erscheint immer hell, auch auf Geräten im Dunkelmodus — sonst kehrt der Browser
die geprüften Farben um.

## Technik

Reines HTML und CSS, **kein JavaScript**, keine fremden Bibliotheken, keine Cookies, keine
Zählpixel. Der Aufklapper bei den Wirkstoffen und den Fragen ist natives `<details>`. Das
Laufband mit den Kundenstimmen läuft über eine CSS-Animation; der Pause-Knopf ist ein
unsichtbares Kontrollkästchen. Wer im Betriebssystem „Bewegung reduzieren" eingestellt hat,
sieht die Stimmen ruhig nebeneinander.

## Das Kontaktformular

`kontakt.html` schickt die Anfrage per POST an einen Webhook bei n8n. Dort prüft ein
If-Knoten ein unsichtbares Feld gegen automatische Einträge, ein Outlook-Knoten verschickt
die Anfrage als Mail an das Kurspostfach und ein Respond-Knoten leitet mit Statuscode 303
auf `anfrage.html` weiter. Der Absender bekommt keine Bestätigungsmail.

**Hinweis:** Das n8n-Probekonto läuft nach 14 Tagen ab. Danach nimmt das Formular zwar noch
Eingaben an, es kommt aber nichts mehr an.

## Kennzeichnungen auf der Seite

Unter dem Produktbild steht „Produktbild mit KI erstellt". Über dem Band mit den
Kundenstimmen steht, dass Personen und Aussagen erfunden sind. Unter den Filialen steht,
woher die Telefonnummern stammen. In der Fußzeile steht „Beispielseite aus dem Kurs".
