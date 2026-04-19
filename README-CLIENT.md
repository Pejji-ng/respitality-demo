# Respitality Website &mdash; Client Review Package

Welcome to your Pejji-standard website for **Respitality**.

This package is ready for your review. Below is everything you need before we connect it to your domain `respitality.ca`.

---

## 1. What's in this package

A multi-page Canadian website with full privacy compliance:

- **Homepage** (`index.html`) &mdash; hero, services, CTA
- **About page** (`about.html`) &mdash; mission, values, team narrative
- **Contact page** (`contact.html`) &mdash; Web3Forms integrated form + WhatsApp button
- **Privacy Policy** (`privacy.html`) &mdash; 10 sections, PIPEDA-aligned (Personal Information Protection and Electronic Documents Act)
- **404 page** &mdash; branded fallback
- **robots.txt + sitemap.xml** &mdash; pointed at respitality.ca
- **_headers** &mdash; strong CSP, HSTS preload, X-Frame-Options, Permissions-Policy

---

## 2. Things WE need from YOU before go-live

Please reply with the following values so we can replace all placeholders:

### REQUIRED (site will not fully work until these are provided)

| Placeholder | What to send us |
|---|---|
| `{{RESPITALITY_WHATSAPP_NUMBER}}` | Your WhatsApp Business number in international format WITHOUT the `+`. Example: `15875551234` (no spaces, no +) |
| `{{RESPITALITY_PHONE_NUMBER}}` | Your display phone number. Example: `+1 (587) 555-1234` |
| `{{RESPITALITY_CONTACT_EMAIL}}` | Email address for privacy + contact inquiries. Example: `hello@respitality.ca` |

### OPTIONAL

| Placeholder | What to send us |
|---|---|
| `{{RESPITALITY_GA4_ID}}` | Your Google Analytics 4 Measurement ID if you want analytics. Format: `G-XXXXXXXXXX`. If you don't want analytics, tell us and we'll remove the 3 GA script blocks + drop `googletagmanager` from the CSP. |

### WEB3FORMS ACCESS KEY
The contact form is wired to **Web3Forms** (free service, no backend). To receive submissions in your email:
1. Sign up at [web3forms.com](https://web3forms.com/) (free)
2. Send us your Access Key
3. We drop it into `contact.html` and the form starts emailing you every time someone submits

---

## 3. Review Checklist

Please look through:
- [ ] Homepage (`index.html`) &mdash; branding, services description, hero messaging
- [ ] About page (`about.html`) &mdash; mission + values copy
- [ ] Contact page (`contact.html`) &mdash; form fields, addresses, WhatsApp link
- [ ] Privacy Policy (`privacy.html`) &mdash; 10 sections. **Important:** we've set this up under Canadian PIPEDA law (not Nigerian NDPA). If you operate under provincial privacy law (Alberta PIPA, BC PIPA, Quebec Law 25), let us know and we'll add province-specific clauses.
- [ ] 404 page (`404.html`)
- [ ] Footer links (Navigation, Contact, Privacy Policy all wired)

---

## 4. Once you approve

We will:
1. Replace all `{{RESPITALITY_*}}` placeholders with your real data
2. Drop in your Web3Forms access key if you want the contact form live
3. Push to Cloudflare Pages
4. Wire your domain `respitality.ca` + `www.respitality.ca`
5. Cloudflare provisions SSL automatically (~5 min)
6. Your site is live, replacing the current Hostinger-suspended page

---

## 5. Why move off Hostinger?
Your current respitality.ca is showing "Website Suspended &mdash; Breach of Terms" on Hostinger. When we switch your domain to point at Cloudflare Pages:
- That suspended page disappears instantly
- Your site becomes fast (global CDN), secure (HSTS + full CSP), and always available
- No more monthly hosting fees to Hostinger
- Cloudflare Pages is free for your usage level

---

## 6. Questions?

Reach out to **Pejji Agency** on WhatsApp: +234 904 452 6924 (or for Canadian clients, Kingsley's local line).

---

**Built with precision by Pejji Agency.**
