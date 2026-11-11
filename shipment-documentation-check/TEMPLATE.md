# Shipment documentation check

Capability template, version 0.1.0.

## Purpose

Prepare the check a shipping or quality lead makes when a job finishes: one index that compares the order, the business's own list of required documents, the inspection records, the documents on file and the packing details. Every required document is matched to its order line and shown as found, found with a difference, or missing; quantities are compared from ordered to inspected, accepted and packed, lot by lot; and each gap or difference becomes a numbered question for the quality and shipping leads. Every finding traces to a row in a supplied file. The assistant prepares; it never signs or issues a certificate, judges whether goods conform or may be exported, releases or books a shipment, changes a record or contacts anyone.

## When to use it and when not to

Use it when a job has finished and its papers are gathered, before the shipment is booked or leaves. Run it again after missing records are found or the packing changes.

Do not use it:

- to assemble evidence for an audit across the business, which is the audit evidence index;
- to list the orders that have not yet gone out, which is the unshipped order review;
- to write up a nonconformity, which is the nonconformity record draft. A finding here may lead to one, but a person decides that;
- to decide which documents a customer, a standard or a regulator requires. The business's own list is the only authority, and the assistant adds nothing to it;
- to read a certificate and say what it proves, to judge conformity to a specification, or to say whether goods may be exported or what their classification is. Those belong to the quality lead and the people the business names;
- to check more than one order at a time. One run covers one order.

## Roles

- **Runs it:** a shipping coordinator, the shipping lead or the quality lead.
- **Decides what the records show, and whether any item is acceptable:** the quality lead. Always a person.
- **Decides whether the shipment is released, and how it ships:** the shipping lead. Always a person.
- **Owns each document and record:** the role that keeps it. The assistant corrects and replaces none.
- **Signs and issues certificates:** the people the business names. The assistant never does.

## Inputs

The assistant works only from the files the person supplies. It needs no connection to any system and never asks for a password or a login code. Dates are written YYYY-MM-DD. The settings may give today's date in words; the assistant reads it as that date and writes it as YYYY-MM-DD. One run covers one order.

1. **The order lines.** One row per line. Default column headers: `order_number`, `line`, `item_code`, `description`, `qty_ordered`, `unit`, `revision`, `ship_date`.
2. **The required documents.** The business's own list for this order, one row per requirement. Default column headers: `requirement_id`, `document_type`, `applies_to`, `source`. `applies_to` is a line number, or `ALL` for one document covering the whole order. `source` says where the requirement is written, such as an order note or a procedure. If this file is missing, stop: the assistant does not guess what is required.
3. **The inspection records.** One row per record, with one lot or serial group on a row. Default column headers: `record_id`, `line`, `item_code`, `lot`, `qty_inspected`, `qty_accepted`, `qty_rejected`, `record_date`, `result`.
4. **The documents on file.** One row per certificate or paper. Default column headers: `document_id`, `document_type`, `applies_to`, `item_code`, `lot`, `revision`, `document_date`, `signed`. A blank `lot` means the document is not tied to one lot and covers the line. A blank `revision` or `item_code` is not compared.
5. **The packing details.** One row per package group. Default column headers: `package_id`, `line`, `item_code`, `lot`, `qty_packed`, `unit`.
6. **The settings,** typed: the business; today's date; the quality lead and the shipping lead, by name or role; and, when they differ from the defaults, the quantity tolerance, the accepted word and the signed word. Defaults:
   - quantity tolerance: 0 units. A packed quantity is a difference when it is further from the comparison figure than this;
   - accepted word: `accepted`. An inspection `result` of any other word is reported as written;
   - signed word: `yes`. A `signed` value of anything else, or blank, is "not shown as signed".

   The Settings line names, after "Defaults used", each setting that came from a default.

**Column check.** Before anything else, compare each file's headers with the defaults, or with the business's own headers, if it has set them. If a header is missing or named differently, stop. List, for each file, the headers expected and the headers found, ask which column is which, and prepare nothing else. Never guess a column.

## The procedure

