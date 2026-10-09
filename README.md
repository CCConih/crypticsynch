# crypticsynch

A cryptic landing page: falling "171026" code rain, a cat logo drawn in falling "H" characters in the centre, the 1024 mark drawn in "1024" characters at the top, a flashlight that follows the cursor (or finger), and three hidden texts that play a teaser when hovered. A CRT overlay and old-TV noise sit on top of everything.

Everything lives in a single `index.html`, with the teasers in `audio/`. No build step, no dependencies. It is served with GitHub Pages and can be embedded elsewhere (e.g. Squarespace) with an iframe:

```html
<iframe src="https://ccconih.github.io/crypticsynch/" allow="autoplay"
        style="width:100%;height:100vh;border:0;display:block"></iframe>
```

## Audio

Find the `ITEMS` list in the script:

```js
const ITEMS = [
  { text: 'teaser 1', src: 'audio/Berdansalah%20-%20Teaser%2040%20Sec.mp3' },
  ...
];
```

- Put files in `audio/` and use a relative path. Write spaces in file names as `%20`.
- An empty `src` plays a test tone.
- `FADE_MS`: fade in/out time in ms. `STOP_ON_LEAVE`: `false` keeps a track playing until another text is hovered.

Browsers block sound until the visitor's first click, tap or key press; the page unlocks audio silently on that first interaction. Leaving the tab stops the music.

## Settings worth knowing

| Setting | What it does |
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

## Spacing between texts

In `placeTags()`, raise the `0.12` in `Math.max(48, Math.min(vw, vh) * 0.12)` to spread texts further apart. Texts are re-placed whenever the window size changes.
