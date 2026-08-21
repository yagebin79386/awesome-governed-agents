# Awesome Governed Agents [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of tools, frameworks, and prior art for **governed agents** — autonomous systems
> whose consequential actions pass through approval gates, policy checks, and auditable decision
> records instead of firing unattended.

An agent that can act is easy. An agent you can let run unattended is a governance problem: which
actions are reversible, who approves the ones that are not, what evidence survives afterwards, and
what happens when nobody answers. This list collects what exists for building that layer.

**Scope.** Tools that constrain, gate, record, or roll back agent behaviour. Not general agent
frameworks, unless they ship a governance primitive worth using on its own.

## Contents

- [Human-in-the-loop and approval gates](#human-in-the-loop-and-approval-gates)
- [Policy engines and guardrails](#policy-engines-and-guardrails)
- [Durable execution and rollback](#durable-execution-and-rollback)
- [Observability, evaluation, and audit](#observability-evaluation-and-audit)
- [Gateways and routing control](#gateways-and-routing-control)
- [Supervision and liveness](#supervision-and-liveness)
- [Governed operating stacks](#governed-operating-stacks)
- [Design notes](#design-notes)

## Human-in-the-loop and approval gates

- [HumanLayer](https://github.com/humanlayer/humanlayer) — Approval and human-contact primitives for
  agents, so a tool call can require a person before it executes.
- [Invariant](https://github.com/invariantlabs-ai/invariant) — Guardrails for secure and robust agent
  development, including contract-style checks on agent traces.
- [fail-closed-gate](https://github.com/yagebin79386/fail-closed-gate) — File-backed approval gates
  with an append-only decision ledger and fail-closed expiry: an unanswered request blocks, and the
  expired record deliberately names no decider.

## Policy engines and guardrails

- [Open Policy Agent](https://github.com/open-policy-agent/opa) — General-purpose policy engine; the
  standard way to express "which actions are allowed" outside application code.
- [Guardrails](https://github.com/guardrails-ai/guardrails) — Validation and correction framework for
  adding guardrails to large language model output.
- [NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) — Toolkit for adding programmable
  guardrails to LLM-based conversational systems.

## Durable execution and rollback

- [Temporal](https://github.com/temporalio/temporal) — Durable execution service; gives long-running
  agent workflows retries, timeouts, and compensating actions as first-class concepts.
- [LangGraph](https://github.com/langchain-ai/langgraph) — Graph-structured agent runtime with
  checkpointing and interrupt points, usable as a place to insert a human gate.

## Observability, evaluation, and audit

- [Langfuse](https://github.com/langfuse/langfuse) — Open-source LLM engineering platform: tracing,
  evaluation, metrics, and prompt management.
- [Phoenix](https://github.com/Arize-ai/phoenix) — AI observability and evaluation, with trace-level
  inspection of agent runs.

## Gateways and routing control

- [Portkey Gateway](https://github.com/Portkey-AI/gateway) — AI gateway with integrated guardrails and
  routing across many model providers.
- [LiteLLM](https://github.com/BerriAI/litellm) — Unified API across LLM providers; a practical choke
  point for budget limits and per-key policy.

## Supervision and liveness

Governance fails quietly when the machinery meant to enforce it stops running.

- [schedule-sentinel](https://github.com/yagebin79386/schedule-sentinel) — Registry plus verifier for
  scheduled machines: proves each entry still exists, ran inside its tolerance, and has not drifted
  out of the scheduler in either direction. Stdlib only.

## Governed operating stacks

Whole systems built around the governance question rather than around the model.

- [governai](https://github.com/rrrozhd/governai) — Governed, deterministic AI backend workflow
  framework for typed tools, policies, approvals, and bounded agents.
- [grounder](https://github.com/territory-grounder/grounder) — Self-hosted, governed-autonomy SRE
  platform: an LLM agent that remediates infrastructure incidents behind a fail-closed prediction
  gate, mechanical verdicts, and a tamper-evident ledger.
- [solo-founder-os](https://github.com/alex-jb/solo-founder-os) — Self-evolving agent stack for
  one-person companies, with a PR-gated evolver so self-modification stays reviewable.
- [SoloDev](https://github.com/EolaFam1828/SoloDev) — AI-native DevOps platform aimed at solo builders
  and very small product teams.

## Design notes

Patterns that recur across the tools above, collected here because the vocabulary is not yet settled.

- **Fail-closed approval.** An approval that expires must count as *not approved*. A timeout that
  reads as consent turns an unanswered message into an unattended action.
- **Decision records over log lines.** A typed record of who decided what, when, and on which
  artifact survives; a chat message does not.
- **Tier the surfaces.** Not every file an agent can edit should be editable by an agent. Freezing a
  small governance tier and letting agents propose diffs against it keeps self-modification bounded.
- **Reversibility as the sorting key.** The useful axis is not "risky vs safe" but "reversible vs
  not". Reversible actions can run unattended; irreversible ones are what gates are for.

## Contributing

Contributions welcome — please read the [contribution guidelines](CONTRIBUTING.md) first. Entries
must be governance-relevant, actively maintained or clearly labelled as prior art, and described in
the project's own terms rather than in marketing language.

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)
