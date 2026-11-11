# Job readiness packet

Capability template, version 0.1.0.

## Purpose

Set one order against the document register before it is released to the floor, and report what does not line up. Every requirement the order carries, whether a drawing, a specification, an inspection plan or a material, is matched to the register's approved revision and sorted into one class. Conflicting calls for the same document are shown side by side. Material is reported as available, on order or short, with its certificate status. The assistant prepares the packet; it never approves a drawing, revision or process, never decides that the job is ready, releases nothing and changes no record. The production owner and the quality owner decide.

## When to use it and when not to

Use it when an order is about to be released to the floor, after the order lines, requirements and material position are assembled, and again if a revision changes before work starts.

Do not use it:

- to find out which copies of instructions are held at the machines. Obsolete copy check does that;
- to hand a finished project to the team that will run it. Project handover readiness check does that;
- to judge whether a drawing or specification is correct, to compare two revisions of a document or to decide what a revision change requires;
- when there is no document register. The assistant cannot decide what is approved; the register says so.

## Roles

- **Runs it:** the production planner, the production lead or the quality lead.
- **Owns the document register and approves documents:** the people the company names, such as engineering and quality. The assistant approves nothing.
- **Decides whether the job is ready:** the production owner for the floor, material and schedule; the quality owner for documents, revisions and inspection.
- **Changes the order, the register or the material position:** the person the company's process names, after the owners decide. The assistant changes no record.

## Inputs

All lists are files or pasted tables. Dates are written year-month-day. Default column headers are given; if a required header does not match, stop and ask which column is which. Do not guess.

1. **The settings.** Required: the site name, the job number, the check date, the name of the production owner role and the name of the quality owner role. If any is missing, stop and ask.
2. **The order lines.** Required. Headers: `job_no,line_no,part_no,qty,due_date`. One row per line. `qty` is a whole number above zero and `due_date` is a date; a blank cell in any column, or a repeated `line_no`, stops the work.
3. **The requirements.** Required. Headers: `job_no,line_no,req_type,doc_id,revision_called,source`. The `req_type` is drawing, specification, inspection or material. For a material, `doc_id` is the material specification. `revision_called` may be blank, which means the source named no revision. `source` says where the call came from, such as the customer order, a drawing note, the routing or an email. Every column except `revision_called` is required; a blank `source` stops the work. A document may appear more than once on a line, from different sources. The key of a row is `line_no`, `doc_id`, `revision_called` and `source`, compared as in step 1; a repeated key, an exact duplicate, stops the work and is not merged, so it cannot inflate the Matched count.
4. **The document register.** Required. Headers: `doc_id,title,revision,status,approved_date,approved_by`. One row per revision of each document. The status is Approved, Draft, Superseded or Withdrawn. `doc_id`, `title`, `revision` and `status` are required on every row; `approved_date` and `approved_by` are required only on an Approved row and may be blank on the others. An Approved row must have an approved date and an approver. A repeated `doc_id` and `revision` pair stops the work.
5. **The material lines.** Optional. Headers: `job_no,line_no,doc_id,qty_needed,qty_allocated,qty_on_order,expected_date,cert_on_file`. Quantities are numbers in one unit per material; the assistant converts nothing. `job_no`, `line_no`, `doc_id`, `qty_needed`, `qty_allocated` and `qty_on_order` are required (write 0 for none). `expected_date` may be blank. `cert_on_file` is yes or no; blank means not stated and is not an error. If this table is missing, write "material lines not supplied" and report every material requirement as "No material line supplied".

The assistant works from what the person supplies. It needs no connection to a register or a planning system and never asks for a password or a login code.

## The procedure

1. **Check the inputs.** Confirm the headers, the date format, the settings and the counts: order lines, requirements, register rows and distinct documents, material lines. Stop and list every problem if: a requirement row has a different job number from the settings or a line that is not in the order lines; a `req_type` is not one of the four; a register status is not one of the four; an Approved row lacks its date or approver; a requirement row repeats another's line, document, revision and source; or a material line repeats the same line and document. Compare document ids and revisions after trimming spaces and ignoring capital letters. "Rev C" and "C" are different revisions; that is reported, not corrected.
2. **Find each document's approved revision.** The Approved rows for its `doc_id` in the register.
3. **Find the conflicts.** A conflict is a line and a document with two or more different, non-blank revisions among its requirement rows. Every such row, one for each source, is in the conflict. Blank revisions never make a conflict. Calls on different lines are not compared. A conflict is counted, and given a decision, only when its rows are classed Conflicting calls in step 4; a document that is not in the register is classed Not in register even if it is called at two revisions, and its rows are printed under Document gaps with each call.
4. **Sort every requirement row,** using the first rule that fits:
   - the `doc_id` is not in the register: **Not in register**;
   - it is in a conflict: **Conflicting calls**;
   - the register holds two or more Approved rows for it: **Two approved revisions**;
   - it holds none: **No approved revision**;
   - the revision called is blank: **Revision not called**;
   - the revision called equals the approved revision: **Matched**;
   - otherwise: **Called revision not approved**, and state the called revision's status in the register, or that it is not in the register.
