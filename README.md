# Bob AI

A study buddy that runs right in your browser, no downloads. Made by FallGameDev (Wildcard Studios).

Everything lives in one file: `index.html`.

## What Bob can do

- **K-12 math:** lessons from counting to calculus, plus a solver that shows every step (equations, quadratics, fractions, percents, area and volume, slope, GCF and LCM, primes, stats, trig, and more)
- **Games, creators, history, and language/AI topics** from the training corpus PDF
- **Quiz mode:** keeps asking questions and grades your answers
- **Online lookups:** if Bob doesn't know a person, he checks Wikipedia (and YouTube, if you add a free API key in Settings) and links to Social Blade and ViewStats

## Login keys

People need a key to get past the home page. Keys are saved in the code as SHA-256 hashes, so the real keys never show up in the source.

**Add a key**
1. Open the site with `#makekey` at the end of the address
2. Type who it's for, type a key (or press Random), then press **Make line**
3. Paste the line into the `LOGIN_KEYS` list in `index.html` (delete the `// key:` note first) and push

**Remove a key:** delete its line from `LOGIN_KEYS`. Anyone using it gets logged out the next time they open Bob.

This is a fun lock, not real security. Since everything runs in the browser, someone who knows code could get around it. A real lock would need a server (like Supabase).

## Saved in the browser (localStorage)

| Key | What it holds |
| --- | --- |
| `bob-login` | Which login key you used |
| `bob-profile` | Display name, avatar color, online search setting, YouTube API key |
| `bob-chats` | Your chat history |
| `bob-learned` | People Bob looked up online |
