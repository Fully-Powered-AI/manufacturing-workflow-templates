# Scrap and trim loss review: tried once on its example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-12

The inputs were the invented example in [example.md](example.md): the scrap records, production counts, material issues, material per good unit, reason code list and settings for the invented Plant C, week of 2026-11-02. No client data was used. The assistant that ran the template did not write it. It followed the template's instruction block and output format on those inputs and did not read the example's published output until its own review was finished. The arithmetic was done with a short throwaway script and checked against the tables adding up; the figures were not copied from the example.

## What came out

The review below is the output in full, as the assistant produced it before comparing.

```
SCRAP AND TRIM LOSS REVIEW: Plant C, 2026-11-02 to 2026-11-06

For: the plant manager. Prepared 2026-11-09 from 17 scrap rows, 8 production rows and 4 material issue rows. Quantities in kg.
Scrap rows: 15 counted, 1 not counted, 1 left out of the period.
Recorded loss rate = recorded loss as a share of good-unit material plus recorded loss.
The review shows what the records say and states no cause.
Defaults used: none.

1. RECORDED LOSS
Good units 9,500; good-unit material 11,000. Scrap 210. Trim 2,230. Recorded loss 2,440. Rate 18.2%.

2. BY PRODUCT
BR-40: 7,500 good units, good-unit material 6,000; scrap 88, trim 1,430, recorded loss 1,518; rate 20.2%.
PN-60: 2,000 good units, good-unit material 5,000; scrap 122, trim 800, recorded loss 922; rate 15.6%.

3. BY MACHINE
Press 1: good-unit material 4,000; scrap 72, trim 950, recorded loss 1,022; rate 20.4%.
Press 2: good-unit material 7,000; scrap 138, trim 1,280, recorded loss 1,418; rate 16.8%.

4. BY SHIFT
A: good-unit material 7,010; scrap 65, trim 1,410, recorded loss 1,475; rate 17.4%.
B: good-unit material 3,990; scrap 145, trim 820, recorded loss 965; rate 19.5%.
(Figures by shift describe the records of a time slot, not the people on it.)

5. BY MACHINE AND SHIFT
Press 1, shift A: good-unit material 2,560; scrap 24, trim 620, recorded loss 644; rate 20.1%. Ran: BR-40 3,200 good units.
Press 1, shift B: good-unit material 1,440; scrap 48, trim 330, recorded loss 378; rate 20.8%. Ran: BR-40 1,800 good units.
Press 2, shift A: good-unit material 4,450; scrap 41, trim 790, recorded loss 831; rate 15.7%. Ran: BR-40 1,500 good units, PN-60 1,300 good units.
Press 2, shift B: good-unit material 2,550; scrap 97, trim 490, recorded loss 587; rate 18.7%. Ran: BR-40 1,000 good units, PN-60 700 good units.

6. BY RECORDED REASON
Reason code list: 5 codes supplied.
Scrap, 210 counted:
DIM out of dimension: 64, 30.5%.
SET setup and first-off parts: 59, 28.1%.
SUR surface damage: 25, 11.9%.
Unclassified: 62, 29.5% (1 row).
Trim, 2,230 counted:
SKL blanking skeleton: 2,190, 98.2%.
END coil head and tail ends: 40, 1.8%.
Unclassified: none.

7. MATERIAL BALANCE FOR COMPLETED ORDERS
WO-501, BR-40, CR-15: issued 5,100 less returned 30 = net 5,070. Good-unit material 4,000 (5,000 good units x 0.80). Scrap 72. Trim 950. Not accounted for 48, 0.9% of net issued; within the 2% tolerance.
WO-502, PN-60, CR-15: issued 6,200 less returned 0 = net 6,200. Good-unit material 5,000 (2,000 good units x 2.50). Scrap 122. Trim 800. Not accounted for 278, 4.5% of net issued; at or above the 2% tolerance, see section 8, item 3.
WO-503: not computed, not named as complete.

8. WHERE THE RECORDS DISAGREE
1. Rejected units with no scrap recorded: the production row for WO-503, 2026-11-05, shift B, Press 2 shows 15 rejected units. No scrap row of type scrap exists for WO-503 on that date, shift and machine (the only scrap row for that order, date, shift and machine is S-14, trim). Question for the production supervisor: what does production know about the 15 rejected units on that run, and is there a scrap record for them?
2. Scrap with no matching production: S-15 (2026-11-05, shift B, Press 2, WO-502, PN-60, scrap, SET, 35 kg) names an order, date, shift and machine that match no production row; the production rows for that date, shift and machine show WO-503. S-15 stays counted under Press 2, shift B and PN-60 as recorded. Question for the production supervisor: what does production know about S-15, and which run does it belong to?
3. Material balance: WO-502 has 278 kg of its 6,200 kg net issued not accounted for, 4.5% against a 2% tolerance (I-03; S-07, S-08, S-09, S-10, S-11 and S-15; production rows 2026-11-03 A, 2026-11-03 B, 2026-11-04 A). Question for the materials controller: are all issues and returns for WO-502 in the export? Question for the production supervisor: what does production know about scrap or trim from WO-502 that is not in the scrap records?

9. ROWS NOT COUNTED, UNCLASSIFIED OR LEFT OUT
Not counted: S-16, unit pcs where the settings say kg (2026-11-05, shift A, Press 2, WO-503, BR-40, scrap, DIM, 12 pcs). Question for the production supervisor: what weight of material in kg do the 12 pieces on S-16 come to?
Unclassified: S-10, scrap, 62, code blank. Question for the production supervisor: which reason on the list applies to S-10?
Not recorded: None.
Left out of the period: S-17, 2026-10-30, 150.

10. IMPROVEMENT QUESTIONS FOR THE PRODUCTION SUPERVISOR
1. DIM (out of dimension) is the largest listed scrap reason: 64, 30.5% of the 210 scrap counted. Recorded on Press 1 for BR-40 (48, S-04) and on Press 2 for BR-40 (16, S-13). Recorded note on S-04: "oversize after die change". Unclassified scrap (62, S-10, section 9) is larger than DIM's lead of 5 over SET, so the order could change once S-10 is classified. S-16, also DIM, is not in these figures (section 9). What does production know about the out-of-dimension scrap on BR-40, and is it worth investigating or trialling?
2. SKL (blanking skeleton) is the largest listed trim reason: 2,190, 98.2% of the 2,230 trim counted. Recorded on Press 1 for BR-40 (910), on Press 2 for BR-40 (480) and on Press 2 for PN-60 (800). What does production know about the skeleton loss on each product, and is it worth investigating or trialling?
3. Press 2: shift B rate 18.7% against shift A 15.7%, a gap of 3.0 points against a threshold of 2.0. Shift A ran BR-40 1,500 good units and PN-60 1,300; shift B ran BR-40 1,000 and PN-60 700. Shift B's figures include S-10 (section 9) and S-15 (section 8, item 2), and its good units include the WO-503 run in section 8, item 1. What does production know about the difference between the two shifts on Press 2, and is it worth investigating or trialling?

Every figure traces to the scrap records (2026-11-02 to 2026-11-06, with S-17 from 2026-10-30), the production counts (2026-11-02 to 2026-11-05), the material issues (2026-11-02 to 2026-11-05) and the material per good unit (specification sheet, CR-15). Draft for the plant manager. No record has been changed and nothing has been sent.
```

