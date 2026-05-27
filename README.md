# Ten Rules for Writing a Planning Document

**English** | [한국어](README.ko.md)

A minimal, drop-in system prompt for any AI agent that helps a human draft service / software / business / strategy planning documents — Claude Code, Codex CLI, Gemini CLI, OpenCode, Cursor, and any tool that reads `AGENTS.md` or `CLAUDE.md`.

Two files. Ten rules. No fluff.

Landing page: **https://cskwork.github.io/planning-doc-rules/**

## Why

A planning document is not an idea brochure. It is a **decision document** that connects, in one traceable line:

> Why we should do it → What problem it solves → Who it is for → What to build → How to execute → How to verify.

Most planning templates fail because they list sections without binding them together. An approver cannot find the cost vs. value. A developer cannot find the exception cases. A QA engineer cannot find the acceptance criteria. The Ten Rules block all of those by forcing the same single thread through every section.

## Install

Drop the file your agent reads into your home directory or project root.

| Tool | File |
|------|------|
| Claude Code | `~/.claude/CLAUDE.md` or `<repo>/CLAUDE.md` |
| OpenAI Codex CLI | `~/.codex/AGENTS.md` |
| Google Gemini CLI | `~/.gemini/AGENTS.md` |
| OpenCode | `~/.config/opencode/AGENTS.md` |
| Cursor / Windsurf / others | `<repo>/AGENTS.md` |

### One-liner

```bash
curl -fsSL https://raw.githubusercontent.com/cskwork/planning-doc-rules/main/AGENTS.md -o ~/.codex/AGENTS.md
curl -fsSL https://raw.githubusercontent.com/cskwork/planning-doc-rules/main/CLAUDE.md -o ~/.claude/CLAUDE.md
```

### Single source of truth across CLIs

```bash
git clone https://github.com/cskwork/planning-doc-rules.git ~/planning-doc-rules

ln -sf ~/planning-doc-rules/CLAUDE.md   ~/.claude/CLAUDE.md
ln -sf ~/planning-doc-rules/AGENTS.md   ~/.codex/AGENTS.md
ln -sf ~/planning-doc-rules/AGENTS.md   ~/.gemini/AGENTS.md
ln -sf ~/planning-doc-rules/AGENTS.md   ~/.config/opencode/AGENTS.md
```

## The Ten Rules

1. **Anchor "Why" first.** Open with the reason this work exists, why it must happen now, what breaks if it does not, and which organizational / user / market need it answers. Never start with "what to build."
2. **Define the problem as an As-Is / To-Be gap.** Write current state, target state, gap, root cause, and the priority of what to solve first.
3. **Turn the reader's worries into the table of contents.** Order the sections by approver / developer / designer / operator / investor anxieties.
4. **Separate claim from evidence with research.** Pull from desk research, competitor analysis, user interviews, logs, reviews, VOC. Mark anything not yet supported as *assumption*.
5. **Derive requirements from user scenarios.** Persona, situation, goal, journey first; features fall out of behavior.
6. **Specify requirements without ambiguity.** ID, name, purpose, detail, users, inputs, processing conditions, outputs, exceptions, priority, acceptance criteria.
7. **Connect IA → Flow → Wireframe → Spec.** Every screen traces back to a requirement; every requirement lands on a screen.
8. **Define policy and exceptions first.** Access, state values, data retention, notifications, approval / rejection, error handling, operator-intervention cases — before the spec stabilizes.
9. **Prove feasibility with numbers and a plan.** Scope, out-of-scope, priority, schedule, headcount, resources, dependencies, risks, alternatives, phased plan.
10. **Close the loop through QA, launch, and operations.** Test scenarios, launch plan, runbook, CS response, KPI, post-launch improvement cycle.

The full content — output structure, self-diagnostic checklist, scoring rubric — lives in [CLAUDE.md](CLAUDE.md) / [AGENTS.md](AGENTS.md).

## Standard Table of Contents

A planning document produced under these rules typically uses this order. The order is itself a rule (see Rule 3): each section answers a specific worry the reader has at that point.

1. One-line conclusion
2. Executive summary
3. Background and problem
4. As-Is / To-Be
5. Goals and success metrics
6. User / market / competitor research
7. Key insights
8. Solution direction and alternatives
9. Scope and out-of-scope
10. User scenarios
11. Requirements (functional + non-functional)
12. IA / menu structure
13. Key flows
14. Wireframes (text tree if no image)
15. Policy / permission / exceptions
16. Schedule / resources / risks
17. QA and verification plan
18. Launch / operations / KPI plan

## Design Notes

- **Two files, identical content.** `AGENTS.md` is the cross-tool standard; `CLAUDE.md` is what Claude Code auto-loads. Keeping both means zero per-tool branching.
- **Imperative, not descriptive.** Every rule is a directive ("Anchor X. Do not start with Y."), not a value statement.
- **Why-anchored, not template-anchored.** The structure exists to serve the why; if a section adds no decision value, drop it for the current document.
- **Self-diagnostic enforced.** The agent is required to run the checklist and score the draft before claiming it is done. This is the single most common reason planning documents ship half-baked.
- **Behavior vs communication.** The Ten Rules govern *what to put in the document*; *Response & Documentation Style* governs *how the agent talks while writing it*.

## Customizing

Fork. Adjust the *Repository Rules* section first — those are team-flavored. Touch the Ten Rules only when you have a real failure mode the existing rules did not catch.

If you add a rule, it should:

- Be one sentence.
- Map to a real failure mode in shipped planning documents.
- Not duplicate an existing rule.

If your fork grows past ~20 rules, you have a wiki, not a system prompt.

## References

These rules are distilled from repeated patterns across:

- 박신영, 『기획의 정석』, 세종서적 — 3WR, 5Why, decomposition, "the planning document removes the reader's fear."
- 조이, 『서비스를 성공시키는 기획자의 비법 노트』, BJ퍼블릭 — full service-planning pipeline: research → problem → requirements → persona → user scenarios → IA → menu tree → flowchart → wireframe → prototyping → functional spec → screen ID → policy doc → QA → launch → operations → measurement.
- 이경희, 『서비스 기획 용어사전』, 연플 — common vocabulary that lets product, design, dev, QA, ops work from the same document.
- Rational 기술팀, 『똑똑한 소프트웨어 개발을 위한 실용 가이드』, 한국아이시스 — requirements management, requirement-development-test traceability, quality management.
- 정보통신산업진흥원(NIPA), Public SW project requirement-detailing guidance — institutional standard for RFP-grade requirement specification.

## Related

- [AGENTS.md spec](https://agents.md) — emerging cross-tool convention
- [coding-agent-rules](https://github.com/cskwork/coding-agent-rules) — Ten Commandments for Coding Agents
- [investment-agent-rules](https://github.com/cskwork/investment-agent-rules) — Ten Commandments for AI Investment Agents

## License

MIT. See [LICENSE](LICENSE).