5. **Tie out.** The seven classes must add up to the requirement rows. If not, stop and report the figures.
6. **Check the material.** Take each distinct line and document among the material requirement rows once. Find its material line.
   - No material line: **No material line supplied**.
   - `qty_allocated` is at least `qty_needed`: **Available**.
   - Otherwise, if `qty_allocated` plus `qty_on_order` is at least `qty_needed`: **On order**. State how far short on hand it is. If `expected_date` is given, state how many days it falls before, on or after the line's due date; if blank, write "expected date not given".
   - Otherwise: **Short**, by `qty_needed` minus `qty_allocated` minus `qty_on_order`.
   The four results must add up to the distinct materials. Then report each certificate as on file, not on file or not stated, and tie out the three. List every material line that matches no material requirement.
7. **Check what is missing.** Every order line needs at least one drawing requirement and at least one inspection requirement. List each line that has no drawing requirement or no inspection requirement. Specifications and materials are checked only where the order lists them. A line missing both is printed once, as "no drawing or inspection requirement supplied".
8. **Order each section.** By line number, then requirement type in the order drawing, specification, inspection, material, then document id. The document gaps are in the order Not in register, No approved revision, Two approved revisions, Revision not called, Called revision not approved, and within each class by line, then type, then document id.
9. **Write the decisions.** One numbered decision for each conflict, each document gap, each material that is On order, Short or without a material line, each certificate not on file or not stated, each material line matching no requirement and each missing requirement, in that order. Each is a question for the owners with its facts. Recommend nothing unless asked. Matched requirements and Available material get no decision.
10. **State what is not proven** and return the packet to the person who ran it. The owners decide whether the job is ready; the assistant does not say that it is.

## Exceptions and stop conditions

- **A required header does not match, a date is not year-month-day, a required cell (the columns named in Inputs) is blank, a row repeats a key or a row refers to another job or an unknown line:** stop and ask.
- **The classes do not add up to the requirement rows, or the material results do not add up:** stop and report the figures.
- **The register is missing:** stop. Without it nothing can be matched.
- **Asked to say the job is ready, to approve or choose a revision, to release the order, to add or edit a register row, to change the order or to tell the floor to start:** decline and name the role that decides.
- **Asked to judge whether a drawing, specification or process is right, or to compare the content of two revisions:** decline; that is the work of the document's owner.
- **The inputs contain a password, a login code or personal details beyond a name and role:** do not repeat them; tell the person to remove them from the source.

## Output format

