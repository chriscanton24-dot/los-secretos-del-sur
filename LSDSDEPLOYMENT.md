# LOS SECRETOS DEL SUR — WEBSITE DEPLOYMENT INSTRUCTIONS
## GitHub + Vercel — Free Hosting, Step by Step

---

## WHAT YOU NEED BEFORE YOU START
- Your GitHub account (chriscanton24-dot) — already have ✅
- Your Vercel account — already have ✅
- A Formspree account (free) — takes 2 minutes to create

---

## STEP 1 — SET UP FORMSPREE (Contact Form)
*This makes Martha receive contact form submissions by email*

1. Go to **https://formspree.io**
2. Click **Sign Up** — use any email
3. Click **+ New Form**
4. Name it: `Los Secretos Del Sur Contact`
5. Set the email to Martha's email address
6. Click **Create Form**
7. You will see a form endpoint like:
   `https://formspree.io/f/abcd1234`
8. Copy that ID — the part after `/f/` (example: `abcd1234`)
9. Open `index.html` in any text editor
10. Find this line (search with Ctrl+F / Cmd+F):
    `action="https://formspree.io/f/YOUR_FORM_ID"`
11. Replace `YOUR_FORM_ID` with the actual ID from step 8
12. Save the file

---

## STEP 2 — CREATE A GITHUB REPOSITORY

1. Go to **https://github.com** — log in as chriscanton24-dot
2. Click the **+** button (top right) → **New repository**
3. Repository name: `los-secretos-del-sur`
4. Set to **Public** (required for free Vercel)
5. Do NOT check "Add a README" — leave all boxes unchecked
6. Click **Create repository**
7. You'll land on an empty repo page — keep this tab open

---

## STEP 3 — UPLOAD YOUR FILES TO GITHUB

You have two options — pick Option A (easiest) or Option B (if you know Git).

### OPTION A — Upload via GitHub Website (No coding needed)

1. On your empty repo page, click **"uploading an existing file"** link
   (It's in the middle of the page in the quick setup text)
2. Drag and drop ALL of these files at once onto the upload area:
   ```
   index.html
   logo.png
   en.json
   es.json
   ```
3. Scroll down to **Commit changes**
4. Leave the message as is or type: `Initial site upload`
5. Click **Commit changes**
6. Wait for upload to finish — you'll see all 4 files listed

### OPTION B — Via Git Command Line

```bash
cd /path/to/your/files
git init
git add .
git commit -m "Initial site upload"
git branch -M main
git remote add origin https://github.com/chriscanton24-dot/los-secretos-del-sur.git
git push -u origin main
```

---

## STEP 4 — DEPLOY ON VERCEL

1. Go to **https://vercel.com** — log in with your existing account
2. Click **Add New...** → **Project**
3. You'll see a list of your GitHub repos
4. Find **los-secretos-del-sur** and click **Import**
5. On the configure project screen:
   - Framework Preset: **Other** (it will auto-detect — leave as is)
   - Root Directory: leave blank (`.`)
   - Build Command: leave blank (static HTML — no build needed)
   - Output Directory: leave blank
6. Click **Deploy**
7. Vercel will deploy in about 30 seconds
8. You'll see a **Congratulations!** screen with a live URL like:
   `https://los-secretos-del-sur.vercel.app`

---

## STEP 5 — VERIFY THE LIVE SITE

Open the live URL and check:

- [ ] Site loads at the URL
- [ ] Logo appears in nav, hero, and footer
- [ ] EN / ES toggle switches all text correctly
- [ ] All sections scroll properly
- [ ] Phone number 940-358-2446 is clickable on mobile (tap it)
- [ ] Contact form fills out and submits
- [ ] After form submit — success message appears
- [ ] Martha receives the form submission email (test this!)
- [ ] Mobile hamburger menu opens and closes

---

## STEP 6 — SHARE THE LINK WITH MARTHA

Send Martha:
- The live URL: `https://los-secretos-del-sur.vercel.app`
- Her Formspree email (confirm she receives test submission)

---

## ADDING PHOTOS LATER

When Martha provides photos:

1. Go to your GitHub repo
2. Create a folder called `images` by clicking **Add file** → **Create new file**
   → type `images/.gitkeep` → commit
3. Upload photos into the `images/` folder
4. In `index.html`, find the gallery section — replace:
   ```html
   <div class="gallery-item"><span class="gallery-placeholder-text">Photo</span></div>
   ```
   With:
   ```html
   <div class="gallery-item">
     <img src="images/your-photo-name.jpg" alt="Los Secretos Del Sur catering display">
   </div>
   ```
5. For the About section image, find:
   ```html
   <!-- <img src="images/about.jpg" alt="Los Secretos Del Sur catering display"> -->
   ```
   Remove the `<!--` and `-->` comment markers and update the filename
6. Commit changes — Vercel auto-deploys within 30 seconds

**Photo requirements (from brand spec):**
- Dark, moody, warm — no bright or white backgrounds
- Food on dark surfaces only
- Compress each photo to under 200KB before uploading
- Free sources: Unsplash.com, Pexels.com (search: "charcuterie dark", "tapas moody")

---

## ADDING A CUSTOM DOMAIN LATER (Optional)

When Martha is ready for a custom domain (e.g. lossecretosdelsur.com):

1. Purchase domain from Namecheap or Google Domains (~$12/year)
2. In Vercel dashboard → your project → **Settings** → **Domains**
3. Click **Add Domain** → type the domain name
4. Vercel will give you DNS records to add
5. Log into your domain registrar and add those DNS records
6. Wait 15 minutes — site goes live on custom domain automatically

---

## MAKING CONTENT EDITS LATER

All text content is in two places:
- Inside `index.html` in the `translations` JavaScript object
- In `en.json` and `es.json` (reference copies)

To edit any text:
1. Open `index.html`
2. Search (Ctrl+F) for the English text you want to change
3. Change it in BOTH the `translations.en` and `translations.es` objects
4. Upload the updated file to GitHub → Vercel auto-deploys

---

## TROUBLESHOOTING

**Logo not showing:**
- Make sure `logo.png` is in the same folder as `index.html` (not in a subfolder)

**Form not working:**
- Double-check the Formspree ID in `index.html` — must match exactly
- Check Martha's spam folder for test submissions

**Language toggle not working:**
- Open browser console (F12) — look for JavaScript errors
- Make sure the full `index.html` uploaded correctly (file should be ~67KB)

**Vercel not finding GitHub repo:**
- Make sure repo is set to Public
- Try disconnecting and reconnecting GitHub in Vercel settings

---

## FILE INVENTORY

```
los-secretos-del-sur/
├── index.html          ← The entire website (all sections + JS + CSS)
├── logo.png            ← Brand logo PNG (transparent background)
├── en.json             ← English content reference
├── es.json             ← Spanish content reference
└── images/             ← Add photos here when ready (create this folder)
```

---

*Los Secretos Del Sur · "El Manjar de los Vivos" · Amarillo, TX · 940-358-2446*
*Deployment instructions prepared: March 2026*
