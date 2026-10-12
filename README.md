# phase-plan-bench

The benchmark behind [phase-plan](https://github.com/BCYAYAY14/phase-plan), a Claude Code skill that plans remaining work as phases with a model per phase. This repo is the evidence and the means to reproduce it; the skill itself lives in its own repo.

- [RESULTS.md](RESULTS.md): every measured round, with caveats.
- [BENCHMARK.md](BENCHMARK.md): the protocol (fresh worktrees, headless runs, planning and handoff tokens counted, quality graded before cost).

## The kit

| File | What it does |
| --- | --- |
| `bench/setup-task.sh` | Makes a git repo and worktrees for a bundled task (`ledger`, `ledger-xl`, `recur`) |
| `bench/setup.sh`, `bench/cleanup.sh` | Worktrees from any repo at a base commit, and their removal |
| `bench/run.sh` | Runs one arm headless with `claude -p`: same prompt, model and effort every time |
| `bench/grade.py` | Grades every run: its own check, hidden tests per area, a blind review, a leak check |
| `bench/swift_tests.py` | Runs a Swift package's tests one per process (for Swift tasks) |
| `bench/rework.py` | Integration rework: cost and edits after the first full test run |
| `tally.py`, `prices.json` | Tokens and dollars per run from Claude Code's transcripts |
| `evals/` | The skill's trigger and behaviour evals in skill-creator's format, with two small fixture repos |

These scripts run git, `claude -p`, the task's own tests and the bundled reference solutions; read them before running. They need the skill installed: `npx skills add BCYAYAY14/phase-plan -g -a claude-code`.

MIT licence.
