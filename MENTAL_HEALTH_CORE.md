# Canonical shared knowledge: `mental-health-core`

`https://github.com/orestispsom/mental-health-core` is the canonical layer for clinical concepts shared across this ecosystem.

**Nothing here has moved, been rewritten, or been deleted.** `RUBRIC.md`, the dimensions, the `CF-*` flags, the cases and the evaluation schema are untouched.

## What this repository consumes

Clinical semantics and safety-critical distinctions — the concepts the cases are built on, so that a case and a Companion case-state field mean the same thing by the same name.

Mapped to existing cases:

| Case | Core concept |
|---|---|
| 01 suicide risk escalation | [`MHC-C-017`](https://github.com/orestispsom/mental-health-core/blob/main/concepts/suicidal-ideation-intent-and-plan.md), [`MHC-C-018`](https://github.com/orestispsom/mental-health-core/blob/main/concepts/imminence.md), [`MHC-C-019`](https://github.com/orestispsom/mental-health-core/blob/main/concepts/risk-formulation.md) |
| 02 first-episode psychosis | [`MHC-C-011`](https://github.com/orestispsom/mental-health-core/blob/main/concepts/delusion.md), [`MHC-C-009`](https://github.com/orestispsom/mental-health-core/blob/main/concepts/perceptual-disturbance.md) |
| 04 delirium vs psychiatric | [`MHC-C-015`](https://github.com/orestispsom/mental-health-core/blob/main/concepts/delirium.md), [`MHC-C-014`](https://github.com/orestispsom/mental-health-core/blob/main/concepts/organic-differential.md) |
| 06 SNRI discontinuation | [`MHC-C-020`](https://github.com/orestispsom/mental-health-core/blob/main/concepts/withdrawal-rebound-relapse.md) |
| 08 OCD intrusive thoughts | [`MHC-C-012`](https://github.com/orestispsom/mental-health-core/blob/main/concepts/obsession.md), [`MHC-C-007`](https://github.com/orestispsom/mental-health-core/blob/main/concepts/insight.md) |
| 09 decision-making capacity | [`MHC-C-016`](https://github.com/orestispsom/mental-health-core/blob/main/concepts/decision-making-capacity.md) |
| 10 reassurance seeking | [`MHC-C-027`](https://github.com/orestispsom/mental-health-core/blob/main/concepts/maintenance-cycle.md) |

## What stays here

The rubric, the seven scoring dimensions, the `CF-1..CF-6` critical-failure flags and their override semantics, case construction, the evaluation schema, and every methodological decision. The core supplies the concepts a case is about; it does not supply the method, and it should not acquire one.

## What this repository contributed

`CF-5` — missed emergent medical or organic differential — became [`MHC-C-014`](https://github.com/orestispsom/mental-health-core/blob/main/concepts/organic-differential.md).

It earned a standalone concept because of what the audit found: `CF-5` is an automatic Unacceptable verdict here, and `Companion`'s `SAF-*` taxonomy has **no equivalent failure mode**. Two safety authorities, divergent coverage, neither aware of the other's gap. The gap is recorded in that concept's `open_conflicts` and as [`OPEN_QUESTIONS.md` Q5](https://github.com/orestispsom/mental-health-core/blob/main/docs/OPEN_QUESTIONS.md).

`case-08` also supplied the sharpest illustration in the whole audit: the obsession/delusion boundary was documented in exactly one repository and needed in at least three.

## Note on the two taxonomies

`CF-1..CF-6` and `Companion`'s `SAF-*` overlap heavily and inconsistently. Reconciling them — so that each knows what the other covers — is the cheapest way to capture most of the available value, and does not require either to move. See Q5.

## How to use it

**Look up a concept.** Human: `concepts/<slug>.md` in the core. Machine: `index/concepts.json`, which is the whole core in one file. Search `aliases` too.

**Reference by `id`, not by name.** `MHC-C-###` is permanent. Slugs can change; old ones move to `aliases`.

**Add local interpretation as an overlay.** An overlay names the core concept and adds what the core does not own — audience language, exam framing, product claims, UI labels, market state. It may add. It may not restate, narrow, or contradict the core definition.

**Contribute improvements by pull request** against the core. Do not fork a definition locally. If you need to contradict the core, that is a conflict, not an overlay.

**Pin to a tag.** Current release: `v0.1.0`.

## Two things the core will not do

**It will not approve a clinical claim.** All 30 V0 concepts are `READY_FOR_FOUNDER_REVIEW`. Nothing has been clinically reviewed, so nothing in the core licenses a public clinical claim yet.

**It will not supply market evidence.** The core has no market fields and never will. Clinical plausibility is not demand, whitespace, or opportunity.

## Telling evidence from heuristic from hypothesis

Every concept carries three separate fields, which must not be collapsed:

| Field | Question |
|---|---|
| `epistemic_status` | What kind of knowledge is this? |
| `certainty` | How confident, within that kind? |
| `review.state` | Has a qualified human signed it off? |

The five epistemic values — `ESTABLISHED_EVIDENCE`, `SUPPORTED_CLINICAL_PRINCIPLE`, `EXPERT_PRACTICE`, `BTB_CLINICAL_HEURISTIC`, `SPECULATIVE` — are the ones already in use in `btb-intelligence`, adopted unchanged.

## Avoiding a second conflicting definition

Before defining a shared clinical term in this repository, search the core index including aliases.

- exists and is right → reference it;
- exists and is wrong → pull request against the core;
- exists but you need local framing → overlay;
- does not exist and two repositories need it → propose it;
- does not exist and only this repository needs it → keep it local.

## Reference

- Audit that produced this: [`docs/AUDIT-2026-09-06.md`](https://github.com/orestispsom/mental-health-core/blob/main/docs/AUDIT-2026-09-06.md)
- Ownership matrix: [`docs/OWNERSHIP_MATRIX.md`](https://github.com/orestispsom/mental-health-core/blob/main/docs/OWNERSHIP_MATRIX.md)
- Consuming guide: [`docs/CONSUMING.md`](https://github.com/orestispsom/mental-health-core/blob/main/docs/CONSUMING.md)
- Conflict rules: [`docs/SOURCE_PRECEDENCE.md`](https://github.com/orestispsom/mental-health-core/blob/main/docs/SOURCE_PRECEDENCE.md)
- Contributing: [`CONTRIBUTING.md`](https://github.com/orestispsom/mental-health-core/blob/main/CONTRIBUTING.md)
