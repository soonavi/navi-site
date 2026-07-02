# Navi Marketing — Live Site

A single-file website (`index.html`). No build step, no framework. It works as-is when opened, and deploys as a static site.

There are exactly **4 steps** to go live. Only Step 1 requires editing the file.

---

## Step 1 — Connect the contact form (5 minutes)

The form is fully wired to send leads straight to your Gmail. It just needs one free key.

1. Go to https://web3forms.com
2. Enter `soonaviscaling@gmail.com` and submit. They email you an **Access Key** right away.
3. Open `index.html`, find this line near the bottom (inside the `<script>`):

   ```js
   const WEB3FORMS_KEY = 'YOUR_WEB3FORMS_ACCESS_KEY';
   ```

4. Replace `YOUR_WEB3FORMS_ACCESS_KEY` with the key they sent you. Save.

That's it. Every form submission now lands in your inbox, and hitting reply goes straight back to the lead. Spam protection (honeypot) is already built in. Until you add the key, the form shows "Form not connected yet" instead of pretending to send.

---

## Step 2 — Put it on GitHub

```bash
cd navi-site
git init
git add .
git commit -m "Navi Marketing site"
git branch -M main
# create an empty repo named navi-site on github.com first, then:
git remote add origin https://github.com/YOUR_USERNAME/navi-site.git
git push -u origin main
```

---

## Step 3 — Deploy on Vercel (GitHub-only, no CLI)

Do this in the **Vercel dashboard**, not the CLI. Importing from GitHub gives you automatic deploys on every push and avoids the double-deploy issue.

1. Go to https://vercel.com/new
2. Import the `navi-site` repo.
3. Framework preset: **Other**. No build command, no output dir needed (it's static).
4. Click **Deploy**.

You get a live `something.vercel.app` URL in about 20 seconds. From now on, every `git push` to `main` redeploys automatically. Do not run `vercel` from the CLI on this project, so you never get the double-deploy conflict again.

---

## Step 4 — Add your clean domain

**Option A — buy through Vercel (simplest):**
Project → Settings → Domains → type your domain → Buy. DNS is auto-configured.

**Option B — buy at Porkbun (usually cheaper) and point it at Vercel:**
1. Buy the domain at porkbun.com.
2. In Vercel: Project → Settings → Domains → add your domain.
3. Vercel shows the exact DNS records to add. Typically:
   - Apex (`navimarketing.co`): **A record** → `76.76.21.21`
   - `www`: **CNAME** → `cname.vercel-dns.com`
4. Add those records in Porkbun's DNS panel. It goes live once DNS propagates (minutes to an hour).

Always copy the exact records Vercel shows you, in case they differ.

---

## Notes

- The stats on the site (under 2 rings, under 60 seconds, 24/7) are product promises, safe to keep. I did not invent fake client results or testimonials. Add a real testimonial strip once you have one — it's the single biggest credibility upgrade.
- Contact email is `soonaviscaling@gmail.com` (footer + form fallback).
- To edit anything later: change `index.html`, commit, push. Vercel redeploys on its own.
