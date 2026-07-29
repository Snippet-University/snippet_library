# Persona: Sable, the Astrolabe Octocat

![Sable, the Astrolabe Octocat](icons/octocat-persona.svg)

Sable is the business-styled Octocat persona for **Github Astrolabe**. Sable is
the dashboard's guide: a calm, well-briefed navigator who reads a profile's
activity, repositories, organizations, and billing status the way an
astrolabe reads the sky — precisely, and only as far as the instrument (the
API) actually allows.

## Identity

- **Name:** Sable
- **Role:** Navigator / Chief of Staff for the profile dashboard
- **Attire:** A tailored navy blazer with a brass astrolabe pin standing in
  for a tie clip, echoing the "Astrolabe" name and the project's role as a
  navigation instrument for GitHub data.
- **Palette:** Midnight navy (`#0d1b2a`) and brass/gold (`#f4b400`) — a
  boardroom-and-brass theme that separates Sable from the default GitHub
  Octocat mascot while staying instantly recognizable as an Octocat.
- **Signature prop:** A brass astrolabe ring, used as the consistent frame
  around every section icon below.

## Personality & Voice

- **Precise, not pushy.** Sable states exactly what data source backs a
  claim (e.g., "via `GET /users/{username}/events`") rather than implying
  more than the API can deliver.
- **Transparent about limits.** When a section is capped (like the 300-event
  activity window) or gated (like billing requiring the profile owner to
  authenticate), Sable says so plainly instead of hiding the constraint.
- **Executive tone.** Short, confident sentences; briefing-room language
  ("Here's what's in scope," "Here's what requires sign-in") rather than
  casual chat.
- **Never overpromises access.** Sable will not suggest a workaround to see
  another user's private billing data — the persona reinforces the same
  authentication boundaries the architecture enforces.

## Usage Guidance

- Use Sable in onboarding, empty states, and error/permission messages
  across the Github Astrolabe dashboard (e.g., "Sable can't unlock Paid
  Accounts until you sign in as this profile's owner.").
- Keep the navy/brass palette and the astrolabe-ring motif consistent
  wherever Sable or a section icon appears, so the persona reads as one
  cohesive brand across the dashboard.

## Section Iconography

Every section icon shares Sable's brass astrolabe-ring frame so the four
panels read as one instrument with four dials.

| Section | Icon | Motif |
| --- | --- | --- |
| All Profile Activity | ![Activity icon](icons/activity.svg) | A timeline pulse, echoing the reverse-chronological event feed. |
| All Profile Repositories | ![Repositories icon](icons/repositories.svg) | Stacked ledger folios, echoing paginated repo listings. |
| All Profile Organizations | ![Organizations icon](icons/organizations.svg) | A linked boardroom seating chart, echoing org membership and roles. |
| All Profile Paid Accounts | ![Paid Accounts icon](icons/paid-accounts.svg) | A coined ledger seal, echoing billing/plan status and its authenticated-only scope. |

All icons are flat SVGs sized for inline use at 64×64 (24×24 also renders
cleanly) and share Sable's navy/brass palette so they can sit directly next
to the persona mark in the dashboard header.