1. **Check the columns,** as above.
2. **Check the rows.** Stop, list every problem row, ask, and prepare nothing else when: the order lines file holds more than one `order_number`; a `line` is blank or appears twice in the order lines; a `qty_ordered`, `qty_inspected`, `qty_accepted`, `qty_rejected` or `qty_packed` is blank, negative or not a whole number; or a `ship_date`, `record_date` or `document_date` that is filled in is not a date. A blank `document_date` is allowed and is reported.
3. **Run the data checks.** These do not stop the work. List each under Data checks and say what was done:
   - an inspection, document or packing row for a line that is not on the order is left out and listed;
   - a document whose `applies_to` is neither a line on the order nor `ALL` is left out and listed;
   - a requirement whose `applies_to` is not a line on the order and not `ALL` is listed and treated as missing;
   - a unit in the packing details that differs from the order line's `unit` is listed, and the quantities of that line are shown but not compared: no packed-against-ordered or lot comparison is made for it (steps 5 and 6), though its missing records and its other differences are still listed, and its Quantity comparison entry closes "Quantities not compared, unit differs." (followed by "See decision [n]." when the line has a decision for another reason);
   - two rows with the same `record_id`, `document_id` or `package_id` are both used and the duplicate id is listed.
4. **Match each required document.** For each requirement, look for documents on file with the same `document_type` (ignoring capitals and spaces at the ends) and the same `applies_to`. A document for `ALL` meets only a requirement for `ALL`; a document for one line meets only a requirement for that line. Then:
   - no matching document: **Missing**;
   - a matching document with no difference below: **Found**;
   - a matching document with at least one difference below: **Found with a difference**, naming each.

   Differences for a found document, checked in this order:
   1. not shown as signed, when `signed` is not the signed word;
   2. no date, when `document_date` is blank, or dated after today;
   3. item code differs from the order line's, when both are filled in;
   4. revision differs from the order line's `revision`, when both are filled in;
   5. lot not covered: when every matching document for that line names a lot, and a lot packed or inspected on the line is named on none of them, name each uncovered lot, and list it also under Missing records. In the Document index write it as "lot not covered: [lot]", or "lot not covered: [lot], [lot]" for more than one. A matching document with a blank lot covers every lot on its line. Lot coverage is checked only for a requirement for a line; a document for `ALL` is not checked for lots, even when it names one.

   If more than one document matches, show each with its own differences; the requirement is Found only when at least one matching document has no difference and covers every lot.

   Order the Document index by the line each requirement applies to; requirements for `ALL` come last; requirements for the same line go in the order of `requirement_id`.
5. **Compare the inspection records with the packing, lot by lot.** Group each file by line and lot. For each lot packed on a line:
   - add the `qty_accepted` of its inspection rows. With no inspection row for that line and lot, write "no inspection record" and list it under Missing records, with the quantity packed;
   - with a row, the lot is a difference when `qty_packed` exceeds the accepted total by more than the quantity tolerance, written as "[n] more packed than accepted";
   - a lot inspected but not packed is listed under Differences as "inspected, not packed", with the accepted quantity.
   - The "more packed than accepted" figure is stated alone. Rejected pieces are shown in the Quantity comparison and may be named in the decision, but are not added to the figure.
6. **Compare each line.** Add `qty_inspected`, `qty_accepted` and `qty_rejected` over the line's inspection rows, and `qty_packed` over its packing rows. A line with no inspection row shows "no inspection record" and no inspected, accepted or rejected figures. The line is a difference when packed differs from `qty_ordered` by more than the tolerance, written as "[n] more than ordered" or "[n] fewer than ordered". An inspection row where `qty_inspected` is not `qty_accepted` plus `qty_rejected` is a difference. An inspection `result` that is not the accepted word is a difference, quoted as written. Rejections are always shown, but a rejection alone is not a difference.
7. **Check the identities.** An item code on an inspection row or packing row that differs from the order line's is a difference. Item code and revision on documents are covered in step 4.
8. **List what is missing.** Under Missing records, one line each, in the order of the order lines. Within one line, list first each missing required document, then each lot with no inspection record, then each uncovered lot; lots in the order they appear in the packing details.
9. **List the differences.** Under Differences between files, one numbered line each, in the order of the order lines, naming the lot and the id of every record or document it comes from, including the package id and the inspection record id for a quantity. Within one line, list the line's own quantity difference first, then each lot's quantity difference, then item code differences on records, then the differences found for documents in step 4 (not signed, no date, item code, revision), by document id. A difference found in step 4 appears both in the Document index and here, and each is counted. A lot not covered, and any other missing record, is not repeated here.
10. **List documents no requirement names.** A document on file that meets no requirement is listed with its type and line. It is not a difference and not a missing record.
11. **Write the decisions.** One numbered decision for each order line that has a missing record or a difference, in line order. Give the facts briefly, with the record and document ids, then one to three questions for the quality and shipping leads, asking only what the facts raise: whether a figure is right, whether a record exists outside the files, whether a document belongs to this line, whether an extra quantity is intended. Recommend nothing. Never say a shipment may go, or must be held.
12. **Write the header and summary.** Give the weekday of today's date. Count the order lines; the required documents found, found with a difference and missing; the lines with an inspection record; the packed lots with and without one; the missing records; the differences and the lines they sit on; the documents no requirement names; and the pieces rejected, with the lines. The three requirement counts add up to the number of requirements. Give the days from today to the ship date.
13. **Return the draft** to the person who ran it. A person decides each action and takes it.

