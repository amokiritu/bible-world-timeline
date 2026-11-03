# Bible & World Timeline

An interactive timeline from creation to AD 100 that lines up the people and events of the Bible against the empires, rulers and thinkers of the ancient world. It is published with GitHub Pages at https://amokiritu.github.io/bible-world-timeline/. Every push to `main` updates the live site within a minute or two.

The owner is a church elder and finance professional, not a developer. Explain changes in plain language with no technical jargon, and keep replies short.

## How the project is built

- **Everything is in `index.html`**: styles, data and script. There is no build step, framework or package manager. Open the file in a browser to test it.
- The only outside resource is Google Fonts (Cinzel, Alegreya Sans, IBM Plex Mono). Keep it a single file that works offline apart from the fonts.
- `README.md` is the public description. Update it when features change.

## Where things are in index.html

- `<style>` at the top: colour tokens on `:root`, with dark values under `prefers-color-scheme: dark` (guarded by `:root:not([data-theme="light"])`) and again under `:root[data-theme="dark"]`. Any new colour must be a token defined in all three places.
- `START`, `END`: the year span (negative numbers are BC, with no year 0).
- `LANES`: the eight tracks. `ERAS`: the shaded era bands. `JUMPS`: the "Jump to" buttons.
- **Data**: one block per track, each a list of rows passed to `add(lane, name, start, end, note, reference, flags)`.
  - `start === end` draws a diamond (single event); otherwise a bar.
  - Flags: `m` = major (bold, always labelled), `c` = approximate, shown with "c." before the date (anything before 900 BC gets "c." automatically), `g` = Genesis 1–11 genealogy date (dashed outline, shows "year of the world").
  - An entry's id is its name turned into a slug, so names must stay unique. `STORIES` cards point at these ids.
- `STORIES`: the "Where the Bible meets world history" cards: `[id, date label, title, text]`.
- Script sections are marked `// ---------- name ----------`: helpers, state and rendering, overview strip, detail panel, controls, phone bottom card, pinch zoom, full screen, light/dark, start.

## Dating conventions (keep consistent)

- **Genesis 1–11**: ages in Genesis 5 and 11 (Hebrew text) added up and counted back from Abraham's birth in 2166 BC. Creation c. 4174 BC, Flood c. 2518 BC. Year of the world = year + 4174.
- **Abraham onward**: traditional "early Exodus" chronology. Exodus 1446 BC (1 Kings 6:1), Solomon's temple 966–959 BC, kings by Edwin Thiele's dates.
- **Egypt and Mesopotamia**: standard (middle) chronology.
- **Jesus**: birth c. 5 BC, crucifixion AD 30 (AD 33 noted as the alternative).
- Where scholars disagree, say so in the entry's note and in the "About the dates" footer rather than picking a side silently.
- Notes are one or two plain sentences. References use full book names (e.g. "2 Kings 18–19").

## Before pushing a change

Check the page in a browser:

1. Desktop width (about 1600px) and phone width (about 390px), with no sideways scrolling of the whole page.
2. Light and dark (use the Auto / Light / Dark switch).
3. Full screen (button or F key), then Esc to leave.
4. Select an entry and check the "at the same time" list.
5. No errors in the browser console.

Write commit messages in plain English that say what changed for the reader.
