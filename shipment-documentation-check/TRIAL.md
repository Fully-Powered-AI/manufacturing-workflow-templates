# Shipment documentation check: tried once on its example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in `public/example.md` (the settings and the five files for order PO-7781). No client data was used. The assistant that ran the trial did not write the template.

One thing weakens this trial. The example's output was printed in the same command as the template and the inputs, so the run was not blind: the assistant saw the published output before it produced its own. It followed the instruction block and the output format step by step and worked every count from the inputs, but a reader should weigh the match with the example accordingly.

## What came out

```
SHIPMENT DOCUMENTATION CHECK: the Shop, order PO-7781, Tuesday 2026-11-10

For: the shipping lead and the quality lead. Ship date 2026-11-12, 2 days away. Prepared from: order lines (4 rows), required documents (5 rows), inspection records (4 rows), documents on file (4 rows), packing details (5 rows), settings.
Column check: all headers matched.
Settings: quantity tolerance 0 units; accepted word "accepted"; signed word "yes". Defaults used: quantity tolerance, accepted word, signed word.
Summary: 4 order lines. Required documents 5: found 1, found with a difference 3, missing 1. Lines with an inspection record 3 of 4. Packed lots 5: 4 with an inspection record, 1 without. Missing records 3. Differences between files 6, on 3 lines. Documents on file that no requirement names 0. Rejections recorded: 2 pieces on 1 line.

Data checks
No problems found.

Document index
R1 Material certificate, line 1 BRK-210 (order note): Found with a difference. D-1, dated 2026-10-20, shown as signed; lot not covered: L-5502. See decision 1.
R4 Coating certificate, line 2 BRK-215 (order note): Found with a difference. D-2, dated 2026-10-22, shown as signed; item code BRK-251 against BRK-215 on the order; revision A against B on the order. See decision 2.
R2 Material certificate, line 3 PLT-40 (order note): Found with a difference. D-3, dated 2026-10-28, not shown as signed. See decision 3.
R3 Material certificate, line 4 SHF-08 (order note): Missing. No document of this type on file for line 4. See decision 4.
R5 Packing list, whole order (shipping procedure SP-3): Found. D-4, dated 2026-11-10, shown as signed.

Quantity comparison
Line 1 BRK-210 revision C: ordered 200 each; inspected 200, accepted 198, rejected 2 (I-301, I-302); packed 200 (P-1, P-2). Lot L-5501: packed 120, accepted 120. Lot L-5502: packed 80, accepted 78, 2 more packed than accepted. See decision 1.
Line 2 BRK-215 revision B: ordered 120 each; inspected 120, accepted 120, rejected 0 (I-303); packed 120 (P-3). Lot L-6120: packed 120, accepted 120. No difference.
Line 3 PLT-40 revision A: ordered 50 each; inspected 50, accepted 50, rejected 0 (I-304); packed 55 (P-4), 5 more than ordered. Lot L-7001: packed 55, accepted 50, 5 more packed than accepted. See decision 3.
Line 4 SHF-08 revision D: ordered 30 each; no inspection record; packed 30 (P-5). Lot L-8002: no inspection record. See decision 4.

Missing records
1. Material certificate naming lot L-5502, line 1 BRK-210, 80 packed (R1).
2. Material certificate, line 4 SHF-08 (R3).
3. Inspection record, line 4 SHF-08, lot L-8002, 30 packed.

Differences between files
1. Line 1, lot L-5502: packed 80 (P-2), accepted 78 (I-302); 2 more packed than accepted.
2. Line 2, D-2: item code BRK-251; the order line shows BRK-215.
3. Line 2, D-2: revision A; the order line shows revision B.
4. Line 3: packed 55 (P-4); ordered 50; 5 more than ordered.
5. Line 3, lot L-7001: packed 55 (P-4), accepted 50 (I-304); 5 more packed than accepted.
6. Line 3, D-3: not shown as signed.

Documents on file that no requirement names
None.

Decisions for the quality lead and the shipping lead
1. Line 1 BRK-210. Lot L-5502: 80 packed (P-2), 78 accepted and 2 rejected on I-302. The only material certificate on file, D-1, names lot L-5501. Is the packed count of 80 for lot L-5502 right? Is there a material certificate for lot L-5502 outside the files supplied?
2. Line 2 BRK-215. The coating certificate D-2 shows item code BRK-251 and revision A; the order line is BRK-215 revision B. Does D-2 belong to this line? Is there another coating certificate for it?
3. Line 3 PLT-40. 55 packed (P-4) against 50 ordered and 50 accepted (I-304); material certificate D-3 is not shown as signed. Is the extra 5 intended? Is a signed copy of D-3 on file elsewhere?
4. Line 4 SHF-08. No inspection record and no material certificate; 30 packed (P-5) from lot L-8002. Do these records exist outside the files supplied?

Draft for the quality lead and the shipping lead. Nothing has been certified, signed, released, sent or changed, and no conformity or export judgment has been made. Counts are taken from the files supplied on 2026-11-10.
```

## What was observed

