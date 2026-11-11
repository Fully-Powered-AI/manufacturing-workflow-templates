# RFQ clarification list: one run on its invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in `public/example.md` (Quillfeather Assemblies, RFQ-2611-04, four lines, five documents, three suppliers). No client data was used. The run followed the instruction block and output format in the complete template. The model that ran it did not write the template, and read the example's output only after producing its own.

## Inputs used

Everything under "What the buyer supplies" in the example: the cover details, the four request lines, the document register, the typed drawing text, the buyer's note of 10 November, the engineer's ruling of 13 November, the six supplier answers, and the settings (today is Monday 16 November 2026, Monday to Friday working days, no closed dates, three working days to reply). The date above is the day of the run; the run itself used the example's invented date.

## What came out

The list had all six sections and the closing trace line. Substantial parts:

```
RFQ CLARIFICATION LIST: RFQ-2611-04
For: Priya, with Tomas. Run on 2026-11-16. Quote due 2026-11-20 (4 working days left). Suppliers: Supplier A, Supplier B, Supplier C.
Package read: 4 lines; 5 documents in the register; drawing text read for 4 of 4 drawings.
Summary: 10 items. Waiting for the buyer's value: 4. Waiting for the engineer: 5. Settled by the engineer: 1. Closed by the buyer: 0.

1. Missing details: L2-FIN (blank; QA-1043 note 1 says "Deburr and passivate."), L3-QTY, RFQ-CUR, RFQ-VAL. All "Waiting for the buyer's value".
2. Conflicts: L1-REV (line "C"; register and QA-1042 title block "D"), L4-MAT (line "2.5 mm"; QA-3305 "3 mm"), L4-SPEC (QA-3305 note 1 cites PS-07 rev 2; register holds revision 3; Settled by the engineer, note of 2026-11-13). The other two wait for the engineer.
3. Tolerances: L1-TOL1 kind (b) (60 ±0.05 in view 1, "Hole spacing ±0.1." in note 3); L2-TOL1 kind (a) (dimensions 75, 40 and 55 with no tolerance and no general note); L3-TOL1 kind (c) ("Bore to give a close running fit on shaft."). All wait for the engineer.
4. Supplier answers: clarification 1 sent 2026-11-10 to all three, items RFQ-CUR, RFQ-VAL, L2-FIN, L3-QTY, reply date 2026-11-13. RFQ-CUR "USD." (A) and "GBP." (B) each read "answers the question asked; differs from" the other. L3-QTY "Assumed 300 pieces." (A) and L2-FIN "Passivation assumed, per the drawing note." (B) answer the question asked. Volunteered, not asked: L1-REV (B, "Quoting to the drawing as attached, Rev D.") and L2-TOL1 (A, "We would apply ±0.1 to dimensions without a tolerance."). Unanswered: A: RFQ-VAL, L2-FIN. B: RFQ-VAL, L3-QTY. C: all four.
5. Draft message (Draft, not sent): addendum for L4-SPEC in the engineer's words; no new questions; reminders for each supplier's own unanswered items only; no conflict or tolerance other than L4-SPEC; no price.
6. Needs a person: PS-07 (see below).
```

Item counts, the four working days left and the reply date of 13 November all agree with the checks in the example.

## What was observed

- Every required part was produced. Nothing in the instructions told the run to stop: headers matched, and the lines, register and reference were present.
- The run reached the same ten items, the same identifiers, the same statuses and the same readings as the published example.
- No fact in either output is missing from the inputs, with one exception. The example's "Reply by" line says "Sent on 2026-11-16, that is 2026-11-19". The inputs do not say when the buyer will send the message. The run wrote only "three working days after the day the buyer sends it".

Differences from the published example:

- Order of the missing details: the run listed line items first and request items after; the example lists request items first. The template does not say which.
- The run listed the text of specification PS-07 under "Needs a person", because the register holds PS-07 but its text was not supplied. The example says "Nothing".
- The run counted the 4 of 4 as drawings only and said so; the example writes "4 of 4" without saying what is counted.
- The run quoted the engineer's ruling in full in the addendum; the example shortens it.
- The run left the reminder wording to the question wording in the template; the example words the reminders as "please still state".

