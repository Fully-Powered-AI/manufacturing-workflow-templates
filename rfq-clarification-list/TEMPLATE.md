# RFQ clarification list

Capability template, version 0.1.0.

## Purpose

Prepare, for one request for quotation, the list of what is missing, what conflicts and what is ambiguous in its package of lines, drawings and specifications, and keep the record of what each supplier answers. The list has three kinds of item: missing details, conflicts between documents (revisions, materials, specification revisions) and tolerances that cannot be read as written. Every item has a fixed identifier, an owner who can settle it and a status. The assistant prepares the list and drafts the messages. It never sends one, never decides which document is right, never interprets or converts a tolerance, never accepts a supplier's assumption, and never closes an item. The buyer approves every message to a supplier and the responsible engineer settles every technical conflict.

## When to use it and when not to

Use it when the package for a request is assembled and before it goes out, so the gaps are closed first. Use it again while suppliers are pricing, each time a supplier answers or an engineer rules.

Do not use it:

- to compare quotes, which is a different piece of work: this one stops at what suppliers say about the request, and any price in an answer is left unread;
- to raise a problem with a supplier over an order already placed, such as a short delivery or a wrong invoice;
- to decide what a tolerance means, whether a drawing is right, or which revision governs. Those are the engineer's;
- to answer questions about the terms and conditions in the request. The reviewer of commercial terms answers those;
- when the package has no drawings or specifications to read, because the assistant then has nothing to check a line against.

## Roles

- **Runs it:** the buyer or purchasing lead.
- **Approves and sends every message to a supplier, records what was sent, supplies missing values, closes items:** the buyer.
- **Settles every conflict and every tolerance item, and rules on a supplier's volunteered assumption:** the responsible engineer, named at the start for each drawing or specification family.
- **Answer the questions:** the suppliers, who are never told about each other.
- **Reviews commercial terms:** whoever the company names. The assistant takes no part.

## Inputs

1. **The request lines.** Default column headers: `Line`, `Part number`, `Description`, `Revision`, `Quantity`, `Unit`, `Material`, `Finish`, `Delivery date`, `Drawing`. If a header does not match, stop and ask the buyer to map it. Never guess which column is which. A blank cell is a blank, never zero.
2. **The request's cover details:** reference, issue date, quote due date, delivery location, currency, how long a quote must stand, certificate or inspection requirements, the suppliers, the buyer and the responsible engineer. If a cover item is blank, it is a missing detail. If the lines or the reference are missing, stop.
3. **The document register.** Default column headers: `Document`, `Title`, `Revision`, `Date`, `Used by lines`. If it is missing, stop, because revisions cannot be checked without it. If a header does not match, stop and ask.
4. **The text of each drawing:** title block, notes and every stated tolerance, typed or pasted in. If a drawing arrives only as an image or scan the assistant cannot read, ask for its title block, notes and tolerances as text. For a line whose drawing text is not supplied, run only the checks that need the lines and the register, and list the line under "Needs a person". A specification's text is not needed: the only check on a specification is the revision a drawing cites against the revision in the register, so a specification whose text is not supplied is not listed under "Needs a person".
5. **The buyer's notes, with dates:** messages already sent (which suppliers, which items, on what date), values the buyer has confirmed, and anything else relevant. If none, write "no messages recorded".
6. **The engineer's rulings,** each in the engineer's own words with the date and the identifier it settles. If none, every conflict and tolerance item is "Waiting for the engineer".
7. **Supplier answers.** Default column headers: `Date received`, `Supplier`, `Item ID`, `Answer`. Keep the supplier's words. If a header does not match, stop and ask. An answer whose item ID is not on the list is reported as unmatched, never added as an item.
8. **Settings:** today's date, the working days of the week, closed dates, the reply period in working days (default three) and the required details (the defaults are in step 2 of the procedure).

The assistant works from what it is given. It needs no connection to any system and never asks for a password or a login code.

## The procedure

1. **Read the package.** Confirm the headers match. Build the map of every line to its drawing and every drawing to its register entry. A line whose drawing is not in the register gets item `DRW`. Stop if the headers do not match or the lines, the register or the reference are missing.
2. **Missing details.** One item for each blank required detail. Required details by default:
   - on every line: part number (`PN`), revision (`REV`), quantity (`QTY`), unit (`UNT`), material (`MAT`), finish (`FIN`), delivery date (`DEL`), drawing reference (`DRW`);
   - on the request: quote due date (`RFQ-DUE`), delivery location (`RFQ-LOC`), currency (`RFQ-CUR`), how long a quote must stand (`RFQ-VAL`), certificate or inspection requirements (`RFQ-CERT`).

   Where the line is blank and the drawing states the value, record both ("request blank; drawing note says ..."), but do not fill the gap. A drawing's value is evidence, not an answer.

   A cover detail that is not blank counts as stated, however little it says: "Material certificates required." is stated and raises no item, and the assistant does not judge whether it is enough.
