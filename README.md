# crypticsynch

## Audio

Find the `ITEMS` list in the script:

```js
const ITEMS = [
  { text: 'teaser 1', src: 'audio/Berdansalah%20-%20Teaser%2040%20Sec.mp3' },
  ...
];
```
- An empty `src` plays a test tone.
- `FADE_MS`: fade in/out time in ms. `STOP_ON_LEAVE`: `false` keeps a track playing until another text is hovered.

Browsers block sound until the visitor's first click, tap or key press; the page unlocks audio silently on that first interaction. Leaving the tab stops the music.

## Settings 

| Setting | 
|---|---|
| `CHAR_PX` | Character size for the rain and both logos (8px). Smaller = more detailed logos, harder to read. |
| `LOGO_REVEAL_MS` | How long the logos take to form on load. |
| `LOGO_LEVEL` | Logo brightness: lower is bluer, higher is whiter. |
| `binaryLogo(..., false)` | The last argument turns a logo's drawn-in glitches (tears, colour split, scattered characters) on or off. |
| `TV_GRAIN` | Strength of the old-TV grain. Burst timing is in `stepTv()`. |
| `.logo` / `.logo.top` CSS | Size and position of the centre (cat) and top (1024) logos. |

Logos are embedded as masks (`LOGO_MASK`, `CAT_MASK`); only their shape (alpha) is used.

## Turning effects off

- CRT look: delete `<div class="crt">`.
- Old-TV noise: add `display: none;` to the `.tv` CSS rule (don't delete the canvas; the script uses it).
- Visitors with "reduce motion" turned on get a still version without the noise.

## Where the texts go
The three texts land at random spots in a band just under the cat. In `placeTags()`, `BAND` is how far below the cat they may go (140px) and `GAP` is the minimum space between two texts (12px). They are re-placed whenever the window size changes.
