# Shipment documentation check

When a job finishes, the shipping or quality lead gets one index comparing the order, the inspection records, the required certificates and the packing details, with each missing record and each quantity that does not agree set out. Nothing is certified or released.

*Workflow template · Manufacturing · Quality management · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/shipment-documentation-check/)*

## The outcome

The last hour before a shipment leaves is a bad time to find that a certificate was never filed, or that fifty-five pieces are on the pallet for an order of fifty. This workflow template does the comparison earlier, in one pass, while there is still time to find the paper or count the pieces again.

You get an index with one entry for every document your own list requires. Each entry says whether a matching document is on file, when it is dated, whether it is shown as signed, and whether it agrees with the order on item code and revision. Under it, each order line has its quantities side by side: ordered, inspected, accepted, rejected and packed, and the same for each lot or serial group, so a lot packed beyond what was accepted is visible.

The list of what is required is yours. The workflow template does not decide which certificates a customer or a standard calls for, and it does not read a certificate to judge what it proves. It reports what is present, what is absent and what disagrees. Quality and shipping make the release decisions.

## Who starts the work, and when

A shipping lead, a quality lead or a coordinator working for either runs it when a job finishes, before the shipment is booked or the goods leave. Run it again after missing records are found or the packing changes.

The quality lead decides what the records show and whether any of them is acceptable. The shipping lead decides whether the shipment goes, and how. The workflow template signs and issues no certificate, makes no judgment on conformity or on export requirements, and contacts nobody.

## What they supply

- **The order lines:** order number, line, item code, description, quantity ordered, unit, revision and the ship date.
- **Your required-documents list:** for each requirement, the document type, the line it applies to (or the whole order) and where the requirement comes from.
- **The inspection records:** line, item code, lot or serial group, quantity inspected, accepted and rejected, the date and the result as written.
- **The documents on file:** each certificate or paper with its type, line, item code, lot, revision, date and whether it is signed.
- **The packing details:** line, item code, lot, quantity packed and unit.
- **Settings:** today's date, the quantity tolerance and the words your records use for accepted and signed.

Each file's column headers are checked first. If one does not match, the work stops and asks which column is which. It works from files you supply and needs no connection to your systems.

## What comes out

One page in a fixed order: a summary and data checks, the document index, the quantity comparison for every line, the records that are missing, the differences between files, any document on file that no requirement names, and a numbered question for the quality and shipping leads on each line that needs a decision. A section with nothing in it says "None."

Every count can be checked against the files you supplied. Each finding names the record or document it comes from.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Quality management](https://fullypowered.ai/functions/quality-management/): the check made before goods leave, from records the quality team already keeps.
- [Supply chain and inventory](https://fullypowered.ai/functions/supply-chain-and-inventory/): the shipping side, where what is packed has to match what was ordered.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/): made-to-order jobs that ship with inspection reports, material certificates and a packing list.
- [Hardware and physical technology](https://fullypowered.ai/industries/hardware-and-physical-technology/): product builds shipped to customers with their records.
- [Logistics and trade](https://fullypowered.ai/industries/logistics-and-trade/): consolidated or forwarded goods where the paper has to travel with them.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/): when the check lives in one person's head and one folder.
- [Growth and scaling](https://fullypowered.ai/situations/growth-and-scaling/): when more jobs ship each week than one person can check by eye.

It checks one finished order's papers against its quantities. Preparing audit evidence across the business is [audit evidence index](https://fullypowered.ai/workflows/audit-evidence-index/). The daily list of orders that have not gone out is [unshipped order review](https://fullypowered.ai/workflows/unshipped-order-review/). A finding that becomes a nonconformity record is [nonconformity record draft](https://fullypowered.ai/workflows/nonconformity-record-draft/).

## What has to change for your company

- **Your required-documents list,** which is the only authority on what a shipment needs. Each customer or product family may have its own.
- **Your export headers,** set once so the column check passes without a question.
- **Your quantity tolerance,** if your orders allow a few pieces over or under.
- **Your words** for accepted and signed in the records.
- **Who decides** whether a flagged item is acceptable, and who may release the shipment.
- **Your AI product.** It is written to run in ChatGPT, Claude, Copilot or Gemini from the files you supply. It sends nothing and never asks for a password.

## What has been checked

Fully Powered AI wrote this workflow template in its own words from its own map of the work, with no third-party text. It was editorially reviewed on 10 November 2026. It was tried on its invented example on 10 November 2026 in Claude; the record is published with it, and the run was not blind. It has not yet been tested in a client environment.

Testing in your environment means running it on a recent shipment that your quality lead knows well, plus hard cases written in advance with their expected results: a renamed column, a certificate for the wrong revision, a lot packed beyond what was accepted, a document that is not signed, a line with no inspection record. The quality lead checks every finding against the files before anyone relies on it.

- Written by Fully Powered AI.
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

- [Unshipped order review](https://fullypowered.ai/workflows/unshipped-order-review/)
- [Audit evidence index](https://fullypowered.ai/workflows/audit-evidence-index/)
- [Nonconformity record draft](https://fullypowered.ai/workflows/nonconformity-record-draft/)
- [Job readiness packet](../job-readiness-packet/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
