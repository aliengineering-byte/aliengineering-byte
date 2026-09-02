# Evidence-first reliability tools for agents, MCP, and scientific software

AEB builds small, independently usable tools that make automated decisions and failures easier to
inspect, reverse, reproduce, and prove. Start with
[ResiliReplay](https://github.com/aliengineering-byte/resilireplay) when an MCP server works on the
happy path but its recovery behavior is unknown.

**Route. Transact. Verify. Replay. Probe. Prove.**

| Need | Start here | Status | Concrete output |
| --- | --- | --- | --- |
| Preserve constraints while selecting an agent, model, or MCP route | [GaugeMesh](https://github.com/aliengineering-byte/gaugemesh) | 0.2.0 GitHub developer preview; crates.io unavailable | selected or denied decision and digest-bound conservation evidence |
| Isolate, inspect, accept, or roll back coding-agent edits | [AgentTX](https://github.com/aliengineering-byte/agenttx) | 0.2.0 GitHub alpha; npm remains 0.1.0 | transaction ledger, diff, risk report, and rollback receipt |
| Retry a frozen model only while an explicit verifier justifies it | [Verifaxis](https://github.com/aliengineering-byte/verifaxis) | 0.2.0 GitHub research prerelease; PyPI unavailable | claim, verifier decisions, stopping reason, and offline-verifiable evidence |
| Inject and replay deterministic MCP failures | [ResiliReplay](https://github.com/aliengineering-byte/resilireplay) | **0.7.0 released flagship** | recovery evidence and an executable regression |
| Find a reproducible qualitative simulation transition | [PhaseProbe](https://github.com/aliengineering-byte/phaseprobe) | 0.3.0 released on PyPI | bracketed transition evidence, standalone verification, and generated pytest regression |
| Check a released Action from outside its source repository | [ResiliReplay Action Smoke](https://github.com/aliengineering-byte/resilireplay-action-smoke) | evidence infrastructure | downstream workflow result and validated artifacts |

The tools exchange versioned files or invoke released CLIs at process boundaries; none requires the
rest of the portfolio. The smoke repository is intentionally not a user-facing product.

[See the scored front-door decision, positioning records, and public claim/evidence matrix.](PORTFOLIO_EVIDENCE.md)

## Public install paths

Every command below resolves an immutable public version. Registry publication is stated explicitly;
GitHub release assets are used where registry ownership is not configured.

```console
# ResiliReplay 0.7.0 from npm
npx --yes resilireplay@0.7.0 mcp demo --keep

# PhaseProbe 0.3.0 from PyPI
python -m pip install "phaseprobe==0.3.0" "pytest==8.4.1"
phaseprobe scan --example logistic
phaseprobe generate-test .phaseprobe/runs/<run-id>/replay.json
phaseprobe verify-evidence tests/generated/logistic_map-pytest-evidence.json
python -m pytest -q tests/generated

# Verifaxis 0.2.0 from its public GitHub release wheel (not PyPI)
python -m pip install "https://github.com/aliengineering-byte/verifaxis/releases/download/v0.2.0/verifaxis-0.2.0-py3-none-any.whl"
verifaxis demo --evidence-output demo-evidence.json
verifaxis verify-evidence demo-evidence.json

# AgentTX 0.2.0 from its public GitHub release tarball (npm latest is 0.1.0)
pnpm dlx "https://github.com/aliengineering-byte/agenttx/releases/download/v0.2.0/agenttx-0.2.0.tgz" demo

# GaugeMesh 0.2.0 Linux release archive (not crates.io)
curl --fail --location --remote-name https://github.com/aliengineering-byte/gaugemesh/releases/download/v0.2.0/gaugemesh-v0.2.0-x86_64-unknown-linux-gnu.zip
unzip gaugemesh-v0.2.0-x86_64-unknown-linux-gnu.zip -d gaugemesh-v0.2.0
./gaugemesh-v0.2.0/gaugemesh route explain --decision-contract > selected.json
./gaugemesh-v0.2.0/gaugemesh route validate selected.json
```

Checksums and release notes: [GaugeMesh 0.2.0](https://github.com/aliengineering-byte/gaugemesh/releases/tag/v0.2.0),
[AgentTX 0.2.0](https://github.com/aliengineering-byte/agenttx/releases/tag/v0.2.0),
[Verifaxis 0.2.0](https://github.com/aliengineering-byte/verifaxis/releases/tag/v0.2.0), and
[PhaseProbe 0.3.0](https://github.com/aliengineering-byte/phaseprobe/releases/tag/v0.3.0).

## Five-minute flagship proof

With Node.js 22 or 24:

```console
npx --yes resilireplay@0.7.0 mcp demo --keep
```

The credential-free local demo runs a clean MCP call, reproduces one deterministic failure, verifies
bounded recovery with no duplicate effect, generates and executes a regression, and keeps the
evidence under `.resilireplay/demo/`. See the
[five-minute MCP guide](https://github.com/aliengineering-byte/resilireplay/blob/main/docs/mcp-reliability/FIVE_MINUTE_MCP_TEST.md)
and the
[independent Action smoke](https://github.com/aliengineering-byte/resilireplay-action-smoke/actions/workflows/resilireplay.yml).

## Two honest tracks

- **Agent reliability:** GaugeMesh routes while preserving declared constraints; AgentTX contains
  repository edits; Verifaxis evaluates explicit claims; ResiliReplay tests MCP recovery. Use only
  the stages the task actually needs.
- **Scientific reliability:** PhaseProbe brackets a qualitative transition and exports a pytest
  regression. Verifaxis or ResiliReplay belongs here only when a real verifier or failure-replay
  boundary is present.

## Current boundaries

- These tools provide evidence for their documented scopes; they are not security certifications.
- AgentTX does not sandbox a child process or reverse external side effects.
- GaugeMesh is a GitHub/GHCR developer preview and is not on crates.io. Verifaxis remains a
  research prototype distributed as a GitHub prerelease wheel, not through PyPI.
- AgentTX 0.2.0 is available from GitHub; the npm registry still serves 0.1.0 as latest.
- PhaseProbe requires the user to define a scientifically meaningful observable and predicate.
- ResiliReplay requires explicit ownership and approval before exercising remote or effectful tools.

Found a reproducibility failure, confusing quickstart, or missing integration? Open an issue in the
affected repository. Successful integrations can be reported through each project's adoption or
compatibility issue path. No AEB tool sends telemetry or stars a repository on a user's behalf.