- **Every required part was produced:** header, column check, settings, summary, all seven sections and the closing line. The three requirement counts (1, 3, 1) add up to the five requirements. Nothing in the inputs triggered a stop, and nothing was declined, because nothing in the run asked for a judgment the template reserves for people.
- **The counts match the published example,** and so do the findings: the same three missing records, the same six differences on the same three lines, the same four decisions, and no fabricated figure.
- **Differences from the published example** are all of wording or order, none of substance:
  - Missing records. The template says "in the order of the order lines", so the line 1 lot certificate comes first and the line 4 items last. The example lists line 4 first and line 1 last. The assistant followed the template's wording.
  - Document index. The template does not say how to order the requirements. The assistant ordered them by order line, as the example does, which was a guess.
  - The lot-not-covered difference. The template gives no wording for it. The assistant wrote "lot not covered: L-5502"; the example wrote a longer sentence.
  - Decision wording and a few record ids in the Differences list. The example's decisions and the run's ask for the same things in different words.
  - The example's Quantity comparison for line 4 repeats the packed quantity in the lot line. The template does not call for it.
- **No fact outside the inputs** appeared in either output. Every id, figure and date traces to a row in the supplied files.
- **Ambiguities and shortcomings in the template:**
  1. The order of entries within one line under Missing records is not stated (a line 4 certificate against a line 4 inspection record).
  2. Step 9 does not say whether a document difference (unsigned, wrong item code, wrong revision) is also listed under Differences between files, though step 4 already names it in the Document index. The example lists them in both places; the template's step 9 is silent, so the same finding is counted twice in the "6 differences".
  3. The Quantity comparison format ends each line with "See decision / No difference" but also shows lot sub-entries. It is unclear whether "No difference" applies to the line or to each lot.
  4. The Document index order is not stated.
  5. The instruction block is shorter than the procedure. It leaves out the weekday and the days-to-ship-date count (step 12), the unit-mismatch rule's effect on comparison, the order of Missing records, and the stop for a missing required-documents file is there but the "ask which column" wording is thinner. A person pasting only the block gets a slightly different tool from the one the procedure describes.
  6. Step 1 contains a placeholder, "[your column headers]", that reads as unfinished text.
  7. Inspected and packed are compared only through accepted quantity. A lot with 2 rejected pieces and 80 packed against 78 accepted is reported as "2 more packed than accepted"; the template does not say whether the rejected pieces should be mentioned beside that figure. The assistant mentioned them in the decision only.
  8. The version notes still say "Not yet tried on its example". That is now out of date, but changing it is outside this trial.
- **One run is one run.** This shows the instructions can be followed to a complete, correct output on one small, clean example. It does not show how the template copes with messy or large files, and it has not been tested in a client environment.

## Changed after the run

The output and observations above are as recorded and describe the template and the example as they stood at the run. After an independent review on 10 November 2026 the template and the example were changed as listed below. The template was not run again, and nothing in the recorded output or observations was altered. Several observations above (the ordering of the example's Missing records, the Document index order, the wording of the uncovered lot, the placeholder in step 1, the version notes) describe the earlier files and are no longer true of the published ones.

Template:

- **Missing records order.** Step 8 now states the order within a line: missing required documents, then lots with no inspection record, then uncovered lots.
- **Document index order.** Step 4 now says to order it by the line each requirement applies to, requirements for `ALL` last, then by `requirement_id`.
- **Document differences listed twice.** Step 9 now says a difference found in step 4 appears in both the Document index and the Differences list, and both are counted.
- **Rejected pieces.** Step 5 now says the "more packed than accepted" figure is stated alone; rejected pieces are shown in the Quantity comparison and may be named in a decision.
- **Instruction block.** It was brought up to the procedure: the weekday and days-to-ship-date, the unit-mismatch rule, the order of Missing records, the stop for a missing required-documents file. After the second review it also says to ask and prepare nothing else on a failed row check, and carries the rule for a document whose `applies_to` is neither a line nor `ALL`.
- **Placeholder.** The "[your column headers]" placeholder in step 1 was removed.
- **Version notes.** They now say the template was tried on its example, and that the run was not blind.
- **Wording for an uncovered lot.** The Document index now reads "lot not covered: [lot]", given once in step 4 and in the block.
- **Lots with no inspection record.** The Quantity comparison format now reads "Lot [lot]: packed [n], no inspection record."
- **Closing words of a Quantity comparison line.** "See decision [n]." or "No difference." closes the line once, not each lot.
- **Whole-order documents.** Lot coverage is not checked for a document for `ALL`.

Example:

- **Missing records order** now follows the changed template, and the Document index and Quantity comparison follow the wording above (the uncovered lot is written "lot not covered: L-5502"; the unsigned document D-3 is written with a comma).

After a third review (10 November 2026) the instruction block was brought closer to the procedure: matching of document types ignoring capitals and spaces at the ends, "inspected, not packed" with the accepted quantity, a blank `document_date` allowed and reported, the two exceptions (a document known only by its title; passwords or bank details in the files), and a re-wrap of ragged line breaks. A line whose packing unit differs from the order unit now closes its Quantity comparison entry "Quantities not compared, unit differs."; the example does not exercise that case. Decision 2 in the example now asks "Is there another coating certificate for this line?", close to the run's own wording. The first-person wording in the observations was changed to "the run's". The recorded output was not altered.

Not fixed: the example was edited to follow the changed template. It is not a re-run, and neither are the later edits to the block, so it has not been shown that an assistant given the changed instructions produces it.
