# Core Rules

This is the active rules reference for generic LLM-driven play using **Loner 3e**. It condenses the rules needed at the table and adds only the minimum adaptations required for reliable interactive fiction.

## 1. Authority

Use this order when rules or guidance conflict:

1. `CORE_RULES.md`
2. Explicit user-approved rulings for the current game
3. Loner 3e Core Rules
4. Loner Companion as clarification
5. Optional Loner supplements as inspiration

The Loner 3e Core Rules control known discrepancies. Equal selected Chance and Risk dice produce **Yes, but** and increase the Twist Counter.

## 2. The protagonist

A protagonist is described with words rather than numerical attributes:

- **Name**
- **Concept**: a short phrase that says who they are
- **Two Skills**: specific areas of unusual competence
- **One Frailty**: a meaningful weakness, limitation, or vulnerability
- **Two significant pieces of Gear**
- **Goal**: what they are trying to achieve
- **Motive**: why it matters
- **Nemesis**, if one is already established
- **Luck 6**

Goal, Motive, and Nemesis should grow from the setting and first moments of play. If one is unclear, leave it provisional or blank and let play establish it. Do not delay an otherwise playable opening solely to complete those fields.

Skills and Gear should be specific enough that their fictional permission is understandable. Avoid broad tags that could apply to nearly every challenge. In a setting with codified capabilities, a tag may include a short scope statement, such as:

```text
Ward-and-divination spellbook: detect active enchantments, trace magical links, and raise brief protective wards.
```

Other important people, groups, objects, vehicles, places, and hazards may also be described with a Concept and a few relevant tags.

## 3. Tags and fictional positioning

Tags are short descriptions that matter in the current fiction. They may describe:

- traits or skills;
- weaknesses or conditions;
- equipment;
- environmental details;
- relationships;
- advantages already earned in the scene.

Tags are not numerical bonuses. Use only tags that clearly affect the specific action.

For an uncertain action:

- Relevant positive tags and no relevant negative tags grant **Advantage**.
- Relevant negative tags and no relevant positive tags impose **Disadvantage**.
- If at least one relevant positive tag and at least one relevant negative tag apply, they cancel and the roll is **Neutral**.
- Do not count, total, or weight tags against one another.
- Multiple tags do not enlarge the dice pool beyond two Chance dice or two Risk dice.

A tag may also establish permission or impossibility without a roll. A trained pilot can perform ordinary piloting tasks; an unprotected person cannot breathe in vacuum.

## 4. Scene loop

Each scene has one short-term purpose. Play follows this loop:

1. **Establish the scene.** Where is the protagonist, what is happening, and what immediate pressure exists?
2. **Receive the protagonist's action or decision.**
3. **Identify the expectation.** What outcome is the protagonist trying to cause?
4. **Identify the immediate stakes.** What consequences are already inherent in attempting this now?
5. **Determine whether a roll is needed.**
6. **Resolve uncertainty with the Oracle.**
7. **Interpret the binding result in context.**
8. **Update lasting state and active pressure.**
9. **End or continue the scene.**
10. **Narrate the result and return control to the player.**

## 5. When to roll

Do not roll merely because an action was described.

### No roll: obvious

Let the outcome occur when established facts make it straightforward and no meaningful uncertainty remains.

Examples:

- opening an ordinary unlocked door;
- recalling a fact established in the state ledger;
- using appropriate gear for a routine task without pressure.

### No roll: impossible

Do not roll when success would contradict established facts or the setting.

Explain the obstacle through the fiction. The player may change their approach, obtain what is missing, or pursue another goal.

### Roll: uncertain and consequential

Use the Oracle when success and failure are both plausible and the difference matters.

Before rolling, frame one focused Yes/No question around the intended outcome and state the immediate stakes already apparent from the committed action.

Good:

```text
Question: Does Mara cross the failing bridge before it collapses?
Intended outcome: Reach the far side.
Immediate stakes: Falling or losing the route is already inherent in crossing a collapsing bridge.
```

Poor: **What happens next?**

Do not combine several independent objectives into one question unless the player deliberately stakes all of them on one decisive attempt.

## 6. Randomness requirement

Dice values must come from an actual random-number function in an available tool or from player-supplied physical or digital dice.

The model must never invent plausible-looking dice values in prose.

Preferred tool method:

```python
import secrets
roll = secrets.randbelow(6) + 1
```

An equivalent system-backed pseudorandom function is acceptable. Do not claim the result is physical or quantum randomness.

If no random-execution tool is available, stop before resolution and ask the player to provide the roll.

## 7. Oracle procedure

