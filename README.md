# Ledger — your stock-writing site

A site you own. The design is yours, the writing lives as markdown in your own
GitHub repo, and you publish from an admin panel in your browser.

---

## Getting it online (about 20 minutes, one time)

You do **not** need to install Node or run anything locally. Netlify does the
building for you.

### 1. Put this folder in a GitHub repo

- On GitHub, create a new **public** repo (e.g. `ledger`)
- **Add file → Upload files**, drag in everything from this folder
- Commit

> Do not upload `node_modules` or `dist` if you happen to have them — they are
> ignored anyway, but they are large and unnecessary.

### 2. Connect it to Netlify

- Go to **netlify.com**, sign up (you can sign in with GitHub)
- **Add new site → Import an existing project → GitHub → pick your repo**
- Netlify reads `netlify.toml` and fills in the build settings itself. Just click **Deploy**
- A minute later your site is live at something like `yourname.netlify.app`

### 3. Turn on the publishing UI

This is what gives you `/admin`.

- In Netlify: **Site configuration → Identity → Enable Identity**
- Under **Identity → Registration**, set it to **Invite only**
  *(otherwise strangers could sign up and publish on your site)*
- Under **Identity → Services → Git Gateway**, click **Enable Git Gateway**
- Go to the **Identity** tab → **Invite users** → invite your own email
- Check your email, click the link, set a password

### 4. Publish

Go to `https://yoursite.netlify.app/admin` and log in.

You get a real editor: ticker, title, conviction, date, and a markdown body.
Hit **Publish**. Decap commits a `.md` file to your GitHub repo, Netlify rebuilds,
and the post is live in about a minute.

That is the whole loop. No terminal, ever.

---

## Writing without the admin panel

If you would rather just write files (often faster once you're used to it):

Add a markdown file to `src/content/posts/`:

```markdown
---
ticker: "RKLB"
title: "Small rockets, and the moat nobody is pricing"
conviction: "high"
date: 2026-07-20
summary: "One line for search engines."
draft: false
---

Your essay here, in plain markdown.
```

Push it to GitHub. Netlify rebuilds automatically. Same result.

`draft: true` keeps a post out of the site until you're ready.

---

## Making it yours

| What | Where |
| --- | --- |
| Site name, tagline, standfirst, footer | `src/config.ts` |
| Colours, type, spacing | `src/styles/global.css` (the `:root` block at the top) |
| The About page | `src/pages/about.astro` |
| Conviction levels | `src/content.config.ts` **and** `public/admin/config.yml` (change both) |

### A custom domain

Netlify → **Domain management → Add a domain**. Buy a domain anywhere
(Namecheap, Cloudflare), point it at Netlify, and the site is fully yours —
your name, your content, your repo.

---

## Running it locally (optional)

Only if you want to preview changes before pushing. Needs Node installed.

```
npm install
npm run dev
```

Then open the address it prints.

---

## What you own

- **The writing** — plain markdown files in your GitHub repo. Portable anywhere, forever.
- **The design** — plain CSS in your repo.
- **The domain** — if you buy one.

Netlify is just a machine that builds and serves it. If you ever want to leave,
your content comes with you unchanged.