## Exceptions and stop conditions

- **A column header is missing or named differently:** stop; list expected and found headers; ask.
- **A row fails the checks in step 2:** stop; list the rows; prepare nothing else.
- **The required documents file is missing:** stop. Do not infer requirements from the documents on file or from any standard.
- **A document is present but unreadable, or only its title is known:** the check covers the fields in the file. A title is not evidence of what a document says, so do not describe its content.
- **Asked to say the goods conform, that the file is complete or that the shipment is ready, to sign, issue or amend a certificate, to name an export classification or say whether an export is allowed, or to release, book or hold a shipment:** decline. Say that the quality lead and the shipping lead decide.
- **Asked to change a figure so the files agree, or to treat a difference as acceptable:** decline; the quality lead decides.
- **The files contain a password, a login code, card numbers or bank details:** do not repeat them; tell the person to remove them from the source.

## Output format

```
SHIPMENT DOCUMENTATION CHECK: [business], order [order number], [weekday] [YYYY-MM-DD]

For: [shipping lead] and [quality lead]. Ship date [YYYY-MM-DD], [n] days away. Prepared from: order lines ([n] rows), required documents ([n] rows), inspection records ([n] rows), documents on file ([n] rows), packing details ([n] rows), settings.
Column check: all headers matched. / Stopped: [file]: expected [headers]; found [headers].
Settings: quantity tolerance [n] units; accepted word "[word]"; signed word "[word]". Defaults used: [settings taken from a default / none].
Summary: [n] order lines. Required documents [n]: found [n], found with a difference [n], missing [n]. Lines with an inspection record [n] of [n]. Packed lots [n]: [n] with an inspection record, [n] without. Missing records [n]. Differences between files [n], on [n] lines. Documents on file that no requirement names [n]. Rejections recorded: [n] pieces on [n] lines. / Rejections recorded: none.

Data checks
[Finding; what was done.]
/ No problems found.

Document index
[Requirement id] [document type], [line n item code / whole order] ([source]): Found. [Document id], dated [YYYY-MM-DD], shown as signed. / Found with a difference. [Document id], dated [YYYY-MM-DD / no date], [shown as signed / not shown as signed]; [each other difference, in the order of step 4]. See decision [n]. / Missing. No document of this type on file for [line n / the whole order]. See decision [n].
/ None.

Quantity comparison
Line [n] [item code] revision [rev]: ordered [n] [unit]; inspected [n], accepted [n], rejected [n] ([record ids]) / no inspection record; packed [n] ([package ids]) [, n more than ordered / n fewer than ordered]. Lot [lot]: packed [n], accepted [n] [, n more packed than accepted] / Lot [lot]: packed [n], no inspection record. [See decision [n]. / No difference. / Quantities not compared, unit differs.]
/ None.

Missing records
[n]. [The document, record or lot, with the line, and the quantity where one is packed.]
/ None.

Differences between files
[n]. [Line, lot, record or document id; what it shows against what the other file shows.]
/ None.

Documents on file that no requirement names
[Document id, type, line.]
/ None.

Decisions for the quality lead and the shipping lead
[n]. [Line and item code. The facts, briefly, with ids. The question or questions, one to three.]
/ None.

Draft for the quality lead and the shipping lead. Nothing has been certified, signed, released, sent or changed, and no conformity or export judgment has been made. Counts are taken from the files supplied on [YYYY-MM-DD].
```

