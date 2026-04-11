# Open Room: Notes for AI Coding Assistants

This file provides context for AI tools (Cursor, Copilot, etc.) helping builders contribute to Open Room. For Claude Code, see CLAUDE.md.

## What this project is

Open Room is a Next.js app where each "room" is a folder in `public/registry/` containing a background image and a `config.json`. The floor plan reads from Supabase to know which rooms exist and where they sit on the grid. Room content (images, hotspots) is served as static files by Vercel.

## Builder workflow

Builders do NOT need to set up a database. The Supabase row is created automatically when they reserve a room through the app. Their job is only to build the room files and open a PR.

1. Builder reserves a room on the live site → gets a room ID (e.g. `warm-harbor`)
2. Forks this repo
3. Copies `public/registry/_template/` to `public/registry/warm-harbor/`
4. Adds `background.jpeg` and edits `config.json`
5. Opens a Pull Request with a screenshot

## Key files

- `public/registry/_template/` — starting point for all new rooms
- `public/registry/_template/README.md` — full schema reference for builders
- `app/components/RoomView.tsx` — renders rooms from config.json
- `app/page.tsx` — the floor plan
- `supabase/migrations/20260411_current_schema.sql` — current DB schema

## config.json actions

- `navigate_floor` — returns to floor plan
- `open_url` — opens an external link in a new tab (requires `url` field)
- `open_image` — opens an image full-screen in a modal (requires `image_url` field)
- `open_modal` — opens a named modal (built-in: `welcome_guide`, `registry`, `diagram`)
