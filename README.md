# mitchind Status - https://status.mitchind.ch

Public status page for mitchind.ch, copied from `Predivo-GmbH/status-site` per
`standards/status-page-standard.md` (decision D13, D-032, 30.10.2026). Layout like status.claude.com, in
mitchind's brand (tokens from mitchind `docs/design-tokens.json`, Nunito self-hosted), German with an
English switch. Hosted on GitHub Pages, not on our web host, so it stays up when mitchind.ch is down.

- Data: Atlassian Statuspage public API (`https://mitchind.statuspage.io/api/v2`) and the Upptime
  history of `Predivo-GmbH/status-mitchind` (`history/summary.json`).
- Services: `website`, `signin` ("?" texts DE + EN in `index.html`, `about`).
- Nothing is stored on the visitor's device (D2): the language comes from `?lang=en` or the browser.

## Not live yet (06.11.2026)

GitHub Pages is OFF until the Statuspage page for mitchind exists; the page still holds these placeholders:

| Placeholder | Comes from |
|---|---|
| `mitchind.statuspage.io` | the Statuspage page for mitchind; its subdomain must be `mitchind` (unclaimed on 06.11.2026), or replace every `mitchind.statuspage.io` |
| `__MITCHIND_PAGE_ID__` | that page's id (Slack subscribe link) |

Filled on 06.11.2026:

- Subscribe endpoint: Cloudflare Worker `mitchind-status-subscribe` from `worker/subscribe.js`
  (https://mitchind-status-subscribe.restless-silence-9277.workers.dev), var `ALLOWED_ORIGIN=https://status.mitchind.ch`,
  Worker secrets `STATUSPAGE_API_KEY` and `TURNSTILE_SECRET`. Its var `PAGE_ID` is set once the Statuspage page exists.
- Bot check: Turnstile widget "mitchind status subscribe" for `status.mitchind.ch` only; its public site key is the
  `TURNSTILE_SITEKEY` constant in `index.html`, its secret is stored in mitchind `docs/Credentials.txt`.

DNS: `status.mitchind.ch` CNAME → `predivo-gmbh.github.io` (Plesk zone mitchind.ch), then the second DNS
provider per the standard §3.5.