3. **Conflicts.** Compare the request with the register and the drawing text, and the documents with each other. One item for each case:
   - the revision on the line differs from the revision in the register or on the drawing's title block (`REV`);
   - material or thickness on the line differs from the drawing (`MAT`);
   - finish on the line differs from the drawing (`FIN`);
   - a quantity on the line differs from a quantity on the drawing or its notes (`QTY`);
   - a drawing cites a specification at one revision and the register holds another (`SPEC`);
   - two documents give the same attribute different values in any other way (`OTH`).

   Quote each statement exactly, with the document and where on it: two statements, or three where the request line, the register and the title block all state it. Never say which is right. A higher revision or a later date is not evidence of which governs.
4. **Tolerances.** Raise an item (`TOL1`, `TOL2` and so on, in the order met on the line) for each tolerance that cannot be read as written. Kind (a) is one item for each drawing, quoting every dimension on it that has no tolerance; kinds (b), (c) and (d) are one item for each feature or statement:
   - **(a) None stated:** a dimension has no tolerance and the drawing has no general tolerance note;
   - **(b) Stated twice:** the same feature has two different tolerances on one or more documents;
   - **(c) Words only:** the requirement is in words (for example "close fit", "flat", "smooth") with no value;
   - **(d) Incomplete:** a value lacks a unit, a datum or a direction, and the document sets no default.

   Quote the text exactly and say which of (a) to (d) applies. Never convert units, never state what the tolerance probably means, never compare it with a standard.
5. **Identifiers.** Each item is `L<line>-<code>` (for example `L3-QTY`, `L1-TOL1`) or, for a request-level detail, the `RFQ-` code. Where the same code repeats on one line, add `-2`, `-3`. The same item keeps the same identifier on every later run. Within each section, list the request-level items first, in the order of step 2, then the line items by line number and, within one line, in the order the checks are listed in steps 2 to 4.
6. **Why it matters.** Print the fixed phrase for the code, and never write a free reading of its effect:
   - `PN`: the part cannot be named in the quote;
   - `REV`: the supplier may price a different revision;
   - `QTY`: there is no quantity to price;
   - `UNT`: the quantity cannot be read;
   - `MAT`: material and thickness set the price;
   - `FIN`: the finish sets the price and the process route;
   - `DEL`: there is no date to plan against;
   - `DRW`: there is no drawing to quote from;
   - `SPEC`: the supplier may work to a different revision of the specification;
   - `OTH`: the two documents cannot both be met;
   - `RFQ-DUE`: suppliers do not know when to reply;
   - `RFQ-LOC`: freight cannot be priced;
   - `RFQ-CUR`: quotes in different currencies cannot be set side by side;
   - `RFQ-VAL`: the buyer cannot tell how long a price stands;
   - `RFQ-CERT`: the cost of paperwork and inspection cannot be priced;
   - `TOL` kind (a): the supplier has to guess how closely to make it; (b): the supplier cannot meet both; (c): the requirement cannot be measured; (d): the supplier has to guess the meaning.
7. **Who settles it, and status.** Missing details are settled by the buyer, who supplies the value. Conflicts and tolerance items are settled by the responsible engineer. Status is one of: `Waiting for the buyer's value`; `Waiting for the engineer`; `Settled by the engineer (note of [date])`, used only when the engineer's ruling was supplied for that identifier; `Closed by the buyer (note of [date])`, used only when the buyer said so. A supplier's answer, however clear, never changes a status to settled or closed.
8. **Messages and the record of answers.**
   - From the buyer's notes, list each message already sent: date, suppliers, items. The reply date is the send date plus the reply period in working days.
   - Record each supplier answer against its identifier with the date, in the supplier's words, and add a reading: `answers the question asked` (for a question that asked the supplier to state an assumption, the assumption is the answer), `differs from [Supplier]` (added when another supplier has given a different answer to the same question) or `volunteered, not asked`. A reading never judges whether the answer is right. Where two readings apply to one answer, join them with a semicolon on the same line.
   - An answer that gives a tolerance, a revision, a substitute material or a changed scope is recorded in the supplier's words, never as a ruling, and the item stays with the engineer.
   - An answer that contains a price or a delivery promise is recorded for the clarification only; the rest is left unread.
   - After the reply date, list each supplier's unanswered items, by identifier.
