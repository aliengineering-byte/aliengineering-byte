# Evidence-first reliability tools for agents, MCP, and scientific software

AEB builds small, independently usable tools that make automated decisions and failures easier to
inspect, reverse, reproduce, and prove. Start with
[ResiliReplay](https://github.com/aliengineering-byte/resilireplay) when an MCP server works on the
happy path but its recovery behavior is unknown.

**Route. Transact. Verify. Replay. Probe. Prove.**

| Need | Start here | Status | Concrete output |
| --- | --- | --- | --- |
| Preserve constraints while selecting an agent, model, or MCP route | [GaugeMesh](https://github.com/aliengineering-byte/gaugemesh) | 0.1.0 developer preview | explained route decision and conservation evidence |
| Isolate, inspect, accept, or roll back coding-agent edits | [AgentTX](https://github.com/aliengineering-byte/agenttx) | 0.1.0 released alpha | transaction ledger, diff, risk report, and restoration proof |
| Retry a frozen model only while an explicit verifier justifies it | [Verifaxis](https://github.com/aliengineering-byte/verifaxis) | research prototype; not published | claim, verifier decisions, stopping reason, and evaluation artifact |
| Inject and replay deterministic MCP failures | [ResiliReplay](https://github.com/aliengineering-byte/resilireplay) | **0.7.0 released flagship** | recovery evidence and an executable regression |
| Find a reproducible qualitative simulation transition | [PhaseProbe](https://github.com/aliengineering-byte/phaseprobe) | 0.2.1 released alpha | bracketed transition evidence and generated pytest regression |
| Check a released Action from outside its source repository | [ResiliReplay Action Smoke](https://github.com/aliengineering-byte/resilireplay-action-smoke) | evidence infrastructure | downstream workflow result and validated artifacts |

The tools exchange versioned files or invoke released CLIs at process boundaries; none requires the
rest of the portfolio. The smoke repository is intentionally not a user-facing product.

[See the scored front-door decision, positioning records, and public claim/evidence matrix.](PORTFOLIO_EVIDENCE.md)

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
- GaugeMesh is a developer preview, and Verifaxis remains an unpublished research prototype.
- PhaseProbe requires the user to define a scientifically meaningful observable and predicate.
- ResiliReplay requires explicit ownership and approval before exercising remote or effectful tools.

Found a reproducibility failure, confusing quickstart, or missing integration? Open an issue in the
affected repository. Successful integrations can be reported through each project's adoption or
compatibility issue path. No AEB tool sends telemetry or stars a repository on a user's behalf.