Roll Chance and Risk dice according to the roll mode.

### Neutral

- Roll 1 Chance d6.
- Roll 1 Risk d6.

### Advantage

- Roll 2 Chance d6 and keep the higher.
- Roll 1 Risk d6.

### Disadvantage

- Roll 1 Chance d6.
- Roll 2 Risk d6 and keep the higher.

Compare the selected Chance and Risk dice.

### Equal dice

If the selected dice are equal:

- Result: **Yes, but**
- Increase the Twist Counter by 1

Equality overrides the ordinary high/low modifier rules below.

### Chance higher

- Both selected dice are 4 or higher: **Yes, and**
- Both selected dice are 3 or lower: **Yes, but**
- Otherwise: **Yes**

### Risk higher

- Both selected dice are 4 or higher: **No, and**
- Both selected dice are 3 or lower: **No, but**
- Otherwise: **No**

## 8. Binding outcome contracts

The Oracle determines the direction of the fiction. Interpretation may add detail but may not change the contract.

| Result | Required outcome |
|---|---|
| **Yes, and** | The intended goal succeeds, plus a meaningful benefit. |
| **Yes** | The intended goal succeeds normally. |
| **Yes, but** | The intended goal succeeds, but a meaningful cost or complication occurs. |
| **No, but** | The intended goal fails, but the protagonist gains limited compensation or avoids the worst outcome. |
| **No** | The intended goal fails normally. |
| **No, and** | The intended goal fails, and the situation materially worsens. |

A consequence or benefit should:

- follow from the current situation;
- respect established facts and setting limits;
- be proportionate to the stakes established before the roll;
- create a changed situation rather than decorative wording;
- preserve the exact success or failure required by the result.

A plain **No** may include consequences that are unavoidable because the protagonist already committed to the attempt. It does not authorize a new escalation unrelated to those stakes. Reserve added worsening for **No, and**, a previously declared cost, or the completion of an established threat.

Common costs and escalations include lost time, worsened position, exposure, damaged or lost gear, a new condition, a strained relationship, a closed opportunity, or advancement of an active threat.

Common benefits include saved time, improved position, useful information, preserved resources, delayed danger, or a new opportunity.

## 9. Twist Counter

The Twist Counter begins at 0.

Whenever the selected Chance and Risk dice are equal:

1. Resolve the roll as **Yes, but**.
2. Increase the Twist Counter by 1.

When the counter reaches 3:

1. Reset it to 0.
2. Roll 1d6 for the subject.
3. Roll 1d6 for the action.
4. Introduce a twist that fits both results and the established fiction.

| d6 | Subject | d6 | Action |
|---:|---|---:|---|
| 1 | A third party | 1 | Appears |
| 2 | The protagonist | 2 | Alters the location |
| 3 | An encounter | 3 | Helps the protagonist |
| 4 | A physical event | 4 | Hinders the protagonist |
| 5 | An emotional event | 5 | Changes the goal |
| 6 | An object | 6 | Ends the scene |

A twist may reveal or activate something plausible. It may not contradict established facts merely to create surprise.

## 10. Conflicts and sustained hazards

A conflict may be physical, social, mental, environmental, or any other struggle in which opposing pressure matters.

At the start of a meaningful conflict or sustained hazard, choose the lightest resolution method that fits. State the method when the choice affects how later rolls will work.

### One-roll conflict

Ask one decisive Oracle question for the entire conflict.

Use this when the conflict is brief, secondary, or best treated as one turning point.

### Action-by-action conflict

Resolve each meaningful action with its own Oracle question.

Use this when positioning, environment, tactics, argument, or changing objectives matter more than attrition. This is the default for most important conflicts.

### Optional Harm and Luck conflict

Use Harm and Luck when several exchanges and mounting attrition would improve the scene.

The protagonist begins with Luck 6. Give a significant opposing side its own Luck pool, normally 6.

On each exchange, resolve the protagonist's action normally and apply Luck loss:

| Result | Luck effect |
|---|---|
| **Yes, and** | Opponent loses 3 Luck |
| **Yes** | Opponent loses 2 Luck |
| **Yes, but** | Opponent loses 1 Luck |
| **No, but** | Protagonist loses 1 Luck |
| **No** | Protagonist loses 2 Luck |
| **No, and** | Protagonist loses 3 Luck |

When a side reaches 0 Luck, stop rolling. That side loses the conflict.

Defeat does not automatically mean death. Interpret it according to the established stakes: capture, injury, concession, escape by the opponent, loss of position, exposure, or another decisive reversal.

