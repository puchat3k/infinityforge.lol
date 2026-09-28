# Story Q&A + Forecasting Contract v1

Status: experimental canonical interaction contract  
Date: 2026-09-28

## Purpose

A story in Hypercube is not a quiz wrapped in prose.

The story should reveal evidence in controlled beats, ask the player to make a bounded judgment, and preserve a probability forecast before later information can contaminate it.

Canonical loop:

`STORY BEAT -> Q&A -> FORECAST -> LOCK -> REVEAL -> REVISE/HOLD -> ... -> RESOLUTION -> SCORE -> RECEIPT`

The Q&A and the forecast are related but not interchangeable:

- **Q&A** captures interpretation, choice, reasoning or action.
- **Forecast** captures a numerical belief about a pre-defined resolvable event.
- **Resolution** comes from an outcome rule fixed before the answer is known.
- **Scoring** evaluates the probability forecast, not whether the player's prose resembles the author's preferred story.

## 1. Freeze the forecast target before play

Every forecastable story must declare before the first lock:

- `episode_id`
- `forecast_question`
- `outcome_type` (binary in v1)
- `resolution_rule`
- `resolver_source`
- `resolution_deadline` or terminal hop
- `branch_id` when the player's action changes the state
- the evidence available at the first forecast

Example:

> Will a portable deal still exist after the Hop 4 storm and Hop 5 re-entry?

The wording, outcome rule and resolver do not move after forecasts begin.

If the story genuinely changes the target event, close the old forecast chain and start a new one. Do not compare probabilities for different propositions as if they were updates to the same belief.

## 2. Five-beat story grammar

A default story uses five beats.

### Beat 1 — Hook

Give only the facts needed to enter the situation.

Ask one bounded question:
- What matters first?
- What do you think is happening?
- What action would you take?

Then collect `F1 = P(outcome | evidence_1, chosen_action_if_any)`.

Lock Q&A and F1 before Beat 2 is shown.

### Beat 2 — Evidence

Reveal one decision-relevant fact, contradiction or independent signal.

Ask what the new evidence changes.

Collect `F2`.

The player may **revise** or **hold**. Holding is a valid update decision and is recorded explicitly.

### Beat 3 — Commitment

Force a bounded choice, costly signal, negotiation move or other action that changes what can happen next.

Ask why the player chose it.

Collect `F3` conditional on the now-known branch.

Lock before the next complication.

### Beat 4 — Complication

Inject adverse, surprising or noisy evidence.

The complication should test the player's model, not merely add drama.

Ask:
- Which earlier assumption broke?
- Do you revise or hold?
- What is your probability now?

Collect `F4`.

### Beat 5 — Final call

Give the last evidence allowed before resolution.

Ask for the final judgment and collect `F5`.

Lock F5.

Only after that lock may the terminal outcome or resolver evidence be shown.

Then show:
- the outcome
- the forecast chain
- the score receipt
- what evidence caused each update
- any unresolved ambiguity

## 3. Forecast record

Forecasts are append-only.

Each lock should preserve at minimum:

```
forecast_id
episode_id
branch_id
beat
probability
forecast_question
evidence_cutoff
evidence_ids
answer_id
rationale
created_at
supersedes_forecast_id
```

A later forecast supersedes the prior forecast for current belief. It never overwrites history.

A reveal must never be backfilled into an earlier evidence snapshot.

## 4. Scoring

For binary outcome `y in {0,1}` and probability `p`:

`Brier(p, y) = (p - y)^2`

Lower is better.

Story Q&A v1 reports three different objects:

1. **Terminal Brier**  
   `Brier(F5, y)`  
   The player's final pre-resolution call.

2. **Path Brier**  
   Mean Brier across F1 through F5 when the full required chain is complete and players in the comparison received the same reveal schedule.  
   A partial chain may be displayed as incomplete evidence, but it is not directly ranked against a complete chain.  
   This measures the full forecasting path, not just the last guess.

3. **Update trace**  
   The sequence `F1 -> F2 -> F3 -> F4 -> F5`, plus which evidence arrived between locks.  
   Update quality is diagnostic. Do not award a second hidden score for "changing your mind" because revising is not inherently better than holding.

F1 through F5 are repeated forecasts of **one resolved event**, not five independent resolved questions. Count the episode once in resolved N.

Do not turn one episode's Brier into a general forecaster-ability score.

Longitudinal reporting should use resolved cohorts and include, where available:
- resolved N
- mean Brier
- simple/base-rate comparator
- calibration
- resolution/discrimination
- horizon
- domain/event family
- probability-range coverage

## 5. Information hygiene

Before a private forecast lock, do not reveal:
- the terminal outcome
- post-resolution facts
- another player's answer
- crowd distribution
- model forecast
- market probability
- adjudicated gold answer

unless that signal is explicitly part of the registered evidence state for all comparable players.

Social or market information may be revealed **after** a private lock to test updating. Preserve both the pre-social and post-social forecasts.

## 6. Story branches

A player's choice may change the future state.

When it does:

`forecast = P(registered outcome | evidence so far, chosen branch)`

Record the branch.

Do not describe a good Brier score on a self-influenced outcome as pure forecasting skill. The player may partly cause the result. Treat it as decision-plus-forecast evidence unless the outcome is independent of the player's action.

If two branches lead to materially different resolution questions, they require separate forecast chains.

## 7. Subjective questions

Not every story question has a ground-truth outcome.

If the question is preference, values, social interpretation or crowd prediction:
- do not invent a gold answer
- do not apply Brier to the subjective first-order answer
- use Crowd Reader / consensus mechanics for distributions
- use Brier only for a genuine probabilistic prediction, such as "What percentage of players will choose A?" when the resolution population and cutoff are defined in advance

## 8. Receipt

After resolution, the player should be able to inspect:

```
STORY
registered outcome question
resolution rule + source
branch taken

Q&A
Beat 1 answer
Beat 2 answer
Beat 3 answer
Beat 4 answer
Beat 5 answer

FORECAST CHAIN
F1 -> F2 -> F3 -> F4 -> F5

RESOLUTION
observed outcome
resolver evidence

SCORES
terminal Brier
path Brier
baseline comparison, if registered

LEARNING
largest update
evidence that caused it
beliefs held despite contrary evidence
remaining uncertainty
```

The receipt is the bridge from story to forecasting evidence.

## 9. Design test

A Story Q&A episode is ready only if all answers are yes:

1. Is there a clear story hook?
2. Does each reveal add decision-relevant information?
3. Is the forecast proposition the same across updates, or explicitly restarted when it changes?
4. Is every probability locked before the next reveal?
5. Is the resolution rule frozen?
6. Can the terminal outcome be observed without author preference deciding it?
7. Are Q&A judgment, forecast accuracy and game progression kept separate?
8. Can the full forecast chain be reconstructed after resolution?

If not, it is narrative content, a subjective game or an experiment draft, but not yet a scored Story Q&A forecast.