## What was observed

- **Every required part was produced.** All ten sections and the trace line came out in the stated format, with no stop condition triggered. The product, machine, shift, and machine-and-shift tables each add to section 1 (9,500 good units, 11,000 kg good-unit material, 210 scrap, 2,230 trim).
- **Nothing in the inputs was a stop.** All headers matched, there were no repeated references, every date was well formed, and every product had a material row. The one unit problem (S-16 in pieces) is handled by the template as "not counted", not as a stop, and it was.
- **Same result as the published output on every figure.** Compared afterwards, the figures, shares, rates, balances and the three records that disagree were the same. The tests produced three improvement questions in the same order.
- **Differences from the published output are in wording only.** The published section 8 asks "what happened to the 15 rejected BR-40 units" and "which order and product does S-15 belong to"; this run used the template's own phrasing, "what does production know about...", and did not name the product in the first question. This run named the S-07 to S-11 rows individually in item 3, added that S-16 (also DIM) is outside the figures in question 1, added that Press 2 shift B's good units include the WO-503 run named in section 8, item 1, and wrote the production counts' date range as 2026-11-02 to 2026-11-05 where the published trace line says 2026-11-06. Neither version contains a fact absent from the inputs.
- **Where the instructions were ambiguous and a guess was needed:**
  - Who gets the question about a blank reason code. Step 9 sends "unlisted codes" to the quality lead and "everything else" to the production supervisor. A blank code is not an unlisted code; this run chose the production supervisor, as the published example does. The template should say so.
  - Whether a scrap row that is not counted (S-16) should be mentioned in an improvement question when it shares the reason being questioned. The rule says to name rows that the figures include; S-16 is not included. This run mentioned it anyway, to be clear that it is outside the figure. The template does not say whether that is wanted.
  - Whether a counted scrap row with no matching production row (S-15) is used in the order balance. Step 7 says to use every row for the order, so it was used, and WO-502's balance and its section 8 item both rest on a row that is itself questioned. The template does not say to flag this; the review does so only by listing S-15 in item 3.
  - How to word the trace line's date ranges, since the template gives only "[name or period]".
  - Whether "Question for [role]" in section 8 item 3 should be one line or two when two roles are asked. The format shows one; this run used two sentences.
