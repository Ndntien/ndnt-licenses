# NullR-GPS — Authorship & Project Attribution

**Project:** NullR-GPS  
**Current project developer:** Ndnt  
**Original upstream project:** XposedFakeLocation  
**Original upstream author:** Noobexon (`noobexon1`)  
**Upstream license:** MIT (retain the exact upstream license text and notices)

## 1. Purpose

This document records the known origins of NullR-GPS, acknowledges the upstream work on which parts of the project are based, and explains how later contributions are tracked.

NullR-GPS is being developed as a substantially modified and independently evolving project. Its interface, user experience, features, effects, map experience, architecture, and other implementation details may be redesigned, replaced, or newly developed over time.

A substantial redesign does not erase the authorship or license obligations attached to code that remains derived from or copied from an upstream project.

## 2. Acknowledgement of the original project

NullR-GPS acknowledges the original work of **Noobexon (`noobexon1`)** on **XposedFakeLocation**.

The upstream project provided an initial technical foundation for parts of this project. We appreciate the time, engineering, and effort invested in that work.

This acknowledgement is not a claim that the upstream author endorses, sponsors, or is affiliated with NullR-GPS.

## 3. Contributions to NullR-GPS

**Ndnt** is the current project developer identified for NullR-GPS. Contributions made by Ndnt and any future contributors should be traceable through source-control history and project records.

New or independently created work may include, where actually implemented:

- redesigned application interface and visual system;
- new interaction patterns, animations, and user experience;
- new or substantially changed features and workflows;
- rewritten or reorganized application architecture;
- new map integration, rendering, and map-related functionality;
- changes to the companion application and LSPosed module;
- performance, compatibility, testing, and maintenance improvements;
- project documentation, build and release infrastructure.

This list describes areas of development; it is not a representation that every item has already been completed.

## 4. Authorship and rights are component-specific

Rights are determined by the actual authorship, provenance, and applicable license of each component:

- **Upstream-derived or copied code:** remains subject to the upstream copyright notices and applicable license terms.
- **Modified upstream code:** may contain both upstream material and new contributions; applicable upstream notices and license terms must be preserved.
- **Independently written code:** is attributed to its actual author(s), subject to any license or agreement that applies to it.
- **Third-party dependencies and assets:** remain subject to their own licenses and terms.
- **Branding, names, logos, and visual assets:** must be checked separately for ownership and permissions.

No statement in this document transfers ownership of upstream work or third-party material to Ndnt.

## 5. License status

The upstream MIT license and its copyright notice must be retained for copies or substantial portions of the upstream software, as required by that license.

**The license for newly written NullR-GPS code has not yet been decided.** Until a separate license is deliberately selected and documented, do not describe all of NullR-GPS as MIT-licensed, proprietary, or otherwise uniformly licensed.

The repository's `LICENSE` file must preserve the exact upstream MIT license text and original copyright notice where upstream MIT-licensed material is included. If the repository contains components under different licenses, document that clearly rather than implying that one license covers everything.

## 6. Development and provenance policy

The project uses the following conceptual categories:

- `inherited/` — material retained from the upstream project or another identified source;
- `rewritten/` — material substantially modified or rewritten from an identifiable source;
- `original/` — material independently created for NullR-GPS.

These are provenance categories, not a requirement to arrange the source tree into directories with those names. They may be tracked in `CODE_PROVENANCE.md`, file headers, commit messages, or an internal inventory.

For meaningful changes, contributors should:

1. identify the source of reused code, assets, and dependencies;
2. preserve applicable copyright and license notices;
3. record substantial rewrites and replacements;
4. use clear commit messages and retain relevant history;
5. review license compatibility before redistributing or commercializing components.

## 7. No endorsement or affiliation

Unless separately agreed in writing, NullR-GPS is an independent project. Mention of XposedFakeLocation or Noobexon is for attribution and provenance only and does not imply endorsement, partnership, or affiliation.

## 8. Corrections and contact

If an attribution, copyright notice, or component provenance is inaccurate or incomplete, please open an issue or contact the project maintainer so it can be reviewed and corrected.

---

*This document is informational. It does not replace the applicable license texts, legal agreements, or a component-by-component license review.*
