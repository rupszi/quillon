# Decisions

One entry per decision: what was chosen, what was rejected, and why. Newest at the bottom. An entry is never edited after the fact; a changed decision gets a new entry that points back to the old one.

## D-01 · Name: Quillon (2026-10-11)

**Chosen:** Quillon, the crossguard of a sword.
**Rejected:** Skynet (wrong signal to the regulated teams this is for, and crowded on GitHub); Quel'Serrar (Blizzard's name, and the apostrophe does not survive as a package name); Warden, Keel, Sentinel, Bulwark (taken on PyPI); Tether (the USDT stablecoin brand).
**Why:** Short, unusual, means "guard" without saying "AI", and was free on PyPI.

## D-02 · License: Apache-2.0 (2026-10-11)

**Chosen:** Apache-2.0.
**Rejected:** MIT.
**Why:** Apache-2.0 includes an explicit patent grant, which corporate legal teams look for before allowing a tool inside.

## D-03 · Releases through PyPI trusted publishing (2026-10-11)

**Chosen:** GitHub Actions publishes to PyPI on a `v*` tag, verified by OpenID Connect, with a `pypi` environment.
**Rejected:** a long-lived API token stored as a repository secret.
**Why:** No secret to leak or rotate. Fits a project whose point is that nothing happens without a check.

## D-04 · Tooling: uv, src layout, Python 3.12+ (2026-10-11)

**Chosen:** uv for environments, builds and publishing; `src/quillon` layout; Python 3.12 or newer.
**Rejected:** Poetry; a flat layout.
**Why:** uv is one fast tool for the whole workflow. The src layout means tests run against the installed package, not the working folder.

## D-05 · Versioning: 0.1.x weekly, 0.2.0 first usable (2026-10-11)

**Chosen:** a 0.1.x release at the end of each milestone week, and 0.2.0 as the first release meant for use.
**Why:** 0.1.0 was already published as the name placeholder, and versions can only go up.