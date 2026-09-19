# Namecheap DNS -> GitHub Pages (hunterh37.github.io/AngioPilotWebsite)

Namecheap: Domain List > Manage > Advanced DNS. Set NAMESERVERS to "Namecheap BasicDNS" first.
Delete the default "CNAME Record @ parkingpage.namecheap.com" and the URL Redirect record.

## Records

Apex (example.com) — four A records, host `@`:

    A   @   185.199.108.153   Automatic
    A   @   185.199.109.153   Automatic
    A   @   185.199.110.153   Automatic
    A   @   185.199.111.153   Automatic

Optional IPv6 (AAAA, host `@`):

    AAAA @  2606:50c0:8000::153
    AAAA @  2606:50c0:8001::153
    AAAA @  2606:50c0:8002::153
    AAAA @  2606:50c0:8003::153

www subdomain:

    CNAME  www  hunterh37.github.io.

Note the CNAME target is the USER site `hunterh37.github.io`, not the repo path.
DNS has no concept of the `/AngioPilotWebsite` path.

## GitHub side (required, or the domain 404s)

1. Repo AngioPilotWebsite > Settings > Pages > Custom domain: enter the apex
   (e.g. `angiopilot.com`) > Save. This commits a `CNAME` file to the publishing branch.
2. Wait for "DNS check successful", then tick **Enforce HTTPS** (cert issuance can take
   up to ~24h; the box is greyed out until it is ready).
3. Once the custom domain is set, GitHub serves the repo at the domain ROOT:
   `https://angiopilot.com/` → the site. `hunterh37.github.io/AngioPilotWebsite/`
   redirects to it.

## Site-relative path caveat

Before the custom domain, the site lives under the `/AngioPilotWebsite/` base path.
After, it lives at `/`. Any hardcoded `/AngioPilotWebsite/...` asset or link URLs will
break. Use relative paths (`./assets/x.png`) or update the base path / `base` config.

## Verify

    dig +short angiopilot.com A
    dig +short www.angiopilot.com CNAME
    curl -sI https://angiopilot.com | head -1

Propagation: typically minutes on Namecheap, up to 30 min. TTL "Automatic" = 30 min.

## Subdomain-only alternative

To serve at `www.angiopilot.com` only, skip the A records, keep the CNAME, and enter
`www.angiopilot.com` as the GitHub custom domain.
