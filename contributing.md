# Contributing

Thank you for helping keep this list accurate. New benchmarks and corrections are both welcome. Open an issue with one of the two forms ("New benchmark" or "Correction"), or send a pull request that changes `README.md`.

## What gets listed

A benchmark is listed if it passes both gates in the README's [Scope](README.md#scope-what-counts):

1. **Gate 1, agentic.** The system takes multiple steps, choosing each action after observing the result of the previous one, against executable tools or an environment.
2. **Gate 2, EO or geospatial workflow.** Most of its tasks, or a good share of them, need information about the physical Earth derived from observation data (satellite, airborne, radar, in-situ, or products derived from them).

Close relatives that pass Gate 2 but fail Gate 1 go under **Near misses**. Benchmarks that pass Gate 1 only weakly are marked **†** with a one-line note.

## What to include in a proposal

Every claim in the list must be checkable against a primary source. Please give:

- **Paper:** an arXiv or DOI link.
- **Venue:** a link to the venue's own page (accepted-papers list, proceedings, journal page). An arXiv comment such as "accepted at X" is not enough on its own. If there is no venue yet, write "preprint".
- **Gate 1 evidence:** a quote from the paper or code showing that the agent sees tool results and chooses its next step.
- **Gate 2 evidence:** which observation data the tasks use, and roughly what share of the tasks use it.
- **Tasks:** the number of tasks, and where it is stated (a table in the paper, or a count of the released files).
- **Code and data:** links, and the licence of each.

## How an entry is written

- One row in the table, in the tier order of the README (journal, conference, workshop, preprint).
- **Availability:** ✅ code + data released · 🟡 partial (something missing, or access needs the authors' approval) · 📄 no tasks released. The note says only what ships and the licence, in about 12 words.
- **Current version only.** When a benchmark releases a new version, update its row; do not add a second row.
- Write "none" for a missing link, never leave a cell empty.

## Corrections

Use the "Correction" form, or a pull request. Name the benchmark and the cell, say what it should be, and link the source that shows it. Facts in this field change quickly (new versions, venues, releases), so corrections are the most useful contribution.

## How the list is checked

- Links are checked automatically every week (`.github/workflows/link-check.yml`). Sites that block scripts (IEEE, Taylor & Francis, LinkedIn) are counted as working.
- Every entry and change is checked against its primary sources (paper, venue page, repository, dataset) before it is listed. The README states the date of the last full check.
- Candidates were found with a scripted literature search and LLM-assisted screening; the maintainer reviews every change.

## Excluded, with reasons

Decided in our July 2026 review. If something has changed, please open a correction.

| Why it is out | Benchmarks | Deciding fact |
|---|---|---|
| Gate 2: map records only | MapEval-API ([arXiv:2501.00316](https://arxiv.org/abs/2501.00316)) | The agent's tools look up places, routes and travel times; nothing about the Earth is measured. |
| Gate 2: almost no observation data | GeoBenchX ([arXiv:2503.18129](https://arxiv.org/abs/2503.18129)) | 2 of its 11 rasters are observation-derived, used in about 1 of 200+ tasks; the rest is map and census data. |
| Gate 2: vector records only | ShapefileGPT's task set | 42 shapefile-processing tasks; no observation-derived data. |
| Gate 2: not geospatial | CORE | General-domain tool-use evaluation. |
| Gate 1: one-shot code | AutoGEEval ([arXiv:2505.12900](https://arxiv.org/abs/2505.12900)) and its follow-ups; GeoCode-Bench / GeoCode-Eval (from GeoCode-GPT) | The model writes code once; it is run and scored. No loop. |
| Gate 1: code never run | GeoGraphRAG's 300 Earth Engine workflows ([doi](https://doi.org/10.1016/j.jag.2025.104712)) | Generated code is graded by similarity, never executed. |
| Gate 1: plans never executed | GTChain-Eval ([doi](https://doi.org/10.1016/j.jag.2024.104312)); GeoTool-GPT's prompt set | Workflows are written once as text; GeoTool-GPT's are carried out by people in ArcGIS. |
| Gate 1: no tools | RS-VL3M ([arXiv:2507.20776](https://arxiv.org/abs/2507.20776)); MineBench; CityBench | A vision-language corpus; a VQA formulation; a simulator with no model-invoked tools. |
| Gate 1: single-turn question answering | VRSBench ([arXiv:2406.12384](https://arxiv.org/abs/2406.12384)), GeoChat, GEOBench-VLM, LHRS-Bench, XLRS-Bench and similar | One image, one question, one answer. |
| Not a benchmark | RS-Agent, GIS Copilot, GeoLLM-Squad, REMSA and other agent systems | These papers describe the system being tested, not a test. |
| Out of scope by type | AstroAgentBench, formerly AstroReason-Bench ([arXiv:2601.11354](https://arxiv.org/abs/2601.11354)); BEDI, ESARBench | Space-mission and satellite tasking (deciding what to photograph); embodied UAV robotics. |