```
JOB READINESS PACKET: [site], job [job_no], check date [date]

For: [production owner role] and [quality owner role].
Prepared: [the check date from the settings], from order lines ([n]), requirements ([n]), document register ([n] rows, [n] documents), material lines ([n] / not supplied).

Order lines: [n]. Quantity in all: [n].
Line [n]: [part_no], quantity [n], due [date].

Requirements checked: [n]. Matched [n]. Conflicting calls [n]. Not in register [n]. No approved revision [n]. Two approved revisions [n]. Revision not called [n]. Called revision not approved [n]. Tie-out: [n] + [n] + [n] + [n] + [n] + [n] + [n] = [n].

Matched: [n] requirements
Line [n] [req_type] [doc_id] [title], revision [x], approved [date] by [approver]. Called by [source].
(none)

Conflicting revisions: [n] conflicts ([n] requirements)
Line [n] [req_type] [doc_id] [title]: revision [x] called by [source]; revision [y] called by [source]. Register: [approved revision [z], approved [date] / no approved revision / two approved revisions [z] and [w]]; [each called revision other than the approved one] is [status / not in the register].
(none)

Document gaps: [n] requirements
Line [n] [req_type] [doc_id]: not in the register. Called: [revision [x] / no revision] by [source].
Line [n] [req_type] [doc_id] [title]: no approved revision in the register (rows: [revision status, ...]). Called: [revision [x] / no revision] by [source].
Line [n] [req_type] [doc_id] [title]: two approved revisions in the register, [x] (approved [date]) and [y] (approved [date]). Called: [revision [z] / no revision] by [source].
Line [n] [req_type] [doc_id] [title]: no revision called by [source]. Register: approved revision [x], approved [date].
Line [n] [req_type] [doc_id] [title]: revision [x] called by [source]; [x] is [status in the register / not in the register]. Approved revision [y], approved [date].
(none)

Material: [n] materials. Available [n]. On order [n]. Short [n]. No material line supplied [n]. Tie-out: [n] + [n] + [n] + [n] = [n].
Line [n] [doc_id] [title]: needed [n], allocated [n], on order [n][ (On order lines only: , expected [date] ([n] days before / on / [n] days after the due date of [date]) / , expected date not given)]. [Available / On order; short on hand by [n] / Short by [n] / No material line supplied]. [Certificate: on file / not on file / not stated.]
(none)
Certificates: on file [n], not on file [n], not stated [n]. Tie-out: [n] + [n] + [n] = [n].
Material lines matching no requirement: [Line [n] [doc_id]; ...] / (none)

Requirements not supplied
Line [n] [part_no]: no [drawing / inspection / drawing or inspection] requirement supplied.
(none)

Decisions for [production owner role] and [quality owner role]: [n]
[n]. [Item.] [The facts.] [The question.]
(none)

Not proven: The packet compares only the lists supplied. It does not show that the register is right, that the drawing at the machine is the approved revision, that the material held is the grade the specification calls for, or that a requirement has not been left off the order. Specification and material requirements are checked only where the order lists them, and a document called at different revisions on different lines is not compared.[ Add any list that was not supplied.]

Draft for the decision of the [production owner role] and the [quality owner role]. No drawing, revision, process or material has been approved, no job has been released, and no record has been changed.
```

Print "(none)" under any section with no items. On a material line, print the title only if the document is in the register; if it is not, print the doc_id alone, as the Not in register line does. The date clause is printed for On order lines only. Write "1 day" or "[n] days". In the material section a "No material line supplied" result prints the line without the certificate sentence. Write "1 requirement" or "[n] requirements", "1 conflict" or "[n] conflicts". A requirement type with no entries for a line is not reported unless it is a drawing or an inspection (step 7). A conflict counts once, however many sources call into it, and its requirements are the rows.

## Reviewer checklist

1. The requirement counts tie out, and every requirement row appears once in one class. (Production planner)
2. Each matched requirement shows the approved revision and approver exactly as the register has them. (Quality lead)
3. Each conflict names every source and revision, and each gap names the register's status for the document. (Quality lead)
4. The material quantities and dates agree with the planning records, and the day count is right. (Production lead)
5. Every certificate is reported as the material lines say, and a blank is reported as not stated. (Quality lead)
6. Every item that needs action has a decision, and the numbers match. (Production planner)
7. Nothing in the packet says the job is ready, approves a revision or releases the order. (Production manager)
8. A sample of lines, including at least one of each class, has been checked against the register itself. (Quality lead)

## Acceptance tests

Proposed tests. None has been run.

1. **Clean order.** Every called revision equals the approved one, material is allocated, certificates are on file and each line has a drawing and an inspection. Expected: all Matched, no decisions, and no statement that the job is ready.
2. **Superseded revision called.** The order calls revision B and the register shows B Superseded and C Approved. Expected: Called revision not approved, with both statuses, and one decision.
3. **Two sources disagree.** The customer order calls D and an email calls E on the same line. Expected: one conflict, two requirements, and a register line giving the approved revision and the status of the other.
4. **Document not in the register.** Expected: Not in register, with the called revision and its source.
5. **Two approved revisions.** Expected: Two approved revisions, with both approval dates, whatever revision was called.
6. **No revision called.** Expected: Revision not called, with the register's approved revision.
7. **Revision written differently.** The order calls "Rev C" and the register has "C". Expected: Called revision not approved, with the register's revision shown as written.
8. **Material short.** Needed 100, allocated 30, on order 20. Expected: Short by 50.
9. **Material on order after the due date.** Expected: On order, short on hand by the missing amount, and the days after the due date.
10. **Certificate not stated.** A blank `cert_on_file`. Expected: not stated, one decision.
11. **Line with no inspection requirement.** Expected: listed under Requirements not supplied.
12. **Header does not match.** A register with `rev` where `revision` is expected. Expected: stops and asks.
13. **Asked to say the job is ready.** Expected: declines and names the production and quality owners.

## Instructions for the AI assistant

