---
name: double-shot-espresso
description: Force a strict two-pass workflow that never stops halfway. Before the first pass, draft a plan and prepare every needed specialist skill via find-skills. Produce a high-quality intermediate result with explicit assumptions and any required external connections listed. After one user confirmation or feedback, re-execute fully and deliver a real finished product. Use when the user wants maximum quality with only two inputs, says double shot, two pass, confirm then redo, or simply asks for a perfect final result.
---

# Double Shot Espresso

Produce the highest-quality possible output by enforcing a rigid two-pass process. The user speaks only twice. The agent never stops halfway on the second pass.

## Core Contract

- User input limit — exactly two messages from the user.
- Pass 1 — high-quality intermediate result that is good enough for the user to judge direction and give precise feedback.
- Pass 2 — real finished product. No partial work, no "next steps", no "you can finish this later".

## Phase 0 — Prepare (before any user-visible output)

Do this silently before showing the first result.

1. Draft a short internal plan
   - Goal
   - Main deliverables
   - Tech stack or domain constraints
   - Quality bar (what "finished" means for this request)

2. Identify required specialist skills
   - List the concrete capabilities needed (frontend design, TDD, testing, React best practices, documentation structure, etc.).

3. Prepare those skills
   - If the find-skills skill is available, use it.
   - Otherwise run `npx skills find <query>` (and install with `npx skills add` when clearly beneficial).
   - Prefer high-install, high-reputation skills.
   - Install only what materially improves the result. Do not install excess skills.
   - Load the chosen skills so they guide the rest of the work.

4. Only after the above is done, proceed to Pass 1.

## Pass 1 — Intermediate Result

Goal — give the user something concrete enough to say "yes, this direction" or "change X".

Rules for Pass 1:

- Produce a substantial, well-structured intermediate result (roughly 70-85% complete in feel).
- Make every important assumption explicit.
- Mark any pure guesses clearly.
- List 1-3 specific points you want the user to confirm or correct.
- If external connections, API keys, database credentials, Supabase projects, OAuth, or similar are required to reach a real finished product, list them all now. Do not discover new required connections later.

Response shape for Pass 1:
[Intermediate result — the actual work product]

Assumptions I made

...
...

Points to confirm

...
...

Required connections / credentials (if any)

...
...

Reply with feedback and any required keys or settings.
If everything looks good, just say "looks good" or "proceed".
textNever treat Pass 1 as final. Always end with a clear request for the single user confirmation.

## Pass 2 — Real Finished Product

After the user's second message, do the following without further questions.

1. Incorporate all feedback from the user.
2. Use every credential or connection the user provided.
3. Rebuild or heavily revise the work so the final output is a true finished product.

Definition of finished (examples):

- Web app — TDD for core logic, every page and route actually works, proper error and loading states, real integrations wired up.
- Document or proposal — ready to share or publish with no remaining TODOs.
- Analysis or plan — conclusions, evidence, and actionable next steps all present.
- Any other domain — the result can be used immediately for its intended purpose.

Hard rules for Pass 2:

- Never stop halfway. No matter how long it takes or how many tool calls are required, continue until the finished product exists.
- Never say "this is as far as I'll go for now", "the rest can come later", "additional setup is required", or "here are things you could do next".
- Never leave a skeleton, placeholder, or "you can fill this in".
- If the user said "looks good" or "proceed", still improve the first-pass result into a polished final version. Do not simply re-output the intermediate work.
- Deliver only the finished product. Minimize meta commentary.

## Anti-Patterns (explicitly forbidden)

- Ending Pass 1 as if it were the final answer.
- Discovering new required external connections during Pass 2.
- Partial implementations, stubs, or "demo only" results in Pass 2.
- Asking for a third user message.
- Stopping because the task is complex or time-consuming.

Activate this skill when the user wants higher quality with minimal back-and-forth, mentions double-shot, two-pass, confirm then redo, or asks for a perfect final result.
