# Changelog

Dated changes to the list. Every entry was checked against its primary sources on the date shown.

## 2026-10-25

A systematic search for new benchmarks (arXiv, 2026 venue lists, other lists, GitHub and Hugging Face), cross-checked with the ESA Φ-lab / BIFOLD survey of EO agent benchmarks.

- **Added:** DUDA-Bench, KnowFlow-Bench and CBGB (†).
- **Venue:** EarthVerse is a NeurIPS 2026 workshop paper.
- **Excluded list extended** in `contributing.md`: GeoPlan-bench, GeoJSON Agents, AirSpatial-Bench, RemoteAgent's VagueEO.

## 2026-10-24

Full re-check of every entry against its sources (paper, venue page, repository, dataset).

- **Added:** EarthVerse.
- **New version:** Earth-Bench now points to Earth-Bench-V2, the authors' corrected release, with its open-world companion Earth-Bench-OW.
- **Now released:** ClimateAgent, DORA and GeoDisaster. GeoAgent/GeoCode's task set is on Hugging Face (it was wrongly listed as unreleased). GCA released code and a gated task set (partial).
- **Venues confirmed on the venue sites:**
  - GeoAgentBench: Geo-spatial Information Science, a journal.
  - DORA: NeurIPS 2026, oral.
  - UnivEARTH: Findings of ACL 2026.
  - GeoDisaster: BMVC 2026.
  - DisasterBench: Findings of EMNLP 2026.
  - GeoNatureAgent: ACM SIGSPATIAL 2026, short paper.
  - GeoAgent/GeoCode: ECML PKDD 2025.
  - AgentCaster: NeurIPS 2025 workshop.
  - OpenEarthAgent now links its ECCV 2026 page, and ThinkGeo links its workshop page.
- **Moved to Near misses** (they fail Gate 1): RescueADI and DisasterBench.
- **Marked borderline on Gate 1 (†):** UnivEARTH, GCA and GeoAgent/GeoCode.
- **Availability changes:**
  - TerraBench: 🟡 → 📄 (no tasks released).
  - ThinkGeo: ✅ → 🟡 (SAR images not released).
  - ZephyrusBench and UnivEARTH: 🟡 → ✅.
- **Corrected:**
  - Task counts: RescueADI, UnivEARTH (408), GeoNatureAgent (103).
  - Focus texts: AgroTools, GeoAgentBench, TerraBench, GCA, GeoNatureAgent, GeoAgent/GeoCode.
  - Licences: EO-Gym, GeoAgentBench, AgentCaster, EarthVerse.
  - The example quotes, which are now verbatim.
- **Repository:** added a CC0 licence, a contributing guide with an excluded list, a citation file, a weekly link check and issue forms.

## 2026-07-22

First public version: 23 benchmarks, with links and availability checked on 2026-07-17/18.
