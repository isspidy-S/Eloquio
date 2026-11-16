# Eloquio

A voice-only practice partner for speaking clearly. Runs as a static web page.

## Put it online (free)
1. On GitHub, create a repository named `eloquio` (public).
2. Upload `index.html`, `README.md`, and a `voices` folder (see below) to the repository root.
3. Go to Settings, then Pages. Set Source to "Deploy from a branch", branch `main`, folder `/ (root)`. Save.
4. After about a minute, open `https://<your-username>.github.io/eloquio/` in Chrome, tap Start, and allow the microphone.

## Use your own voice for the coach
Record each line below, export it as MP3, and save it in a `voices` folder with the exact file name. Any missing file falls back to the device voice.

| File | Line |
|---|---|
| voices/warmup.mp3 | Warm-up. Tell me what you did today. |
| voices/more.mp3 | Tell me more about that. |
| voices/next.mp3 | What happened next? |
| voices/who.mp3 | Who else was involved? |
| voices/best.mp3 | What was the best part? |
| voices/why.mp3 | Why do you think that happened? |
| voices/choice1.mp3 | Was it more about the people or the situation? |
| voices/choice2.mp3 | Did that feel easy or hard? |
| voices/easy1.mp3 | Tell me about your favorite food. |
| voices/easy2.mp3 | Describe the room you’re in. |
| voices/easy3.mp3 | Tell me one thing you did this week. |

Only use your own voice or a voice you have clear permission to use.

## AI replies (details)
In `index.html`, set `AI_ENDPOINT` to the URL of your own small backend. Never put an AI key in this repository. The backend receives `{task, ...}` where task is `chat`, `word`, or `rewrite`, and returns `{text}`.

## Turn on the AI (free tier)
1. Get a free key at aistudio.google.com (Google account, no card). Keep it private.
2. Create a free Cloudflare account, then Workers & Pages, Create Worker. Paste in `worker.js` and deploy.
3. In the Worker's Settings, Variables and Secrets, add:
   - `GEMINI_API_KEY` (secret): your key
   - `ALLOWED_ORIGIN`: `https://<your-username>.github.io`
   - `MODEL` (optional): a current model name from AI Studio
4. Copy the Worker's URL, paste it into `AI_ENDPOINT` in `index.html`, and re-upload the file to GitHub.

Privacy note: on Google's free tier, requests may be used to improve Google products. Eloquio sends what the user says (as text) to the AI, so tell users, and consider the paid tier before launching publicly.
