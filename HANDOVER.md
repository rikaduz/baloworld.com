# Baloworld Handover

Date: 2026-05-27

## Current State

- Local repo: `C:\dev\repos\baloworld.com`
- GitHub repo: `git@github.com:rikaduz/baloworld.com.git`
- Public repo URL: `https://github.com/rikaduz/baloworld.com`
- Branch: `main`
- Site type: static GitHub Pages site
- Custom domain: `baloworld.com`

## What Is Done

- Standalone Baloworld project created outside the main Balo application.
- Static country selector implemented in `index.html` and `styles.css`.
- GitHub Pages enabled from `main`.
- DNS updated in GoDaddy:
  - `A @ 185.199.108.153`
  - `A @ 185.199.109.153`
  - `A @ 185.199.110.153`
  - `A @ 185.199.111.153`
  - `CNAME www rikaduz.github.io.`
- GitHub Pages health confirmed DNS points to Pages and is eligible for HTTPS.

## Pending

- GitHub has not issued the HTTPS certificate yet.
- `Enforce HTTPS` cannot be enabled until GitHub finishes certificate provisioning.
- Recheck tomorrow:

```powershell
cd C:\dev\repos\baloworld.com
gh api repos/rikaduz/baloworld.com/pages/health --method GET
gh api repos/rikaduz/baloworld.com/pages --method PUT -F https_enforced=true
```

If GitHub still says `The certificate does not exist yet`, wait longer and retry.

## Useful Checks

```powershell
nslookup baloworld.com 8.8.8.8
nslookup www.baloworld.com 8.8.8.8
curl.exe -I http://baloworld.com/
curl.exe -I https://baloworld.com/
```

Expected before HTTPS is ready: HTTP works, HTTPS may fail certificate verification.

Expected after HTTPS is ready: `https://baloworld.com/` works and GitHub Pages reports `enforces_https: true`.

## Notes

- The main `balo` repo is separate and should not be used for the Baloworld landing page now.
- The previous server folder `/home/aed04a5jwv81/public_html/baloworld.com` exists, but production is currently GitHub Pages.
- Do not remove the Brevo DKIM/TXT DNS records in GoDaddy; they were already present and were left intact.
