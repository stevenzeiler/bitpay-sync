# AGENTS.md

## Stack

Node.js (2015-era), `bridges` framework with Express 4, Bookshelf and Knex on Postgres, `bitpay-invoice-generator`, gulp + 6to5 build, mocha tests. Dormant since 2015-01-18; see `docs/STATUS.md`.

## Layout

- `src/config/routes.js` routes; `src/controllers/` invoices, callbacks, notifications
- `src/models/invoice.js` Bookshelf model; `src/lib/invoice_generator.js` BitPay client
- `src/migrations/`, `src/knexfile.js` database; `src/processes/server.js` HTTP server
- `build/` compiled output (git-ignored); `gulpfile.js` build

## Commands

`npm install`, `npm run build`, `npm start`, `npm test`, `npm run db:migrate`. None were run in the docs pass.

## Rules

- Never commit secrets. The BitPay key and database credentials come from environment variables only.
- Use Conventional Commits.
- Keep `docs/STATUS.md` current when behaviour or status changes.
- Do not change behaviour in docs-only changes.
