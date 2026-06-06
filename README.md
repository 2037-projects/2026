# Summer Care Schedule — Deployment Project

A single-page, static website displaying the family's summer 2026 childcare schedule (July 7–30). Built as one self-contained `index.html` file with no dependencies, no build step, and no backend. The goal is to host it on a free, beautiful, shareable link that each caregiver can open on their phone.

## What this is

- `index.html` — the complete site. Seven tabs: Overview, Calendar, Angi, Olga, Yulia, Parents, The Kids. Each caregiver gets a personalized view of their schedule.
- Pure HTML/CSS/JS. Uses Google Fonts (Cormorant Garamond + DM Sans) loaded via CDN. Works offline once loaded.
- Mobile-first responsive design.

## Goal for Claude Code

Help me deploy this to a free hosted link. I do **not** yet have a GitHub account or a Vercel account. I'd like to:

1. Set up a free GitHub account (or use one if I make it during this session)
2. Create a public repo and push this `index.html`
3. Connect to Vercel (free tier) and deploy
4. End with a live, shareable URL

I'd prefer the simplest path. Since this is a single static HTML file, no framework or build configuration is needed — Vercel can deploy a static file directly.

## Deployment steps (reference)

### Option A — Vercel (recommended, matches the reference site)

1. **GitHub account**: Sign up at https://github.com (free). Verify email.
2. **Create repo**: New repository → name it e.g. `summer-care-schedule` → set to Public → create.
3. **Push the file**: From the project folder:
   ```bash
   git init
   git add index.html README.md
   git commit -m "Add summer care schedule"
   git branch -M main
   git remote add origin https://github.com/<YOUR_USERNAME>/summer-care-schedule.git
   git push -u origin main
   ```
   (GitHub will prompt for auth — use a personal access token or the GitHub CLI `gh auth login`.)
4. **Deploy on Vercel**: Sign up at https://vercel.com with "Continue with GitHub" (free). → Add New Project → import the `summer-care-schedule` repo → Vercel auto-detects it as a static site → Deploy.
5. **Done**: Vercel gives a URL like `https://summer-care-schedule.vercel.app`. Every `git push` auto-redeploys.

### Option B — Even simpler, no GitHub: Vercel CLI

If skipping GitHub is preferable:
```bash
npm i -g vercel
vercel login
vercel --prod
```
Run from the project folder; follow the prompts. Vercel hosts the static file directly and returns a live URL.

### Option C — GitHub Pages (no Vercel)

1. Push to GitHub (steps 1–3 above).
2. Repo → Settings → Pages → Source: `main` branch, `/root` → Save.
3. Live at `https://<YOUR_USERNAME>.github.io/summer-care-schedule/` within a minute or two.

## Custom domain (optional, later)

Both Vercel and GitHub Pages support custom domains for free if you ever want something like `schedule.ourfamily.com`. Vercel: Project → Settings → Domains. Requires owning a domain (~$10–15/yr from a registrar).

## Editing the schedule later

All content lives in `index.html`. To change a shift, find the relevant day cell (search for the date, e.g. `>15<` for July 15) and edit the `<span class="slot ...">` lines. Push the change and it redeploys automatically (Vercel/Pages).

## Schedule summary (for reference)

- **Angi (au pair)**: ~28 hrs/week base. Bedtimes 9–11pm nightly (Tue–Sun); full overnights Fri + Sat 9pm–7am. Rest: Sat 7am → Sun 7pm (36 hrs). Monday fully off. Max 45 hrs/week, 10 hrs/single shift.
- **Olga (babysitter)**: ~34 hrs/week. Mon/Thu/Fri/Sat 7am–1pm; Sun 8am–6pm. Off Tue + Wed. No overnights, no split shifts.
- **Yulia (friend)**: Weekdays only, 3–9pm. Brings daughter Sana.
- **Parents**: Work 3pm–midnight. Cover 1–3pm daily, Tue/Wed mornings, Monday bedtime, Sat daytime, Sun morning. Go out Fri + Sat (until 7am) + up to 2 weeknights with notice.
- **Exceptions**: July 12 boat day (Olga covers morning, family+Angi on boat). July 14 parent commitment 9am–1pm (covered by Olga's standing shift).
