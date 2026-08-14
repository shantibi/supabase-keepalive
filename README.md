# supabase-keepalive

Keeps free-tier Supabase projects from auto-pausing.

Free Supabase projects pause after **7 days** with no API requests. The GitHub
Actions workflow in `.github/workflows/keepalive.yml` pings each project's
`/auth/v1/health` endpoint **every 3 days**, which counts as activity and keeps
them awake. It runs on GitHub's free runners — no server needed.

## Projects pinged
- Dissertation Muse — `rgnvtvjfnnpchyzrkgtl`
- Mindful Selfish Teacher — `prynyomewwdpluafbccx`
- Property Grabber / Pull.land — `cgikjiuwgrnjluwvjiqe`
- EdBud — `lcxoxbutkjorfddralaa`

## Add another project
Edit the `PROJECTS` list in `.github/workflows/keepalive.yml` — add a line:
`"Name|project-ref|publishable-anon-key"`. Only **publishable/anon** keys go here
(they're public by design). Never put a `service_role` / secret key in this file.

## Notes
- A project that has *already* paused won't be revived by a ping — restore it once
  from the Supabase dashboard, and the workflow keeps it awake from then on.
- To run it on demand: Actions tab → "Supabase keep-alive" → "Run workflow".
