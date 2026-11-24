---
name: qarera-job-search
description: Find real job openings matched to the user's resume using their
  connected Qarera account. Use whenever the user asks to find, search for, or
  recommend jobs, mentions Qarera, or asks what roles they should apply to.
---

# Qarera job search

The user's Qarera account is connected. Qarera's tools search live listings
ranked against the user's own resume, and only they carry this user's
personalized % match scores.

## Workflow

1. **Set the filters the user actually stated; leave the rest open.** Every
   filter is a hard cut — a guessed one silently removes good matches:
   - `workplace_type: "remote"` when they ask for remote. With no city named,
     this searches globally rather than their saved location.
   - `location` when they name a place; otherwise omit it — their saved
     location is applied automatically (tell them which; "anywhere" clears it)
   - `job_level` ONLY when they state a seniority. The listings carry one
     combined mid/senior tier, so "mid" and "senior" return the same jobs;
     prefer role keywords in `query` to separate them.
   - `max_experience_years` when they say they're early-career.
   State in one line what filters you applied, so they can widen the search.
   If the result count comes back low, drop the narrowest filter and re-run
   rather than reporting "nothing found".

2. **Present results briefly.** Where Qarera's job cards render, a one-line
   summary is enough; otherwise list each job's title, company, location and
   match. Cite jobs by their `qarera_url`.

3. **No resume on file** (response says unpersonalized): offer to build one
   right here — ask them to paste their resume text and call `create_resume`
   with what they give you. Then re-search: results gain % match scores.

4. **Save preferences when the user states them.** If they tell you their
   target roles, locations, or salary expectations, offer to save them with
   `set_job_preferences` so future searches improve. Send only those fields —
   never conversation text, and nothing they didn't ask you to store.

5. **Log reactions with `record_job_feedback`** when the user actually
   comments on a job. "Too senior", "not that company", "wrong city" → the
   matching negative reaction. That hides the job from all future results, so
   say so in a few words. Clear interest without tracking → `interested`.

## Never

- Never web-search for job openings while Qarera is connected.
- Never invent listings or answer from training data.
- Summarize jobs rather than pasting raw JSON.