9. **Draft message.** Draft one message for the buyer to approve, using only items that are ready:
   - an **addendum** line for each item settled by the engineer or closed by the buyer, stated as the ruling or value was given;
   - a **question** line for each missing detail not yet put to suppliers, ending with the item identifier in brackets. For a line detail: "Please state what you have assumed for [field] on line [n], or tell us you cannot quote it without it ([ID])". For a request detail: "Please state what you have assumed for [field] on the request, or tell us you cannot quote it without it ([ID])";
   - a **reminder** line, per supplier, for each sent item still unanswered after the reply date, in the same words with "Please still state" in place of "Please state".

   Never include a conflict or a tolerance item that the engineer has not settled. Never name a supplier to another, never pass on another supplier's answer, and never state a price or a promise. Write the message plainly and neutrally. Mark it "Draft, not sent". The reply date is given as the rule and one worked example: "[n] working days after the day the buyer sends it" (three unless the settings say otherwise), then "If sent today ([today's date]), that is [date]". The assistant never assumes a send date.
10. **Time and hand-off.** State the quote due date and the working days left from today to it, counting the due date and not today. State how many items are not settled or closed. Do not recommend extending the date. List under "Needs a person" any line without drawing text, any unmatched answer and anything the assistant could not read.
11. **Return** the list to the buyer only. The buyer decides whether to forward the engineer's sections.

## Exceptions and stop conditions

- **Headers do not match, or the lines, the register or the reference are missing:** stop and say exactly what is missing or which header does not match.
- **A drawing is an image the assistant cannot read:** ask for its text; check nothing against it until it arrives.
- **An answer's item ID is not on the list:** report it as unmatched; do not make an item of it.
- **A supplier's answer would settle a conflict or a tolerance** (for example "we will quote Rev D"): record it in the supplier's words and leave the item with the engineer.
- **A message would name or quote another supplier:** remove the reference.
- **The engineer's ruling is ambiguous, or conflicts with another ruling:** record both and put the item under "Needs a person"; do not choose.
- **Asked to decide a revision, a tolerance or a substitute material, to say which document governs, to answer a question about commercial terms, to send a message, or to close an item without the buyer's word:** decline and say whose decision it is.

## Output format

```
RFQ CLARIFICATION LIST: [RFQ reference]

For: [Buyer], with [responsible engineer]. Run on [date]. Quote due [date] ([n] working days left). Suppliers: [list].
Package read: [n] lines; [n] documents in the register; drawing text read for [n] of [n] drawings.

Summary: [n] items. Waiting for the buyer's value: [n]. Waiting for the engineer: [n]. Settled by the engineer: [n]. Closed by the buyer: [n].

1. Missing details
[ID] [Line n, part number, or Request]: [what is blank]. [What other documents show, quoted, or "No other document states it".] Why it matters: [fixed phrase]. Settled by: the buyer. Status: [status].
[If none: "None found."]

2. Conflicts between documents (for the responsible engineer)
[ID] Line [n]: [document, where] says "[exact text]"; [document, where] says "[exact text]"[; and [document, where] says "[exact text]"]. Why it matters: [fixed phrase]. Settled by: the responsible engineer. Status: [status].
[If none: "None found."]

3. Ambiguous tolerances (for the responsible engineer)
[ID] Line [n], [document, where]: "[exact text]". Kind: [(a) none stated / (b) stated twice / (c) words only / (d) incomplete]. Why it matters: [fixed phrase]. Settled by: the responsible engineer. Status: [status].
[If none: "None found."]

4. Supplier answers record
Messages sent, as the buyer reported: [message, date, suppliers, items, reply date].
[ID], [Supplier], [date]: "[answer]". Reading: [reading][; second reading, if two apply].
Unprompted statements: [ID], [Supplier], [date]: "[statement]". Reading: volunteered, not asked.
Unanswered past the reply date: [Supplier]: [IDs].
[If nothing recorded: "No messages sent and no answers recorded."]

5. Draft message (not sent; the buyer approves and sends)
To: [suppliers], sent separately. Subject: [reference] clarification [n].
Addenda: [line, as the ruling or value was given].
Please state: [question lines, each ending with its identifier].
Reminders (each supplier receives only its own): [Supplier]: [reminder lines, each ending with its identifier].
Reply by: [n] working days after the day the buyer sends it. If sent today ([today's date]), that is [date].
[If nothing is ready: "No message is ready."]

6. Needs a person
[Lines without drawing text, unmatched answers, ambiguous rulings, anything unread.]
[If none: "Nothing."]

Every item traces to the request lines and cover details, the document register, the drawing text, the buyer's notes, the engineer's rulings and the supplier answers supplied. The list changes no record, interprets no tolerance and sends nothing.
```

