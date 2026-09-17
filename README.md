# Warmup

A minimal training log that follows your Google Doc plan, suggests weights, warns when you are stuck, and tracks body weight. Everything is stored on your phone. The "intelligent" parts (voice → sets, photo of a paper sheet → sets, new plan document → app screens) call DeepSeek V4.1 Flash with your own API key.

## Files
- `index.html` — the whole app
- `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png` — what makes it installable and openable offline

## Put it on your phone (once, ~5 minutes)
The app must be served over https to be installable. GitHub Pages is free:

1. Create a new public repository on github.com, e.g. `warmup`.
2. Upload these five files to it (drag and drop on the repository page): `index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`.
3. Repository → Settings → Pages → Source: "Deploy from a branch", branch `main`, folder `/ (root)` → Save.
4. After a minute the app is at `https://<your-user>.github.io/warmup/`.
5. On the iPhone: open that URL in Safari → Share → "Add to Home Screen". On Android: Chrome → menu → "Add to Home screen".

Any other static host works too (Netlify, Vercel, Cloudflare Pages).

To update the app later, replace `index.html` in the repository; the phone picks it up on the next open with a connection.

## First use
Begin → your name → the block you are in → the week → the day. From then on the app moves to the next day, week and block by itself every time you tap "Finish session". If a week goes off plan, correct it in Plan & settings → "Where I am".

## AI features
Plan & settings → DeepSeek API key (from platform.deepseek.com). The key stays in the phone's storage and is only ever sent to api.deepseek.com.
- **Voice**: tap 🎤 on an exercise and say the sets, e.g. "80 kilos 8 reps, 80 8, 82.5 7". The phone transcribes, the AI turns it into sets.
- **Paper sheet**: at the end of the session tap "Fill from a photo of my sheet"; the AI reads the handwriting and fills every exercise it recognises. Check the numbers before finishing.
- **New plan**: Google Docs → File → Download → Plain text; paste the text in Plan & settings → "Convert with AI". The app rebuilds its blocks, weeks, days and exercises from it and asks where you are.

## Suggestions and warnings
- Suggested weight = last top weight + 2.5 %, rounded to 0.5 kg (at least +0.5 kg).
- Stuck = same top weight for the last three sessions of an exercise.
- Stats also flags "reps not dropping at a fixed weight" (too light) and "heavier weight, fewer reps" (as expected).

## Backup
Plan & settings → Export data saves a JSON file; Import data restores it (also for moving to a new phone).
