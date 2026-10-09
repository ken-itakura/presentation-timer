# Vorstellungs-Timer

[English](README.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [हिन्दी](README.hi.md) | [Español](README.es.md) | [Français](README.fr.md) | [العربية](README.ar.md) | [বাংলা](README.bn.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Bahasa Indonesia](README.id.md) | [Deutsch](README.de.md) | [한국어](README.ko.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md)

Ein Ein-Seiten-Timer, damit sich bei Klassentreffen und ähnlichen Anlässen alle der Reihe nach vorstellen. `index.html` einfach im Browser öffnen — ohne Installation, Server oder Internetverbindung.

## Verwendung

1. `index.html` im Browser öffnen (Safari / Chrome).
2. Im Einstellungsbildschirm: CSV laden (siehe `sample/participants.csv` oder „Beispiel laden“), Anwesenheit je Person umschalten, nach beliebigem Feld sortieren, Titel / Zeit pro Person / Anrede / Sprache festlegen und die Töne testen.
3. „Zum Timer“ klicken (das aktiviert auch den Ton).
4. Den Timer bedienen:

| Aktion | Wirkung |
|---|---|
| `Leertaste` / Start-Button | Nächste Person starten (mit Applaus) |
| Klick auf einen Namen in der rechten Liste | Diese Person starten; wer davor stand, wandert zu „Übersprungen“ |
| Klick auf einen Namen unter „Übersprungen“ | Diese Person starten |
| „Anwesend“ unter „Übersprungen“ abwählen | Nach Bestätigung als abwesend markieren und entfernen (der Timer läuft weiter) |

Noch 10 s: jede Sekunde ein Ticken · noch 3 s: schnelle Pieptöne · bei 0 s: Explosionsgeräusch und Hinweis „Zeit abgelaufen!“. Oben rechts steht die gesamte vergangene Zeit, in der rechten Spalte die nächsten 10 Personen.

## CSV-Format

Die erste Zeile ist die Kopfzeile. UTF-8 und Shift_JIS werden automatisch erkannt. Die Spalten für Name und Anrede werden anhand der Kopfzeile gewählt (z. B. `name`, `anrede`) und lassen sich in den Einstellungen ändern. Ist die Anrede-Zelle leer, gilt die Standard-Anrede.

```csv
name,honorific,group,year
Alex Morgan,,A,2001
Sam Rivera,Dr.,B,2001
```

## Sprachen

16 Sprachen: Umschalten über „Sprache“ im Einstellungsbildschirm (zunächst wird die Browsersprache verwendet, Ihre Wahl wird gespeichert). Oberflächentexte, Standardtitel, Standard-Anrede, Beispieldaten und die Position der Anrede (vor/nach dem Namen) folgen der Sprache; Arabisch nutzt ein Rechts-nach-links-Layout. Die Übersetzungen wurden nicht von Muttersprachlern geprüft — zum Korrigieren `I18N` in `index.html` bearbeiten. Zum Hinzufügen einer Sprache Einträge in `LANGS`, `I18N` und `SAMPLE_NAMES` ergänzen.

## Mobil

Layouts für Smartphones im Hoch- und Querformat. Beim iPhone schaltet der Stummschalter den Ton aus. Am zuverlässigsten ist das Öffnen über die Dateien-App; mit GitHub Pages genügt das Öffnen einer URL.

## Aufbau

```
.
├── index.html            # app (HTML / CSS / JavaScript in one file)
├── sample/
│   └── participants.csv  # sample list
├── README.md             # + README.<lang>.md (16 languages)
```

`index.html` enthält alles: das Sprachwörterbuch, einen CSV-Parser, den Einstellungsbildschirm, die Tonsynthese per Web Audio (keine Audiodateien), die Timer-Logik (zeitstempelbasiert, daher ohne Drift) und den Ablaufbildschirm. Einstellungen und Fortschritt werden automatisch in `localStorage` gespeichert.

Lizenz: nicht angegeben
