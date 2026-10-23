# Awesome-Mlops-Platforms

# Top MLOps Platforms Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Experiment Tracking, GenAI Tracing & Model Registry Governance*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **MLOps Platforms**. These tools manage the machine learning lifecycle — logging experiments, versioning datasets and models, tracing GenAI applications, and promoting artifacts from development to production — without stitching together a dozen disconnected scripts.

**Examples** include MLflow, Weights & Biases, Comet ML, ClearML, Neptune.ai, and the managed platforms (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, transparent model registries, and GenAI observability — ideal for teams wanting data sovereignty and zero per-seat licensing without sacrificing experiment tracking.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **Weights & Biases** — **The research team's default for training visualization.** **Free tier: unlimited experiments, 100GB storage, all core features for individuals.** **Team at $50/user/month** adds shared projects, access controls, and advanced reports; Enterprise adds SSO, on-prem deployment, and SLAs . **Standout features**: side-by-side run comparison with interactive parallel coordinates plots, **Weave** for LLM evaluation and prompt tracing, and collaborative reports that embed live charts . **Best for research-heavy teams** fine-tuning foundation models who need to spot hyperparameter patterns visually in seconds .

- **Comet ML** — **The compliance-focused enterprise option.** **Community tier free** (unlimited experiments, 50GB storage, public projects only); **Team pricing tiers** with expanded storage and collaboration; Enterprise adds SOC 2 Type II, on-premise deployment, and audit logs . **Covers the full lifecycle** from experiment tracking and model registry through production monitoring . **Best for regulated industries** (finance, healthcare, government) where compliance features justify the premium over W&B .

- **Neptune.ai** — **The metadata-heavy workflow tracker.** **No free tier** — paid plans start around **$150/month** for teams tracking foundation model training experiments at moderate scale . **Clean UI** praised by users who prefer focused metadata tracking over full-platform sprawl . **Best for teams wanting a polished tracker** without the broader platform ambitions of W&B or Comet.

## Open-Source GitHub Projects

- **MLflow** — **The open-source standard for the ML lifecycle.** Apache 2.0 licensed, created by Databricks in 2018 and now one of the most widely adopted experiment tracking frameworks . **Four core components**: Tracking (log parameters, metrics, artifacts with three lines of code), Projects (package reproducible runs), Models (deploy to diverse serving environments), and **Model Registry** (version, stage, and deploy through centralized staging → production → archived workflows) . **MLflow 3** (June 2025) fundamentally expanded the platform for GenAI: **LoggedModel** as a first-class entity grouping traces, prompts, and evaluation metrics by model version rather than by run; **hierarchical tracing** that captures LLM calls, vector retrieval, document ranking, and token usage with full execution timelines; and a **Prompt Registry** with optimization capabilities . **Breaking changes in MLflow 3**: Recipes removed, fastai and mleap flavors dropped, and model logging now uses `name` instead of `artifact_path` without requiring `start_run()` . **The hard limit**: you run the tracking server, backend database (Postgres recommended over SQLite for query performance), and artifact store yourself — no vendor to call when Postgres falls over . **Best for teams with DevOps capacity** wanting zero per-seat fees and a central model registry, especially those already on Databricks where Managed MLflow is included .

- **ClearML** — **The tracking-plus-orchestration platform for GPU clusters.** Apache-2.0 licensed, bundling experiment tracking with task orchestration, agent-based scheduling, and **automatic logging of code state, dependency hashes, and random seeds** — the most convenient out-of-the-box reproducibility coverage among open-source platforms . **Includes ClearML Serving** with canary/A/B deployment and traffic splitting, though automatic rollback is not clearly documented in the OSS edition . **The hard limit**: the extra orchestration surface area means more moving parts to configure and operate (Postgres, Elasticsearch, MongoDB) than MLflow's single tracking service . **Best for teams managing multi-GPU distributed training** wanting tracking, pipeline scheduling, and agent management from one open-source tool .

- **Aim** — **The zero-cost, self-hosted-only tracker.** Apache 2.0 licensed, no hosted SaaS offering at all — you install it and run it yourself . **Modern, fast UI** for comparing runs without per-seat fees . **The hard limit**: no vendor support line, no managed hosting, and no built-in model registry or pipeline orchestration — it's a tracker, not a platform . **Best for solo developers and small teams** with somewhere to run a lightweight service, who want a fast UI and will never pay for tracking .

- **Kubeflow** — **The Kubernetes-native ML platform.** Open-source, with **Kubeflow Pipelines** for orchestration and **KServe** for model serving. **KFP** provides APIs, SDKs, and REST API for CI/CD integration; KServe enables canary deployment and rollback through traffic splitting, though Kubeflow's official docs don't document these as built-in first-class features . **The hard limit**: **high entry barrier** — requires Kubernetes expertise, with a master node needing 4 vCPU and 16 GB RAM . **Best for organizations already standardized on Kubernetes** wanting end-to-end ML pipelines with serving.

### Additional Strong Open-Source Options

- **DagsHub** — Open-source platform built on Git and DVC for data versioning and experiment tracking. **Best for teams wanting first-class dataset versioning** alongside model tracking .
- **Determined AI** — Open-source deep learning training platform with distributed training and hyperparameter tuning. **Best for teams wanting an open-source alternative** to managed training platforms .

**Frameworks for building custom systems**: Combine **MLflow** for experiment tracking, model registry, and GenAI tracing with the broadest ecosystem support, **ClearML** for GPU orchestration and automatic reproducibility when you need pipeline scheduling, **Aim** for zero-cost lightweight tracking on a self-hosted service, and **Weights & Biases** or **Comet ML** if you want managed UX and can accept per-seat pricing — to build an MLOps stack tailored to your team's DevOps capacity, compliance requirements, and tolerance for operational overhead.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- MLOps platforms differ significantly in scope, operational burden, and pricing model. **MLflow is free to self-host but you own the Postgres instance, backup schedule, and security patching** — query performance degrades on the default SQLite backend well before it does on a tuned Postgres one . **Weights & Biases has the fastest setup and richest training visualization** but costs $50/user/month at team scale . **Comet ML is the compliance choice** with SOC 2 Type II and on-prem options . **ClearML bundles orchestration with tracking** but has more moving parts to operate than a pure tracker . **Aim is a tracker, not a platform** — no registry, no orchestration . **Neptune.ai has no free tier** . **MLflow 3 contains breaking changes** — test in a separate environment before upgrading production workflows .
- Self-hosted open-source solutions require proper database configuration (Postgres recommended for MLflow at scale), backup strategies for artifact stores, and someone on the team who owns the server — "free" self-hosted still has a headcount cost.

---

**Made for ML engineers and platform teams managing the model lifecycle without vendor lock-in.**
Let's make MLOps platforms more open, self-hostable, and GenAI-aware.
