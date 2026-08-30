# stpeters-newsletter-assets

**Newsletter images only. No HTML, ever.**

Images referenced by St Peter's newsletter, served as a static Netlify site so they are not
hosted on the church's main site (`stpeters.ch`).

🔴 **Be clear what this buys.** The images are publicly fetchable either way — every
recipient's mail client fetches them with no credentials, so this is not privacy. What it buys
is that they are **not on the main site**: not in its sitemap, its analytics or its search
results; not browsable (there is no index page); content-addressed, so not guessable; and
`noindex` via `_headers`.

## Rules

- **Append-only.** A delivered newsletter re-loads these URLs for years. Replacing a file
  changes the picture inside mail that has already been sent, which cannot be undone.
- **Content-addressed names** (`<slug>-<sha8>.<ext>`), written by
  `StPeters/mailerlite/static_host.py`. Re-using a name for different bytes is refused there.
- **Nothing but images.** No pages, no HTML, no data. That restriction is what licenses the
  automatic push.

## How a file gets here

`mailerlite/static_host.py` in the StPeters repo copies the file in and, with
`NEWSLETTER_ASSET_AUTOPUSH=1`, pushes. The public URL is the file's path under the site:
`https://<site>/assets/newsletter/<file>`.

🔴 **Staging is not publishing.** The URL 404s until Netlify has rebuilt. `compile_issue`
drops an image that is not answering 200 and warns Guy rather than sending a broken picture
(Guy's ruling, 2026-08-30).
