# Fully Powered Capability Templates: Manufacturing

A plant where the next job is always ready to run. These capability templates are written for manufacturers. They prepare the schedules, packets and checks around a job from your own orders and records, and the people who run the plant decide what is made, when, and whether it ships.

This repository holds 6 capability templates for production, planning and operations leads at a manufacturer. Each one is a single piece of work with its own folder: what it is for and who starts it, the complete template an AI assistant follows, a worked example with invented data, what to change for your company, what has been checked, and its sources.

## The capabilities

- **[Field issue handoff to engineering](field-issue-handoff-to-engineering/)**: When a delivered product misbehaves for a customer, the customer service lead gets one case brief for engineering: the revision and serial references, the symptoms as reported, the photographs supplied, what service has done and the questions still unanswered. It names no cause.
- **[Job readiness packet](job-readiness-packet/)**: Before an order goes to the floor, the production or quality lead gets one packet: each requirement matched to its approved drawing, specification or inspection plan, with conflicting revisions, gaps and material shortfalls listed. The owners decide; nothing is approved or released.
- **[Production cost variance sheet](production-cost-variance-sheet/)**: At period close the plant controller gets one sheet that separates material, labor and overhead differences from standard, by order and by product, with missing actuals and changed standards flagged. Each difference is a question for operations, never a cause.
- **[Production schedule rebuild](production-schedule-rebuild/)**: When orders or forecasts change, the production planner gets a draft build schedule from open orders, work-centre capacity and material availability, with every overload and shortage listed, not quietly fixed. The planner checks feasibility and approves the changes.
- **[RFQ clarification list](rfq-clarification-list/)**: A buyer sending drawings and specifications out for quotation gets one list of missing details, conflicting revisions and ambiguous tolerances, and a record of each supplier's answers. The buyer approves every message; the engineer settles every technical question.
- **[Shipment documentation check](shipment-documentation-check/)**: When a job finishes, the shipping or quality lead gets one index comparing the order, the inspection records, the required certificates and the packing details, with each missing record and each quantity that does not agree set out. Nothing is certified or released.

## How to use one

Open a folder and start with its README. Every folder stands alone, so copy the one you want and leave the rest. The templates are written for ChatGPT, Claude, Copilot and Gemini: paste the instruction block and the output format in as custom instructions, or load the folder in a product that reads `SKILL.md` packages.

In every template a person starts the work, supplies the inputs and decides. The template prepares and checks. Anything that sends, posts, pays or changes a record waits for a person to approve it.

## What SKILL.md is

Each folder holds a file named `SKILL.md`. It is the technical file: the same instructions and output format as the template, in the packaged form that AI products which load instructions from a folder read. It is generated from `TEMPLATE.md`, so the two always agree. The capability template is the whole folder; `SKILL.md` is one way of loading it. If your AI product does not read that format, use `TEMPLATE.md`.

## What "checked" means here

Each folder says exactly what was checked and when: who wrote it, that its sources and rights were reviewed, the date of its editorial review, and whether it has been tried on its invented example in a named AI product. Nothing is described as tested for a client unless it was. Test a template on your own past work before your team relies on it; each one comes with acceptance tests for that.

## More capabilities

The [Fully Powered Capabilities Directory](https://fullypowered.ai/capabilities/) lists every capability across functions and industries, with search. A machine-readable list of this repository is in [index.json](index.json).

## Licence and credits

MIT, in [LICENSE](LICENSE) and in every folder. Each folder's SOURCES.md names what the capability drew on. Published by [Fully Powered AI](https://fullypowered.ai/).
