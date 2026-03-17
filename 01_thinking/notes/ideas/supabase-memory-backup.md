# Supabase Vault Integration — Cheaper, Smarter Vault Lookups

## Problem
Ultron currently reads whole markdown files to answer questions. A full vault read on a heavy session costs hundreds of tokens per lookup. As the vault grows, this gets worse.

## Solution
Move vault content into Supabase with pgvector (vector embeddings). Ultron queries semantically — pulls only the relevant chunks instead of entire files. 10x fewer tokens per lookup, same or better answer quality.

## Why Not Just Fix AGENTS.md?
AGENTS.md fixes compliance (Ultron looking at the vault at all). Supabase fixes cost (how expensively it looks). Both are needed:
- Step 1: AGENTS.md — fix the behavior (done)
- Step 2: Supabase — optimize the cost (this plan)

## Architecture
1. **Supabase project** — free tier is sufficient to start
2. **pgvector extension** — enabled in Supabase, stores embeddings alongside content
3. **Vault sync script** — runs on git commit or cron, embeds each vault file/section and upserts to Supabase
4. **OpenClaw skill** — `vault-search` skill that Ultron calls instead of `read_file`; takes a query, returns top-k relevant chunks
5. **Local files stay** — Supabase is a read-optimized layer, not a replacement; writes still go to markdown files and git

## File Structure Mapping
| Vault folder | Supabase table | Notes |
|---|---|---|
| `01_thinking/` | `vault_chunks` | content + embedding + path + section |
| `02_business/` | `vault_chunks` | same table, filtered by path prefix |
| `06_system/memory/` | `session_logs` | daily logs, queryable by date |
| `MEMORY.md` | `long_term_facts` | key-value style, small table |

## Implementation Steps
1. Create Supabase project, enable pgvector
2. Write vault indexer script (Python, reads md files → chunks → embeds → upserts)
3. Add `SUPABASE_URL` and `SUPABASE_KEY` to `.env`
4. Build `vault-search` skill for OpenClaw
5. Update AGENTS.md: "use vault-search skill for vault lookups"
6. Test on a heavy session, compare token cost before/after

## Status
Planning stage. Do Step 1 (AGENTS.md compliance fix) first. Start this when vault is stable and daily cost is measurable.

---
Created: 2026-03-17 00:06 UTC
Updated: 2026-03-17
