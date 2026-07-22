# Awesome EO Agent Benchmarks [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of benchmarks for evaluating **Earth-Observation (EO) agents** — LLM-based systems that take multiple steps and call tools to solve tasks over Earth observation data.

## Scope — what counts

A benchmark is listed here if it passes two gates. The examples below are real
benchmarks; the ones that *fail* a gate are named, so the boundary is checkable.

### Gate 1 — Agentic

The system takes multiple steps, choosing each action after observing the
result of the previous one, against executable tools or an environment.

- **Passes** — take task 0 from *OpenEarthAgent* ([arXiv:2602.17665](https://arxiv.org/abs/2602.17665)): *"Which fire station and police station are closest to each other in Banff National Park within 3 km?"* To answer it, the agent first fetches the park boundary, sees it saved, then adds a fire-station layer, checks how many it found, adds a police-station layer, and only then computes the pairwise distances. Each call depends on what the previous one returned — that back-and-forth is what makes it agentic.
- **Fails — single-turn VQA.** *VRSBench* ([arXiv:2406.12384](https://arxiv.org/abs/2406.12384), NeurIPS 2024) hands a model a remote-sensing image, asks a question about it, and grades the one-shot answer. The model looks once and replies; there's no result to observe and no next move to pick, so there's no loop.
- **Fails — one-shot code generation.** In *AutoGEEval* ([arXiv:2505.12900](https://arxiv.org/abs/2505.12900)) the model writes a piece of Google Earth Engine code that gets run once and scored. Generate, execute, score is a straight line — the model never sees how it went and adjusts.

### Gate 2 — EO / geospatial workflow

A benchmark passes this gate when most of its tasks — or a good share of them —
require the agent to work with information about the physical Earth derived from
observation data: satellite, airborne, radar, in-situ, or products derived from
them (reanalysis, land cover, NDVI, SST), possibly alongside other geospatial data.

Some tasks can be answered just by looking things up in a map database — where
places are, how far apart they sit, how to get between them (OpenStreetMap,
Google Maps). Nothing there is measured about the Earth. A benchmark made up
mostly of such tasks does not pass; a handful of them inside an otherwise-EO
benchmark is fine.

- **Passes** — for example, task 3 from *OpenEarthAgent* ([arXiv:2602.17665](https://arxiv.org/abs/2602.17665)) asks the agent to *"assess urban growth in Nizwa Province, Oman between 2019 and 2024 using the NDBI change layer."* Here the agent has to call a tool to compute the NDBI — a built-up index — from satellite imagery for each year and then take the difference, so the answer comes straight out of the observation data.
- **Fails** — *MapEval-API*, the tool-using half of MapEval ([arXiv:2501.00316](https://arxiv.org/abs/2501.00316), ICML 2025 Spotlight), is a real multi-step agent, so it clears Gate 1. A typical task reads: *"I am driving to Brassica in Bexley via E Whittier St. After reaching Lockbourne Rd, where should I go next?"* But to solve it the agent only ever looks things up in a map — place search, place details, travel time, directions, nearby search — and nothing about the Earth is ever measured. A benchmark built mostly of tasks like this doesn't pass.

**Availability legend:** ✅ code + data released · 🟡 partial release · 📄 paper only (no artifacts located).
All links and availability statuses were verified by actually fetching them on **2026-07-17/18**. As of that date: **9 ✅ · 4 🟡 · 10 📄.**

## The benchmarks

Ordered by peer-review tier: journal → conference → workshop → preprint.

| # | Benchmark | Paper | Venue | Focus | Tasks | Code | Data | Availability |
|---|---|---|---|---|---|---|---|---|
| 1 | **RescueADI** | [arXiv:2410.13384](https://arxiv.org/abs/2410.13384) | [IEEE TGRS (journal)](https://ieeexplore.ieee.org/document/10849780) | disaster response | 998 | — | — | 📄 no public release located (2026-07) |
| 2 | **ClimateAgent** | [arXiv:2511.20109](https://arxiv.org/abs/2511.20109) | [TMLR (journal)](https://mlanthology.org/tmlr/2026/li2026tmlr-climateagent/) | climate workflows (SST, drought, cyclones) | 85 | — | — | 📄 the paper's repo link returns 404 (2026-07) |
| 3 | **Earth-Bench** (Earth-Agent) | [arXiv:2509.23141](https://arxiv.org/abs/2509.23141) | [ICLR 2026](https://openreview.net/forum?id=dkIXAbWuxO) | generalist EO | 248 | [GitHub](https://github.com/opendatalab/Earth-Agent) | [HF](https://huggingface.co/datasets/Sssunset/Earth-Bench) | ✅ MIT / Apache; golden tool-traces ship |
| 4 | **OpenEarthAgent** | [arXiv:2602.17665](https://arxiv.org/abs/2602.17665) | [ECCV 2026](https://arxiv.org/abs/2602.17665) | generalist EO | 1,169 eval | [GitHub](https://github.com/mbzuai-oryx/OpenEarthAgent) | [HF](https://huggingface.co/datasets/MBZUAI/OpenEarthAgent) | ✅ golden trajectories + grader; code repo has no license file |
| 5 | **ZephyrusBench** | [arXiv:2510.04017](https://arxiv.org/abs/2510.04017) | [ICLR 2026](https://openreview.net/forum?id=XOKasWdySX) | weather (WeatherBench-2 reanalysis) | 2,230 | [GitHub](https://github.com/Rose-STL-Lab/Zephyrus) | [HF](https://huggingface.co/datasets/Rose-STL-Lab/Zephyrus) | 🟡 MIT; answers ship, golden traces do not |
| 6 | **GCA** (Gulf Climate Agent) | [arXiv:2604.12306](https://arxiv.org/abs/2604.12306) | [ACL 2026](https://aclanthology.org/2026.acl-long.1967/) | climate + hydrology / air quality | 91 | — | — | 📄 no public release located (2026-07) |
| 7 | **UnivEARTH** | [arXiv:2504.12110](https://arxiv.org/abs/2504.12110) | [ICML 2025 workshop (TerraBytes)](https://openreview.net/forum?id=1ozeeVxfNd) | Google Earth Engine workflows | 140 | [GitHub](https://github.com/IandRover/univearth_arr) | [HF](https://huggingface.co/datasets/AaronKao/UnivEARTH) | 🟡 QA pairs public; no reference solutions or packaged grader; running needs a GEE account |
| 8 | **ThinkGeo** | [arXiv:2505.23752](https://arxiv.org/abs/2505.23752) | [CVPR 2026 workshop (MONTI)](https://openreview.net/forum?id=qSs6tJ5RjC) | RS tool use, optical + SAR | 486 | [GitHub](https://github.com/mbzuai-oryx/ThinkGeo) | [HF](https://huggingface.co/datasets/MBZUAI/ThinkGeo) | ✅ Apache / CC-BY; golden dialogs ship (436 RGB + 50 SAR) |
| 9 | **GeoLLM-Engine** | [arXiv:2404.15500](https://arxiv.org/abs/2404.15500) | [CVPR 2024 workshop (EarthVision)](https://openaccess.thecvf.com/content/CVPR2024W/EarthVision/html/Singh_GeoLLM-Engine_A_Realistic_Environment_for_Building_Geospatial_Copilots_CVPRW_2024_paper.html) | GIS platform / copilot control | ≈522k auto-generated | [project page](https://dstamoulis.github.io/geollm-engine/) | — | 📄 project page lists code and dataset as "coming soon" (2026-07) |
| 10 | **GeoLLM-QA** | [arXiv:2405.00709](https://arxiv.org/abs/2405.00709) | [ICLR 2024 workshop (ML4RS)](https://ml-for-rs.github.io/iclr2024/camera_ready/papers/65.pdf) | GIS platform / copilot control | 1,000 | — | — | 📄 no artifacts located (2026-07) |
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

## Maintainer

Curated by [Alexandros Oikonomidis](https://www.linkedin.com/in/aleoikon). Suggestions and corrections are welcome — get in touch or contribute on GitHub.
