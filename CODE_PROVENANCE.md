# NullR-GPS — Code Provenance and Change Tracking

This document defines how the project records where code and other project materials came from. It is an evolving inventory, not a claim that every file has already been audited.

## 1. Provenance categories

| Category | Meaning | Required record |
|---|---|---|
| `inherited` | Code copied or retained from XposedFakeLocation or another upstream source | Source project, source file/path if known, license, notice requirements |
| `rewritten` | Code modified or rewritten from an identifiable upstream component | Original source, extent of change, remaining inherited portions, applicable license |
| `original` | Code independently created for NullR-GPS | Author/contributor, date or commit, applicable license status |
| `third-party` | External library, SDK, asset, map data, style, font, or other dependency | Exact component/version, source, license, required notices |

A file may contain a mixture of inherited and new material. Do not label an entire file `original` merely because it has been heavily edited.

## 2. Current known project lineage

| Item | Current record |
|---|---|
| Project | NullR-GPS |
| Current developer | Ndnt |
| Upstream project | XposedFakeLocation |
| Upstream author | Noobexon (`noobexon1`) |
| Upstream license | MIT, subject to verification against the exact upstream repository copy |
| New-code license | Undecided |

The exact upstream repository URL, commit or release used as the starting point, and import date should be added after verifying them from the actual Git history and source checkout.

## 3. Component inventory

Populate this table during the repository audit. Do not guess provenance.

| Component / path | Category | Original source / author | License | Changes / notes |
|---|---|---|---|---|
| To be audited | inherited / rewritten / original / third-party | Verify | Verify | Add commit or source reference |

Suggested areas to audit:

- application UI and Compose screens;
- application services and location logic;
- LSPosed/Xposed module and hooks;
- map renderer, tile sources, map styles, and map assets;
- networking and API integrations;
- native binaries and bundled assets;
- build scripts, Gradle plugins, and GitHub Actions;
- icons, fonts, images, and other design resources.

## 4. Recording a rewrite

When replacing or substantially rewriting an inherited component, record:

1. the previous path and source revision;
2. the new path and relevant commit(s);
3. which upstream portions, if any, remain;
4. whether any upstream copyright or license notice still applies;
5. the author(s) of the new contribution.

A rewrite does not automatically remove obligations for upstream code that remains in the result.

## 5. Git workflow recommendations

Use descriptive commits, for example:

- `refactor: replace inherited map screen with NullR-GPS map UI`
- `feat: add independently developed map controls`
- `docs: record provenance for location module`
- `chore: update third-party license inventory`

For imported source, retain the original repository URL and commit identifier in project records. Avoid rewriting or deleting history in a way that obscures provenance.

## 6. Release audit

Before publishing a release, confirm:

- [ ] All copied and adapted code has an identified source.
- [ ] Applicable upstream copyright and license notices remain.
- [ ] New code has an explicitly chosen license before making licensing claims.
- [ ] Third-party dependencies and assets are inventoried.
- [ ] Map data, tile services, and map styles comply with their separate terms.
- [ ] Binary distributions include required notices.
- [ ] The release notes distinguish new work from inherited components where useful.

## 7. Status

This inventory is a starting framework. It must be completed against the actual NullR-GPS repository, its Git history, dependency manifests, bundled assets, and the exact upstream source revision before it is treated as a complete provenance audit.
