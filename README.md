<p align="center">
  <img src="https://em-content.zobj.net/source/apple/391/vulcan-salute_1f596.png" width="120" />
</p>

<h1 align="center">LCARS</h1>

<p align="center">
  <strong>why use many token when computer say less</strong>
</p>

---

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skill/plugin and Codex plugin that makes your agent respond like the USS Enterprise-D computer — cutting **~80% of output tokens** while keeping full technical accuracy. Plus progressive disclosure: short answer first, detail on demand.

Inspired by [caveman](https://github.com/JuliusBrussee/caveman). Same principle, different voice. Language patterns derived from actual TNG episode transcripts.

## Before / After

<table>
<tr>
<td width="50%">

### Normal Claude (69 tokens)

> "The reason your React component is re-rendering is likely because you're creating a new object reference on each render cycle. When you pass an inline object as a prop, React's shallow comparison sees it as a different object every time, which triggers a re-render. I'd recommend using useMemo to memoize the object."

</td>
<td width="50%">

### 🖖 LCARS Claude (15 tokens)

> "Inline object prop creates new ref each render. `useMemo`."
>
> Access diagnostic? y/n

</td>
</tr>
<tr>
<td>

### Normal Claude

> "Sure! I'd be happy to help you with that. The issue you're experiencing is most likely caused by your authentication middleware not properly validating the token expiry. Let me take a look and suggest a fix."

</td>
<td>

### 🖖 LCARS Claude

> "Token expiry check uses `<`, should be `<=`."
>
> Access diagnostic? y/n

</td>
</tr>
</table>

**Same fix. Fewer tokens. Progressive disclosure.**

User says `y` → one more level of detail. Otherwise, move on.

## Intensity Levels

<table>
<tr>
<td width="33%">

#### 🟢 Ensign

> "The component re-renders because a new object reference is created on each render cycle. Apply `useMemo` to memoize the object."

</td>
<td width="33%">

#### 🟡 Commander (default)

> "Inline object prop creates new ref each render. `useMemo`."

</td>
<td width="33%">

#### 🔴 Captain

> "Inline obj prop → new ref → re-render. `useMemo`."

</td>
</tr>
</table>

## Install

```bash
npx skills add chezluc/lcars
```

For a specific agent:

```bash
npx skills add chezluc/lcars -a cursor
npx skills add chezluc/lcars -a github-copilot
npx skills add chezluc/lcars -a cline
npx skills add chezluc/lcars -a windsurf
npx skills add chezluc/lcars -a codex
```

Or with Claude Code plugin system:

```bash
claude plugin marketplace add chezluc/lcars
claude plugin install lcars@lcars
```

Or manually:

```bash
cp -r skills/lcars ~/.claude/skills/lcars
```

## Usage

Trigger with:
- `/lcars` or `/lcars commander`
- "computer mode" or "lcars mode"

Stop with: "stop computer" or "normal mode"

| Level | Trigger |
|-------|---------|
| **Ensign** | `/lcars ensign` |
| **Commander** | `/lcars` or `/lcars commander` |
| **Captain** | `/lcars captain` |

## How It Works

Voice rules derived from 100+ actual TNG computer dialogue lines ([transcript corpus](transcripts/tng_computer_dialogue.md)):

| Rule | Example |
|------|---------|
| No filler, no pleasantries | Never "Sure!", "Happy to help" |
| Declarative only | "Token expiry incorrect." not "I think it might be..." |
| Single-word when sufficient | "Affirmative." "Negative." "Acknowledged." |
| Data-first | Numbers and facts before explanation |
| Progressive disclosure | Short answer → "Access diagnostic? y/n" → detail on demand |

## What Changes / What Doesn't

| Thing | LCARS? |
|-------|--------|
| English explanation | Compressed, declarative, data-first |
| Code blocks | Written normally |
| Technical terms | Preserved exactly |
| Error messages | Quoted exactly |
| Git commits & PRs | Written normally |
| Filler / pleasantries | Purged from memory banks |
| Security warnings | Full clarity (auto-expands) |

## Why

- **Faster** — fewer tokens = faster response
- **Readable** — no wall of text, just the answer
- **Accurate** — all technical info preserved
- **Cheaper** — ~80% fewer output tokens
- **Progressive** — detail on demand, not by default
- **Fun** — every code review sounds like a bridge briefing

## License

MIT — free like replicator credits on a starship.
