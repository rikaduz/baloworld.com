# Balo World

Standalone country selector for `baloworld.com`.

## Purpose

This repo is intentionally separate from the main Balo application. It owns the global entry page only: visitors choose a country, and country-specific domains remain independent applications or deployments.

## Current country behavior

- Brazil: visible as `Soon...`, but links to `https://balo.com.br`.
- Nigeria, Portugal, United Kingdom, India, Dubai, Spain, Guinea-Bissau and Angola: visible as `Soon...`.

## Deployment

The included GitHub Actions workflow can deploy the static site by rsync over SSH once these repository secrets exist:

- `BALOWORLD_SSH_HOST`
- `BALOWORLD_SSH_USER`
- `BALOWORLD_SSH_KEY`
- `BALOWORLD_DEPLOY_PATH`

Recommended server document root after the cPanel domain is attached:

```text
/home/aed04a5jwv81/public_html/baloworld.com
```

DNS still needs to point `baloworld.com` and `www.baloworld.com` to the chosen hosting target before the public domain will resolve to this site.