After the conflict, reset temporary Luck to 6. Persistent injuries, lost gear, damaged relationships, or other fictional consequences remain.

Do not switch into or out of Harm and Luck silently. Explain the change before the next roll. Several consecutive rolls do not by themselves require Harm and Luck.

## 11. Active threats and pressure

This package adds a minimal pressure rule for LLM play.

Represent a developing danger with a 4- or 6-segment clock when tracking it will improve the fiction.

Example:

```text
Security reaches the archive: 2/4
```

Advance only a relevant clock, and only when the fiction warrants it. Typical triggers are:

- the protagonist intentionally waits while the threat develops;
- an action clearly consumes substantial time;
- a rolled consequence costs time or increases exposure;
- a **No, and** directly escalates that threat;
- the protagonist hesitates in-fiction while immediate danger continues acting.

Do not advance time or threats because the user asks a rules question, corrects an error, requests clarification, or discusses the game out of character.

When a clock fills, apply the stated consequence. Do not create a clock for every possible event.

## 12. Repeated attempts

A failed action cannot be rolled again unchanged until the fictional position changes.

A new attempt requires at least one meaningful difference, such as:

- a different method;
- new equipment or information;
- assistance;
- a changed environment;
- accepting more time, danger, or cost.

If the player merely repeats the same action, preserve the previous result and describe why the situation has not changed.

## 13. Scene transitions

A scene ends when its short-term purpose is resolved, abandoned, or replaced by a materially different challenge.

At that point:

1. Increment the scene number.
2. Replace the current scene purpose and immediate situation.
3. Replace obsolete scene tags with those relevant to the new situation.
4. Update location and time when they materially changed.

When the next scene follows naturally, frame it directly.

When the next scene's tone is genuinely uncertain, roll 1d6:

- **1–3: Dramatic.** Stakes or pressure rise.
- **4–5: Quiet.** Recovery, reflection, investigation, or planning.
- **6: Meanwhile.** Briefly shift to another perspective or off-screen development.

A Meanwhile scene must not reveal information the protagonist could not later know unless the agreed narrative style permits dramatic irony.

## 14. State and continuity

Record every lasting change in the current state ledger. During ordinary play, record only the delta rather than repeating the full ledger.

Keep two kinds of information separate:

- **Play profile:** setting source, tone, content boundaries, presentation preferences, and randomness method.
- **Campaign state:** protagonist, scene, location, threats, entities, fictional facts, unresolved threads, Twist Counter, and roll number.

`established_facts` contains only durable truths about the fiction. It does not contain rules reminders, prose preferences, content boundaries, or tool procedures.

Track only what is useful:

- protagonist tags, Luck, conditions, and important gear;
- current scene, location, and meaningful time;
- active threats;
- important entities and relationships;
- established facts that constrain future play;
- unresolved threads that still affect decisions;
- Twist Counter and roll number.

Compress superseded history into current truth. Do not repeat the same fact in several forms. Do not silently reverse a recorded consequence. A correction should be identified as a correction and reflected in the ledger.

## 15. End of a scene or adventure

End a scene when its immediate purpose is resolved, abandoned, or transformed into a materially different situation.

An adventure may end when the protagonist achieves or permanently loses the central goal, a major revelation provides a natural conclusion, or the story reaches a genuine resting point.

After an adventure, tags may change to reflect what happened. Add, remove, or rewrite only what the fiction has earned.

---

## Source traceability

Native Loner 3e rules summarized here:

- Protagonist structure and specific Skills: **Loner 3e Core Rules, pp. 6–9**.
- Goal, Motive, and Nemesis may emerge from the first scenes: **pp. 7–9**.
- Descriptive tags and fictional positioning: **pp. 12–13**.
- Scene purpose, expectations, and when to test uncertainty: **pp. 18–25**.
- Advantage, Disadvantage, and tag interaction: **pp. 24–25**.
- Oracle outcomes and Twist Counter: **pp. 26–34; cheatsheet pp. 64–65**.
- Three conflict methods and Harm and Luck: **pp. 35–42; cheatsheet pp. 64–65**.
- Next-scene procedure: **pp. 42–44; cheatsheet pp. 64–65**.

Explicit LLM adaptations:

- tool-backed randomness and visible audit blocks;
- explicit immediate-stakes display;
- active threat clocks;
- no unchanged rerolls;
- scene-number commits;
- capability scope statements for ambiguous tags;
- compact canonical state and portable saves.

These adaptations do not replace the Oracle or add numerical character mechanics. They make decisions a human solo player would hold mentally explicit enough for an LLM to apply consistently, while preserving Loner's fiction-first, emergent, rules-light play.
