# Leadexon — Landing Page

**Leadexon** — Lead Recovery & Conversion for HVAC Companies
Live URL: https://leads.rankintelligence.net/
Contact: leads@rankintelligence.net

A single-page, static, conversion-focused landing page. No build step, no
framework, no dependencies except Google Fonts (Manrope). Everything is in
`index.html`.

## Files

| File | Purpose |
|---|---|
| `index.html` | The complete landing page (markup, CSS, JS in one file) |
| `favicon.svg` | Leadexon logo mark as favicon |
| `robots.txt` | Crawl rules + sitemap pointer |
| `sitemap.xml` | Single-URL sitemap for the landing page |
| `_headers` | Cloudflare Pages security/cache headers |

## Deploy on Cloudflare Pages

1. Cloudflare Dashboard → **Workers & Pages** → **Create** → **Pages** →
   **Connect to Git**.
2. Select this repository: `dazzlitco/Leadexon`, production branch `main`.
3. Build settings:
   - **Framework preset:** None
   - **Build command:** *(leave empty)*
   - **Build output directory:** `/` (root)
4. **Save and Deploy.** Cloudflare gives you a `*.pages.dev` URL first —
   verify the page and submit a test demo request there.
5. Custom domain: Pages project → **Custom domains** → add
   `leads.rankintelligence.net`. If DNS for `rankintelligence.net` is on
   Cloudflare, the required CNAME is created automatically; if DNS is
   elsewhere, add a CNAME for `leads` pointing to your `*.pages.dev` host.
6. Every push to `main` auto-deploys.

## Form endpoint — REQUIRED before launch

The demo form in `index.html` supports **two** providers. Pick one, paste its
key into the `FORM_CONFIG` block near the end of `index.html`, commit, and
Cloudflare redeploys automatically.

### Option A — Web3Forms (default, free)

1. Go to https://web3forms.com and enter **leads@rankintelligence.net**.
2. Copy the **Access Key** you receive by email.
3. In `index.html` set:
   - `provider: "web3forms"` (already the default)
   - `web3formsAccessKey: "<paste the key>"`

### Option B — Formspree

1. Go to https://formspree.io, create a form, set its recipient to
   **leads@rankintelligence.net**.
2. Copy the form ID — the part after `/f/` in the form endpoint.
3. In `index.html` set:
   - `provider: "formspree"`
   - `formspreeFormId: "<paste the ID>"`

### Behaviour notes

- Submissions are sent with `fetch` (no page reload). On success the visitor
  sees: “Thanks — your request has been received. We'll be in touch shortly.”
- Validation is built in; the submit button shows “Sending…” while in flight,
  and a clear error (with the direct email address) if sending fails.
- A hidden honeypot field blocks basic bots.
- **Safety fallback:** if no key has been pasted in yet, the form opens the
  visitor's email app pre-addressed to leads@rankintelligence.net instead of
  failing — so the page can go live before the key is added, but add the key
  before driving real traffic.

## Launch checklist

- [ ] Paste Web3Forms access key **or** Formspree form ID into `FORM_CONFIG`
- [ ] Submit a real test request on the `*.pages.dev` URL and confirm it
      arrives at leads@rankintelligence.net
- [ ] Attach custom domain `leads.rankintelligence.net`
- [ ] Submit a second test request on the live domain
- [ ] Check the page on a real phone (nav, sticky CTA, form)

## Notes

- No testimonials, logos, case studies, statistics, or guarantees are shown —
  none exist yet, by design. Add real proof only when it exists.
- Page title: *HVAC Lead Recovery & Conversion | Leadexon*
- Colours: Deep Navy `#102A43`, Teal `#3EC9C0`, Light `#F5F8FA`
