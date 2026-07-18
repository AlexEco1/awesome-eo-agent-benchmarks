# Awesome EO Agent Benchmarks [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of benchmarks for evaluating **Earth-Observation (EO) agents** — LLM-based systems that take multiple steps and call tools to solve tasks over Earth observation data.

## Scope — what counts

A benchmark is listed here if it passes two gates:

1. **Agentic** — the system takes multiple steps, choosing each action after observing the result of the previous one, against executable tools or an environment. One-shot code generation (generate → execute → score) and single-turn VQA do **not** count.
2. **EO / geospatial workflow** — the task derives information about the physical Earth from observation data (satellite, airborne, radar, in-situ, or products derived from them — reanalysis, land cover, NDVI, SST), or uses those outputs together with other geospatial data. Purely record-based tasks (POI search, routing, generic vector operations) do not count.

**Availability legend:** ✅ code + data released · 🟡 partial release · 📄 paper only (no artifacts located).
All links and availability statuses were verified by actually fetching them on **2026-07-17/18**. As of that date: **9 ✅ · 4 🟡 · 10 📄.**

## The benchmarks

Ordered by peer-review tier: journal → conference → workshop → preprint.

| # | Benchmark | Paper | Venue | Focus | Tasks | Code | Data | Availability |
|---|---|---|---|---|---|---|---|---|
| 1 | **RescueADI** | [arXiv:2410.13384](https://arxiv.org/abs/2410.13384) | IEEE TGRS (journal) | disaster response | 998 | — | — | 📄 no public release located (2026-07) |
| 2 | **ClimateAgent** | [arXiv:2511.20109](https://arxiv.org/abs/2511.20109) | TMLR (journal) | climate workflows (SST, drought, cyclones) | 85 | — | — | 📄 the paper's repo link returns 404 (2026-07) |
| 3 | **Earth-Bench** (Earth-Agent) | [arXiv:2509.23141](https://arxiv.org/abs/2509.23141) | ICLR 2026 | generalist EO | 248 | [GitHub](https://github.com/opendatalab/Earth-Agent) | [HF](https://huggingface.co/datasets/Sssunset/Earth-Bench) | ✅ MIT / Apache; golden tool-traces ship |
| 4 | **OpenEarthAgent** | [arXiv:2602.17665](https://arxiv.org/abs/2602.17665) | ECCV 2026 | generalist EO | 1,169 eval | [GitHub](https://github.com/mbzuai-oryx/OpenEarthAgent) | [HF](https://huggingface.co/datasets/MBZUAI/OpenEarthAgent) | ✅ golden trajectories + grader; code repo has no license file |
| 5 | **UnivEARTH** | [arXiv:2504.12110](https://arxiv.org/abs/2504.12110) | ACL 2026 Findings | Google Earth Engine workflows | 140 | [GitHub](https://github.com/IandRover/univearth_arr) | [HF](https://huggingface.co/datasets/AaronKao/UnivEARTH) | 🟡 QA pairs public; no reference solutions or packaged grader; running needs a GEE account |
| 6 | **ZephyrusBench** | [arXiv:2510.04017](https://arxiv.org/abs/2510.04017) | ICLR 2026 | weather (WeatherBench-2 reanalysis) | 2,230 | [GitHub](https://github.com/Rose-STL-Lab/Zephyrus) | [HF](https://huggingface.co/datasets/Rose-STL-Lab/Zephyrus) | 🟡 MIT; answers ship, golden traces do not |
| 7 | **GCA** (Gulf Climate Agent) | [arXiv:2604.12306](https://arxiv.org/abs/2604.12306) | ACL 2026 | climate + hydrology / air quality | 91 | — | — | 📄 no public release located (2026-07) |
| 8 | **ThinkGeo** | [arXiv:2505.23752](https://arxiv.org/abs/2505.23752) | CVPR 2026 workshop (MONTI) | RS tool use, optical + SAR | 486 | [GitHub](https://github.com/mbzuai-oryx/ThinkGeo) | [HF](https://huggingface.co/datasets/MBZUAI/ThinkGeo) | ✅ Apache / CC-BY; golden dialogs ship (436 RGB + 50 SAR) |
| 9 | **GeoLLM-Engine** | [arXiv:2404.15500](https://arxiv.org/abs/2404.15500) | CVPR 2024 workshop (EarthVision) | GIS platform / copilot control | ≈522k auto-generated | [project page](https://dstamoulis.github.io/geollm-engine/) | — | 📄 project page lists code and dataset as "coming soon" (2026-07) |
| 10 | **GeoLLM-QA** | [arXiv:2405.00709](https://arxiv.org/abs/2405.00709) | ICLR 2024 workshop (ML4RS) | GIS platform / copilot control | 1,000 | — | — | 📄 no artifacts located (2026-07) |
| 11 | **OpenEarth-Bench** | [arXiv:2603.22148](https://arxiv.org/abs/2603.22148) | preprint | generalist EO (agent-created tools) | 596 | [GitHub](https://github.com/walking-shadow/OpenEarth-Agent) | — | 📄 repo currently contains README + paper PDF only |
| 12 | **TerraBench** | [arXiv:2606.13148](https://arxiv.org/abs/2606.13148) | preprint | generalist EO | 403 | [GitHub](https://github.com/Takerdat23/TerraBench) | — | 🟡 framework code MIT; dataset access requires authors' approval (per README) |
| 13 | **EO-Gym** | [arXiv:2605.01250](https://arxiv.org/abs/2605.01250) | preprint | generalist EO, 6 task families | 1,436 test | [HF (single repo)](https://huggingface.co/datasets/paperuploadacount/EO-Gym) | [HF (single repo)](https://huggingface.co/datasets/paperuploadacount/EO-Gym) | ✅ golden trajectories + tool server + grader + data in one repo; license "other" |
| 14 | **GeoDisaster** | [arXiv:2606.17246](https://arxiv.org/abs/2606.17246) | preprint | disaster, optical + SAR | 292 test | — | — | 📄 claimed repo not found (2026-07) |
| 15 | **DORA** | [arXiv:2605.11633](https://arxiv.org/abs/2605.11633) | preprint | disaster response, 45 real events | 515 | — | — | 📄 release stated as planned (paper May 2026) |
| 16 | **DisasterBench** | [arXiv:2605.27957](https://arxiv.org/abs/2605.27957) | preprint | disaster response | 233 | [GitHub](https://github.com/TamuChen18/DisasterBench_Open) | [in repo](https://github.com/TamuChen18/DisasterBench_Open) | ✅ MIT; golden plans + grader (its 26 "agents" are typed JSON manifests, not executable tools) |
| 17 | **AgentCaster** | [arXiv:2510.03349](https://arxiv.org/abs/2510.03349) | preprint | tornado forecasting | 40 forecast days | [GitHub](https://github.com/agentcaster/agentcaster) | [HF](https://huggingface.co/datasets/agentcaster/agentcaster) | ✅ GT polygons + grader + 40-day HRRR archive; **reports evaluation cost (~$500)**; no license file |
| 18 | **AgriWorld / AgroBench** | [arXiv:2602.15325](https://arxiv.org/abs/2602.15325) | preprint | agriculture, RS time-series | 541 | — | — | 📄 nothing located (2026-07); not to be confused with the unrelated AgroBench ([arXiv:2507.20519](https://arxiv.org/abs/2507.20519)) |
| 19 | **AgroTools** | [arXiv:2605.22366](https://arxiv.org/abs/2605.22366) | preprint | agriculture (~half SPOT 6-7 imagery) | 539 | — | [HF](https://huggingface.co/datasets/AgroTools/AgroTools) | 🟡 QA + 1,097 images public; tool layer, traces and grader not included |
| 20 | **GeoAgentBench** | [arXiv:2604.13888](https://arxiv.org/abs/2604.13888) | preprint | GIS + Landsat band math | 57 | [GitHub](https://github.com/GeoX-Lab/GABench) | [in repo (Git-LFS)](https://github.com/GeoX-Lab/GABench) | ✅ golden toolchains + executable toolbox + data; no license file; clone with `git lfs` |
| 21 | **GeoNatureAgent** | [arXiv:2606.12821](https://arxiv.org/abs/2606.12821) | preprint | ecology (BigEarthNet Sentinel-2 + LUCAS in-situ) | 93 | [GitHub](https://github.com/gabrielireland/GeoNatureAgent_Benchmark) | [Zenodo](https://doi.org/10.5281/zenodo.20450995) | ✅ Apache; tasks + grader + self-hostable API; 33/93 tasks numerically keyed, 60 rubric-graded |
| 22 | **GeoAgent / GeoCode** | [arXiv:2410.18792](https://arxiv.org/abs/2410.18792) | preprint | GEE / Sentinel-2 code agents | 1,356 multi-turn (of 19,504) | [GitHub](https://github.com/Yusin2Chen/GeoAgent) | — | 📄 agent code public; the task set is not released (repo contains 1 example task) |
| 23 | **TerraLogic** | [arXiv:2607.12497](https://arxiv.org/abs/2607.12497) | preprint | hierarchical geospatial reasoning, optical + SAR + IR | 545 | [GitHub](https://github.com/Ireliya/TerraLogic) | [HF](https://huggingface.co/datasets/Ireliya/hierarchical-geospatial-reasoning) | ✅ Apache / CC-BY; questions + gold answers + tool stack (no step-by-step traces) |
