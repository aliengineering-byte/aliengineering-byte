# AEB

### Reliable engines. Inspectable workflows.

Route work, control changes, recover from failures, and inspect the result.

**[Choose an engine](#choose-an-engine)** · **[See a real proof workflow](https://aliengineering-byte.github.io/agenttx/)** · **[Engineering notes](PORTFOLIO_EVIDENCE.md)**

AEB builds independently usable tools for developers and researchers working with agents,
software, and computational workflows. Each engine has a specific responsibility and a
bounded contract. Use one on its own, or compose the public interfaces a task actually needs.

Domain-specific models and student-facing interfaces belong in separate applications — not
inside the execution, routing, transaction, or verification engines.

## Choose an engine

| You need to… | Engine | Its responsibility |
| --- | --- | --- |
| Route work under explicit constraints and recover bounded multi-step execution | **[GaugeMesh](https://github.com/aliengineering-byte/gaugemesh)** | Capability routing, durable Tasks/Runs, persisted state, and explicit reconciliation |
| Inspect, accept, or roll back supported coding-agent changes | **[AgentTX](https://github.com/aliengineering-byte/agenttx)** | Repository transactions, declared validation gates, and inspectable proof packs |
| Reproduce MCP failures and retain a regression | **[ResiliReplay](https://github.com/aliengineering-byte/resilireplay)** | Controlled fault injection, bounded recovery evidence, replay, and generated tests |
| Evaluate explicit claims before continuing a model workflow | **[VerifAxis](https://github.com/aliengineering-byte/verifaxis)** | Verifier-conditioned recurrence, stopping decisions, and evidence inspection |
| Preserve a qualitative transition in a user-provided simulation | **[PhaseProbe](https://github.com/aliengineering-byte/phaseprobe)** | Bounded transition discovery, replayable fixtures, and generated regression tests |

**Independent release proof:** [ResiliReplay Action Smoke](https://github.com/aliengineering-byte/resilireplay-action-smoke)
checks the released ResiliReplay Action from a separate consumer repository. It is evidence
infrastructure, not another required runtime or a competing application.

## Compose responsibilities, not a mandatory stack

```text
Application / agent / client
        |
        +-- Route and execute ........ GaugeMesh
        +-- Control repository edits . AgentTX
        +-- Test failure and recovery  ResiliReplay
        +-- Evaluate explicit claims . VerifAxis
        +-- Preserve transitions ..... PhaseProbe

Released artifacts ................. independent downstream checks
```

These are optional interfaces, not a fixed pipeline. Files, documented CLIs, and supported
protocols connect components; importing every engine or installing the entire portfolio is
not required. A specialized application owns its subject-matter rules and user experience.

## Start with something you can inspect

**Changing code with an agent?** Start with the
[AgentTX workflow and proof gallery](https://aliengineering-byte.github.io/agenttx/).
The gallery shows declared validators rejecting a test-weakening change and the resulting
transaction record. It is not a general detector of every unsafe edit.

**Building an MCP integration?** Use the
[ResiliReplay quickstart](https://github.com/aliengineering-byte/resilireplay)
to exercise the documented failure/recovery path and inspect its artifacts.

**Need restartable execution?** Read
[GaugeMesh's public interfaces and limits](https://github.com/aliengineering-byte/gaugemesh)
and choose a supported Task or Run path.

## A real proof workflow

```bash
agenttx proof --validator '["npm","test"]' -- codex exec "fix the failing test without weakening it"
```

[![Real AgentTX Proof Card: a weakened test was rejected and rolled back](https://aliengineering-byte.github.io/agenttx/agent-cheated/proof-card.svg)](https://aliengineering-byte.github.io/agenttx/agent-cheated/proof.html)

The [three-case proof gallery](https://aliengineering-byte.github.io/agenttx/)
shows a declared policy accepting a supported change and rejecting a weakened test.
Inspect the receipt and declared gates; this is bounded transaction evidence, not
proof that every possible bad edit or external side effect is detected.

[Portfolio engineering evidence](PORTFOLIO_EVIDENCE.md) is a historical record of
the observations made at the recorded dates, not a current cross-project version inventory.

## Applications

[Concrete Lab — open the browser calculator](https://aliengineering-byte.github.io/concrete-lab/)
is a separate educational prescribed-strain section-mechanics application.
Edit inputs, inspect equilibrium and signed layer results, and compare or export
a study. It provides no code compliance, design capacity, or safety approval.
The static browser app does not execute GaugeMesh or any other AEB engine.
See its [source and qualification limits](https://github.com/aliengineering-byte/concrete-lab).

The separate [3D FEM workbench](https://github.com/aliengineering-byte/concrete-lab/blob/main/WORKBENCH.md)
uses the reusable [AEB FEM engine](https://github.com/aliengineering-byte/aeb-fem):
tagged Gmsh solids, actual DOLFINx/PETSc elasticity, SLEPc modes, numerical checks,
and a Blender authoring/result round trip. Its container-backed local service
uses GaugeMesh's bounded public Run interface. Source and local execution are
available; public compute is not deployed. This is not nonlinear concrete or
design-code approval, and it does not change the six infrastructure projects.

## Public releases and documentation

| Project | Releases | Usage and boundaries |
| --- | --- | --- |
| GaugeMesh | [GitHub releases](https://github.com/aliengineering-byte/gaugemesh/releases) | [README](https://github.com/aliengineering-byte/gaugemesh#readme) |
| AgentTX | [GitHub releases](https://github.com/aliengineering-byte/agenttx/releases) | [README](https://github.com/aliengineering-byte/agenttx#readme) |
| ResiliReplay | [GitHub releases](https://github.com/aliengineering-byte/resilireplay/releases) | [README](https://github.com/aliengineering-byte/resilireplay#readme) |
| VerifAxis | [GitHub releases](https://github.com/aliengineering-byte/verifaxis/releases) | [README](https://github.com/aliengineering-byte/verifaxis#readme) |
| PhaseProbe | [GitHub releases](https://github.com/aliengineering-byte/phaseprobe/releases) | [README](https://github.com/aliengineering-byte/phaseprobe#readme) |

Use the chosen release's exact installation instructions, supported platform, and versioned
contract. Availability of an artifact does not imply production readiness or support for
an untested platform. Preview and research status remain visible in the project releases.

## What the evidence means

Execution, artifact integrity, policy acceptance, and independent numerical checks answer
different questions. A successful run is not automatically a correct model or a safe design.

AgentTX is not an operating-system sandbox and cannot undo arbitrary external side effects.
GaugeMesh's recovery and cancellation guarantees are bounded by its documented execution
surface. Hashes and unsigned receipts are not producer authentication. VerifAxis depends on
the scope and quality of its verifiers; PhaseProbe depends on the supplied observable and
predicate. Exercise effectful targets only with explicit authorization.

## Help improve an engine

Report a reproducible failure, unclear quickstart, or real compatibility result in the
relevant repository. Share only sanitized examples — never credentials, private prompts,
research data, or proprietary files.

Useful tools earn support through use. Feedback and repository stars are voluntary; they
are never required to install, run, or verify a result.
