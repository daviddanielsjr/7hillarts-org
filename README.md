# 7 Hill Arts — 7hillarts.org

Static launch page for 7 Hill Arts. Same deploy path as daviddaniels.ai: plain HTML/CSS on Vercel, no framework, no build step.

## Local preview

```bash
cd "/Users/ddsmac/7 Hill Arts/7HillArts.org"
python3 -m http.server 8080
```

Open http://localhost:8080

## Deploy (Vercel + Squarespace DNS)

Canonical site: **https://7hillarts.org**  
Aliases (301 into canonical): `7hillarts.com`, `sevenhillarts.org`, `sevenhillarts.com` (plus their `www` hosts). Redirects are in `vercel.json`.

Do **not** connect these domains to a Squarespace *website*. Keep them as domains only and point DNS at Vercel (same pattern as daviddaniels.ai).

### A. Put the code on GitHub and deploy on Vercel

1. Create a GitHub repo (e.g. `7hillarts-org`) and push this folder to `main`.
2. In [vercel.com](https://vercel.com) → **Add New… → Project** → import that repo.
3. Framework: **Other**. Build Command: empty. Output: leave default. **Deploy**.
4. Confirm the `*.vercel.app` URL loads the landing page.

### B. Attach `7hillarts.org` in Vercel

1. Project → **Settings → Domains**.
2. Add `7hillarts.org`. Set it as the **primary** domain.
3. Add `www.7hillarts.org` and redirect it to `7hillarts.org` (or rely on `vercel.json`).
4. Vercel will show DNS records. Keep that panel open. Typical values:
   - Apex (`7hillarts.org`): **A** → `76.76.21.21`
   - `www`: **CNAME** → `cname.vercel-dns.com`

### C. Point DNS in Squarespace (for each domain)

For **7hillarts.org** first:

1. Squarespace → **Domains** → `7hillarts.org` → **DNS Settings** (or Advanced DNS).
2. Remove any Squarespace website / parking records that conflict (old A/AAAA/CNAME for `@` or `www`).
3. Add the records Vercel showed (A for `@`, CNAME for `www`).
4. Save. Wait until Vercel shows **Valid Configuration** (often 5–60 minutes).

Then repeat for the three aliases. For each of `7hillarts.com`, `sevenhillarts.org`, `sevenhillarts.com`:

1. In Vercel Domains, **Add** the domain.
2. Choose **Redirect to Primary Domain** (`7hillarts.org`) — or rely on the host redirects already in `vercel.json` once DNS points at Vercel.
3. In Squarespace DNS for that domain, add the same style of A / CNAME records Vercel shows for it.

### D. Smoke test

- https://7hillarts.org → landing page  
- https://7hillarts.com → 301 → 7hillarts.org  
- https://sevenhillarts.org → 301 → 7hillarts.org  
- https://sevenhillarts.com → 301 → 7hillarts.org  

## Assets

Logo files come from `Downloads/7HillArts_LogoPackage`. Hero photo is a loft concert image from `photos from concerts`.
