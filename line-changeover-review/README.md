# Line changeover review

From the observed steps and timings of one changeover, the production lead gets every step sorted into work that needs the line stopped and work that could be done while it runs, the stop totalled, and an improvement plan to test on the line. Safety and quality steps are never proposed for removal.

*Workflow template · Manufacturing · Operations and process improvement · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/line-changeover-review/)*

## The outcome

Every minute a line stands still between products is a minute it makes nothing. This workflow template turns one timed changeover into a clear picture of where those minutes go, and a plan to win some of them back with the people and parts you already have.

Every observed step is sorted. Some need the line stopped: taking out the old change parts, fitting the new ones, setting the machine. Others were done during the stop only out of habit: walking to the store, searching for a part, waiting for materials, washing parts that could be washed once the new product is running. Those become proposals to move before the stop or after restart, each with the minutes it took. Where the record shows a setting found by trial every time, or a second person standing free while one person does the heavy fitting, the plan says so as an idea to try.

The lockout, the guard checks, the line clearance, the clean between products and the first-off check stay exactly as they are. They are listed apart, named as protected, and never put forward for removal, shortening or moving.

The plan comes with an estimate whose working is shown, labelled as something to test on the line, and with a short test plan: which steps to time at the next few changeovers. The production lead decides what to test and what to adopt.

## Who starts the work, and when

The continuous-improvement lead, the production lead or a shift lead starts it once a changeover has been timed step by step: when changeovers are eating into the week, before an improvement session on one changeover, or after a change has been tried and the changeover observed again.

One run covers one observed changeover on one line, from one product to the next. The production lead reads the draft, settles the questions with the safety owner, the quality owner and the maintenance or engineering contact, and chooses what to test. The operators test it on the line.

## What they supply

- **Settings:** the line, the product changed from and to, the date, the observer, the time the line stopped and the time the first good unit of the new product passed its first-off check, the people who own safety, quality and engineering, and, if wanted, how many changeovers of this kind happen a week.
- **The observation sheet:** each step in order, who did it, its start and end times, whether the line was stopped or running, whether it is a safety or quality step, whether it was typical, and any notes. A spreadsheet export is fine; the template names the column headings it expects and stops to ask when they differ.
- **The setup sheet** for the new product, if there is one: change parts, tools, materials and settings.
- **Operator notes:** what the people who did the changeover said about it.

## What comes out

One review in a fixed order: the stop timed and checked against the record, with any minutes nobody recorded; each step with its sort and the reason for it; totals by sort; the protected steps, kept as observed; any steps marked not typical; the improvement plan, moves first and then ideas to shorten; the estimate to test, with its working; how to test it on the line; questions for the observer, the safety owner and the quality owner; and the decisions for the production lead. Check lines prove that the minutes add up.

The review changes nothing on the line, in the written procedure, in the setup sheet or in any record, and judges nothing safe. Those calls stay with the people who own them.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Operations and process improvement](https://fullypowered.ai/functions/operations-and-process-improvement/), where cutting changeover time is one of the plainest ways to get more from the same line.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/), where every product change on a line is lost making time.
- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/), for brands that fill and pack their own products and change sizes and flavours often.
- [Hardware and physical technology](https://fullypowered.ai/industries/hardware-and-physical-technology/), where small batches mean many changeovers on the same equipment.
- [Growth and scaling](https://fullypowered.ai/situations/growth-and-scaling/), when more products on the same line mean more changeovers every week.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where changeovers are done the way they have always been done and nobody has timed one in years.

It is not [a production schedule rebuild](https://fullypowered.ai/workflows/production-schedule-rebuild/), which decides which week each order is built in. It is not [an SOP written from how the work is done](https://fullypowered.ai/workflows/sop-from-how-the-work-is-done/), which writes the procedure down; once a tested change is adopted, that is the way to update the changeover procedure. And it is not [a process map and bottleneck review](https://fullypowered.ai/workflows/process-map-and-bottleneck-review/), which looks for the one step that limits a whole process. This one takes a single changeover apart, step by step, minute by minute.

## What has to change for your company

Agree what the stop is: the template counts from the last good unit of the old product to the first unit of the new one that passes its first-off check. Use one observation sheet with the headings the template expects, and time steps by the clock so that two people working at once can be seen. Mark safety and quality steps on the sheet, and name any step your production lead always protects, such as an allergen clean or a line clearance. Add the words your observers use for steps to the template's lists. Name who answers for safety, quality and engineering. Decide how many changeovers each test runs for. Keep your own rules for who may work on a machine at once; the template only raises the question. It runs in ChatGPT, Claude, Copilot or Gemini, from files and notes you supply, with no connection to your systems.

## What has been checked

Fully Powered AI wrote this workflow template. It was editorially reviewed on 12 November 2026. It was tried once on its invented example in Claude on 12 November 2026, and the record of that run is published with it; no stop condition or decline was exercised in that run, and the small edits made afterward have not been run again. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a changeover your production lead has already timed and knows well, with hard cases written in advance: two people working at once, a gap in the record, a clean marked as neither safety nor quality, a step that went unusually, a request to drop the first-off check. The production lead checks every minute against the sheet before anyone relies on the plan. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/) sets those cases up, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) describes the record we keep.

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

- [Production schedule rebuild](../production-schedule-rebuild/)
- [Write an SOP from how the work is done](https://fullypowered.ai/workflows/sop-from-how-the-work-is-done/)
- [Process map and bottleneck review](https://fullypowered.ai/workflows/process-map-and-bottleneck-review/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
