---
name: arbituro-file-job
description: File work as a new job in Arbituro through the Arbituro MCP server. Use when the user asks to file, log, track or create a job, task, bug or follow-up in Arbituro, or when work turns up mid-task that nobody has written down and the user wants it recorded rather than done now.
license: MIT
---

# File a job in Arbituro

A filed job arrives unassigned and unagreed: nobody has said what done means for it yet, and nothing
runs. Filing is cheap for you and costs a person a reading, so file what is worth one.

## 1. Check it is not already there

Call `search` with the project's key and two or three specific terms. If a job already covers it:

- Open: add what you found to that job with `post_note`, and tell the user its key.
- Finished or dropped: tell the user, and file a new job only if they still want one.

## 2. Write it

Call `create_job` with:

- **`title`**: short and imperative. "Stop the invoice download timing out", not "Invoice issue".
- **`description`**, as Markdown:
  - What you found, with the file, command or error that shows it.
  - Why it matters, in a sentence.
  - What you did not check.

Leave out how to fix it unless you know. Leave out a done-when: a person agrees that on the job.

One job for one piece of work. Three problems are three jobs.

## 3. Say what you filed

Give the user the new job's key and title. If you filed it in the middle of other work, mention it in
that job's closing note too.

## Changing a job that exists

You cannot edit a job. To suggest a better title, description or extra done-when clauses, call
`propose_job_update` with a `rationale` that says what you found. The job's owner accepts, edits or
dismisses it in one press.

## What not to put in a job

Secrets, tokens, customer data, or anything from another workspace. A job is read by everyone on its
project.