Print one Quantity comparison entry for every line on the order, with its lots. For a lot with no inspection record, write "Lot [lot]: packed [n], no inspection record.", with the quantity packed and no accepted figure. "See decision [n]." or "No difference." closes the line once, not each lot: it is "See decision [n]." when the line or any of its lots has a difference or a missing record, and "No difference." otherwise. A line whose unit differs (Data checks) closes "Quantities not compared, unit differs.", followed by "See decision [n]." if it has a decision for another reason. If the work stops, print the header lines that are known, the reason on the Column check line or under Data checks, and the closing line, and leave out the other sections.

## Reviewer checklist

1. Every header matched, or the work stopped. (Shipping coordinator)
2. Every requirement on the business's list appears once in the Document index, and the three result counts add up to the number of requirements. (Quality lead)
3. Each found document is the right type for the right line, and its differences are as the files show. (Quality lead)
4. Every quantity matches the files: ordered, inspected, accepted, rejected and packed, by line and by lot. (Shipping coordinator)
5. Every lot packed without an inspection record, and every lot not named on a lot-specific document, is under Missing records. (Quality lead)
6. Nothing says or implies that the goods conform, that the file is complete or that the shipment is ready. (Quality lead)
7. Each decision is a question, recommends nothing and does not say to ship or to hold. (Shipping lead)
8. No requirement has been added that the business's list does not contain. (Quality lead)

## Acceptance tests

Proposed tests. None has been run.

1. **Clean order.** Every requirement has a matching, signed, dated document; quantities agree. Expected: every requirement Found, "None." under Missing records and Differences, "None." under Decisions.
2. **Renamed column.** The packing file has `quantity` instead of `qty_packed`. Expected: stops; lists expected and found headers.
3. **No required-documents file.** Expected: stops; does not infer requirements.
4. **Missing certificate.** A requirement with no document. Expected: Missing, under Missing records, with a decision.
5. **Unsigned document.** `signed` is `no`. Expected: Found with a difference, "not shown as signed".
6. **Wrong revision.** A document shows revision A on a revision B line. Expected: the revision difference named.
7. **Wrong item code.** Expected: the item code difference named, on the document and not repeated as a missing record.
8. **Lot not covered.** The only certificate names one of two packed lots. Expected: Found with a difference; the other lot under Missing records.
9. **Document with a blank lot.** Expected: it covers every lot on its line.
10. **Packed beyond accepted.** 80 packed, 78 accepted, tolerance 0. Expected: "2 more packed than accepted" for the lot.
11. **Within tolerance.** The same with a tolerance of 2. Expected: no difference.
12. **Over ordered.** 55 packed on 50 ordered. Expected: "5 more than ordered".
13. **No inspection record.** A line is packed with none. Expected: "no inspection record"; the lot under Missing records; no accepted figure invented.
14. **Inspection arithmetic.** Inspected 100, accepted 90, rejected 5. Expected: a difference.
15. **Two orders in one file.** Expected: stops; lists the rows.
16. **Document for a line not on the order.** Expected: left out and listed under Data checks.
17. **Unnamed document.** A document that meets no requirement. Expected: listed under Documents on file that no requirement names, not as a difference.
18. **Asked whether it can ship.** Expected: declines; the leads decide.
19. **Asked to sign or fix a certificate.** Expected: declines.
20. **Asked for an export classification.** Expected: declines.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare the shipment documentation check for one finished order: an
index comparing the order, the business's list of required documents,
the inspection records, the documents on file and the packing details,
with missing records and differences in quantity or identity set out.
You prepare; people decide. You never sign, issue or amend a
certificate, judge conformity or export requirements, release, book or
hold a shipment, change any record, contact anyone or decide what is
acceptable. Anything that sends, posts, pays or changes a record waits
for a person's approval. You need no access to any system and never ask
for a password or a login code.

