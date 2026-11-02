# TradingView Indicator Builder 2

An independent Codex skill for building and checking Pine Script indicators from written rules, screenshots, and chart examples. Version 2 adds source-to-rule reconstruction, signal-timing checks, meaningful counterexamples, and separate verification of saved source, applied studies, and chart layouts.

## Install on a server with Codex CLI

Requirements: Codex CLI, Git, GitHub access, and a writable user skill directory.

    mkdir -p "$HOME/.agents/skills"
    git clone https://github.com/amadeo987/codex-tradingview-indicator-2-skill.git "$HOME/.agents/skills/tradingview-indicator-2"

Run these commands as the operating-system user running Codex. Git refuses to clone into an existing non-empty directory.

Invoke in Codex:

    $tradingview-indicator-2 Build this indicator from the attached reference. Verify its signal rule, a counterexample, and the applied chart result.

Conversation, indicator labels and working documentation follow the user's language.

Update:

    git -C "$HOME/.agents/skills/tradingview-indicator-2" pull --ff-only

Preserve local edits before updating. Restart Codex if the skill does not appear. The install location follows the [Codex skill documentation](https://learn.chatgpt.com/docs/build-skills).

## Local coding and live verification

The instruction files have no executable dependencies. Local Pine authoring works without a connected TradingView session.

Live compilation, chart installation, screenshots, and persistence checks require a running TradingView session and a compatible, authorized TradingView bridge or UI tool. This repository does not install or bundle those tools. A headless server without that connection cannot independently verify the live TradingView result.

The skill checks current official Pine documentation when needed. It does not place exchange orders, guarantee profits, or equate chart inspection with a backtest. Existing alerts remain intact unless their replacement is authorized.

## Files

- SKILL.md — authoring, verification and publication workflow.
- agents/openai.yaml — Codex display metadata and invocation.
- references/pine-standards.md — official documentation and Pine invariants.
- references/reference-to-rules.md — reference reconstruction and semantic checks.

An optional references/local-workspace.md may define your own canonical indicator root. It is ignored by Git and is not included in this repository. Without it, the skill uses a local tradingview-indicators directory in the task workspace.

## Compare with version 1

Use the same model, reasoning setting, prompt, reference, tools and initial files in separate tasks. Invoke only the selected version. Use a fixed historical chart range and separate test layouts.

Compare rule fidelity, signal time, counterexamples, visual alignment, compilation/runtime results, saved chart state, manual corrections and observed resource use. A longer response is not evidence of a better result.

Skill structure and local references have been validated. No model benchmark or live Pine compilation is claimed for publishing this instruction package.

## Cost, attribution and license

Codex usage and any required TradingView plan are separate from this repository. No paid API is bundled.

By [Amadeusz / amadeo987](https://github.com/amadeo987), with Codex-assisted development. Derived from the original TradingView Indicator Builder skill. MIT licensed; see LICENSE. Not affiliated with TradingView or OpenAI.
