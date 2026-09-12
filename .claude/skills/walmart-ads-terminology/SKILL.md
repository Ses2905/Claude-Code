---
name: walmart-ads-terminology
description: The canonical terminology, naming rules, and platform map for Walmart Global Ads advertiser-facing work. Use this skill whenever writing, reviewing, or editing anything an advertiser or an internal stakeholder will read — PRDs, specs, UI copy, error messages, help content, release notes, roadmap slides, exec decks, research findings, metric definitions — and whenever naming a feature, surface, metric, audience, or capability. Also use it when auditing existing material for terminology drift, when two documents disagree about what something is called, or when someone asks what we call X. Trigger even when the user does not mention terminology, naming, or glossary — if the output contains a Walmart Ads product, surface, or metric name, this skill applies.
---

# Walmart Ads Terminology

Language is part of the product. Advertisers experience our organization as
fragmented largely because our words are fragmented: the same object has three
names across three surfaces, and the same name means three things. Every
document that ships with a casually-chosen term makes that worse and is
expensive to unwind later, because names propagate into UI, docs, training,
support macros, and advertiser habits.

This skill exists to make the right term the cheap default.

## The one rule that matters most

**Never invent a Walmart-specific name.** If a product, surface, metric, or
audience name is not in `references/registry.md`, do not generate a
plausible-sounding one. A confident wrong name is far more damaging than an
open question, because it reads as authoritative and gets copied forward.

When a term is missing, write the placeholder and flag it:

> `[TERM NEEDED: the self-serve surface where marketplace sellers create
> campaigns]` — not in registry; confirm with Sasha before this ships.

Then list every such gap at the end of your output under **Open terminology
questions**. Missing terms are a normal, expected outcome — surfacing them is
the skill working, not failing.

This applies with equal force to metric definitions. "ROAS" is safe; "ROAS as
we calculate it, on a 14-day window, excluding in-store" is a claim about
Walmart's methodology, and you must not assert it from memory.

## How to use this skill

**Read `references/registry.md` first.** It is the canon. It is short by
design — every entry earns its place.

Then, depending on the task:

| Task | Also read | What you produce |
|---|---|---|
| Writing or editing prose, specs, UI copy | registry only | Correct terms applied silently, gaps flagged |
| Naming something new | `references/naming-rules.md` | 2–3 candidate names with rationale and rejections |
| Auditing existing material for drift | `references/audit.md` | A findings table, ranked by advertiser impact |

## Applying terms while writing

Use the canonical term on first mention and stay on it. Do not elegantly vary —
synonyms that read as good prose are terminology drift in a product context,
because a reader cannot tell whether two words mean two things.

Three checks before you hand back any advertiser-facing text:

1. **Same object, same name, every time.** Scan your own draft for two words
   pointing at one thing.
2. **Advertiser's vocabulary, not ours.** Internal system names, team names,
   and project codenames do not belong in advertiser-facing surfaces. A person
   manages a *campaign budget*, not a *budget entity*.
3. **Deprecated terms are gone, not softened.** If the registry marks a term
   deprecated, replace it. Do not write "Ad Center (formerly X)" unless the
   registry's `transition` field says the parenthetical is still needed — that
   field exists because a rename has a defined sunset, after which the crutch
   itself becomes clutter.

## When sources disagree

Conflicts are the normal case in a fragmented org, and resolving them silently
is the failure mode — it buries a real decision inside a document edit.

Surface the conflict, recommend a resolution, and say what it costs:

> **Conflict.** The campaign setup flow says "daily budget"; the API docs and
> the reporting export say "budget cap". These are the same field.
> **Recommendation.** "Daily budget" — it is what advertisers say out loud, and
> it is the term in the higher-traffic surface.
> **Cost.** API field rename, or a documented alias. Not free; needs a decision.

If the registry already resolves it, just apply the registry and note that you
did. If the registry is silent, the conflict is a finding — add it to
**Open terminology questions**.

## Precedence

When guidance collides, resolve in this order:

1. An explicit instruction in the current conversation
2. `references/registry.md`
3. `references/naming-rules.md`
4. Established usage in the document you are editing
5. General ad-industry convention

Industry convention is last for a reason: it is what produces plausible,
confident, wrong names. Reach for it only for genuinely generic terms
(impression, CTR, frequency cap) that no company owns.

## Maintaining the registry

The registry is only as good as its upkeep, and it decays silently.

Propose an addition when a term is used consistently across two or more
surfaces and has survived a real review. Do not add aspirational names for
things that do not exist — a registry full of unshipped vocabulary teaches
everyone to distrust it.

When adding an entry, fill every field in the template at the top of
`references/registry.md`, including `status` and `source`. An entry without a
source is a rumor, and a future reader has no way to check it.
