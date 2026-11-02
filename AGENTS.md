# Development rules

- Keep this repository private. Do not change GitHub visibility or publish releases/assets without the owner's explicit instruction.
- Canonical local source lives in `F:/Peca-Digital/software/peca-image-studio`; all generated documentation and assets must remain within `F:/Peca-Digital`.
- Treat `src/` as the single software source. Generate trial and offline editions using `npm run build`; do not separately patch generated editions.
- Run `npm test`, `npm run check`, and `npm run build` for meaningful behavior changes. Browser QA uses the supported CUA tool, never an alternate automation path.
- Never commit credentials, NewebPay settings, personal account data, customer images, Downloads, runtime caches, or build archives.
- Keep trial publication separate from enabling sales. No live payment, order collection, public full-edition downloads, or customer outreach unless explicitly authorized.
- New work uses a feature/fix branch, clear commits, a CHANGELOG entry, and a SemVer prerelease tag until store-owner acceptance. Do not mark a release stable while compatibility checks remain incomplete.
- Record actual validation limits. The in-app browser rejects file:// navigation; do not circumvent it. Offline file opening and 50-image stress testing await owner-side validation. Mobile viewport overrides did not take effect in the current runtime, so mobile QA is not verified.
