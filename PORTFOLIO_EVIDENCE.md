# Portfolio positioning and evidence

Reviewed 2026-09-02. Scores are 1 (weak) to 5 (strong). `maintainability` scores a
smaller continuing burden higher. Stars and download counts are intentionally excluded.

## Front-door score

| Repository | Maturity | Reliability | Usefulness | Urgency | Time to value | Breadth | Unique boundary | Release readiness | Demo | Portfolio fit | Integration potential | Maintainability | Total / 60 |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| ResiliReplay | 5 | 5 | 5 | 5 | 5 | 4 | 4 | 5 | 5 | 5 | 5 | 2 | **55** |
| AgentTX | 4 | 4 | 5 | 5 | 4 | 5 | 3 | 5 | 5 | 5 | 4 | 3 | 52 |
| GaugeMesh | 4 | 5 | 4 | 4 | 4 | 4 | 4 | 4 | 5 | 5 | 4 | 2 | 49 |
| PhaseProbe | 4 | 5 | 3 | 3 | 4 | 2 | 4 | 5 | 5 | 3 | 3 | 4 | 45 |
| Verifaxis | 2 | 4 | 3 | 3 | 3 | 3 | 3 | 1 | 4 | 4 | 2 | 4 | 36 |

ResiliReplay is the current front door because a zero-credential published command produces an
executed regression, the released Action has an independent downstream verifier, and GaugeMesh
already invokes the pinned released CLI across a real MCP boundary. Its monorepo has the highest
maintenance burden; that is a reason to keep the flagship scope MCP-first, not to hide the score.

## Positioning records

| Repository | Target user and painful job | Common workaround | Specific result and evidence | Unique boundary / non-goal | High-intent discovery phrase | Primary path and integration |
| --- | --- | --- | --- | --- | --- | --- |
| ResiliReplay | MCP implementer who cannot prove recovery after a tool failure | happy-path tests, mocks, or protocol conformance alone | deterministic injected failure, bounded retry evidence, and generated executable regression | tests recovery behavior; it is not MCP conformance or a security certification | `deterministic MCP server fault injection` | `npx --yes resilireplay@0.7.0 mcp demo --keep`; released Action and GaugeMesh verifier |
| PhaseProbe | scientific developer protecting a qualitative simulation regime | manual parameter sweep plus handwritten numeric assertion | bracket, replay fixture, hashes, offline report, and generated pytest | user supplies a scientifically meaningful observable; it does not discover scientific truth | `convert simulation transition to pytest` | `pip install phaseprobe pytest`; logistic-map scan to generated regression |
| AgentTX | coding-agent user who needs a reversible review boundary | ad-hoc Git commits, stash, or editor-local checkpoint | isolated transaction, redacted diff/risk evidence, conflict-safe accept or rollback | repository transaction, not an OS sandbox or external-side-effect undo | `roll back AI coding agent changes` | `agenttx demo`; arbitrary command adapter |
| Verifaxis | researcher comparing bounded correction policies on an unchanged model | fixed retries, majority vote, or untyped self-critique | typed verifier evidence, budget accounting, stopping reason, and abstention | runtime/benchmark prototype, not a truth machine or established quality improvement | `adaptive stopping for frozen language models` | source install and deterministic replay-model demo; no registry release yet |
| GaugeMesh | MCP/model infrastructure engineer who must preserve policy and identity while routing | application-specific router or broad gateway | deterministic decision, rejected alternatives, invariant checks, and digest-bound evidence | invariant routing preview, not a general gateway or certification | `MCP server routing with constraints` | v0.1.0 release binary `gaugemesh demo`; optional `resilireplay@0.7.0` verification |

The ResiliReplay Action smoke repository is deliberately excluded from flagship scoring. It is an
independent downstream proof fixture, not a sixth product.

## Material claim/evidence matrix

| Public claim | Class | Evidence and scope |
| --- | --- | --- |
| ResiliReplay reproduces a deterministic MCP failure and executes a regression | A — directly tested | v0.7.0 local `mcp demo`, repository tests, and the released Action smoke; local fixture scope |
| PhaseProbe finds the packaged logistic transition and exports pytest | A — directly tested | v0.2.1 packaged example, replay/generator tests, and PyPI wheel/sdist validation; finite-time bracket, not an exact bifurcation |
| AgentTX restores repository state after rejecting an isolated agent change | A — directly tested | v0.1.0 offline demo and conflict/rollback tests; repository files only |
| Verifaxis implements verifier-conditioned recurrence and observable stopping | A — directly tested | deterministic replay model, verifier tests, and smoke benchmark |
| Verifaxis improves arbitrary frozen-model answers | E — hypothesis | no general claim is made; existing benchmark results are workload-specific research evidence |
| GaugeMesh preserves its declared invariants in the release demo | A — directly tested | v0.1.0 release binary and CI fixtures; declared invariant set only |
| GaugeMesh and ResiliReplay interoperate | A — directly tested | GaugeMesh `verify --resilireplay` exact-pins 0.7.0 and reports explicit partial outcomes |
| Any AEB project is production-ready or a security certification | F — unsupported | no such claim is made |

## Serious alternatives and boundaries

- [Official MCP conformance](https://github.com/modelcontextprotocol/conformance) tests protocol
  behavior; [mcprec](https://github.com/erphq/mcprec) preserves MCP conversations. ResiliReplay's
  narrower wedge is injected recovery plus duplicate-effect evidence and regression generation.
  These categories complement rather than replace each other.
- [SciPy `root_scalar`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.root_scalar.html)
  brackets scalar roots, while [Hypothesis](https://hypothesis.readthedocs.io/) searches input
  examples. PhaseProbe's contract is a declared qualitative predicate over a simulation plus a
  replayable pytest artifact.
- [VS Code checkpoints](https://code.visualstudio.com/docs/agents/run/review-code-edits),
  [Claude Code checkpoints](https://code.claude.com/docs/en/checkpointing), and Git already undo
  changes. AgentTX's boundary is a tool-independent, inspectable transaction around an arbitrary
  coding-agent command; it cannot undo external writes.
- [Self-Refine](https://arxiv.org/abs/2303.17651),
  [CRITIC](https://arxiv.org/abs/2305.11738), and
  [self-consistency](https://arxiv.org/abs/2203.11171) establish substantial prior art. Verifaxis
  therefore positions typed evidence, matched accounting, and stopping diagnostics as an
  experimental runtime/benchmark rather than a new correction principle.
- [vLLM Semantic Router](https://github.com/vllm-project/semantic-router),
  [RouteLLM](https://github.com/lm-sys/RouteLLM), and
  [Microsoft MCP Gateway](https://github.com/microsoft/mcp-gateway) cover intent, model economics,
  proxying, and broad operations. GaugeMesh stays narrow around deterministic selection and
  fail-closed conservation of declared constraints.

No competitor wording, adoption claim, benchmark number, or endorsement is used here.
