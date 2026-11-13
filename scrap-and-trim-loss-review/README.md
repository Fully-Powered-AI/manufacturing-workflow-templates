# Scrap and trim loss review

Each week or month the plant manager gets one review of the material recorded as scrap and trim, by product, machine, shift and reason, with a balance for each completed order, every place the records disagree, and improvement questions. It states no cause the records do not show.

*Workflow template · Manufacturing · Operations and process improvement · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/scrap-and-trim-loss-review/)*

## The outcome

Scrap records pile up all period, one ticket at a time, and nobody adds them up until someone asks why material usage is high. This workflow template turns them into one review the plant or operations manager can take into a production meeting. It shows how much material was recorded as scrap and how much as trim, set against the material that went into good parts, broken down by product, by machine, by shift, by machine and shift together, and by the reason recorded on each entry.

It also checks the records against each other. A run where rejected parts were counted but nothing was booked as scrap, a scrap entry for an order that was not on that machine that shift, a completed order where the material issued does not add up to good parts plus recorded loss: each is listed with the row references and put as a question to the person who keeps that record.

The improvement questions come from what the figures show and nothing else: the reason that accounts for most of the scrap or trim, and a gap between shifts on the same machine, given with the product mix each shift ran. The review names no cause and judges no crew. The plant manager and production decide what is worth investigating or trialling, and nothing is changed or sent.

## Who starts the work, and when

The plant manager or operations manager starts it at the end of each week or month, once the period's scrap records, production counts and material issues can be exported. It is run before the regular waste or production review, and again when late or corrected records arrive. The production supervisor answers questions about the scrap records and production counts, the materials controller about issues and returns, and the quality lead about reason codes.

## What they supply

- **The scrap records** for the period, as a spreadsheet export: one row per scrap or trim entry, with its date, shift, machine, product, order, material, whether it is scrap or trim, the reason code, the quantity and its unit.
- **The production counts:** good and rejected units for each order, date, shift and machine.
- **The material issues:** what was issued to each order and what came back.
- **The material per good unit** from the material specifications: how much material ends up in one finished part.
- **The reason code list,** with each code marked as scrap or trim.
- **A short settings note:** the plant, the period, the unit of measure, which orders were completed, and the thresholds that decide when a figure becomes a question.

The template states the default column headers for every export and stops to ask when one does not match.

## What comes out

One review in a fixed order: the period's recorded loss and rate; the same figures by product, machine, shift, and machine and shift together; scrap and trim by recorded reason; a material balance for each completed order; where the records disagree; rows that were not counted, have no reason, or fall outside the period; and the improvement questions. Every table adds back to the same total, and an empty section says "None." The worked example uses an invented stamping plant and shows the full inputs as well as the result.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Manufacturing](https://fullypowered.ai/industries/manufacturing/), where scrap tickets, production counts and stores issues are kept by different people and rarely read side by side.
- [Hardware and physical technology](https://fullypowered.ai/industries/hardware-and-physical-technology/), for product makers who cut, form or mould their own parts and want to see where material goes.
- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/), for brands that run their own production and watch material loss as closely as sales.
- [Operations and process improvement](https://fullypowered.ai/functions/operations-and-process-improvement/), which runs the production floor and decides where to look for waste.
- [Quality management](https://fullypowered.ai/functions/quality-management/), which owns the reason codes and investigates once a pattern is worth chasing.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where years of scrap records exist and are seldom added up.
- [Growth and scaling](https://fullypowered.ai/situations/growth-and-scaling/), when more shifts and machines make the waste harder to see from the floor.

It sits beside two related workflow templates and does not replace them. [Cost of poor quality worksheet](https://fullypowered.ai/workflows/cost-of-poor-quality-worksheet/) puts a money value on failures; this review counts material and never costs it. [Production cost variance sheet](https://fullypowered.ai/workflows/production-cost-variance-sheet/) explains cost differences from standard for finance; this one shows where material was recorded as lost, for the people running the floor.

## What has to change for your company

Map your own export columns to the default headers. Agree the reason code list with quality and decide which codes are scrap and which are trim, then keep the list stable so one period can be read against the next. Confirm that your material figure per part is what ends up in the finished part, not the gross amount drawn, or trim will be counted twice. Set the three thresholds: how far a completed order's material balance may be out before it is raised, how large a share one reason must reach, and how wide a gap between shifts on one machine must be before it becomes a question. Say who answers questions about scrap records, issues and reason codes. If parts pass several machines, decide which step's count is the finished count. It runs in ChatGPT, Claude, Copilot or Gemini from the exports you supply and needs no access to your systems.

## What has been checked

Fully Powered AI wrote this workflow template. It was editorially reviewed on 12 November 2026. It was tried once, with Claude, on its invented example on 12 November 2026; no stop condition, request for a cause or a culprit, request to cost the loss, or note naming a person was exercised in that run, and the record is published with it. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past month your plant manager already knows, with cases written in advance: a scrap entry recorded in pieces instead of weight, a run with rejected parts and no scrap entry, a completed order whose issues do not balance, a blank reason code. The plant manager recomputes two groups and one balance by hand before anyone relies on the review. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/) builds that test set, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) shows the record we keep.

- Written by Fully Powered AI.
- Sources and rights reviewed.
- Editorially reviewed on 12 November 2026.
- Package format checked by script on every release.
- Tried once on its invented example in Claude on 12 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete workflow template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example with invented data.
- [TRIAL.md](TRIAL.md): what came out when the template was tried on its example.
- [SKILL.md](SKILL.md): the technical file, for AI products that load packaged instructions from a folder.
- [SOURCES.md](SOURCES.md): what the workflow template drew on, with licences.
- [LICENSE](LICENSE): MIT. Use it, change it, make it yours.

## Start using it

1. Read [EXAMPLE.md](EXAMPLE.md) to see what a good result looks like.
2. Open [TEMPLATE.md](TEMPLATE.md) and set every item under "What to customize" to your own rules, roles and limits.
3. Give your AI assistant the instruction block and the output format from the template, with your own limits in place of the ones the instructions leave open in square brackets. Paste them in as custom instructions in ChatGPT, Claude, Copilot or Gemini, or copy this whole folder into a product that loads `SKILL.md` packages. This folder stands alone; you do not need the rest of the repository.
4. Run it on past work first, using the reviewer checklist and acceptance tests in the template, before anyone relies on it.

## Related workflow templates

- [Cost of poor quality worksheet](https://fullypowered.ai/workflows/cost-of-poor-quality-worksheet/)
- [Production cost variance sheet](../production-cost-variance-sheet/)
- [Operations KPI scorecard](https://fullypowered.ai/workflows/operations-kpi-scorecard/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
