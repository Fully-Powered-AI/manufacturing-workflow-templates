# Production cost variance sheet

Get one period-close sheet separating material, labor and overhead differences from standard, by order and product. Operations explains each one.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** This is a template, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See Production cost variance sheet on our website](https://fullypowered.ai/workflows/production-cost-variance-sheet/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet) Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Quick start**

1. Read EXAMPLE.md to see what a good result looks like.
2. Copy all of TEMPLATE.md into your assistant, then give it your own inputs, or the invented ones from EXAMPLE.md.
3. Read what comes back. It marks what it checked and what is left for you.

*Workflow template · Manufacturing · Finance and accounting · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/production-cost-variance-sheet/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet)*

## The outcome

When production closes for the period, the controller does not start from a pile of exports. The sheet is ready: for every closed order, what the standard cost card allowed for the good units made, what was actually booked, and the gap between them, split into material price and material usage, labor rate and labor efficiency, and overhead spending and overhead efficiency. The same figures are added up by element and by product, and every set of parts ties back to actual cost less standard cost.

The sheet is careful about what it does not know. An order with no labor hours posted does not get a labor variance of zero; it gets a flag and a question. A product whose standard changed during the period is named with the old and new figures, and an order that straddled the change is marked, so nobody reads a price gap that is really a standard update. Every difference over your limits becomes a question addressed to a named role in operations, written with the figures and no explanation. The controller verifies the arithmetic. Operations supplies and confirms any reason.

Nothing is posted, no standard cost is changed and no new standard is proposed.

## Who starts the work, and when

The plant controller, or a cost accountant working for the controller, starts it once production actuals for the period have closed. It is run before the variance accounts are reviewed and before anyone explains the month to plant management. Operations answers the questions it produces, and the controller decides what goes into the close and the management pack.

## What they supply

- The standard cost cards: one row per product and effective date, with the material quantity and price, labor hours and rate, and overhead rate per labor hour.
- The actuals for each closed order: product, start and close dates, good units, material quantity and cost, labor hours and cost, and overhead assigned to the order.
- A short settings note: plant name, period, currency, material unit, the limits that decide which differences become questions, and who in operations answers which kind of question.

## What comes out

One fixed-order sheet: totals by element, a block for each order, totals by product, the flags (missing actuals, changed standards, anything else), the questions for operations, and a tie-out that shows the parts add up. Empty sections say "None." The worked example uses an invented plant and shows the full inputs as well as the result.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Manufacturing](https://fullypowered.ai/industries/manufacturing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet), where standard costs are the yardstick and the close is when the gaps get explained.
- [Hardware and physical technology](https://fullypowered.ai/industries/hardware-and-physical-technology/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet), for product makers who run builds against a costed bill of materials and routing.
- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet), for brands that make their own goods and watch product cost closely.
- [Finance and accounting](https://fullypowered.ai/functions/finance-and-accounting/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet), which owns the cost records and the close.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet), where the plant has run long enough to have standards worth measuring against.
- [Private equity & portfolios](https://fullypowered.ai/situations/private-equity-and-portfolios/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet), where a portfolio plant reports the same variance view to its owners every period.

It sits beside two related workflow templates and does not replace them. [Budget-versus-actual variance commentary](https://fullypowered.ai/workflows/budget-versus-actual-variance-commentary/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet) works from budget lines in the results; this one works from unit standards by order. [Cost of poor quality worksheet](https://fullypowered.ai/workflows/cost-of-poor-quality-worksheet/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet) sorts rework, scrap and return costs; this one never says why material or hours ran over.

## What has to change for your company

Map your own column names and cost-card layout to the default headers. Set the review limits, the percentage and the amount a difference must reach before it becomes a question. Say who in operations answers material, labor, overhead and missing-posting questions. Confirm that overhead is applied on labor hours in your plant; if it is applied on machine hours or another base, the overhead rule needs rewriting before use. Decide whether the over-limit test is applied to the parts only (the default) or to totals as well, and whether the plant's fixed overhead needs a spending and volume split. Decide whether orders are listed by order number or by product, and who receives the finished sheet.

## What has been checked

FullyPowered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried once, with Claude, on its invented example on 10 November 2026, and the record is published with it. That run was not blind: the model had seen the published example and an earlier run before it worked the arithmetic. No stop condition came up in the run. It has not yet been tested in a client environment or as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a closed period your controller already knows, with cases written in advance: an order with no labor posting, a standard that changed mid-order, a header that does not match. The controller recomputes every variance by hand before anyone relies on the sheet. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet) builds that test set, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet) shows the record we keep.

- Written by FullyPowered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its invented example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
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

- [Budget-versus-actual variance commentary](https://fullypowered.ai/workflows/budget-versus-actual-variance-commentary/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet)
- [Cost of poor quality worksheet](https://fullypowered.ai/workflows/cost-of-poor-quality-worksheet/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet)
- [Month-end close checklist](https://fullypowered.ai/workflows/month-end-close-checklist/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet)

## Make it yours

This workflow template is an example and a starting point. FullyPowered AI adapts it to how your company works, proves it on real work and rolls it out to the roles that use it. We can also build any other workflow for your company, including one that runs several steps, in a Workflow Sprint or a scoped implementation. [Talk with us](https://fullypowered.ai/contact/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-cost-variance-sheet&from=gh-production-cost-variance-sheet).
