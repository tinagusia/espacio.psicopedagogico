# PR Context: TINAGUSIA-289 subdomain migration

## Branches

- Source fork: `tinagusia/espacio.psicopedagogico`
- Source branch: `feature/TINAGUSIA-289-subdomain-migration`
- Target repository: `txna25/espacio.psicopedagogico`
- Target branch: `main`
- PR: pending

## Objective

Prepare the existing Espacio Psicopedagógico GitHub Pages site for `https://espaciopsicopedagogico.tinagusia.com/` without changing the visible experience or publishing before local approval.

## Scope

- Add the GitHub Pages `CNAME` file.
- Update canonical, Open Graph, Twitter, JSON-LD, robots, and sitemap URLs.
- Add a real local social preview image.
- Replace missing favicon and manifest icon references with the existing site SVG.
- Remove unverified placeholder phone, address, coordinates, price range, and opening hours from structured data.
- Add an owner-operated DNS, HTTPS, validation, and rollback runbook.
- Add TinagusIA child-repository agent instructions.

## Validation

- [x] JSON-LD parses successfully.
- [x] Local static server returns `200`.
- [x] 320 px: no horizontal overflow.
- [x] 1440 px: no horizontal overflow.
- [x] Workshop modal opens and closes at both widths.
- [x] No local resource responses at 400 or above.
- [x] No browser console errors.
- [x] Five WhatsApp links and three LinkedIn links remain present.
- [x] Canonical, Open Graph, Twitter, JSON-LD, robots, and sitemap use the target host.
- [x] Social preview is 1200 x 630 and stored locally.

## Deployment Boundary

- Opening this PR does not deploy the fork or the original site.
- Merging to the original `main` branch publishes through GitHub Pages and therefore requires explicit approval.
- Domain verification and GitHub Pages custom-domain registration must happen before creating the DNS record.
- The `txna25` owner profile can review and merge this PR.
- Redirecting the historical `espacio-psicopedagogico.github.io` URL remains blocked by access to that separate duplicate account.

## Jira

- [TINAGUSIA-289](https://tinagusia.atlassian.net/browse/TINAGUSIA-289)
