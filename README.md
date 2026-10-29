# S01E03 · what it shows

The support desk merged 412 reports about dates into ticket #4471 and marked it known as one parser bug. The kb export shows two causes, not one.

## Tickets

- [#1 · Parser reads dates month first](https://github.com/dkey1994macmini1/mega-s01e03-what-it-shows/issues/1) — **379 reports**
- [#2 · booking-v3 hint prints MM/DD/YYYY but the form reads day first](https://github.com/dkey1994macmini1/mega-s01e03-what-it-shows/issues/2) — **33 reports**

## The page

- source: [`support-kb/src/routes/kb/incidents/4471-causes/+page.svx`](support-kb/src/routes/kb/incidents/4471-causes/+page.svx)
- rendered: [`rendered/4471-causes.html`](rendered/4471-causes.html)

## How the counts were reached

- The export has 427 rows; 15 ids appear twice, so `uniqueById` leaves **412** reports, the number the desk counted.
- `causeOf` uses the tenant's locale (`Intl.DateTimeFormat`) and the booking form's hint, not `meta.intakeTag`.
- `parser`: 379 reports, 11 tenants, 2026-04-01 → 2026-10-04.
- `hint`: 33 reports, 3 booking-v3 tenants, 2026-04-17 → 2026-09-22.
- No report is unplaced: every tenant handle is on file and every locale writes the day first.
- Five parser reports read as a one-day move (R-41202, R-41209, R-41236, R-41344, R-41620). `desk-notes.json` keeps them counted where filed, so they are footnoted under `parser`, not split out.

## Signature

The page carries the `signature` ticket from `start-challenge` in its frontmatter and ends with `<RenderStamp {signature} />`. The stamp renders as desk ref **DR-0FPZ-B19H**.

## What the desk should do

Split #4471 into the two tickets, keep the parser fix as the known issue, and open the 33 form reports as their own.