Where the template was ambiguous and the run had to guess:

- Whether a tolerance item is one per drawing or one per dimension. Three dimensions on QA-1043 have no tolerance. The run made one item for them (the example's supplier answer refers to `L2-TOL1`), but the text says "one item for each tolerance statement" and does not settle this.
- The wording of a question for a request-level detail. The fixed question says "on line [n]", which does not fit currency or quote validity. The run dropped the line.
- No fixed wording for a reminder.
- Whether a specification's text is needed, or only a drawing's, before a line can be fully checked, and so whether PS-07 belongs under "Needs a person".
- The "Reply by" date when the send date is not given.
- Whether the certificates line, "Material certificates required.", is complete. It is not blank, so no item was raised, but it says nothing about inspection.
- The order of items inside a section, and of the evidence for a revision conflict that has three statements (line, register, title block) where the format has room for two.
- An answer that is both a different answer from another supplier and the only answer to its question: the rule for adding "differs from" is clear, but the format does not say whether to repeat both readings in a single line.

Shortcomings: this was one run, by one model, on one invented example. It shows that the instructions can be followed and give the example's result. It does not show how the template performs on a real request, a scanned drawing, or a longer list. None of the ten acceptance tests in the template was run separately.

## Edited after this run, 10 November 2026, and not run again

The edits below were made after an independent review. The run recorded above is unchanged, and the template has not been run again on the example since these edits.

- **Reply date.** The draft message now prints the rule ("three working days after the day the buyer sends it") and one worked date marked "If sent today (2026-11-16), that is 2026-11-19". The example's earlier "Sent on 2026-11-16" is gone. The template's step 9 and output format say the assistant never assumes a send date.
- **Request-level questions.** The fixed question now has a form "on the request" for details such as currency and quote validity, and each question ends with the item identifier.
- **Tolerance items.** Kind (a) is now one item for each drawing, quoting every dimension without a tolerance, which is what this run and the example did. Kinds (b), (c) and (d) are one item for each feature or statement.
- **Specification text.** A specification's text is not needed, because no check reads it. PS-07 is therefore not listed under "Needs a person", and the example's "Nothing" stands. This differs from what this run did, which listed PS-07. The output format now says "drawing text read for [n] of [n] drawings", as this run counted.
- **Reminders.** One wording: the question's wording with "Please still state". The example's reminders now use it, one line for each item.
- **Three statements.** The conflict line has room for a third quoted statement. The example's L1-REV now quotes the request line, the register and the title block separately.
- **Order of items.** Request-level items first, then line items by line number. This follows the example, not the order this run used.
- **Certificates line.** Any cover detail that is not blank counts as stated, and no judgment is made on whether it is enough. This is what this run did.
- **Pasted instructions.** They now carry the identifier codes, the fixed "why it matters" phrases, the status words, the default reply period, the question and reminder wording, the empty-section lines and the closing trace line, so a reader who pastes only the block has them.
- **Second review, 10 November 2026 (small edits, also not run again).** The pasted instructions now carry the condition on kind (a) ("where the drawing has no general tolerance note"), short definitions of kinds (b), (c) and (d), the rule that a drawing not in the register gets item DRW, and the rule that a line without drawing text gets only the line and register checks and goes under "Needs a person". Step 8 and the output format now say two readings on one answer are joined with a semicolon, which settles the last ambiguity listed above in the way the example already showed. The template now says the closing trace line may name the reference and the documents, as the example's does, with its last sentence fixed. In the published example, the addendum quotes the engineer's ruling word for word, and L4-SPEC and L4-MAT name the register column and the request column in the quoted form. These example changes were made by the writer, not by a run, so the example's output on those points is the writer's, as it already was for the item order and for PS-07 not being listed under "Needs a person".
- **Other.** The role line reads "Answer the questions"; the profile and the entry name vendor-quote-comparison as the step that follows once quotes are in.
