# TRAE — Unified IDE + SOLO Automation

## Overview
Trae is an AI-powered development IDE with dual modes (IDE + SOLO). As of November 2025, SOLO mode is broadly available to Pro users, enabling end-to-end automation from PRD to preview and release. Trae is highly effective for solo developers thanks to one-shot execution and streamlined workflows.

## Key Strengths
- Solo Mode widely accessible: One-shot, end-to-end execution (PRD → tasks → code → preview → release) for rapid prototyping.
- Streamlined workflow: Built-in agents (SOLO Coder, SOLO Builder), integrated tools, minimal coordination overhead.
- State-of-the-art models: Built-in `Gemini-3-Pro-Preview` and other premium models; BYOK custom models supported.
- Excellent value: Pro plan at $10/month (first month $3) with generous quotas and unlimited slow requests.

## Modes: When to Use SOLO vs IDE
- Use SOLO for end-to-end scaffolding, automated planning/task orchestration, and one-shot app builds.
- Use IDE for day-to-day coding, controlled refactors, and multi-step edits with manual review.

## Pricing & Quota (Current)
- Plans: Free and Pro (`USD $10`/month; first month `USD $3`; annual discount available).
- Quota (Pro): `600 fast requests` per month and `unlimited slow requests`; fast request queue ≤ 15 seconds.
- Extra packages: `$3 → +100 fast`, `$7 → +300 fast`, `$12 → +600 fast` (30-day validity).
- Models: Premium includes `Gemini-3-Pro-Preview`/`(200k)`, `Gemini-2.5-Pro`, GPT-4o/4.1, Grok-4, Kimi K2, DeepSeek V3.1; Advanced includes `Gemini-2.5-Flash`.
- Notes: SOLO workflows consume fast requests quickly; Max Mode converts token-based costs into fast request usage.

## Performance & Limitations
- Context limits are model-dependent (e.g., 200k on Gemini 3 preview variants).
- End-to-end SOLO pipelines naturally increase fast request consumption; plan extra packages for spikes.
- Best for small–medium projects and rapid iterations; very large monorepos still require careful context management.

## Real-World Examples
- One-shot web app: SOLO Builder generates PRD, tasks, code, preview, and supports release/deployment.
- Complex refactor: SOLO Coder with Plan mode coordinates multi-step changes; diff view aids verification.
- Budget IDE workflow: Use IDE mode with `Gemini-3-Pro-Preview` for reasoning-heavy edits; leverage slow requests for bulk operations.

## Comparative Advantages
- Over Kilo Code: Stronger end-to-end SOLO automation, built-in agents, generous quotas per price.
- Over Qwen CLI: Rich IDE integration and premium models; Qwen excels for zero-cost starts.
- Over Gemini CLI: Cohesive IDE + automation; Gemini CLI best for API/CLI experimentation.
- Over Octofriend: Integrated planning, preview/release pipelines; Octofriend strongest for MCP-first CLI workflows.
- Over Copilot: More automation and generous slow requests; Copilot has fixed monthly prompt caps.

## References
- SOLO availability: https://docs.trae.ai/ide/changelog?_lang=en
- Billing: https://docs.trae.ai/ide/billing
- Models: https://docs.trae.ai/ide/models
- Max Mode: https://www.trae.ai/changelog
- Gemini API context: https://ai.google.dev/gemini-api/docs/pricing

Back: [Development Tools](../README.md)