- **The skeleton test is trivially met.** Trim had one dominant reason (98.2%), so the reason-concentration test always fires for trim in this example and the question reads as little more than "trim is mostly skeleton". That is what the template says to do, but a reader may find it low in value. The template does not provide for it.
- **The instructions block is long.** It restates most of the procedure from the main text. In this run the two agreed with each other; no conflict between them was met.
- **Not tried:** any of the stop paths (renamed column, gross material figure, repeated references), asking for a cause, a culprit or a cost, or a note naming a person. The example's inputs contain none of these, so this run says nothing about them.
- **Not done by this run:** the reviewer checklist was walked through only as a comparison of the output with the inputs; no plant manager, supervisor or materials controller checked it.

## Changes made to the template after this run

Added on 12 November 2026. Nothing above this heading was altered. The run above was not repeated, and it was made before these changes. They clarify points this run found ambiguous or that the review raised; none changes a figure, a test or a threshold, and the output above is still what the template would now produce except as noted.

- A blank reason code is now stated to go to the production supervisor, and a section 8 item that asks two roles now has a "Question for" sentence for each. This run did both.
- The trace line now says to give each file's name and the dates of the rows supplied. This run gave the production counts and material issues as 2026-11-02 to 2026-11-05, which is what the rule now says; the published example's trace line was changed to match, so the difference noted above no longer applies to it. The trace line format now reads "name, if given", because the example's inputs name no files; the run's trace line gave dates only, as the format now allows.
- A balance that uses a counted row which section 8 or 9 questions now names that row and its item. This run's section 8, item 3 listed S-15 without saying that item 2 questions it, so it does not follow the new rule on that point.
- The rule that an improvement question names the rows it includes is now limited to rows that sections 8 and 9 question, list as not counted or unclassified, or list as a production run with rejected units. This run's questions 2 and 3 name only rows that fall under it. Question 1 also names S-16, which the rule as now written does not call for (S-16 is not in the figures); the run did it anyway, as noted above.
- The published example now carries the sentence that Press 2 shift B's good units include the WO-503 run, which this run had added; and its section 7 line for WO-502 now names S-10 and S-15 and the items that question them, as the format asks. This run's WO-502 balance line does not name them.
- The instruction block now also states the order of the improvement questions, that a note naming a person is reported as such, and thousands separators. It also carries the rules to ask when the reason code list or the completed orders are missing, and to name rows dated before the period in a balance. This run did not meet either case.
- "What to customize" now says the reason concentration test always fires for a trim type dominated by one or two codes, as it did here.
