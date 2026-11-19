# Production schedule rebuild

Get a draft build schedule from open orders, capacity and material, with every overload and shortage listed. The production planner checks and approves.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** This is a template, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See Production schedule rebuild on our website](https://fullypowered.ai/workflows/production-schedule-rebuild/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild). Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Quick start**

1. Read EXAMPLE.md to see what a good result looks like.
2. Copy all of TEMPLATE.md into your assistant, then give it your own inputs, or the sample ones from EXAMPLE.md.
3. Read what comes back. It marks what it checked and what is left for you.

*Workflow template · Manufacturing · Operations and process improvement · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/production-schedule-rebuild/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild)*

## The outcome

An order moves, a rush arrives, a forecast is revised, and the planner has a new draft schedule the same day instead of rebuilding a spreadsheet. Each order that can be placed sits in the week it is due. Each work centre shows its hours against its capacity, and each material shows its balance week by week.

Where the plan does not hold, the draft says so plainly: this work centre is over by this many hours in this week, this material runs out in this week, this order has nowhere to go. It does not shuffle work to hide the problem. Firm orders and forecast are kept apart, so the planner can see which problems exist on firm orders alone and which appear only if the forecast arrives.

The draft also lists every change to the current plan, so the planner approves each one knowingly. Weeks the plant has frozen are left alone.

## Who starts the work, and when

The production planner runs it whenever the picture changes: a customer moves a date, a rush order lands, the forecast is revised, a supplier slips a delivery, or a work centre loses hours. It is also useful as the first draft of a regular weekly rebuild.

The planner reads the draft, checks it against what the floor can really do, and decides every conflict. Sales and purchasing are named beside the conflicts that depend on them, and the planner talks to them.

## What they supply

- **The open orders,** each with an item, a quantity, a due week, whether it is firm or a forecast, and whether it is a rush.
- **The routings:** the hours each unit of an item needs at each work centre.
- **The capacity** of each work centre, in hours, for each week covered.
- **The bills of material:** how much of each material one unit of an item uses.
- **Material supply:** stock on hand and receipts due, each marked confirmed or not.
- **The current plan,** if there is one, so the draft can show what would change.
- **Settings:** the weeks covered and how many of them are frozen.

## What comes out

One draft in a fixed order: the schedule by week; each work centre's load against its capacity; each material's balance; the capacity conflicts and material shortages, with the orders involved and any room left in other weeks; the orders that could not be placed and why; the changes to the current plan held for approval; and a numbered list of decisions for the planner. Check lines prove that the hours and materials in the draft add up to the orders behind them.

The draft releases no work order, orders no material and changes no record.

See the worked example in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Operations and process improvement](https://fullypowered.ai/functions/operations-and-process-improvement/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild), where the weekly plan is the plant's main working document.
- [Supply chain and inventory](https://fullypowered.ai/functions/supply-chain-and-inventory/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild), which supplies the material dates the schedule depends on.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild), where orders, capacity and material have to line up before a job starts.
- [Hardware and physical technology](https://fullypowered.ai/industries/hardware-and-physical-technology/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild), where small production runs change often.
- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild), for brands that make their own products and rebuild around seasonal demand.
- [Growth and scaling](https://fullypowered.ai/situations/growth-and-scaling/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild), when volume outgrows the planner's spreadsheet.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild), where the plan is rebuilt many times a year and each rebuild should follow the same rules.

It is not [a demand and supply review](https://fullypowered.ai/workflows/demand-and-supply-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild), which compares demand with supply month by month and decides nothing about the shop floor. It is not [an inventory reorder plan](https://fullypowered.ai/workflows/inventory-reorder-plan/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild), which works out what to buy. This one places orders on a weekly build schedule and shows where the plant cannot meet it.

## What has to change for your company

Set how many weeks are frozen. The template plans in weeks that start on a Monday; a different week would need the Monday checks changed. Decide what counts as a work centre in your plant, and keep the routings and capacities in one agreed export with the headers the template expects. Decide whether your forecast rows belong in the schedule at all. Agree who answers each kind of conflict: the planner for load, purchasing for material dates, sales for customer dates. Keep your own rules for sequencing within a week, set-up time and changeovers; this template places orders by week and does not sequence them.

## What has been checked

FullyPowered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried once on its example in Claude on 10 November 2026, and the record of that run is published with the template; it lists the edits made afterward, which have not been run again. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past rebuild the planner already knows, with cases written in advance: a rush into a frozen week, a work centre with no capacity row, a material receipt that is not confirmed. The planner checks every hour and every balance before anyone relies on the draft. [Demand and supply review](https://fullypowered.ai/workflows/demand-and-supply-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild) is the monthly companion, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild) describes the record we keep.

- Written by FullyPowered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete workflow template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example.
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

- [Demand and supply review](https://fullypowered.ai/workflows/demand-and-supply-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild)
- [Inventory reorder plan](https://fullypowered.ai/workflows/inventory-reorder-plan/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild)
- [Schedule recovery options](https://fullypowered.ai/workflows/schedule-recovery-options/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild)

## Make it yours

This workflow template is an example and a starting point. FullyPowered AI adapts it to how your company works, proves it on real work and rolls it out to the roles that use it. We can also build any other workflow for your company, including one that runs several steps, in a Workflow Sprint or a scoped implementation. [Talk with us](https://fullypowered.ai/contact/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-production-schedule-rebuild&from=gh-production-schedule-rebuild).
