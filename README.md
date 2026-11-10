# AppLovin verification site

A small public page so AppLovin has a crawlable site to review, instead of a
password-protected Shopify dev store — which is what got the previous account
suspended ("your promoted site does not appear to meet our advertising standards").

## Before deploying — replace three placeholders in `index.html`

| Placeholder | Replace with |
|---|---|
| `YOUR_EVENT_KEY_HERE` | Event Key from AppLovin → Account → General → Keys |
| `REPLACE_WITH_YOUR_EMAIL` | a real inbox you can answer from |
| `REPLACE_WITH_YOUR_LEGAL_COMPANY_NAME` | the same legal name entered on the AppLovin sign-up form |

The brand name and products in the page are placeholders too. Change them to
something you actually intend to promote: AppLovin reviews the site, and a page
describing goods you do not sell is worse than no page.

The Event Key can be filled in AFTER deploying — the page is valid without it and
simply logs a warning.

## Deploy — GitHub Pages

    git init && git add . && git commit -m "AppLovin verification site"
    git branch -M main
    git remote add origin https://github.com/<you>/<repo>.git
    git push -u origin main

Then: repo → Settings → Pages → Source "Deploy from a branch" → `main` / `/ (root)`.
The URL is `https://<you>.github.io/<repo>/`.

## Deploy — Vercel

    npx vercel --prod

## After it is live

1. Open the URL in a normal browser and confirm it loads with no password prompt.
2. Enter that URL as the Company website on the AppLovin sign-up form.
3. With the Event Key filled in, reload the page and check `document.cookie`
   contains `_axwrt` — that is the pixel confirming it ran.
