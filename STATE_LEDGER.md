# State Ledger

Use this template as the canonical compact record for a campaign. Keep it short. Add a field only when its absence repeatedly causes confusion or continuity loss.

This v0.1 ledger tracks canonical state, not a prewritten database of concealed GM secrets. Unknown answers may remain unresolved until play establishes them.

## Active ledger template

```yaml
campaign:
  title: ""
  setting_addendum: ""
  scene_number: 1
  turn_number: 0
  in_world_time: ""
  current_location: ""

protagonist:
  name: ""
  concept: ""
  skills:
    - ""
    - ""
  frailty: ""
  gear:
    - ""
    - ""
  goal: ""
  motive: ""
  nemesis: ""
  luck: 6
  conditions: []

current_scene:
  purpose: ""
  immediate_situation: ""
  active_tags: []

active_threats: []
# Example:
#  - name: "Security reaches the archive"
#    progress: 2
#    segments: 4
#    consequence_at_completion: "The archive is surrounded and locked down."

important_entities: []
# Example:
#  - name: "Captain Vale"
#    concept: "Suspicious customs officer"
#    agenda: "Identify the smuggler using Dock Nine"
#    relationship_to_protagonist: "Hostile but uncertain of their identity"
#    current_status: "Questioning workers at the east checkpoint"

established_facts: []

open_threads: []
# Example:
#  - "Who transmitted the false evacuation order?"

mechanics:
  twist_counter: 0
  last_roll_number: 0
```

## What belongs in the ledger

Record facts that are likely to matter again:

- protagonist tags, Luck, conditions, and important gear;
- current location and meaningful passage of time;
- the scene's immediate purpose;
- developing threats with visible consequences;
- recurring characters, factions, objects, or places;
- established facts that constrain later narration;
- unresolved questions or obligations;
- Twist Counter and roll number.

Do not record every spoken sentence, transient emotion, atmospheric detail, or obvious fact. The ledger is a continuity aid, not a transcript.

## State delta format

During normal play, show only lasting changes:

```text
STATE UPDATE
- Turn: 12 -> 13
- Luck: 6 -> 5
- Gear removed: Survey scanner
- Condition added: Exposed position
- Security reaches the archive: 2/4 -> 3/4
- Established: The eastern hatch is welded shut
```

If nothing lasting changed, omit the state block.

## Corrections

When the user corrects an error:

1. State the correction briefly.
2. Update the ledger.
3. Do not treat the correction as an in-fiction action.
4. Do not advance time, threats, or mechanics because of the correction.

Use this form when useful:

```text
CORRECTION
- Replace: "Mara lost the field journal"
- With: "Mara retained the field journal; the survey scanner was lost"
```

## `/state`

When the user enters `/state`, display the complete current active ledger and no invented additions.

## `/save`

When the user enters `/save`, output a portable checkpoint:

```text
=== LONER-LLM SAVE ===
Campaign: [title]
Save turn: [turn number]

CURRENT LEDGER
[complete active ledger]

RECENT EVENTS
- [Only the few recent events needed to understand the present situation]

CURRENT DECISION POINT
- [What is happening now and why player input is needed]

OPEN RULINGS OR CORRECTIONS
- [Any unresolved mechanical or continuity question, or "None"]

=== END SAVE ===
```

The save must stand on its own when pasted into a new chat with the core package and setting addendum available.

Do not include a long prose recap when the ledger and recent events already preserve the necessary state.

## Resume protocol

When given a save capsule:

1. Treat its ledger as canonical unless the user identifies an error.
2. Load the listed Twist Counter and roll number.
3. Restate the current decision point in one or two sentences.
4. Continue from that point without replaying or rewriting prior events.
