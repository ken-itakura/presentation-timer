# Presentation Timer

[English](README.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [हिन्दी](README.hi.md) | [Español](README.es.md) | [Français](README.fr.md) | [العربية](README.ar.md) | [বাংলা](README.bn.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Bahasa Indonesia](README.id.md) | [Deutsch](README.de.md) | [한국어](README.ko.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md)

A one-page timer for self-introductions at reunions and similar events. Just open `index.html` in a browser — no installation, server or internet connection needed.

## Usage

1. Open `index.html` in a browser (Safari / Chrome).
2. On the setup screen: load a CSV (see `sample/participants.csv`, or use “Load sample”), toggle attendance for each person, sort by any field, set the title / time per speaker / honorific / language, and test the sounds.
3. Press “Go to timer” (this also enables audio).
4. Run the timer:

| Action | Effect |
|---|---|
| `Space` / Start button | Start the next speaker (with applause) |
| Click a name in the right-hand list | Start that person; everyone before them moves to “Skipped” |
| Click a name in the Skipped list | Start that person |
| Uncheck “Present” in the Skipped list | After confirmation, mark them absent and remove them (the timer keeps running) |

10 s left: a tick every second · 3 s left: rapid beeps · 0 s: explosion sound and a “Time's up” label. The top right shows total elapsed time; the right column shows the next 10 speakers.

## CSV format

The first row is the header. UTF-8 and Shift_JIS are detected automatically. The name and honorific columns are auto-detected from the header (e.g. `name`, `honorific`, or their translations) and can be changed in settings. If a person's honorific cell is empty, the default honorific is used.

```csv
name,honorific,group,year
Alex Morgan,,A,2001
Sam Rivera,Dr.,B,2001
```

## Languages

16 languages: switch with “Language” on the setup screen (the browser language is used at first and your choice is saved). UI text, default title, default honorific, sample data and honorific position (before/after the name) follow the language; Arabic uses a right-to-left layout. Translations have not been reviewed by native speakers — edit `I18N` in `index.html` to fix them. To add a language, add entries to `LANGS`, `I18N` and `SAMPLE_NAMES`.

## Mobile

Layouts for portrait and landscape phones. On iPhone, the silent switch mutes sound. Opening the file via the Files app is the most reliable; with GitHub Pages you can simply open a URL.

## Structure

```
.
├── index.html            # app (HTML / CSS / JavaScript in one file)
├── sample/
│   └── participants.csv  # sample list
├── README.md             # + README.<lang>.md (16 languages)
```

`index.html` contains everything: the i18n dictionary, a CSV parser, the setup view, Web Audio sound synthesis (no audio files), timer logic (timestamp-based, so it does not drift) and the run view. Settings and progress are saved automatically to `localStorage`.

License: not specified
