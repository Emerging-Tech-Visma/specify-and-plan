# Specify & Plan

A [Claude Desktop (Cowork)](https://claude.ai) skill that guides you through the first two phases of spec-driven development — **Specify** and **Plan** — before you hand off to [Claude Code](https://docs.anthropic.com/en/docs/claude-code) for implementation.

## Why SPEC.md and PLAN.md?

AI coding agents are powerful, but they work best when they know exactly what to build. Without a clear brief, they guess — and guesses lead to rewrites.

**SPEC.md** captures *what* you're building and *why*. It answers the questions that matter before any code is written: Who uses this? What do they experience? What does "done" look like? Writing a spec forces you to think through user journeys, success criteria, and scope boundaries upfront. The result is a document that both you and the coding agent can refer back to whenever the project drifts.

**PLAN.md** captures *how* to build it. Tech stack, project structure, data model, deployment strategy, and — critically — the rules the coding agent should follow. It uses a three-tier boundary system (Always do / Ask first / Never do) that tells the agent when to proceed, when to pause for approval, and when to stop entirely. The plan also includes a CLAUDE.md starter, so Claude Code picks up the project's context from the first command.

Together, these two files turn a vague idea into a clear, implementation-ready brief. The spec keeps the agent aligned with what users actually need. The plan keeps the code structured and the deployment predictable.

## How it works

The skill runs in Cowork (Claude Desktop) and walks you through two phases conversationally:

**Phase 1 — Specify:** You describe your idea. The skill asks clarifying questions about users, journeys, and success criteria, then drafts a SPEC.md. You iterate until it captures what you want.

**Phase 2 — Plan:** You choose your stack and deployment target. The skill produces a PLAN.md with architecture, commands, agent boundaries, and a CLAUDE.md starter. It knows common stacks (Bun, React, Shadcn, PostgreSQL) and deployment targets (GCP Cloud Run, UpCloud via [et-upcloud](https://github.com/Emerging-Tech-Visma/et-upcloud)).

Then you hand off to Claude Code:

```
claude "Read SPEC.md and PLAN.md, then begin implementation starting with the deployment script"
```

## The workflow

```
Cowork (Specify & Plan)  →  Claude Code (Implement)  →  Deploy (UpCloud or GCP)
```

1. Open Cowork, describe your idea
2. The skill produces SPEC.md + PLAN.md in your project folder
3. Open Claude Code in that folder — it reads both files automatically
4. Start building, with the spec as your source of truth

## Install

Download [`specify-and-plan.skill`](./specify-and-plan.skill) and open it in Claude Desktop to install, or copy the `SKILL.md` file into your `.claude/skills/specify-and-plan/` directory.

## Based on

This skill draws on practices from the article [How to write a good spec for AI agents](https://www.anthropic.com/) and the GitHub Spec Kit's four-phase gated workflow. The key insight: planning in advance matters even more with an agent — iterate on the plan first, then let the agent write the code.

## Part of the Emerging Tech Visma toolkit

- [et-upcloud](https://github.com/Emerging-Tech-Visma/et-upcloud) — Claude Code plugin for UpCloud deployment
- **specify-and-plan** — This skill. Specify what to build, plan how to build it
