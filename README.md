# regnum

A daily history game. You get the years of a monarch's reign and a map of their realm as it stood when the reign ended. Name the ruler in three guesses.

**Play:** https://aaditya3625.github.io/regnum/

## How it plays
- The map shades the ruler's territory. The corner shows the reign, from accession (purple) to end (gold).
- Each wrong guess tells you how far apart the reigns were, and puts the guessed ruler's own territory and capital on the map.
- There are four optional hints: first letter, trivia, capital and dynasty. Opening the capital hint adds the distance and direction to each guess; opening the dynasty hint adds a "same dynasty" tag.
- There's a new monarch every day, plus unlimited practice rounds.

## Data & credits
- **Historical borders:** [historical-basemaps](https://github.com/aourednik/historical-basemaps) by André Ourednik and contributors, licensed under GPL-3.0. Each puzzle uses the snapshot nearest the end of the reign. The borders are smoothed and fitted to Natural Earth coastlines, so they're approximate.
- **Coastlines:** [Natural Earth](https://www.naturalearthdata.com/) 1:50m land (public domain), via [world-atlas](https://github.com/topojson/world-atlas) (ISC).
- **Reign dates, capitals, dynasties and trivia** follow standard references. Where historians disagree, the dates are approximate. Corrections are welcome.
- **Fonts:** Space Grotesk and Nunito Sans (SIL Open Font License), served by Google Fonts.
- Format inspired by [Lifelines](https://lifelines.day). This is an independent project with no affiliation.

## Building
`index.html` is self-contained. To regenerate it:

```
cd build
git clone --depth 1 https://github.com/aourednik/historical-basemaps   # source borders
npm i world-atlas@2 topojson-client@3 && node make_land.js            # coastlines
pip install shapely
python build2.py      # -> puzzles2.json
python assemble.py    # -> ../index.html
```

Edit `monarchs.py` (rulers, reign years, map snapshots, capitals) and `trivia.py` to change the puzzle pool.

## Licence
GPL-3.0, because the game embeds geometry derived from historical-basemaps. See `LICENSE`.
