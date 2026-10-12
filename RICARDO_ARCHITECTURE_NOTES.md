# Structured research for data enrichment

Portfolio lab curated for Ricardo Chacón — Data & AI Architecture / Agentic AI Consulting.

## Attribution and contribution scope

This is a public fork of [langchain-ai/data-enrichment](https://github.com/langchain-ai/data-enrichment), under its original MIT license. The upstream authors built the application. This fork adds an architecture assessment and a reproducible installation record; it does not claim upstream implementation as Ricardo's original work. Notes were prepared with AI assistance and remain open to revision.

## Business application

Convert public supplier research into a structured, reviewable input for a data platform. This is a proposed application, not a completed client delivery.

## Data and control flow

Business topic + extraction schema → research agent → web search / scrape tools → structured extraction → reflection → bounded retry / result

## Architecture decision

Define the output contract before allowing research. Require evidence URLs, preserve unknown values, and validate both structure and source support before writing to any business system.

## Verification record — 2026-10-11

Python 3.11 isolated environment installed. Upstream configuration unit test: 1 passed. Graph import and compilation succeeded; nodes: call_agent_model, tools, reflect.

These checks establish installation/build behavior only; they do not establish model accuracy, production readiness or business impact.

## Runtime requirements and limitations

Live enrichment was not run. Configure a supported model provider and Tavily credentials locally. API use can incur charges.

Never commit real credentials or private client documents. Use the upstream README for runtime setup and retain its license and attribution.

## Next adaptation

Add a supplier extraction schema and an evaluation set covering missing information, conflicting sources and unsupported claims.

## Reproduce the installation checks

```sh
python3.11 -m venv .venv
.venv/bin/python -m pip install -e . pytest pytest-asyncio
.venv/bin/python -m pytest tests/unit_tests -q
.venv/bin/python -c 'from enrichment_agent.graph import graph; print(sorted(graph.get_graph().nodes))'
```
