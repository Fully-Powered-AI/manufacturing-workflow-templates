# Field issue handoff to engineering

Give engineering one case brief for a misbehaving delivered product: revision and serial, symptoms as reported, photos. Names no cause; people decide.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** This is a template, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See Field issue handoff to engineering on our website](https://fullypowered.ai/workflows/field-issue-handoff-to-engineering/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-field-issue-handoff-to-engineering&from=gh-field-issue-handoff-to-engineering). Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Quick start**

1. Read EXAMPLE.md to see what a good result looks like.
2. Copy all of TEMPLATE.md into your assistant, then give it your own inputs, or the invented ones from EXAMPLE.md.
3. Read what comes back. It marks what it checked and what is left for you.

*Workflow template · Manufacturing · Customer support and service · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/field-issue-handoff-to-engineering/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-field-issue-handoff-to-engineering&from=gh-field-issue-handoff-to-engineering)*

## The outcome

Engineering receives a case it can read in a few minutes instead of a forwarded email chain. The brief says which product and revision the customer has, which serial numbers are settled and which are not, what the customer says is happening and since when, which photographs came in and what the sender says they show, what service has already done, and what nobody yet knows.

Every symptom stays what it is: the customer's account, not yet checked. The brief never says what is wrong with the product and never suggests a fix. Where the customer mentions smoke, a burning smell, heat, shock or an injury, that goes to the top of the page, with the name of the specialist who should see the case before anything else happens.

Customer service checks the facts. Engineering decides whether to investigate and what to tell the customer technically. The assistant prepares the page and sends nothing.

## Who starts the work, and when

The customer service lead, or the service coordinator who holds the case, starts it when a customer reports that a delivered product is not behaving as it should and the case is about to move to engineering. It is run once per case, and again if new information changes the picture before engineering has taken the case.

The person running it gathers the customer's report, the delivery record for the units named, the list of photographs, the service notes so far and the company's intake checklist. The service lead reads the brief, corrects it and chooses who receives it.

## What they supply

- **The customer's report,** as written or as noted from the call, with the date it arrived and how.
- **The delivery record** for the units concerned: serial, product, revision, ship date and, where kept, the ship-to site.
- **A list of the photographs and files received,** with who sent each, when, what the sender says it shows and any text that can be read in it.
- **The service notes so far,** one row per note: date, who, what.
- **The company's issue-intake checklist.**
- **The company's settings:** the engineering contact, the safety specialist, who owns the revision record, and any extra safety words.
- **The date of the brief.**

## What comes out

One internal brief in a fixed order: a safety check, the case, product, revision and serial references, symptoms as reported, evidence supplied, what service has done, conflicts and gaps, the intake checklist with a count, the questions still unanswered and who can answer each, the points for engineering to decide, and the questions for the service lead to settle before it goes. A section with nothing to report says so in a fixed line.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Customer support and service](https://fullypowered.ai/functions/customer-support-and-service/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-field-issue-handoff-to-engineering&from=gh-field-issue-handoff-to-engineering): the moment a case outgrows the front desk and needs the people who built the product.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-field-issue-handoff-to-engineering&from=gh-field-issue-handoff-to-engineering): units leave with a serial number and a revision, and the case is only as useful as the match between what the customer holds and what the plant shipped.
- [Hardware and physical technology](https://fullypowered.ai/industries/hardware-and-physical-technology/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-field-issue-handoff-to-engineering&from=gh-field-issue-handoff-to-engineering): devices in the field, mixed revisions on one customer site, and reports that arrive as a photograph and a sentence.
- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-field-issue-handoff-to-engineering&from=gh-field-issue-handoff-to-engineering): a small service desk handing physical-product problems to a product team that is not on the same floor.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-field-issue-handoff-to-engineering&from=gh-field-issue-handoff-to-engineering): hand-overs have run on forwarded emails, and what engineering receives depends on who forwarded it.

## What has to change for your company

- **Write down who the safety specialist is** and what counts as a safety word for your products. The template carries a starting list; your products will need their own words.
- **Map your delivery record.** The default column headings are stated in the template. Adjust them to what your system exports, and decide how a serial is written.
- **Use your own intake checklist** if you have one; the template carries an eleven-item default.
- **Decide who receives the brief** in engineering and who owns the revision record.
- **Decide what service may say to the customer** while engineering decides. The template drafts nothing for the customer.
- **Your platform.** It runs in ChatGPT, Claude, Copilot or Gemini from files you supply and needs no connection to your systems.

## What has been checked

FullyPowered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried on its invented example in Claude on 10 November 2026; the record of the latest run, made by the same session that revised it after an independent review led to edits, is published with it. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a few past cases your service lead remembers well, plus hard cases written in advance, each with the expected result: a delivery-record export whose headings do not match, a serial number that is only partly readable, two records with different revisions for one serial, a report that mentions a burning smell, a customer who asks what is wrong. The service lead checks every serial, date and statement against the case before anyone relies on the brief. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-field-issue-handoff-to-engineering&from=gh-field-issue-handoff-to-engineering) sets those cases up, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-field-issue-handoff-to-engineering&from=gh-field-issue-handoff-to-engineering) describes the record we keep.

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

- [Support escalation brief](https://fullypowered.ai/workflows/support-escalation-brief/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-field-issue-handoff-to-engineering&from=gh-field-issue-handoff-to-engineering)
- [Help article from a resolved issue](https://fullypowered.ai/workflows/help-article-from-a-resolved-issue/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-field-issue-handoff-to-engineering&from=gh-field-issue-handoff-to-engineering)
- [Support ticket triage](https://fullypowered.ai/workflows/support-ticket-triage/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-field-issue-handoff-to-engineering&from=gh-field-issue-handoff-to-engineering)

## Make it yours

This workflow template is an example and a starting point. FullyPowered AI adapts it to how your company works, proves it on real work and rolls it out to the roles that use it. We can also build any other workflow for your company, including one that runs several steps, in a Workflow Sprint or a scoped implementation. [Talk with us](https://fullypowered.ai/contact/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-field-issue-handoff-to-engineering&from=gh-field-issue-handoff-to-engineering).
