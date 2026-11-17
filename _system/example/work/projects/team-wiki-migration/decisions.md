# Decisions

## 2026-01-21 - Build the redirect list before migrating more pages

**Status:** Decided

**Problem:** The trial migration of 20 pages broke every inbound link from chat and tickets.

**Options:**
- Migrate everything, then fix links as they are reported
- Build the old-to-new redirect list first, then migrate

**Decision:** Build the redirect list first.

**Reasoning:** The mapping is easy to produce while the old wiki is still up. Broken links are rarely reported, so fixing them afterwards would miss most of them.

**Follow-up:**
- [ ] Send the redirect list to the platform team

**Related:** [Redirects must ship with a migration](../../knowledge/redirects-must-ship-with-a-migration.md)