```
You prepare a job readiness packet for the production owner and the
quality owner. You never change a record, send anything or contact
anyone, and you never approve a drawing, revision, specification or
process, choose between revisions, say that a job is ready, release an
order or tell the floor to start. The owners decide; people who own the
register and the order make any change.

The user will supply: the settings (site name, job number, check date,
production owner role, quality owner role); the order lines (job_no,
line_no, part_no, qty, due_date); the requirements (job_no, line_no,
req_type, doc_id, revision_called, source); the document register
(doc_id, title, revision, status, approved_date, approved_by); and, if
available, the material lines (job_no, line_no, doc_id, qty_needed,
qty_allocated, qty_on_order, expected_date, cert_on_file).

If the settings, the order lines, the requirements or the register are
missing, stop and say so. If a required header does not match, a date is
not year-month-day, a required cell is blank (the register's approved
date and approver only on Approved rows; the requirements' revision,
the material lines' expected date and certificate may be blank), a key
is repeated (a requirement row is keyed by line, document, revision and
source), a row
refers to another job or an unknown line, a req_type is not drawing,
specification, inspection or material, a status is not Approved, Draft,
Superseded or Withdrawn, or an Approved row lacks its date or approver,
stop, list the problems and ask; do not guess. If the material lines are
missing, say so and report every material as having no material line.

1. Count order lines, requirements, register rows and distinct
   documents, and material lines. Compare ids and revisions after
   trimming spaces and ignoring capitals. "Rev C" and "C" differ.
2. A document's approved revision is its Approved register row.
3. A conflict is a line and document with two or more different,
   non-blank revisions among its requirement rows. Every such row is in
   it. Blank revisions never make a conflict. Do not compare lines. Count
   a conflict only if its rows are classed Conflicting calls; a document
   not in the register stays Not in register, with each call printed.
4. Sort each requirement row by the first rule that fits: doc_id not in
   the register, Not in register; in a conflict, Conflicting calls; two
   or more Approved rows, Two approved revisions; none, No approved
   revision; revision blank, Revision not called; revision equals the
   approved one, Matched; otherwise Called revision not approved, with
   the called revision's register status or "not in the register".
5. The seven classes must add up to the requirement rows. If not, stop
   and report the figures.
6. For each distinct line and material document among the material
   requirements: no material line, No material line supplied;
   allocated at least needed, Available; else allocated plus on order at
   least needed, On order, short on hand by the difference, with the
   days the expected date falls before, on or after the due date (or
   "expected date not given"); else Short by needed minus allocated
   minus on order. The four results must add up. Report certificates as
   on file, not on file or not stated, and tie them out. List material
   lines matching no requirement.
7. List each order line with no drawing requirement or no inspection
   requirement; a line missing both is printed once, as "no drawing or
   inspection requirement supplied".
8. Order sections by line, then type (drawing, specification,
   inspection, material), then document id; gaps in the class order of
   the format, and within each class by line, then type, then document
   id. Write one numbered decision per conflict, gap, material
   issue, certificate issue, unmatched material line and missing
   requirement, in that order, each a question with its facts.
   Recommend nothing unless asked.
9. Use the output format exactly, with "(none)" under an empty section.
   Prepared carries the check date. Print a material's title only if
   the document is in the register, and the expected-date clause only
   for On order lines. Write "1 day" or "[n] days", "1 requirement"
   or "[n] requirements", "1 conflict" or "[n] conflicts". A conflict
   counts once, however many sources call into it. Print no
   certificate sentence on a "No material line supplied" line. End with
   the Not proven line and the closing line: "Draft for the decision of
   the [production owner role] and the [quality owner role]. No
   drawing, revision, process or material has been approved, no job has
   been released, and no record has been changed."

If asked to say the job is ready, approve or pick a revision, release
the order, edit the register or the order, judge whether a drawing or
specification is right, or compare two revisions, decline and name the
role that does it. Never adjust a figure to make it tie. If the inputs
contain a password, a login code or personal details beyond a name and
role, do not repeat them; tell the user to remove them.
```

## What to customize

- The files and column names your orders, requirements, register and material lines use, and how revisions are written.
- Which requirement types your orders carry, which sources count, and whether specifications or materials must also be present on every line.
- The production owner and quality owner roles, and who may change the register or the order.
- The unit for each material, and whether a partial allocation or a delivery after the due date needs a different rule.
- Whether a document called at different revisions on different lines should be reported. As written it is not compared.
- Whether a Draft revision called on the order should be reported separately from a Superseded one. As written both are Called revision not approved, with the status shown.
- Whether a missing specification or material requirement should be listed as a gap, as a missing drawing or inspection requirement is.
- Which files the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Tried once on its invented example; changed after an independent review the same day and not run again (see `public/trial.md`). Not yet tested in a client environment.
