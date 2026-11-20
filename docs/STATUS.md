# Status

Last updated 2026-11-20 (pass 02 of the GitHub audit). Nothing was installed or run; everything below is read from the source.

## What works

- Routes, controllers, model and one migration are present and consistent with each other.
- Configuration comes from environment variables; no API key is committed.

## Known broken or unverified

- Not run: `npm install`, `npm test`, `npm start`, migrations. Dependencies are 2015 versions.
- `src/models/invoice.js`, `Invoice.pay`: the BitPay status check is not awaited (its rejections are lost), and `!response.status === 'confirmed'` is always false, so that guard never fires. Only the `payment.status !== 'confirmed'` check on the callback body is effective. **(inference)** from reading the code.
- `GET /notifications` etc. return errors through `next(error)` with no error-handling middleware in `src/processes/server.js` **(inference: `bridges-express` may install one)**.
- Only one test (`src/test/models/invoice.js`) exists.

## Next

1. Fix the `Invoice.pay` verification (await the status call, correct the comparison).
2. Add a `LICENSE` file matching `package.json` (ISC), a `repository` field and `engines`.
3. Run the tests on a Node version the dependencies support.

## Not yet from the repo standard

AGENTS.md and CLAUDE.md are added alongside this file. Missing: CONTRIBUTING.md, docs/ARCHITECTURE.md, docs/RELEASING.md, docs/decisions/, events/CATALOG.md, CHANGELOG.md, SECURITY.md, LICENSE, `.github/`.
