# Bob AI

A study buddy that runs right in your browser, no downloads. Made by FallGameDev (Wildcard Studios).

Everything lives in one file: `index.html`.

## What Bob can do

- **K-12 math:** lessons from counting to calculus, plus a solver that shows every step (equations, quadratics, fractions, percents, area and volume, slope, GCF and LCM, primes, stats, trig, and more)
- **Games, creators, history, and language/AI topics** from the training corpus PDF
- **Quiz mode:** keeps asking questions and grades your answers
- **Online lookups:** if Bob doesn't know a person or thing, he checks Wikipedia, then Wikidata (and YouTube, if you add a free API key in Settings) and links to Social Blade and ViewStats
- **Response settings:** length (Summary, On point, Detailed), type (Explanatory, Visual, Both), and gist (Serious, Calm, Slang, Cute)
- **Visuals:** pictures from the topic's Wikipedia article, plus math diagrams Bob draws himself (step cards, shapes, graphs, fraction bars, percent grids, bar charts)
- **Saved answers:** answers are cached on your device, so asking again is instant
- **Business finder:** "pizza near me", "Walmart hours", "phone number for CVS in Miami" use OpenStreetMap for address, hours, phone, and website, plus a button to the Google Business profile on Google Maps
- **Image maker:** "draw a cat in space" searches the web for free SVG templates (whole pictures, backgrounds, and coloring pages from Wikimedia Commons, plus objects from Iconify), then edits them: recolors, places, sizes, and adds words or a frame. Try another pages through results forever, plus PNG and SVG downloads
- **+ menu:** Upload files, Create image, Research, and Create website
- **Uploads:** text files (.txt, .md, .csv, .html...) become part of Bob's knowledge so you can ask about them; pictures go into websites
- **Research:** reads several Wikipedia articles and writes a report with a summary, overview, key facts, a fun fact, related topics, and numbered sources
- **Website builder:** searches GitHub for a free license template (MIT, Apache, and others), downloads its HTML, CSS, and JS, swaps in your pictures, recolors its main colors to yours, and puts your name and topic in the logo, title, and big headings. The files show in the chat, with a side panel for a live preview (computer, tablet, phone), code view, .zip download, and Try another template. Brand clones and unlicensed repos are skipped
- **Chats and projects:** rename, delete, or move chats into project folders, and edit your messages to get a new answer
- **Report a bug:** builds a full report and opens Gmail, Outlook, Yahoo, AOL, or Proton

## Accounts (Supabase)

People sign in with **Google**, **GitHub**, or **email** (a sign-in link, or a password with "Forgot password?"). Each account gets its own chats, projects, and settings on the device. Names and profile pictures come from Google or GitHub automatically.

Bob is connected to the Supabase project **bob-ai** (`msvjvnlczfbsipaxktti`, in the Here Studios organization). Email sign-in is on. Google and GitHub need their Client Secrets added in Supabase (see below).

If the Supabase keys are ever removed, the home page shows a setup note and a **Try Bob without an account** button.

### One-time setup

1. Make a free project at [supabase.com](https://supabase.com).
2. **Project Settings > API:** copy the **Project URL** and the **anon public** key into `SUPABASE_URL` and `SUPABASE_ANON_KEY` at the top of PART 9 in `index.html`. (The anon key is meant to be public.)
3. **Authentication > URL Configuration:** set **Site URL** to `https://fallgamedev.github.io/bob-ai/` and add the same address under **Redirect URLs**.
4. **Authentication > Providers > Email:** it's on by default. Sign-in links and password sign up both use it.
5. **Authentication > Providers > GitHub:** on GitHub go to **Settings > Developer settings > OAuth Apps > New OAuth App**. Use your site as the homepage and `https://<your-project-id>.supabase.co/auth/v1/callback` as the callback URL. Paste the Client ID and a new Client Secret into Supabase.
6. **Authentication > Providers > Google:** in [Google Cloud Console](https://console.cloud.google.com/apis/credentials) make an **OAuth client ID** (Web application). Add `https://<your-project-id>.supabase.co/auth/v1/callback` as an authorized redirect URI, then paste the Client ID and Secret into Supabase.

Google and GitHub sign in only work on the real website (like GitHub Pages), not when opening the file directly.

## Saved in the browser (localStorage)

Sign-in itself is handled by Supabase (it saves its own session). Bob's data is saved per account:

| Key | What it holds |
| --- | --- |
| `bob-profile:<account>` | Display name, avatar color, response settings, your city, online search setting, YouTube API key |
| `bob-chats:<account>` | Your chat history (and which project each chat is in) |
| `bob-projects:<account>` | Your project folders |
| `bob-learned` | People and things Bob looked up online |
| `bob-cache` | Saved answers (up to 200, cleared when Bob's version changes) |
