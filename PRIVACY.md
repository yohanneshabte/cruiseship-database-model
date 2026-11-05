# Privacy policy for this repository

## Private by policy
This repository is kept **private-safe**: its current files are written so that
making it public would expose no personal data. Personal values (names, contact
details, vehicle and device identifiers, locations, schedules, credentials, and
any customer or client data) never belong in tracked files. Use generic
placeholders such as `<OWNER_NAME>`, `<EMAIL>`, `<PHONE>`, `<VIN>`,
`<GOOGLE_DOC_LINK>`, `<API_KEY>`, `<CLIENT_NAME>`, or env-var references like
`${API_KEY}`, and keep real values in untracked `.env` / local config files.

## PII scrub checklist (run before every commit)
- [ ] No owner real name in content, signatures, or copyright lines (the GitHub username in repo links is fine)
- [ ] No phone numbers or personal/work email addresses (also check commit author email; prefer the GitHub noreply address)
- [ ] No VINs, Tesla account IDs, vehicle IDs, or vehicle/API tokens
- [ ] No GPS coordinates, home address, or trip/charging/drive history
- [ ] No calendar events, meeting times, or personal schedules or routines
- [ ] No credentials: passwords, API keys, OAuth/refresh/session tokens, private keys, certificates, connection strings
- [ ] No device serial numbers, MAC/BLE addresses, or Wi-Fi SSIDs/passwords
- [ ] No Home Assistant long-lived tokens or real `secrets.yaml` values
- [ ] No opaque Google Docs/Drive (or other cloud) document IDs tied to a personal account
- [ ] No health, medical, or financial details about a real person
- [ ] **No customer or client data**: names, contact details, addresses, orders, bookings, testimonials, user lists, CRM/exports, analytics dumps, intake forms, waitlists, even when it does not look like typical PII
- [ ] Test fixtures use clearly fake data (example.com, 555-01xx, RFC 5737 IPs, made-up MACs)

## Admin & plugins
- [ ] No admin credentials committed (passwords, admin tokens, session secrets, default admin logins)
- [ ] Admin routes and URLs are not hardcoded with personal identifiers
- [ ] Admin/plugin configs read secrets from env vars (e.g. `${ADMIN_PASSWORD}`), never literal values
- [ ] Demo/seed codes and seed data are generic (e.g. `desk-a`, `store-1`) and do not identify real places or people

## Tesla-proprietary & employer-confidential
Only public information belongs here. Cite public sources, such as
[commaai/opendbc](https://github.com/commaai/opendbc) for vehicle CAN signals, the
public Tesla Owner's Manual and service.tesla.com Service Manual, and public parts
catalogs/listings.
- [ ] No internal Tesla data: no Toolbox/internal tooling details, internal hostnames/URLs, or anything marked confidential/internal/do-not-distribute
- [ ] No non-public CAN IDs, signals, or protocols (check against opendbc `tesla_*.dbc`), firmware internals (build names, unreleased versions, decrypted images, keys, gateway configs), or undocumented service-mode menus/codes
- [ ] No internal part numbers beyond public catalogs and service manuals
- [ ] No self-driving training data, camera clips/frames, camera analytics, fleet telemetry, or data-engine/autolabel/shadow-mode internals
- [ ] Personal dashcam/TeslaCam/Sentry media stays out of the repo (plates, faces, and GPS metadata are PII)
- [ ] No ex-employer (e.g. Google) confidential info: no codenames, go/ links, internal hostnames, LDAPs, bug IDs, internal docs or design-doc content, or code copied from internal repos
- [ ] No other third party's NDA or confidential material

This checklist is a hygiene aid, **not legal advice**. If any such data is ever
committed by accident, treat it as a **rewrite-immediately** event: purge it with
`git filter-repo` or BFG Repo-Cleaner, force-push, have collaborators re-clone, and
rotate any exposed keys. Do not just fix it forward.

## Git history warning
Deleting or editing a file does **not** remove it from past commits. Anyone with
access to the repository (or a fork or clone) can still read the old content.
Removing it requires rewriting history with `git filter-repo` or BFG
Repo-Cleaner, followed by a force push and asking collaborators to re-clone.
Any credential that was ever committed must be treated as leaked and rotated.
An accidental PII or secret commit is a **rewrite-immediately** event, not a
fix-forward: do not just commit a correction on top.
