# Publishing 101 Chauffeured

The whole site is one file: `index.html`. No build step, no database, no dependencies
to install. Publishing it means putting that single file somewhere on the internet.

- **Repository:** https://github.com/HaitzuPP/101chauffeur (public)
- **Currently live at:** https://haitzupp.github.io/101chauffeur/
- **Publishing source:** the `main` branch, root folder

---

## Before you point a real domain at it

**1. Decide the domain.** The trading name is now *101 Chauffeured*, but the domain
first mentioned was `101chauffeur.com`. Pick one and stay with it.

**2. Then update four lines in `index.html`.** They currently contain a placeholder
domain (`101chauffeur.com`) and will send the wrong signal to Google and to
link previews if left as-is:

| Line | What it is |
|---|---|
| `<link rel="canonical" href="...">` | the one true address of the page |
| `<meta property="og:url" content="...">` | the URL in share previews |
| `"url"` inside the JSON-LD block | the business record Google reads |
| `"@id"` values inside the JSON-LD block | identifiers, must match the real domain |

Ask me and I will change all four and redeploy in one go.

---

## Option A — keep GitHub Pages, add your domain (free, recommended)

GitHub already hosts and serves the site. You are only changing the address.

**Step 1 — tell GitHub the domain**
1. Go to https://github.com/HaitzuPP/101chauffeur/settings/pages
2. Under **Custom domain**, type the domain, e.g. `101chauffeur.com`
3. Click **Save**. This writes a `CNAME` file into the repo automatically.

**Step 2 — point the domain at GitHub**

Log in wherever the domain is registered (GoDaddy, Namecheap, Crazy Domains,
Cloudflare) and open the DNS settings.

For the bare domain (`101chauffeur.com`), create four **A** records, all with
name `@`:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

For the `www` version, create one **CNAME** record:

```
Name:  www
Value: haitzupp.github.io
```

Note the CNAME value has **no repository name on the end**. Delete any existing
parking or placeholder record the registrar added, or it will fight yours.

**Step 3 — turn on HTTPS**

Back on the GitHub Pages settings screen, tick **Enforce HTTPS**. The checkbox may
be greyed out for up to 24 hours while a certificate is issued. That is normal.
Do not skip it — an insecure padlock warning on a site quoting a licence number
undoes the credibility the page is built on.

DNS changes take anywhere from a few minutes to 24 hours to spread.

---

## Option B — a normal web host (cPanel, GoDaddy hosting, etc.)

If the domain already comes with hosting:

1. Log in to the hosting control panel and open **File Manager**
2. Open the `public_html` folder (sometimes `www` or `htdocs`)
3. Upload `index.html`
4. Visit the domain

That is the entire process. If an existing `index.html` or `index.php` is already
there, rename it to `index-old.html` first so you can put it back.

---

## Option C — drag and drop (Netlify)

Fastest way to get a working link without touching DNS:

1. Go to https://app.netlify.com/drop
2. Drag `index.html` onto the page
3. You get a live URL immediately, and can attach a custom domain later

---

## Updating the site later

**Through me:** tell me what to change. I edit the file, push it, and it is live in
about a minute.

**By hand on GitHub:**
1. Open https://github.com/HaitzuPP/101chauffeur/blob/main/index.html
2. Click the pencil icon
3. Edit, then **Commit changes**
4. Wait roughly one minute and hard-refresh the site (Cmd+Shift+R)

**On a normal web host:** upload the new `index.html` over the old one.

A change can take a minute or two to appear because of caching. If the site looks
unchanged, hard-refresh before assuming something broke.

---

## Still outstanding before launch

- **Privacy policy.** The dead placeholder links were removed rather than left
  pointing nowhere. A real page is expected for a business collecting enquiries.
- **Registered address.** Corporate clients often cannot raise a purchase order
  against a mobile number alone, and Google wants one for local search.
- **Photography.** Every image is stock, including the cars. For a business whose
  promise is *our* vehicles and *our* chauffeurs, real photographs are the single
  biggest improvement left.
- **Acknowledgement of Country.** Have the nation names confirmed with the relevant
  Local Aboriginal Land Councils before launch.
- **Authorisation expiry.** BSP-466037 runs to 7 September 2036. Worth a calendar
  reminder; the expiry is deliberately not printed on the site.
