# Job readiness packet

Before an order goes to the floor, the production or quality lead gets one packet: each requirement matched to its approved drawing, specification or inspection plan, with conflicting revisions, gaps and material shortfalls listed. The owners decide; nothing is approved or released.

*Capability template · Manufacturing · Operations and process improvement · version 0.1.0 · [Capabilities Directory](https://fullypowered.ai/capabilities/job-readiness-packet/)*

## The outcome

An order reaches the floor with a short list of what is wrong with it, instead of a surprise at the machine. The production or quality lead gets a packet that sets what the order calls for beside what the document register says is approved: the drawing, the process specifications, the inspection plan and the material. Each requirement is sorted into one plain class, so nothing is quietly skipped.

The packet is strict about the things that go wrong between the office and the machine. A drawing revision on the order that is not the approved one is listed, with the status the register gives it. Two sources calling the same drawing at different revisions are shown side by side. A specification that is not in the register at all is a gap, not an assumption. Material is shown as available, on order with a date, or short, and a missing certificate is named.

The packet decides nothing. The production owner and the quality owner decide whether the job is ready. It approves no drawing, revision or process, and it releases nothing.

## Who starts the work, and when

The production planner, the production lead or the quality lead starts it when an order is about to be released to the floor, and again if a revision changes before work begins. The production owner and the quality owner read the packet and decide, each for their own side.

## What they supply

- **The settings:** the site name, the job number, the check date and the names of the production and quality owner roles.
- **The order lines:** each line's part, quantity and due date.
- **The requirements:** what the order and its documents call for on each line, such as a drawing, a specification, an inspection plan or a material, with the revision called and where the call came from.
- **The document register:** every revision of each controlled document, with its status, approval date and approver.
- **The material lines,** if available: for each material, how much the job needs, how much is set aside, how much is on order, when it is expected and whether the certificate is on file.

If the columns of an export are named differently from those the template expects, the assistant stops and asks which is which.

## What comes out

One packet in a fixed order. It opens with the job's lines and a count of every requirement checked, with a tie-out line proving the counts add up. Then come the requirements that match the register, the conflicting revisions, the other document gaps, the material and certificate position, and any line missing a drawing or inspection requirement. It ends with a numbered list of decisions for the production and quality owners and a line stating what it cannot prove.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Operations & process improvement](https://fullypowered.ai/functions/operations-and-process-improvement/), where the readiness of the next order is a daily question for the production lead.
- [Quality management](https://fullypowered.ai/functions/quality-management/), where the revision on the order must be the one the quality lead approved.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/), where an order released with the wrong revision becomes scrap or rework.
- [Hardware & physical technology](https://fullypowered.ai/industries/hardware-and-physical-technology/), where small production runs change revision often.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where readiness lives in several people's heads and spreadsheets.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when more orders mean the check can no longer be done from memory.

It differs from two neighbours. [Obsolete copy check](https://fullypowered.ai/capabilities/obsolete-copy-check/) looks at which copies of instructions are held at the points of use; this packet looks at one order against the register. [Project handover readiness check](https://fullypowered.ai/capabilities/project-handover-readiness-check/) is for handing a finished project to the team that will run it, not for releasing an order.

## What has to change for your company

Fix the files and their column names once, so every order starts from the same exports. Write revisions the way your register does, since the comparison reads them as they appear. Decide which requirement types your orders carry and which sources count, such as the customer order, the drawing notes or the routing. Name the production owner and the quality owner roles. Decide how material is counted, in one unit per material. Agree what a person must do with each class of gap, and who may change the register.

## What has been checked

Fully Powered AI wrote this capability template. It was editorially reviewed on 10 November 2026. It was tried on its invented example in Claude on 10 November 2026; the record is published with it. The small points that run found open were settled the same day, after an independent review, without a rerun; the record lists them. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past order you already know well, with cases written in advance: a drawing called at a superseded revision, two sources calling different revisions, a specification missing from the register, material on order after the due date. The production and quality owners check every line of the packet against the register itself before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/capabilities/pilot-acceptance-test-preparation/) sets those cases up, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) describes the record we keep.

- Written by Fully Powered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its invented example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete capability template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example with invented data.
- [TRIAL.md](TRIAL.md): what came out when the template was tried on its example.
- [SKILL.md](SKILL.md): the technical file, for AI products that load packaged instructions from a folder.
- [SOURCES.md](SOURCES.md): what the capability drew on, with licences.
- [LICENSE](LICENSE): MIT. Use it, change it, make it yours.

## Start using it

1. Read [EXAMPLE.md](EXAMPLE.md) to see what a good result looks like.
2. Open [TEMPLATE.md](TEMPLATE.md) and set every item under "What to customize" to your own rules, roles and limits.
3. Give your AI assistant the instruction block and the output format from the template, with your own limits in place of the ones the instructions leave open in square brackets. Paste them in as custom instructions in ChatGPT, Claude, Copilot or Gemini, or copy this whole folder into a product that loads `SKILL.md` packages. This folder stands alone; you do not need the rest of the repository.
4. Run it on past work first, using the reviewer checklist and acceptance tests in the template, before anyone relies on it.

## Related capabilities

- [Obsolete copy check](https://fullypowered.ai/capabilities/obsolete-copy-check/)
- [Supplier quality response check](https://fullypowered.ai/capabilities/supplier-quality-response-check/)
- [Unshipped order review](https://fullypowered.ai/capabilities/unshipped-order-review/)

## Make it yours

This is the starting version. Fully Powered AI adapts capabilities to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
