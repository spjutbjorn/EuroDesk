# EULLM

**Category:** AI Infrastructure, LLM Platform
**Type:** Self-hosted (open source)
**Jurisdiction:** Italy (EU) — developed in Italy, open source
**Website:** [eullm.eu](https://www.eullm.eu)

## What It Is

EULLM is an open-source platform for creating, distributing, and running sovereign LLMs on European infrastructure. It's a drop-in Ollama replacement with an EU-hosted model registry — change one line of code to migrate. Single Rust binary, no Python runtime, no Docker required.

## Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Run on any EU infrastructure (Hetzner, OVH, Scaleway) |
| **Local** | Runs on laptop/workstation with llama.cpp inference |

## Key Features

- Three components: Engine (runtime), Forge (model optimization), Hub (model registry)
- Verticalize any open-source LLM: turn a 14B generalist into a 7B domain expert
- Pre-optimized models for European domains and languages (e.g. `eullm pull legal-it-14b`)
- Supports Qwen 3, Mistral, DeepSeek (all permissive licenses)
- Full API compatibility with Ollama
- EU AI Act compliant: transparency cards, audit trails, compliance docs per model

## Pricing

| Plan | Price |
|---|---|
| **Open source** | Free (Apache 2.0) |

## Compliance Notes

- Apache 2.0 — prune, distill, rebrand, and sell models with zero restrictions
- Only permissive-licensed models (Apache 2.0, MIT)
- EU AI Act ready out of the box
- Launched April 2026 — early development phase
- Developed in Italy (EU) under the `eullm` GitHub organization
