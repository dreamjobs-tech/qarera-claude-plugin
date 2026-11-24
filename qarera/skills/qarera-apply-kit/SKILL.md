---
name: qarera-apply-kit
description: Build a complete application kit for a specific job — fit
  analysis, tailored resume, and cover letter — using the user's connected
  Qarera account. Use when the user asks whether to apply to a job, wants help
  applying, or wants their resume adapted for a specific role.
---

# Qarera apply kit

Turn "should I apply to this?" into a ready-to-send application, entirely in
this chat.

## Workflow

1. **Fit analysis** — fetch `get_job` (full requirements) and `get_resume`
   (their master resume). Compare honestly: strong matches, gaps, and a clear
   verdict. Don't flatter; a wrong application wastes their week.

2. **Tailor** — on a go-ahead, call `tailor_resume` with targeted edits:
   rewrite the summary for this role, reorder/emphasize matching experience
   bullets, align skills with the job's keywords. Where Qarera's resume card renders, it
   shows the changes; otherwise summarize what changed.
   Never fabricate experience — reframe what's real.

3. **Cover letter** — write it in-chat: specific to the job's actual
   requirements and the user's real experience, no template filler. Iterate
   with the user, then persist the final version with `save_cover_letter` —
   it lands in their Qarera account next to the tailored resume.

4. **Deliver the files** — after tailoring and after saving a cover letter,
   proactively offer PDFs via `export_resume` (kind="resume" and
   kind="cover_letter"). Present each `download_url` as a tappable link —
   it downloads the finished document directly, phone or desktop.

5. **Track** — `track_job` / `update_tracked_job(status="applied")` when they
   apply. Point them to the job's `qarera_url` apply link. You cannot submit
   applications yourself — say so if asked.

5. **No resume on file** — build one first: ask for pasted resume text and
   call `create_resume`, then continue the kit.

## Notes

- Keep each artifact short and real: hiring managers skim.
- If the fit is genuinely poor, say so and offer `search_jobs` for closer
  matches instead — record the mismatch with `record_job_feedback`.
