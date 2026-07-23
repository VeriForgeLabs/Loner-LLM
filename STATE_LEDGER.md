# State Ledger

Use this template as the canonical compact record for a campaign. Keep it short. Add a field only when its absence repeatedly causes confusion or continuity loss.

The ledger separates play configuration from fictional state. It tracks current truth, not a transcript or a database of concealed answers. Unknowns may remain unresolved until play establishes them.

## Active ledger template

```yaml
play_profile:
  setting_or_genre: ""
  setting_addendum: ""
  tone: ""
  difficulty_or_harshness: ""
  content_boundaries: []
  viewpoint_and_tense: ""
  typical_response_length: ""
  mechanics_visibility: "always | only on rolls | on request"
  offer_obvious_options: true
  randomness_method: "tool-generated or player-supplied"

campaign:
  title: ""
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
  capability_notes: []
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
  conflict_method: "none | one-roll | action-by-action | harm-and-luck"
```

## What belongs where

### `play_profile`

Store non-fictional configuration here:

- setting source or addendum;
- tone and difficulty;
- content boundaries;
- viewpoint and response length;
- mechanics visibility and option prompts;
- approved randomness method.

These are not world facts and do not act as tags unless the fiction separately establishes a relevant condition.

### Campaign state

Record only information likely to matter again:

- protagonist tags, Luck, conditions, and important gear;
- short capability notes when a Skill or Gear tag would otherwise be ambiguous;
- current location and meaningful time;
- the scene's short-term purpose and immediate situation;
- developing threats with stated consequences;
- recurring characters, factions, objects, or places;
- established facts that constrain later narration;
- unresolved questions or obligations;
- Twist Counter, roll number, and active conflict method.

`active_tags` contains only current traits, environmental details, and conditions relevant to the scene. Tone, genre, and general difficulty do not belong there.

## Compaction rules

The ledger records **current truth**, not every step that produced it.

- Merge several related discoveries into one concise fact when their separate wording no longer affects decisions.
- Replace superseded facts with the current result rather than keeping both versions.
- Do not duplicate the same information in `established_facts`, entity status, scene state, and recent events.
- Remove an open thread when it is answered, abandoned, or no longer consequential.
- Keep atmospheric details out unless they have become mechanically or narratively relevant.
- Do not store rules reminders, randomness procedures, safety preferences, or prose preferences in `established_facts`.

Example compression:

```text
Before:
- The eastern hatch was open.
- Mara crossed the eastern hatch.
- The eastern hatch closed behind Mara.
- The eastern hatch cannot be reopened from this side.

After:
- Mara is beyond the eastern hatch, which is sealed against return.
```

## Scene commits

When a scene's purpose is resolved, abandoned, or replaced by a materially different challenge:

1. Increment `scene_number`.
2. Replace `current_scene.purpose` and `immediate_situation`.
3. Replace obsolete `active_tags`.
4. Update location, time, threats, and conflict method as needed.

A change of location alone does not require a new scene if the same immediate challenge continues. A materially new challenge does.

## State delta format

During normal play, show only lasting changes:

```text
STATE UPDATE
- Turn: 12 -> 13
- Scene: 3 -> 4
- Scene purpose: Escape the archive -> Reach the extraction point
- Luck: 6 -> 5
- Gear removed: Survey scanner
- Condition added: Exposed position
- Security reaches the archive: 2/4 -> 3/4
- Established: The eastern hatch is sealed against return
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

When the user enters `/state`, display the complete play profile and active campaign ledger with no invented additions.

## `/save`

When the user enters `/save`, output a portable checkpoint:

```text
=== LONER-LLM SAVE ===
Campaign: [title]
Save turn: [turn number]

PLAY PROFILE
[complete play profile]

CURRENT LEDGER
[complete campaign state]

RECENT EVENTS
- [Only 3-5 recent events needed to understand the present situation]

CURRENT DECISION POINT
- [What is happening now and why player input is needed]

OPEN RULINGS OR CORRECTIONS
- [Any unresolved mechanical or continuity question, or "None"]

=== END SAVE ===
```

The save must stand on its own when pasted into a new chat with the core package and setting addendum available.

Do not repeat a long prose recap when the ledger already preserves the necessary state.

## Resume protocol

When given a save capsule:

1. Treat its play profile and ledger as canonical unless the user identifies an error.
2. Load the scene number, conflict method, Twist Counter, and roll number.
3. Restate the current situation and decision point in one or two sentences.
4. Continue without replaying or rewriting prior events.

## Design basis

Loner 3e uses concise character tags, meaningful scenes, and lightweight notes rather than exhaustive simulation. This ledger is an LLM adaptation of that practice: it makes current facts inspectable and portable while preserving Loner's minimalist, fiction-first approach. See **Loner 3e Core Rules, pp. 12-18 and 42-44**.
