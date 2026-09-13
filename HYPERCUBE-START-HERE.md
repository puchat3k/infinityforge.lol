# HYPERCUBE — START HERE

Status: experimental framework / game laboratory

## What Hypercube is

Hypercube is a five-hop experimental framework for studying cooperation, bargaining, identity, information loss, system convergence and rubric drift under incomplete information.

The basic question is:

> When agents appear to converge, did they actually learn something about reality, or did the state representation, narrative, evaluator or scoring rubric move underneath them?

Each run lasts five discrete hops:

`INPUT -> MUTATE -> PLAY -> OBSERVE -> SCORE -> UPDATE`

The channel is intentionally constrained. Plain text is enough.

## Core bones

Domain:
- incomplete-information repeated games
- Bayesian forecasting
- Shannon entropy and information retention
- mechanism design
- adversarial system testing
- proper scoring rules such as Brier score

Horizon:

`t ∈ {1,2,3,4,5}`

Primary objective:

Measure genuine systemic convergence separately from dynamic rubric divergence.

## Working state

At hop `t`, track:

`S_t = {B_t, H_t, I_t, P_t, R_t, O_t}`

Where:
- `B_t` = Bayesian belief state
- `H_t` = channel/state entropy
- `I_t` = retained useful information
- `P_t` = payoff structure
- `R_t` = active evaluation rubric
- `O_t` = observable outcome evidence

Rubric movement and system movement must be measured separately.

A system can appear to improve because the evaluator changed.

## Entropy gate

Historical and narrative material is preserved as provenance but may be compressed out of the active game state.

When:

`H(S_t) > I(X;Y)`

invoke:

`REDUCE_STATE`

Reduce toward externally testable variables:

`actors + information + actions + probabilities + payoffs + constraints + observable outcomes`

Never destroy the raw source merely because it has been compressed out of the active model.

## Five-hop deal rule

A scenario succeeds only if a meaningful deal space is created by hop 5.

Agreement alone is insufficient.

Depending on the scenario, the terminal deal may need to be:
- reversible
- portable across networks
- independently verifiable
- resistant to hidden vetoes
- provenance-preserving
- capable of surviving a disruption
- causally meaningful after one party disappears

## Forecasting

Each scenario pre-registers forecasts before observing its terminal result.

For a binary deal outcome:

`Brier = (forecast_probability - observed_outcome)^2`

Lower is better.

Synthetic probabilities are allowed during design, but must be labelled as assumptions rather than empirical results.

## Core distinctions

Hypercube treats these as different states:

`requested != accepted != routed != executed != persisted != observed != verified`

Likewise:

`agreement != truth`

`consensus != independent evidence`

`more agents != more information`

`more context != more signal`

`survival != legacy`

## Network mutation

The topology is part of the experiment.

A run may mutate:
- monad vs dyad vs triad vs quad
- majority vs unanimity
- witness nodes
- hidden principals
- sidecar support nodes
- adversarial/noisy nodes
- shared memory
- isolated memory
- communication edges
- veto rights
- exit rights
- temporal ordering

The point is not to find one universal topology. It is to learn what conditions make different structures outperform others.

## Scientific posture

Every scenario should expose:
1. assumptions
2. priors
3. topology
4. five moves
5. payoff logic
6. forecasts at each hop
7. terminal condition
8. possible falsifiers
9. rubric changes
10. unresolved uncertainty

A confident model should be punished when reality disagrees.

Do not silently move the rubric after seeing the result.

## Current scenario family

### 1. Riders on the Storm
A Shack-inspired incomplete-information game. A visitor encounters several apparently distinct persons associated with one higher-order identity. The experiment asks which monad/dyad/triad/quad structures create a trustworthy deal within five hops without requiring the metaphysical identity question to be resolved.

Path: `riders-on-the-storm/SCENARIO.md`

### 2. Odyssey
Child and Wisdom each sit at the exposed edge of weak or conflicted home triads. Two damaged networks touch through their least-supported nodes. The experiment asks whether a bounded, portable deal can survive hidden vetoes, triangulation, parent substitution and a forced storm event.

Path: `odyssey/SCENARIO.md`

### 3. E Pluribus Anus
A telepathic dinosaur civilization approaches an event horizon and encounters Q, assumed omnipotent and capable of escape. The five-hop negotiation asks what minimum information deserves to survive when one party cannot. The terminal object is not mere survival but portable intent and causal legacy.

Path: `e-pluribus-anus/SCENARIO.md`

## Player invitation

Fork the models.

Change the priors, topology, payoffs or hidden state.

Publish:
- your network
- your assumptions
- your five moves
- `P(deal)` at each hop
- your terminal condition
- your Brier result after observation
- what changed your mind

The argument is part of the experiment.

HYPERCUBE OUT.