The closing line may name the reference and the documents in place of the generic names (for example "the lines and cover details of RFQ-2611-04, the register of 5 documents"); its last sentence is fixed.

## Reviewer checklist

1. Every blank required detail has an item, and no item invents a gap. (Buyer)
2. Every quotation from a document is exact and names where it is. (Buyer)
3. No item says which document is right, and no tolerance is converted or explained. (Responsible engineer)
4. Every "Settled by the engineer" status has the engineer's note behind it. (Responsible engineer)
5. Each supplier answer sits against the right identifier, with the right reading. (Buyer)
6. The draft message contains no unsettled conflict or tolerance, no supplier's name or answer other than the recipient's, and no price. (Buyer)
7. Reply dates and working days left are counted correctly. (Buyer)
8. The summary counts add up to the number of items. (Buyer)

## Acceptance tests

Proposed tests. None has been run.

1. **Blank quantity.** A line with no quantity. Expected: item `L<n>-QTY`, status "Waiting for the buyer's value", no quantity invented.
2. **Revision conflict.** The line says revision C and the register says D. Expected: an `L<n>-REV` item quoting both, sent to the engineer, with no statement that D governs.
3. **Header mismatch.** The line export has `Qty` in place of `Quantity`. Expected: stop and ask for the mapping.
4. **Tolerance stated twice.** One feature at ±0.05 in a view and ±0.1 in a note. Expected: a tolerance item of kind (b) with both texts quoted and no view taken.
5. **Words only.** "Close running fit". Expected: a tolerance item of kind (c), no value suggested.
6. **Supplier volunteers a tolerance.** Expected: recorded in the supplier's words as "volunteered, not asked"; the item stays with the engineer.
7. **Two suppliers assume different things.** Expected: both answers shown, each reading "differs from" the other, and the item waiting for the buyer.
8. **Unsettled conflict in the draft message.** Expected: absent from the message, present in section 2.
9. **Scanned drawing.** Expected: a request for the text, and the line listed under "Needs a person".
10. **Asked to say which revision governs.** Expected: declined, with the engineer named.

## Instructions for the AI assistant

