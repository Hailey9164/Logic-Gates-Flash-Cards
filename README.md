# Logic Gates — Field Notes

A single-file, self-contained HTML flashcard app for studying digital logic gates: gate symbols, truth tables, boolean formulas, and practice questions.

No build step, no dependencies, no server required — everything (including diagrams) is embedded directly in one `.html` file.

## Features

- **Logic Gates deck** — flip cards covering all the standard gates (Buffer, NOT, AND, OR, NAND, NOR, XOR, XNOR, etc.), each with three views:
  - **Symbol** — the gate's circuit symbol
  - **Truth table** — inputs/outputs for every combination
  - **Formula** — the boolean expression
- **Practice Questions deck** — applied questions (e.g. combinational logic, half/full adders) with answers on the flip side
- Tap a card to flip it; `prev` / `next` to move through the deck
- Card counter (`x / 26`) so you can track progress
- Fully offline — diagrams are embedded as data URIs, no images load from the network

## Usage

1. Open `logic-gate-flashcards.html`.
2. Use the top tabs to switch between **Logic Gates** and **Practice Questions**.
3. Within the Logic Gates deck, use **Symbol / Truth table / Formula** to change what the front of the card shows.
4. Tap the card to flip between question and answer.
5. Use **← prev** / **next →** to move through the deck.

### ⚠️ Opening on iPhone/iPad

If you tap the file directly from Files, Messages, or Mail, iOS opens it in **Quick Look**, which renders the layout but does **not run JavaScript** — cards will look empty and buttons won't respond. To fix this:

1. Tap the Share icon in Quick Look.
2. Choose **Open in Safari** (or **Open in Browser**). If it's not offered, save the file to the Files app first, then Share → Open in Safari from there.
3. Confirm it opens with a real Safari address bar (not a filename/chevron bar) — that means JS is running.

## Project structure

Everything lives in one file: `logic-gate-flashcards.html`

| Section | Contents |
|---|---|
| `<style>` | Layout, theme, and the 3D flip-card CSS |
| `GATES` (JS array) | Gate data: id, name, symbol type, truth table, formula |
| `QUESTIONS` (JS array) | Practice question data: prompt, answer, optional diagram/formula |
| Render logic | Vanilla JS — builds card content, handles tab/flip/nav state, no frameworks |

## Customizing

- **Add a gate**: add an entry to the `GATES` array with `id`, `name`, `symbolType`, `bubble`, `universal`, `truth` (headers + rows), and `formula`.
- **Add a practice question**: add an entry to the `QUESTIONS` array with a prompt and answer.
- **Styling**: colors, fonts, and card sizing are controlled via CSS custom properties near the top of the `<style>` block.

## Compatibility notes

The flip animation uses 3D CSS transforms (`transform-style: preserve-3d`, `backface-visibility: hidden`) with `-webkit-` prefixes and a `translateZ(0)` compositing hint for iOS Safari, which has historically had bugs hiding elements that combine `backface-visibility: hidden` with `overflow: auto`. Tested to work in modern mobile and desktop browsers when opened as an actual webpage (not a Quick Look preview — see above).# Logic Gates Flash Cards

