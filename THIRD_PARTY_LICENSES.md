# NullR-GPS — Third-Party Licenses and Components

This inventory tracks software, libraries, SDKs, assets, and external data used by NullR-GPS. It is intentionally a verification template until each dependency and asset has been checked against the actual repository and build outputs.

## 1. Project source foundation

| Component | Source / author | License | Required action |
|---|---|---|---|
| XposedFakeLocation source foundation | Noobexon (`noobexon1`) | MIT (verify exact upstream license file) | Preserve original copyright notice and full MIT license text for applicable copies or substantial portions |

## 2. Dependency inventory

Add one row for every direct and transitive dependency that must be disclosed, and every separately licensed asset or data source.

| Component | Version | Purpose | License | License/notice location | Verified |
|---|---|---|---|---|---|
| To be audited | — | — | — | — | No |

Recommended sources for the audit:

- Gradle version catalogs and dependency declarations;
- resolved dependency reports and lockfiles;
- bundled JAR/AAR files and native libraries;
- Android assets and resources;
- map SDKs, tile providers, map data, and styles;
- fonts, icons, illustrations, and images;
- build tools, plugins, and code generators where redistribution terms apply.

## 3. Map-related materials require separate review

A map renderer library, map data, tile server, style, font, and API service may each have different terms. Do not assume that a free-to-use map endpoint grants unrestricted caching, offline use, redistribution, commercial use, or removal of attribution.

Record at least:

| Map component | Provider / source | Terms or license | Attribution / usage restrictions |
|---|---|---|---|
| Renderer | To be verified | To be verified | To be verified |
| Tile source / data | To be verified | To be verified | To be verified |
| Style | To be verified | To be verified | To be verified |
| Fonts / icons | To be verified | To be verified | To be verified |

## 4. License compatibility and distribution

Before distributing NullR-GPS, review each component's terms for:

- commercial use;
- redistribution in APKs or other binaries;
- source-code disclosure requirements, if any;
- attribution and notice requirements;
- patent or trademark terms;
- modification and derivative-work conditions;
- network-service, API, caching, and rate-limit restrictions.

Do not assume that the upstream MIT license automatically applies to every dependency or that every dependency permits the same use.

## 5. New NullR-GPS code

The license for newly written NullR-GPS code is **not yet decided**. Do not state that all new code is MIT-licensed or proprietary until the project maintainer has made and documented that decision.

The upstream MIT notices must still be preserved for upstream MIT-licensed material included in the project, regardless of the future license chosen for independently written code.

## 6. Verification status

This file is not a completed software bill of materials (SBOM) or legal audit. Update it using the actual dependency graph, packaged artifacts, source headers, and asset origins before each public release.
