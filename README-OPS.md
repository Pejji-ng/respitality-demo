# Respitality Site &mdash; Ops Runbook (Pejji Internal)

## Deployment target
- GitHub: `Pejji-ng/respitality-demo`
- Hosting: Cloudflare Pages
- Domain: `respitality.ca` (already registered, on CF Registrar)
- **Current public state**: respitality.ca points to a Hostinger-suspended page ("breach of terms"). Once we cutover to CF Pages, that disappears immediately.

## Placeholders needing client values
- `{{RESPITALITY_WHATSAPP_NUMBER}}` &mdash; contact.html (x1)
- `{{RESPITALITY_PHONE_NUMBER}}` &mdash; all 5 HTMLs (footer + privacy)
- `{{RESPITALITY_CONTACT_EMAIL}}` &mdash; all 5 HTMLs (footer + privacy)
- `{{RESPITALITY_GA4_ID}}` &mdash; all 5 HTMLs (GA scripts); optional

### Sweep commands (after client sends values)
```bash
WA="15875551234"        # international format no +
PHONE="+1 (587) 555-1234"
EMAIL="hello@respitality.ca"
GA="G-XXXXXXXXXX"       # OR empty if client opts out

sed -i "s|{{RESPITALITY_WHATSAPP_NUMBER}}|$WA|g" index.html about.html contact.html privacy.html 404.html
sed -i "s|{{RESPITALITY_PHONE_NUMBER}}|$PHONE|g" index.html about.html contact.html privacy.html 404.html
sed -i "s|{{RESPITALITY_CONTACT_EMAIL}}|$EMAIL|g" index.html about.html contact.html privacy.html 404.html
sed -i "s|{{RESPITALITY_GA4_ID}}|$GA|g" index.html about.html contact.html privacy.html 404.html

grep -r "{{RESPITALITY_" . --include="*.html" || echo "All placeholders filled."
```

### If client opts out of GA
Delete the GA script blocks at top of each HTML head (2 consecutive `<script>` tags). Then edit `_headers` CSP to remove `https://www.googletagmanager.com` and `https://www.google-analytics.com`.

### Web3Forms access key
Contact form uses Web3Forms. Client provides their access key. Find + replace in `contact.html`:
```bash
# When Web3Forms key arrived:
sed -i 's|value="YOUR_ACCESS_KEY_HERE"|value="ACTUAL_KEY"|' contact.html
```
(Check current state: `grep "access_key" contact.html` &mdash; if not yet wired, we need to add the hidden input.)

## Important context
Respitality is a Canadian business (respitality.ca). Privacy policy is PIPEDA-aligned, NOT NDPA. This differs from our Nigerian clients. Do NOT copy this privacy template to Nigerian partner sites.

## CF Pages deploy checklist

1. Merge the `feat/pejji-standard-upgrade` PR to `main`
2. CF dashboard -> Workers & Pages -> Create -> Connect to Git
3. Select `Pejji-ng/respitality-demo`, branch `main`
4. Build settings: **None** preset, no build command, output directory = `.` (static)
5. Deploy
6. Once first deploy OK -> Custom domains -> Add `respitality.ca` AND `www.respitality.ca`
7. CF auto-creates CNAMEs + SSL in ~3 min
8. Hostinger suspension page disappears the moment the new records propagate
9. Verify: `curl -I https://respitality.ca/` returns 200 + all 7 security headers

## Post-deploy verification
```bash
curl -sI https://respitality.ca/ | grep -iE "(content-security|x-frame|strict-transport|permissions|referrer|x-content|x-xss)"
curl -s https://respitality.ca/ | grep -c "{{RESPITALITY_"   # must be 0
curl -sI https://respitality.ca/privacy.html | head -1
curl -sI https://respitality.ca/about.html | head -1
curl -sI https://respitality.ca/contact.html | head -1
```

## Add to uptime monitor after go-live
- https://respitality.ca/
- https://www.respitality.ca/
- https://respitality.ca/contact.html (contact form is revenue-critical, separate check worthwhile)
