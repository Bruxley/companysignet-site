# companysignet-site

Source for **https://companysignet.com/** — the business identity reference
("entity anchor") node for **Mr. Electric of Tucson**, operated by Acuity LLC.

## What this is

A single static page that restates and cross-links the business's verified
identity — address, phone, license, and third-party identifiers — so that AI
agents and knowledge graphs can resolve the business to one entity with high
confidence. It exists because the franchise-operated customer site cannot carry
this structured data.

It is **not** a marketing or lead-generation page: it defers all customer
activity to the official site, `mrelectric.com/tucson-southern-az`.

The substance is the JSON-LD block in `public/index.html` (schema.org
`Electrician`), which carries the identifiers, the AZ ROC credential, and the
`sameAs` cross-links. The visible HTML mirrors it for human readers.

## Layout

public/index.html the identity page (served at the site root)
wrangler.jsonc Cloudflare Workers static-assets config


## Deploying

Hosted on Cloudflare Workers with
[static assets](https://developers.cloudflare.com/workers/static-assets/).
Commits to `main` deploy automatically via Workers Builds.

## Maintaining

- Every identifier should be independently verifiable; when adding one, link its
  source of record in **both** the visible table and the JSON-LD `sameAs` array.
- Keep the NAP (name / address / phone) exactly consistent with the other
  authoritative listings — inconsistent variants defeat the purpose.
- Update `dateModified` in the JSON-LD when facts change, and the "last verified"
  dates in the page body when the facts are actually re-checked.

Related: the public OKF knowledge bundle at `companysignet.com/okf/`
(repo: `mr-electric-of-tucson-okf`), served by the `okf-proxy` Worker.
