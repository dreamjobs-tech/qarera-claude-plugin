# Qarera for Claude

Qarera turns Claude into a job-search assistant connected to your own Qarera account. Search live job openings by
role, company, location or remote, and see a % match against your resume on every job. Read any job in full, build or
update your resume from text you paste, have Claude tailor it for one job (saved as a copy, with a PDF link), save a
cover letter to the job, and track every application in a private pipeline: bookmarked, applied, interviewing,
negotiating, offered, rejected.

Qarera is free to use in Claude. Full documentation: https://www.qarera.com/claude-connector

## Install

From Claude's directory, or in Claude Code:

```
/plugin install qarera --marketplace dreamjobs-tech/qarera-claude-plugin
```

## What's in this plugin

- **Connector:** Qarera's remote MCP server at `https://mcp.qarera.com/mcp` (declared in `.mcp.json`). It is the only
  service this plugin talks to, and it is run by Qarera.
- **Skills:**
  - `qarera-job-search`: find jobs matched to your resume;
  - `qarera-apply-kit`: fit check, tailored resume and cover letter for one job;
  - `qarera-pipeline-coach`: review and update your application pipeline.
- No hooks, no scripts, no local code, and nothing installed on your machine.

## Sign-in and data

- **Sign-in:** the first time a Qarera tool runs, Claude opens Qarera's OAuth sign-in. Sign in with Google; the first
  sign-in creates a free Qarera account. Claude never sees your password.
- **What Qarera receives:** only the inputs a tool needs, such as the search words and place for a job search, or the
  resume text you ask it to save. It never receives your chat history.
- **Disconnecting:** remove Qarera in Claude's connector settings. Your resumes and pipeline stay in your Qarera
  account (https://www.qarera.com).
- Privacy policy: https://www.qarera.com/privacy · Terms: https://www.qarera.com/terms

## Example prompts

- "Find remote backend engineer jobs on Qarera."
- "Show me the full requirements for the first one."
- "Tailor my resume for that job and give me the PDF."
- "Show my Qarera application pipeline."

## Support

https://www.qarera.com/support · contact@qarera.com
