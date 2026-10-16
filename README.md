# Starter website for the Google OAuth "Branding" fields

Google now keeps the **Publish app** button disabled until the OAuth consent
screen has a homepage URL and a privacy-policy URL, and any URL there forces an
**authorized domain**. A free GitHub Pages site satisfies those fields without
buying a domain. (No Search Console verification is needed just to *publish* —
verification only matters if you later submit your app for brand verification,
which you don't need for personal use.)

## 1. Edit the placeholders

In `index.html` and `privacy.html`, replace `YOUR-EMAIL-HERE` with your email
address.

## 2. Create the site on GitHub (public repo)

```powershell
cd "C:\Users\Thinkpad T14 Gen 4\gdrive-watcher-pages"
git init
git add .
git commit -m "Personal Drive watcher: homepage + privacy policy"
git branch -M main
# create an empty PUBLIC repo named e.g. gdrive-watcher-pages on github.com,
# then (replace kevinbudiman):
git remote add origin git@github.com:kevinbudiman/gdrive-watcher-pages.git
git push -u origin main
```

Then on GitHub: **Settings → Pages → Source: Deploy from a branch →
Branch: main / (root) → Save**. After a minute your site is live at
`https://kevinbudiman.github.io/gdrive-watcher-pages/`.

> If you'd rather have it at the root (`https://kevinbudiman.github.io/`),
> name the repo exactly `kevinbudiman.github.io` instead.

## 3. Fill in Google Auth Platform → Branding → App domain

| Field | Value |
|-------|-------|
| Application home page | `https://kevinbudiman.github.io/gdrive-watcher-pages/` |
| Application privacy policy link | `https://kevinbudiman.github.io/gdrive-watcher-pages/privacy.html` |
| Authorized domains | `kevinbudiman.github.io` |

Save. The **Publish app** button on the **Audience** page should now be clickable
→ click it → **Confirm**. Ignore any "Needs verification" note; do **not** click
"Prepare for verification" or "Verify branding".

## 4. Get a fresh token

Tokens issued while the app was still in "Testing" keep the 7-day expiry, so
re-consent once:

```powershell
cd "C:\Users\Thinkpad T14 Gen 4\gdrive-watcher"
.venv\Scripts\python.exe gdrive_watcher.py auth
```

You'll see the "Google hasn't verified this app" screen once — click
**Advanced → Go to … (unsafe)** → **Allow**.

---

*This is a private, single-user utility. The pages here exist to satisfy the
OAuth consent-screen fields; see `privacy.html` for the full policy.*
