# Coil — the Github Astrolabe Decision Simulator

Coil is an original, business-themed decision simulator built as a companion
module to **Github Astrolabe**. Where Astrolabe's four panels (Activity,
Repositories, Organizations, Paid Accounts) show a profile's *current state*,
Coil takes that same data and plays it forward: it lets a user explore
"what if" scenarios against their own GitHub activity before they commit to a
real action.

## Purpose

- Turn passive dashboard data into an interactive decision-support tool.
- Model likely outcomes of common developer/maintainer decisions (e.g.
  "What happens to my review backlog if I archive these five repos?") using
  only data already surfaced by Astrolabe's sections.
- Keep every simulation traceable to a real GitHub API data source — Coil
  never fabricates numbers it can't attribute to an endpoint.

## Relationship to Github Astrolabe

Coil is not a replacement for Astrolabe; it is the "what if" layer that sits
on top of it:

| Astrolabe section | Feeds Coil scenario |
| --- | --- |
| All Profile Activity | Projects near-term workload from recent commit/PR/issue velocity. |
| All Profile Repositories | Simulates the effect of archiving, transferring, or making a repo private. |
| All Profile Organizations | Models the impact of joining, leaving, or changing role in an org. |
| All Profile Paid Accounts | Estimates seat/usage cost changes before a plan or seat change is made. |

## How it works

1. **Inputs**: Coil reads the same cached, per-section data Astrolabe already
   fetched (see `Github Astrolabe/README.md#architecture`) — it makes no
   additional GitHub API calls beyond what a section already requested.
2. **Scenario builder**: the user picks a lever (e.g. "archive repo X",
   "leave org Y") from a short list scoped to what the underlying data
   supports.
3. **Simulation**: Coil recalculates the affected section's summary metrics
   (event counts, repo counts, seats, etc.) under the hypothetical change,
   without mutating any real GitHub data.
4. **Comparison view**: current state vs. simulated state are shown side by
   side so the user can decide whether to actually perform the action
   through GitHub itself.

Coil never calls a mutating GitHub API endpoint. It is strictly a read/model
layer over data Astrolabe already has permission to display.

## UI/UX enhancement goals

- Give users a low-risk way to preview the consequences of an action before
  taking it, reducing accidental repo/org/billing changes.
- Surface trends (e.g. "activity has grown 20% over 90 days") as a forecast
  rather than a flat historical count.
- Keep the simulation transparent: every projected number is labeled with
  the section and API source it was derived from, matching Sable's
  "precise, not pushy" voice.

## Persona

See [`PERSONA.md`](PERSONA.md) for Coil's persona definition and
[`icons/`](icons) for its iconography, both original to this repository.

## Notes

This folder is documentation-first, matching the design-first approach used
by `Github Astrolabe/` and `snippet engine/` elsewhere in this repository,
and can grow into a full implementation spec over time.
