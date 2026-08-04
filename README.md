# The Last Bell at Briar House

A deliberately small format-2 story for testing basic Narrator gameplay.

## Action schema

Actions use one concrete story-object type per parameter. For polymorphic
examine and question actions, select the one optional character, entity,
setting, event, or deduction parameter that matches the intended target.
Moving always moves the acting player to the selected setting.

Facts are intentionally not an action parameter type. `command.claim` and
`command.deduce` therefore remain parameterless engine hooks until notebook and
deduction turns move into the gameplay engine. Fact and time topics on
`command.question` are not representable by the new action form either.

## Test shape

- Exactly five characters: one victim and four suspects
- Three navigable rooms with two simple routes
- Five examinable objects or records
- No hidden routes, inventory gates, or delayed work
- One false deduction based on one red herring: the red wool fiber
- A short three-branch path to the final solution

## Intended play path

Players can identify the weapon, establish Lena's opportunity, and discover her
motive in any order:

```text
EXAMINE character.adrian_bell
CLAIM fact.wound_matches_bell
EXAMINE entity.brass_service_bell
CLAIM fact.adrian_blood_on_bell
DEDUCE fact.wound_matches_bell fact.adrian_blood_on_bell

EXAMINE entity.study_door_log
CLAIM fact.code_14_entered_study_at_2012
CLAIM fact.study_closed_until_2017
QUESTION character.lena_ortiz entity.study_door_log
CLAIM fact.code_14_belongs_to_lena
DEDUCE fact.code_14_belongs_to_lena fact.code_14_entered_study_at_2012 fact.study_closed_until_2017

EXAMINE entity.cash_ledger
CLAIM fact.cash_deposits_missing
QUESTION character.lena_ortiz entity.cash_ledger
CLAIM fact.lena_managed_cash_deposits
DEDUCE fact.cash_deposits_missing fact.lena_managed_cash_deposits

DEDUCE deduction.bell_was_murder_weapon deduction.lena_had_opportunity deduction.lena_had_motive
SOLVE character.lena_ortiz deduction.lena_killed_adrian
```

The optional red-herring path points to Noah. Examining the hall telephone log
and Adrian's watch produces the deduction that disproves it.

> Workspace branch created at `2026-08-04T20:59:37.342Z`.
