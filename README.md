# binary-spotlight

A cryptic landing page: glitchy binary rain in the logo's palette, a flashlight that follows the cursor (or finger), a glitching logo that always stays on top, and hidden text scattered at random positions on every refresh. Hovering a text plays its sound.

Everything lives in a single `index.html` — no build step, no dependencies.

## Adding audio

Open `index.html` and find the `ITEMS` list near the top of the script:

```js
const ITEMS = [
  { text: 'placeholder text 01', src: '' },                                    // test tone
  { text: 'placeholder text 02', src: 'audio/track-02.mp3' },                  // file in this repo
  { text: 'placeholder text 03', src: 'https://soundcloud.com/artist/track' }, // SoundCloud
];
```

- Empty `src` plays a test tone.
- Direct audio files (mp3/m4a/ogg) are the most reliable. Put them in an `audio/` folder in this repo and use a relative path.
- SoundCloud tracks must be public.

Other settings just below the list:
- `FADE_MS`: fade in/out time in ms.
- `STOP_ON_LEAVE`: `false` keeps a track playing until another text is hovered.

Browsers block sound until the visitor's first click, tap or key press. The page unlocks audio silently on that first interaction.

## Spacing between texts

In `placeTags()`, raise the `0.12` in `Math.max(48, Math.min(vw, vh) * 0.12)` to spread texts further apart.

## Hosting with GitHub Pages

Settings → Pages → Source: "Deploy from a branch" → Branch: `main`, folder `/ (root)` → Save.
The site will be live at `https://<your-username>.github.io/binary-spotlight/` after a minute or two.
