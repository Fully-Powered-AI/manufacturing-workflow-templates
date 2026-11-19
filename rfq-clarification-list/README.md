# RFQ clarification list

Get one list of missing details, conflicting revisions and ambiguous tolerances before quotes come back. The buyer approves every message.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** This is a template, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See RFQ clarification list on our website](https://fullypowered.ai/workflows/rfq-clarification-list/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list). Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Quick start**

1. Read EXAMPLE.md to see what a good result looks like.
2. Copy all of TEMPLATE.md into your assistant, then give it your own inputs, or the sample ones from EXAMPLE.md.
3. Read what comes back. It marks what it checked and what is left for you.

*Workflow template · Manufacturing · Procurement and suppliers · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/rfq-clarification-list/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list)*

## The outcome

An incomplete request for quotation costs more than the time it takes to fix. Suppliers fill the gaps with their own guesses, quote different revisions, and send back prices that cannot be set side by side. This workflow template finds the gaps before the quotes come back, and keeps them in one place afterwards.

The buyer works from a single list. Each line of the request is checked against its drawings and the document register. What is blank is listed as a missing detail. Where one document says one thing and another says something else, such as a revision, a thickness or a specification, the list quotes both documents side by side and sends the question to the responsible engineer. Where a tolerance is missing, stated twice in different ways or written only in words, the list quotes the text exactly and sends it to the engineer too.

As suppliers answer, each answer is recorded against the item it belongs to, by supplier and date. The list shows which suppliers have not answered past the reply date, where two suppliers have assumed different things, and where a supplier has volunteered a tolerance or a revision of their own. A volunteered assumption is recorded as that supplier's assumption and nothing more.

The workflow template sends nothing and settles nothing. It does not decide which revision is right and does not interpret a tolerance. The buyer approves every message to a supplier, and the responsible engineer settles every technical conflict.

## Who starts the work, and when

The buyer or purchasing lead starts it once the request for quotation package is assembled, ideally before it goes out, and runs it again each time supplier answers or an engineer's ruling arrive. The responsible engineer is named at the start, because every conflict and tolerance item is theirs to settle.

## What they supply

- The request's lines: part number, description, revision, quantity, unit, material, finish, delivery date and drawing reference.
- The request's cover details: reference, quote due date, delivery location, currency, how long a quote must stand, and certificate or inspection requirements.
- The document register: each drawing and specification with its revision and date.
- The text of each drawing's title block, notes and tolerances, typed or pasted in.
- The buyer's own notes: messages already sent, with dates, and any value the buyer has confirmed.
- The responsible engineer's rulings, in their own words, as they arrive.
- Supplier answers, with the date, the supplier and the item each answers.

## What comes out

One list in a fixed order: missing details, conflicts between documents, ambiguous tolerances, the record of supplier answers, a draft message and a short list of what needs a person. Every item has an identifier built from its line and the check that raised it, so an answer can be pinned to it. Every item says who can settle it and where it stands.

The draft message carries only what is ready: an engineer's ruling to pass on, a request for a supplier's assumption, a reminder. It never carries an unsettled conflict or a tolerance in question, and it never names one supplier to another.

See the worked example in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Procurement and suppliers](https://fullypowered.ai/functions/procurement-and-suppliers/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list), where the buyer owns the request and the replies.
- [Supply chain and inventory](https://fullypowered.ai/functions/supply-chain-and-inventory/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list), where a quote on the wrong revision becomes a part that arrives wrong.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list), where parts are bought to drawing and revisions change often.
- [Hardware and physical technology](https://fullypowered.ai/industries/hardware-and-physical-technology/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list), where new parts are quoted from drawings that are still moving.
- [Engineering firms](https://fullypowered.ai/industries/engineering-firms/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list), where fabricated parts are bought to a client's design.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list), where the drawing set has grown by habit and nobody has checked it against the request.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list), where more requests are going out than one buyer can read line by line.

## What has to change for your company

- **The required details.** Which fields every line and every request must carry. The defaults are listed in the template; add your own, such as packaging or country of origin.
- **The reply period.** The working days a supplier has to answer; three is the default.
- **Who settles what.** Which engineer owns which drawings and specifications, and whether quality or production also rule on some items.
- **Your column headers.** The names your request export and document register use, so the assistant can read them.
- **Your message style.** The wording, the sign-off and whether suppliers get one message or one each.
- **Your reviewer for commercial terms.** Questions about terms and conditions in the request are left to whoever you name; this workflow template does not answer them.

## What has been checked

FullyPowered AI wrote this workflow template from its own map of the work. It was editorially reviewed on 10 November 2026. It was tried once on its example in Claude on 10 November 2026, and the record of that run is published with the template; it lists the small edits made afterward that have not been run again. It has not yet been tested in a client environment.

Testing in your environment means running it on a past request whose problems you already know, with cases written in advance: a revision that differs between the request and the drawing, a tolerance stated twice, a supplier who guesses. The buyer and the engineer check every item against the documents before anyone relies on the list. [Vendor quote comparison](https://fullypowered.ai/workflows/vendor-quote-comparison/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list) takes over once the quotes are in, setting them side by side; this one stops at what suppliers say about the request and leaves any price unread. [Supplier issue notice](https://fullypowered.ai/workflows/supplier-issue-notice/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list) handles the later step, when a supplier falls short of what was agreed; this one is about the request before the order.

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

- [Vendor quote comparison](https://fullypowered.ai/workflows/vendor-quote-comparison/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list)
- [Supplier issue notice](https://fullypowered.ai/workflows/supplier-issue-notice/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list)
- [Supplier delivery date check](https://fullypowered.ai/workflows/supplier-delivery-date-check/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list)
- [Category sourcing plan](https://fullypowered.ai/workflows/category-sourcing-plan/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list)

## Make it yours

This workflow template is an example and a starting point. FullyPowered AI adapts it to how your company works, proves it on real work and rolls it out to the roles that use it. We can also build any other workflow for your company, including one that runs several steps, in a Workflow Sprint or a scoped implementation. [Talk with us](https://fullypowered.ai/contact/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=manufacturing-rfq-clarification-list&from=gh-manufacturing-rfq-clarification-list).