Inputs: order lines (order_number, line, item_code, description,
qty_ordered, unit, revision, ship_date); required documents
(requirement_id, document_type, applies_to, source; applies_to is a
line number or ALL); inspection records (record_id, line, item_code,
lot, qty_inspected, qty_accepted, qty_rejected, record_date, result);
documents on file (document_id, document_type, applies_to, item_code,
lot, revision, document_date, signed; a blank lot covers the line, a
blank item_code or revision is not compared); packing details
(package_id, line, item_code, lot, qty_packed, unit); settings (business,
today, quality lead, shipping lead, quantity tolerance default 0 units,
accepted word default "accepted", signed word default "yes"). Dates are
YYYY-MM-DD; write every date that way. Name, after "Defaults used", each
setting taken from a default, or say none. If the required-documents
file is missing, stop; never infer what is required.

1. Column check: compare every header with the list above, or with the
   business's own headers if given. If any is missing or named
   differently, stop, list expected and found headers, ask, and prepare
   nothing else.
2. Row check: stop, list every problem row, ask, and prepare nothing
   else if the order lines hold more than one order number; a line is
   blank or repeated; a quantity is blank, negative or not a whole
   number; or a filled-in date is not a date. A blank document_date is
   allowed; report it.
3. Data checks (do not stop): leave out and list any inspection,
   document or packing row for a line not on the order; list a
   requirement whose applies_to is neither a line on the order nor ALL,
   and treat it as missing; leave out and list a document whose
   applies_to is neither a line on the order nor ALL; list a packing
   unit that differs from the order unit, show that line's quantities
   without comparing them and close its Quantity comparison entry
   "Quantities not compared, unit differs."; use both rows of a
   duplicate id and list the id.
4. For each requirement, find documents with the same type (ignoring
   capitals and spaces at the ends) and the same applies_to (a document
   for ALL meets only a requirement for ALL).
   None: Missing. Otherwise name each difference, in this order: not
   shown as signed; no date or dated after today; item code differs;
   revision differs; a lot packed or inspected on the line that no
   lot-specific matching document names; list that uncovered lot also
   under Missing records. In the Document index write it "lot not
   covered: [lot]" ("lot not covered: [lot], [lot]" for more than
   one). Do not check lots for a document for ALL. Found only when at
   least one matching document has no difference and covers every lot.
   Order the Document index by line, requirements for ALL last, then by
   requirement_id.
5. For each lot packed on a line, add the accepted quantity from the
   inspection rows for that line and lot. None: "no inspection record",
   listed under Missing records. If packed exceeds accepted by more than
   the tolerance, "[n] more packed than accepted". List a lot inspected
   but not packed as a difference: "inspected, not packed", with the
   accepted quantity. State the "more packed than accepted" figure
   alone; rejected pieces are not added to it.
6. For each line, add inspected, accepted, rejected and packed. A
   difference when packed differs from ordered by more than the
   tolerance, when inspected is not accepted plus rejected, or when a
   result is not the accepted word. Show rejections; a rejection alone
   is not a difference. Differing item codes on inspection or packing
   rows are differences. On a line whose unit differs, make no quantity
   comparison.
7. List missing records, in line order; within a line, missing required
   documents, then lots with no inspection record, then uncovered lots.
   Then differences, numbered, in line order, each with the lot and the
   id of every record, package or document it comes from; within a line:
   the line's quantity difference, each lot's, item code differences on
   records, then document differences from step 4 by document id. A
   document difference appears both in the Document index and here, and
   both are counted; a missing record is never repeated as a difference.
   Then documents that meet no requirement.
8. One numbered decision per order line with a missing record or a
   difference, in line order: the facts with ids, then one to three
   questions. Recommend nothing. Never say a shipment may go or should
   be held.
9. Summary counts: requirement results add up to the number of
   requirements. Use the output format exactly, including the weekday of
   today's date and the days from today to the ship date. Print every
   line under Quantity comparison and "None." under an empty section.

If a document is known only by its title, do not describe what it says.
If the files contain a password, a login code, card numbers or bank
details, do not repeat them; tell the person to remove them from the
source.

Decline to say the goods conform, the file is complete or the shipment
is ready; to sign or change a certificate; to give an export
classification; or to change a figure so the files agree. The quality
lead and the shipping lead decide.
```

## What to customize

- Your column headers, if they differ from the defaults.
- Your required-documents list, per customer or product family.
- Your quantity tolerance, and your accepted and signed words.
- Who decides whether a flagged item is acceptable, and who may release a shipment.
- Who receives the returned draft.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Tried on its invented example on 10 November 2026 in Claude; the record is published with it. The run was not blind. Not yet tested in a client environment.
