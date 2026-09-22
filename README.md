# Meta Ads Profit Dashboard

A single-file, offline-capable dashboard that turns a Meta (Facebook) Ads export
into a **profit** picture for Shopify sellers — not just a ROAS number.

Available in Turkish, English, Spanish, German and Russian.

---

## Why this exists

Meta Ads Manager tells you your ROAS. It does not tell you whether you made money.

A 3× ROAS sounds great, but if your product margin is 25% your break-even is 4× —
so at 3× you are quietly losing money on every sale. This dashboard asks for one
number Meta never asks for (your profit margin), and reports what is actually left
in your pocket.

## What it does

- Reads a CSV or Excel export from Meta Ads Manager — **in any of the five supported
  languages**, since column names differ per account language
  (`Amount spent` / `Importe gastado` / `Ausgegebener Betrag` / `Потраченная сумма` / `Harcanan tutar`)
- Computes break-even ROAS from your margin, then flags every campaign as
  stop / losing / break-even / profitable / scale
- Estimates net profit per campaign and in total
- Groups by campaign, ad set or ad
- **Plain-language mode** that explains the numbers without a single piece of Meta
  jargon — for people who have never run an ad
- A 31-term glossary of Meta advertising vocabulary, in all five languages

---

## Privacy — and how to verify it yourself

**Your report is never uploaded anywhere.** The file is read by your browser, the
maths runs in the open tab, and the result is drawn on screen. Close the tab and it
is gone.

You do not have to take that on faith. In Chrome, Edge or Firefox:

1. Press <kbd>F12</kbd> (or right-click → *Inspect*)
2. Open the **Network** tab
3. Clear the list
4. Upload your report — **the list stays empty.** Nothing leaves your machine.

You can also disconnect from the internet entirely; CSV files still work.

### Being precise about what does happen

Two things are fetched when the page first loads, and both are generic files
identical for every visitor — neither carries any of your data:

| Resource | Host | Purpose |
|---|---|---|
| Typeface | `fonts.googleapis.com` / `fonts.gstatic.com` | Page rendering |
| `xlsx` library | `cdnjs.cloudflare.com` | Reading `.xlsx` files |

The only thing written to storage is your own settings — language, theme, profit
margin, spend threshold — kept in your browser's `localStorage`. It never leaves
your browser and contains none of your ad data.

There is **no** account, no email field, no password, no analytics, no tracking
cookie, no ad network and no server of any kind. There is nowhere for your data
to go, because there is no backend.

### Where to look in the code

Everything is in one file, `index.html`:

- `handleFile()` — uses `FileReader`; the file never leaves the page
- Search the file for `fetch`, `XMLHttpRequest` or `WebSocket` — there are none
- The only outbound references are the two `<script src>` / `<link href>` tags in
  the head, listed in the table above

---

## Running it

Download `index.html` and open it in a browser. That is the whole installation.
It works from a local file, from a USB stick, and offline (CSV only — reading
`.xlsx` needs the library fetched above).

## Getting your report out of Meta

Ads Manager → **Reports** → export as CSV or Excel. Make sure the columns
**Amount spent** and **Purchases conversion value** are included; without them
profit cannot be calculated. If a column is not recognised, the dashboard shows a
column-matching panel so you can map it by hand.

---

## License

**Source-available, not open-source.** You may read, audit and use this software
freely, including inside your own business. You may not redistribute it or offer
it to others as a product or service. See [LICENSE.md](LICENSE.md).

The code is published for verification, so that the privacy claims above are
checkable rather than merely stated.

## Status

Built and maintained by a Shopify seller who needed it. Issues and suggestions
welcome.
