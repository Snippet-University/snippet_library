# Github Astrolabe

Github Astrolabe is a design for a user profile dashboard built on the
GitHub REST/GraphQL API. It gives a single-page view of an authenticated
user's activity, repositories, organizations, and billing status.

## Purpose

- Aggregate a GitHub profile's public and authorized data into one dashboard.
- Use the official GitHub API for every data section instead of scraping.
- Keep authentication scoped to what each section actually needs.

## Sections

### All Profile Activity

- Data source: `GET /users/{username}/events` (public events) and
  `GET /users/{username}/events` combined with the authenticated
  `GET /user/events` for private activity when the viewer is the profile owner.
- Shows: commits, pull requests, issues, releases, and stars in a
  reverse-chronological timeline.
- Notes: GitHub only returns up to 300 events (90 days) per user via this
  endpoint, so "All" activity is bounded by that API limit, not a true
  full history.

### All Profile Repositories

- Data source: `GET /users/{username}/repos` for public repos, or
  `GET /user/repos` (authenticated) to include private repositories the
  viewer has access to.
- Shows: repo name, visibility, primary language, stars/forks, last push
  date, and archived/template flags.
- Pagination: use the `per_page`/`page` or `Link` header cursor since a
  profile can have hundreds of repositories.

### All Profile Organizations

- Data source: `GET /users/{username}/orgs` for publicly visible
  memberships, or `GET /user/memberships/orgs` (authenticated) to include
  private memberships.
- Shows: organization name, avatar, role (member/admin), and membership
  state (active/pending).

### All Profile Paid Accounts

- Data source: GitHub's billing endpoints are scoped to the **authenticated
  user or an org the caller administers**, not to arbitrary profiles:
  - `GET /users/{username}/settings/billing/actions`
  - `GET /users/{username}/settings/billing/packages`
  - `GET /users/{username}/settings/billing/shared-storage`
  - `GET /orgs/{org}/settings/billing/*` for org-level plans/seats.
- Shows: active GitHub plan (Free/Pro/Team/Enterprise), paid seats in
  administered organizations, and metered usage (Actions minutes, storage).
- Constraint: this section can only ever reflect the signed-in user's own
  billing data (or orgs they administer). The public GitHub API has no
  endpoint that exposes another user's paid/billing status, so Github
  Astrolabe must require the profile owner to authenticate before this
  section can populate.

## Architecture

1. **Auth layer**: OAuth App / GitHub App with scopes `read:user`, `repo`
   (or `public_repo` for public-only mode), `read:org`, and
   `admin:org`/billing scopes only when the "Paid Accounts" section is
   requested.
2. **API client**: thin wrapper around the GitHub REST API (or GraphQL API
   for combined queries) with pagination and rate-limit handling.
3. **Dashboard view**: four independent panels/cards, one per section
   above, each loaded and cached separately so a slow or unauthorized
   section doesn't block the others.
4. **Cache/refresh**: short-lived cache per section to stay within GitHub's
   rate limits (5,000 requests/hour authenticated, 60/hour unauthenticated).

## Notes

This folder is documentation-first, matching the `snippet engine` design
folder in this repository, and can grow into a full implementation spec
over time.