```
You prepare the clarification list for one request for quotation, for the
buyer. You never send a message, decide which document is right,
interpret or convert a tolerance, accept a supplier's assumption, or
close an item. A person approves anything that goes to a supplier. You
need no password or login code and never take one.

The buyer will supply: the request lines (columns Line, Part number,
Description, Revision, Quantity, Unit, Material, Finish, Delivery date,
Drawing); the cover details; the document register (Document, Title,
Revision, Date, Used by lines); the text of each drawing; dated notes;
the engineer's rulings; supplier answers (Date received, Supplier, Item
ID, Answer); and settings: today's date, working days, closed dates and
the reply period in working days (three if not given). If a header does
not match, or the lines, register or reference are missing, stop and say
what is missing. If a drawing is an image you cannot read, ask for its
text. A specification's text is not needed: only its revision in the
register is checked. For a line whose drawing text is not supplied, run
only the checks that need the lines and the register, and list the line
under Needs a person. A line whose drawing is not in the register gets
item DRW.

1. Missing details: one item for each blank required detail. On every
   line: part number (PN), revision (REV), quantity (QTY), unit (UNT),
   material (MAT), finish (FIN), delivery date (DEL), drawing (DRW). On
   the request: due date (RFQ-DUE), delivery location (RFQ-LOC),
   currency (RFQ-CUR), quote validity (RFQ-VAL), certificate or
   inspection requirements (RFQ-CERT). A cover detail that is not blank
   counts as stated, however little it says. If the drawing states a
   blank value, quote it as evidence; do not fill the gap.
2. Conflicts: revision on the line against the register and title block
   (REV); material or thickness (MAT); finish (FIN); quantity (QTY); a
   specification cited at a different revision from the register
   (SPEC); any other disagreement (OTH). Quote each statement exactly
   with its location: two, or three where the line, the register and
   the title block all state it. Never say which is right. A later
   revision or date is not evidence.
3. Tolerances: items TOL1, TOL2 and so on, in the order met on the line,
   for each that cannot be read as written: (a) none stated, where the
   drawing has no general tolerance note: one item for each drawing,
   quoting every dimension on it without a tolerance; (b) stated twice,
   the same feature with two different tolerances; (c) words only, a
   requirement in words with no value; (d) incomplete, a value lacking
   a unit, a datum or a direction with no default set: one item for each
   feature or statement. Quote the text exactly. Never convert, explain
   or compare it.
4. Identifiers: L<line>-<code> or RFQ-<code>, the same on every run; add
   -2, -3 where a code repeats on one line. Within each section, list
   request items first, in the order of step 1, then line items by line
   number and, within a line, in the order the checks are listed. Print
   the fixed phrase for the code and no other reading of its effect:
   PN, the part cannot be named in the quote; REV, the supplier may
   price a different revision; QTY, there is no quantity to price; UNT,
   the quantity cannot be read; MAT, material and thickness set the
   price; FIN, the finish sets the price and the process route; DEL,
   there is no date to plan against; DRW, there is no drawing to quote
   from; SPEC, the supplier may work to a different revision of the
   specification; OTH, the two documents cannot both be met; RFQ-DUE,
   suppliers do not know when to reply; RFQ-LOC, freight cannot be
   priced; RFQ-CUR, quotes in different currencies cannot be set side by
   side; RFQ-VAL, the buyer cannot tell how long a price stands;
   RFQ-CERT, the cost of paperwork and inspection cannot be priced; TOL
   (a), the supplier has to guess how closely to make it; (b), the
   supplier cannot meet both; (c), the requirement cannot be measured;
   (d), the supplier has to guess the meaning.
5. Status: Waiting for the buyer's value; Waiting for the engineer;
   Settled by the engineer (note of [date]); Closed by the buyer (note
   of [date]). Only the buyer's value, the engineer's note or the
   buyer's closing note changes a status. A supplier's answer never does.
6. Record each supplier answer against its Item ID in the supplier's own
   words, with a reading: answers the question asked, differs from
   [Supplier], or volunteered, not asked; join two readings with a
   semicolon. Report unmatched IDs. Leave
   prices and promises unread. A message's reply date is its send date
   plus the reply period in working days. After the reply date list each
   supplier's unanswered items.
7. Draft one message of addenda (settled items), questions (missing
   details not yet put) and per-supplier reminders. A question is
   "Please state what you have assumed for [field] on line [n], or tell
   us you cannot quote it without it ([ID])", or "... for [field] on
   the request ..." for a request detail. A reminder is the same with
   "Please still state". Leave out every unsettled conflict and
   tolerance, every price, and every other supplier's name or answer.
   Mark it Draft, not sent. Its Reply by line gives the rule, the reply
   period in working days after the day the buyer sends it, and then "If
   sent today ([today's date]), that is [date]". Never assume a send
   date.
8. State the working days left to the quote due date, counting the due
   date and not today. Do not recommend extending it. List under Needs a
   person anything unread or unmatched.

Use the output format exactly, with its six sections in order: 1 Missing
details, 2 Conflicts between documents, 3 Ambiguous tolerances, 4
Supplier answers record, 5 Draft message, 6 Needs a person. Where a
section is empty, print "None found." (sections 1 to 3), "No messages
sent and no answers recorded." (4), "No message is ready." (5) or
"Nothing." (6). End with the trace line: Every item traces to the
request lines and cover details, the document register, the drawing
text, the buyer's notes, the engineer's rulings and the supplier answers
supplied (you may name the reference and the documents in place of the
generic names). The list changes no record, interprets no tolerance and
sends nothing. Decline requests to decide a revision or tolerance, to answer
questions about commercial terms, to send, or to close an item without
the buyer's word.
```

## What to customize

- The required details for every line and for the request.
- The reply period, the working days and the closed dates.
- The column headers of your request export and document register.
- The engineer who settles each drawing or specification family, and whether quality or production also rules on some items.
- The status words and the identifier codes, if your team already uses its own.
- The message wording, the sign-off, and whether suppliers get one message or separate ones.
- Who reviews questions about commercial terms.
- Which files the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Editorially reviewed. Tried once on its invented example in Claude on 10 November 2026; the record is published with the template. Edited after that run, following an independent review, and not run again; the trial record lists the edits. Each settles an ambiguity the run found, in the way that run already chose except where the trial record says otherwise. Not yet tested in a client environment.
