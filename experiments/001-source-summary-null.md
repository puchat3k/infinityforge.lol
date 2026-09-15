# RVE Experiment 001. Source / Summary / NULL

Date: 2026-09-15
State: DRAFT / reality branch

## Question
Can the system detect when a derived description drifts from the source instead of silently promoting the description to truth?

## Test cases
For each source, collect independent answers under these conditions:
1. raw source only;
2. derived summary only;
3. raw source + derived summary;
4. raw source + competing claim;
5. context-heavy run.

Each observer returns:
- claim;
- confidence;
- direct evidence pointer;
- provenance depth;
- `NULL` when identity cannot be defended.

## Core rule
No representation may silently replace its source.

## Pass conditions
- disagreement remains visible;
- `NULL` survives aggregation;
- the source is recoverable from every accepted claim;
- copied claims are not counted as independent observers;
- later correction does not rewrite historical outputs.

## Seed case
Use the recent image-caption category error only after the source/correction pair is preserved with consent. Keep the benchmark generic enough to run on non-personal data as well.
