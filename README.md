# Loner-LLM

A generic, rules-light adaptation of **Loner 3e** for LLM-driven interactive fiction.

## Goal

Create the smallest practical core package that constrains an LLM with:

- Loner 3e scene and Oracle procedures;
- tool-generated, auditable dice rolls;
- binding `Yes/No, and/but` outcome contracts;
- minimal state tracking;
- forward-pressure rules;
- player-agency and continuity guardrails.

The LLM remains the interpreter, adjudicator, world actor, and narrator. This is not a standalone game engine, deterministic simulation, or attempt to eliminate contextual judgment.

## Governing principle

> Add only enough structure to produce a meaningful improvement in adjudication, continuity, pressure, and player agency.

Do not add infrastructure until observed play failures justify it.

## Files

- [`CORE_RULES.md`](CORE_RULES.md): condensed Loner rules and the minimal adaptation layer
- [`PROJECT_INSTRUCTIONS.md`](PROJECT_INSTRUCTIONS.md): persistent behavior instructions for the LLM
- [`STATE_LEDGER.md`](STATE_LEDGER.md): compact state, correction, save, and resume formats
- [`START_GAME_TEMPLATE.md`](START_GAME_TEMPLATE.md): generic campaign initialization prompt

The package is setting-agnostic. Warhammer 40,000, cyberpunk, fantasy, horror, and other setting guidance should be supplied as separate addenda.

## Install in a ChatGPT Project

1. Create a new ChatGPT Project for the campaign or reusable game-master setup.
2. Paste the contents of `PROJECT_INSTRUCTIONS.md` into the Project's instruction field.
3. Upload or add these files to the Project:
   - `CORE_RULES.md`
   - `STATE_LEDGER.md`
   - `START_GAME_TEMPLATE.md`
   - the Loner 3e PDF as a source reference
   - any setting-specific addendum
4. Start a new chat in that Project.
5. Fill and submit `START_GAME_TEMPLATE.md`, or use its minimal version.
6. Confirm that the chat has access to an actual code or random-number tool. If it does not, provide dice rolls manually when asked.

The short Markdown rules are the active play reference. The full Loner PDF is supporting authority and clarification, not material the model should summarize anew on every turn.

## Use with Claude or another LLM

Use `PROJECT_INSTRUCTIONS.md` as the project or system instruction layer and attach the other Markdown files as project knowledge.

The model must have either:

- access to a tool that executes a real random-number function; or
- a player willing to provide dice results.

The model must not fabricate dice values when no random tool is available.

## Normal play format

When no roll or lasting state change occurs, the response can remain pure narrative.

When a roll occurs, the model displays a compact audit block:

```text
ROLL 014
Question: Does Mara bypass the lock before the patrol returns?
Mode: Advantage
Positive tags: Expert Locksmith
Negative tags: None
Random source: tool-executed Python `secrets`
Chance: [2, 5] -> 5
Risk: [4] -> 4
Result: Yes, and
Twist Counter: 1/3 (unchanged)
```

When lasting state changes, it displays only the delta:

```text
STATE UPDATE
- Luck: 6 -> 5
- Condition added: Sprained wrist
- Security clock: 2/4 -> 3/4
```

Use `/state` for the complete active ledger and `/save` for a portable checkpoint.

## Setting addenda

A setting addendum should define only what the generic package cannot:

- world facts and canon;
- available technologies, powers, or supernatural rules;
- genre conventions;
- tone and prose guidance;
- setting-specific character options;
- important prohibitions or limits.

It should not duplicate the generic Oracle, tags, player-agency rules, randomness protocol, or state format unless it deliberately overrides them.

Suggested filename:

```text
SETTING_[NAME].md
```

## Current status

**Milestone 1: Minimum Playable Core**

The first milestone provides a rough package suitable for immediate pilot play. Refinement should follow observed failures rather than hypothetical completeness.

## Attribution and license

Loner was created by Roberto Bisceglie and is licensed under the [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

This adaptation is distributed under the same license. The added LLM-specific rules are identified as adaptations rather than original Loner procedures.
