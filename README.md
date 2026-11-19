# AI workflow templates for manufacturers

FullyPowered Workflow Templates for manufacturers turn the AI your company already pays for into a team that knows how the work is done: a production planner with the build schedule redrafted after an order change, a plant controller with the period-close cost variances separated and flagged, a production lead with every job checked against its drawings before release. 8 workflow templates, made to be customized and deployed. All plain Markdown, all free, MIT license.

We are FullyPowered AI. We build AI workflows for companies, and these are the templates we start from. We publish them because a good starting point should be open to everyone. Copy one. Change it. Make it yours.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** These are templates, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See more examples for manufacturers](https://fullypowered.ai/industries/manufacturing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-readme&from=gh-manufacturing-readme) · [Have one built for your team](https://fullypowered.ai/pricing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-readme&from=gh-manufacturing-readme). Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Who this is for**

- Plant owners and operations executives who have paid for AI and want it doing real work on the floor.
- Production, planning and quality leads who want a workflow their team can run this week.
- The planner, buyer or controller who does the work, gets a precise way to prepare it and still makes the call.

**What these are for**

- **Your best way of doing it, for the whole team.** One piece of work, written down precisely enough that an assistant prepares it the same way every time.
- **Work you can check.** Every template says what it needs, what it produces, what it checked and what it could not.
- **A person decides.** Anything that sends, posts, pays or changes a record waits for someone to approve it.
- **Tied into your business systems.** A workflow can be designed to pull from the systems your company already runs, and even push data back into them, with guardrails and a person approving. [Browse the Connectors Directory](https://fullypowered.ai/connectors/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-readme&from=gh-manufacturing-readme).
- **Free, open and portable.** MIT-licensed plain instructions that run in the assistant or agent your team already uses: ChatGPT, Claude, Claude Code, Claude Cowork, Codex, Copilot, Gemini, Grok, Perplexity.

**Quick start**

1. **Find the gaps in a quote request before suppliers do.** Open ChatGPT, Claude, Copilot or Gemini. Copy the text below into a new chat, replace the square brackets with a request for quotation you already have, and send it. You need no sign-in here and nothing to download.

   ```text
   You are helping a buyer prepare a clarification list for one request for
   quotation. Do not send anything, decide which document is right,
   interpret a tolerance, or accept a supplier's assumption. The buyer
   approves every message and the engineer settles every technical
   question. Here is the request: [paste each line with part number,
   revision, quantity, material, finish and delivery date], the cover
   details [currency, quote due date, how long a quote must stand,
   certificates], and the drawing notes [paste the title block and
   tolerance text]. List: 1. Details left blank. 2. Places where two
   documents disagree, quoting each exactly and never saying which is
   right. 3. Tolerances that cannot be read as written. For each item say
   who settles it. Draft one message to suppliers, marked not sent.
   ```

2. Read what comes back. It marks what it checked and what is left for you. What comes out, with invented data:

   ```text
   RFQ CLARIFICATION LIST: RFQ-2611-04

   For: Priya, with Tomas (responsible engineer). Run on 2026-11-16. Quote due 2026-11-20 (4 working days left). Suppliers: Supplier A, Supplier B, Supplier C.
   Package read: 4 lines; 5 documents in the register; drawing text read for 4 of 4 drawings.

   Summary: 10 items. Waiting for the buyer's value: 4. Waiting for the engineer: 5. Settled by the engineer: 1. Closed by the buyer: 0.

   1. Missing details
   RFQ-CUR Request: the currency is blank. No other document states it. Why it matters: quotes in different currencies cannot be set side by side. Settled by: the buyer. Status: Waiting for the buyer's value.
   RFQ-VAL Request: how long a quote must stand is blank. No other document states it. Why it matters: the buyer cannot tell how long a price stands. Settled by: the buyer. Status: Waiting for the buyer's value.
   L2-FIN Line 2, QA-1043: the finish is blank. Drawing QA-1043, note 1, says "Deburr and passivate." Why it matters: the finish sets the price and the process route. Settled by: the buyer. Status: Waiting for the buyer's value.
   L3-QTY Line 3, QA-2210: the quantity is blank. No other document states it. Why it matters: there is no quantity to price. Settled by: the buyer. Status: Waiting for the buyer's value.
   ```

3. Stop there. You will know if this is for you. When you want it fitted to your company, or built into your agents, [that is what we do](https://fullypowered.ai/pricing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-readme&from=gh-manufacturing-readme).

A person starts every workflow, supplies the inputs and decides; the template prepares and checks, and nothing is approved, sent or released for you.

These are examples and a starting point, made to be customized to your plant, your records and your way of working. Work that is not listed here can be built, as one step or many.

## The workflow templates here today

- **[Field issue handoff to engineering](field-issue-handoff-to-engineering/)**: When a delivered product misbehaves for a customer, the customer service lead gets one case brief for engineering: the revision and serial references, the symptoms as reported, the photographs supplied, what service has done and the questions still unanswered. It names no cause.
- **[Job readiness packet](job-readiness-packet/)**: Before an order goes to the floor, the production or quality lead gets one packet: each requirement matched to its approved drawing, specification or inspection plan, with conflicting revisions, gaps and material shortfalls listed. The owners decide; nothing is approved or released.
- **[Line changeover review](line-changeover-review/)**: From the observed steps and timings of one changeover, the production lead gets every step sorted into work that needs the line stopped and work that could be done while it runs, the stop totalled, and an improvement plan to test on the line. Safety and quality steps are never proposed for removal.
- **[Production cost variance sheet](production-cost-variance-sheet/)**: At period close the plant controller gets one sheet that separates material, labor and overhead differences from standard, by order and by product, with missing actuals and changed standards flagged. Each difference is a question for operations, never a cause.
- **[Production schedule rebuild](production-schedule-rebuild/)**: When orders or forecasts change, the production planner gets a draft build schedule from open orders, work-centre capacity and material availability, with every overload and shortage listed, not quietly fixed. The planner checks feasibility and approves the changes.
- **[RFQ clarification list](rfq-clarification-list/)**: A buyer sending drawings and specifications out for quotation gets one list of missing details, conflicting revisions and ambiguous tolerances, and a record of each supplier's answers. The buyer approves every message; the engineer settles every technical question.
- **[Scrap and trim loss review](scrap-and-trim-loss-review/)**: Each week or month the plant manager gets one review of the material recorded as scrap and trim, by product, machine, shift and reason, with a balance for each completed order, every place the records disagree, and improvement questions. It states no cause the records do not show.
- **[Shipment documentation check](shipment-documentation-check/)**: When a job finishes, the shipping or quality lead gets one index comparing the order, the inspection records, the required certificates and the packing details, with each missing record and each quantity that does not agree set out. Nothing is certified or released.

## How to use one

Open a folder and start with its README. Every folder stands alone, so copy the one you want and leave the rest. The templates are written for ChatGPT, Claude, Copilot and Gemini: paste the instruction block and the output format in as custom instructions, or load the folder in a product that reads `SKILL.md` packages.

To take the whole collection, press **Use this template** at the top of this page: it copies every folder into a repository in your own account, yours to change.

In every template a person starts the work, supplies the inputs and decides. The template prepares and checks. Anything that sends, posts, pays or changes a record waits for a person to approve it.

## What SKILL.md is

Each folder holds a file named `SKILL.md`. It is the technical file: the same instructions and output format as the template, in the packaged form that AI products which load instructions from a folder read. It is generated from `TEMPLATE.md`, so the two always agree. The workflow template is the whole folder; `SKILL.md` is one way of loading it. If your AI product does not read that format, use `TEMPLATE.md`.

## What "checked" means here

Each folder says exactly what was checked and when: who wrote it, that its sources and rights were reviewed, the date of its editorial review, and whether it has been tried on its invented example in a named AI product. Nothing is described as tested for a client unless it was. Test a template on your own past work before your team relies on it; each one comes with acceptance tests for that.

## More workflow templates

The [FullyPowered Workflows Directory](https://fullypowered.ai/workflows/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-readme&from=gh-manufacturing-readme) lists every workflow template across functions and industries, with search. A machine-readable list of this repository is in [index.json](index.json).

For the work these templates come from, by area of the business and by task, see [AI workflow examples for manufacturers](https://fullypowered.ai/industries/manufacturing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-readme&from=gh-manufacturing-readme).

## Licence and credits

MIT, in [LICENSE](LICENSE) and in every folder. Each folder's SOURCES.md names what the workflow template drew on. Published by [FullyPowered AI](https://fullypowered.ai/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-readme&from=gh-manufacturing-readme).
