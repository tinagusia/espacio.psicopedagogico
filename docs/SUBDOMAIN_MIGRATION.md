# Subdomain Migration Runbook

Target: `https://espaciopsicopedagogico.tinagusia.com/`

Current public URL: `https://espacio-psicopedagogico.github.io/`

## Safety Boundary

- Review this branch locally before merging.
- Do not merge the PR until DNS ownership and GitHub repository access are confirmed.
- Do not remove the current GitHub Pages site.
- Keep a rollback path to the current `main` commit.

## Recommended Hosting Path

Keep the site on its current GitHub Pages repository and configure the custom domain through the committed `CNAME` file. This preserves one source of truth and lets GitHub Pages redirect the existing `github.io` URL to the custom domain after activation.

The TinagusIA identity contributes through a fork. The `txna25` owner profile reviews and merges the migration PR.

## DNS Preparation

Create this DNS record only after local approval, domain verification, and registration of the custom domain in GitHub Pages:

| Type | Name | Target |
| --- | --- | --- |
| `CNAME` | `espaciopsicopedagogico` | `txna25.github.io` |

If Cloudflare manages DNS, use DNS-only mode during GitHub certificate provisioning. Do not enable a proxy until HTTPS and redirects are stable.

## Cutover Order

1. Confirm control of `tinagusia.com` DNS and admin access to the GitHub Pages repository.
2. Verify `tinagusia.com` for the `espacio-psicopedagogico` GitHub account to reduce takeover risk.
3. Approve the local review and record the current `main` commit for rollback.
4. With an explicit GO, merge the migration PR to `main`; the committed `CNAME` registers the custom domain for this branch-published site.
5. Confirm GitHub Pages shows `espaciopsicopedagogico.tinagusia.com` as its custom domain.
6. Add the DNS record above immediately after GitHub recognizes the custom domain.
7. Wait until DNS resolves directly to GitHub Pages and the TLS certificate is ready.
8. Enable `Enforce HTTPS`.
9. Validate the new URL on desktop and mobile.
10. Keep the historical GitHub Pages URL available. It belongs to a separate duplicate account and cannot redirect until access to that repository is recovered.
11. Submit the new sitemap in Search Console and request indexing for the home page.

## Validation

- New URL returns `200` over HTTPS.
- Canonical, Open Graph, Twitter, JSON-LD, robots, and sitemap all use the new host.
- WhatsApp, LinkedIn, QR, workshops, and modals still work.
- The old URL redirects without a loop.
- There is only one indexable canonical URL.

## Rollback

If HTTPS, DNS, or redirects fail:

1. Revert the migration commit on `main`.
2. Remove the custom domain from GitHub Pages settings.
3. Remove the new DNS record.
4. Confirm `https://txna25.github.io/espacio.psicopedagogico/` serves the previous version.
