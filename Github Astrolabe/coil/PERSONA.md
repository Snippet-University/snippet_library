# Persona: Coil, the Decision-Simulator Octocat

![Coil, the Decision-Simulator Octocat](icons/coil-persona.svg)

Coil is the business-styled Octocat persona for the **Coil decision
simulator**, the "what if" companion to Github Astrolabe. Where Sable reads
a profile the way an astrolabe reads the sky, Coil takes those readings and
winds them forward — coiling and uncoiling possible futures for a decision
before the user acts on it in real life.

## Identity

- **Name:** Coil
- **Role:** Scenario strategist / forecasting partner to Sable
- **Attire:** A copper-toned waistcoat with a teal pocket watch chain shaped
  like a coiled spring, marking Coil as Astrolabe's forward-looking
  counterpart rather than a duplicate of Sable.
- **Palette:** Copper (`#b5651d`) and teal (`#0f6f6f`) — distinct from
  Sable's navy/brass so the two personas are never mistaken for one another,
  while staying in the same "instrument" family.
- **Signature prop:** A coiled brass spring held like a pocket watch,
  representing stored potential energy — a decision not yet made.

## Personality & Voice

- **Forward-looking, not speculative.** Coil always frames output as "if you
  do X, then Y changes" — never a guess detached from the user's own data.
- **Comparative by default.** Coil shows current-state vs. simulated-state
  side by side rather than the simulated number alone, so nothing is
  presented as if it already happened.
- **Reversible framing.** Coil reminds the user that a simulation is not an
  action: "Nothing changes on GitHub until you do it yourself."
- **Complements Sable's voice.** Same executive, briefing-room tone, but
  where Sable reports "what is," Coil reports "what could be" — e.g. "If you
  archive these 5 repos, your active repo count drops from 42 to 37."

## Usage Guidance

- Use Coil only in scenario/simulation surfaces layered on top of an
  existing Astrolabe section — never as a standalone data source.
- Every Coil projection must cite the Astrolabe section and API endpoint the
  underlying numbers came from (e.g. "based on `GET /users/{username}/repos`
  via All Profile Repositories").
- Keep the copper/teal palette and coiled-spring motif consistent so users
  can tell at a glance whether they're looking at Sable's live data or
  Coil's simulated data.

## Section Iconography

| Scenario | Icon | Motif |
| --- | --- | --- |
| Repository decisions | ![Repo scenario icon](icons/repo-scenario.svg) | A coiled spring wound around a repo folio, echoing a reversible "what if" on repo state. |
| Organization decisions | ![Org scenario icon](icons/org-scenario.svg) | A coiled spring looping a seating-chart node, echoing a hypothetical membership change. |
| Activity forecast | ![Forecast icon](icons/forecast.svg) | An uncoiling spring tracing an upward trend line, echoing projected future activity. |

All icons are flat SVGs sized for inline use at 64×64 (24×24 also renders
cleanly) and share Coil's copper/teal palette so they read as a distinct but
related instrument alongside Sable's navy/brass iconography.
