# Security Status

**Prototype only. Do not use this static demo for real shared accounts or sensitive personal data.**

LocalStorage can be edited by the user and is not a secure database. Scores are local and can be manipulated. There is no authentication, cloud database, authorization layer, server-side score validation, or rate limiting in this prototype.

## Not implemented yet
- No student account/login system or server-side login history.
- No real shared leaderboard or cloud-sync progress.
- No secure student admin dashboard.
- No daily contest feature in the website UI.
- No full 100-question/90-minute mock exam.

## Production plan:
- Supabase Auth (or comparable managed auth)
- PostgreSQL tables for profiles, attempts and leaderboard totals
- RLS policies so users can edit only their own profile and attempts
- Server/Edge Function validates allowed test IDs, answer submissions and score calculations
- Public leaderboard exposes only username/avatar/aggregate score
- No Supabase service-role secret in client code
- Input validation, anti-abuse rate limiting, backup and retention/cleanup policy
