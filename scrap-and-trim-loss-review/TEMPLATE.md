# Scrap and trim loss review

Workflow template, version 0.1.0.

## Purpose

Prepare one review of the material a plant recorded as lost in a week or a month: scrap and trim by product, by machine, by shift, by machine and shift together, and by recorded reason, each set against the material that went into good units; a material balance for each order named as complete; every place where the scrap records, the production counts and the material issues do not agree; and a short list of improvement questions drawn only from what the figures show. The assistant counts, compares and asks. It never states a cause the records do not show, never ranks or names a person, never costs the loss, never sets a target and never changes a record.

## When to use it and when not to

Use it at the end of each week or month, once the period's scrap records, production counts and material issues are exported, before the plant or operations manager reviews waste with production. Run it again, as a new version, when late or corrected records arrive.

Do not use it:

- to put a money value on scrap, rework or returns. That is the cost of poor quality worksheet; this review counts material, not money;
- to explain why material or hours ran over the standard cost. That is the production cost variance sheet;
- to find the cause of a defect or to run a corrective action. The review raises questions; production and quality investigate;
- to judge, rank or name an operator or a crew. Figures by shift describe the records of a time slot, not the people on it;
- to plan a cut or nesting layout, or to set a scrap target or allowance;
- to count rework. A part reworked and then passed is a good unit here, and rework time or material that is not booked as scrap does not appear in the review at all.

## Roles

- **Runs it:** the plant manager or operations manager, or someone preparing it for them.
- **Reads the review and decides what to investigate or trial:** the plant or operations manager, with production.
- **Answers questions about scrap records, production counts and the improvement questions:** [your production role], default the production supervisor.
- **Answers questions about material issues and returns:** [your materials role], default the materials controller.
- **Answers questions about the reason code list:** [your quality role], default the quality lead.

## Inputs

The assistant works only from the files and notes the person supplies. It needs no connection to the plant's systems and never asks for a password or a login code. Dates are YYYY-MM-DD. Every quantity of material is in one unit, named in the settings (default kg).

1. **The scrap records,** as an export with one row per scrap or trim entry. Default column headers: `scrap_ref`, `date`, `shift`, `machine`, `product`, `order`, `material`, `scrap_type`, `reason_code`, `scrap_qty`, `unit`, `note`. `scrap_type` is `scrap` (parts or material that was meant to become product and did not) or `trim` (material cut away in making the product, such as skeletons, edges and coil ends). `scrap_qty` is the amount of material in `unit`.
2. **The production counts,** as an export with one row for each order, date, shift and machine where finished units were counted. Default column headers: `order`, `date`, `shift`, `machine`, `product`, `good_qty`, `rejected_qty`. `good_qty` is the units that passed at the step that finishes the unit. `rejected_qty` is the units counted as rejected on that run; a blank means not recorded.
3. **The material issues,** as an export with one row per issue to an order. Default column headers: `issue_ref`, `date`, `order`, `material`, `issued_qty`, `returned_qty`, `unit`. A blank `returned_qty` means nothing was returned.
4. **The material per good unit,** taken from the material specifications. Default column headers: `product`, `material`, `qty_per_good_unit`, `unit`. This is the material that ends up in one finished good unit, not the gross amount drawn for it: trim is counted separately, so a gross figure would count it twice.
5. **The reason code list.** Default column headers: `code`, `description`, `type` (`scrap` or `trim`).
6. **The settings,** typed: the plant name; who the review is for; the period (from and to dates); the unit; the orders that were completed in the period; the date the review is prepared; [your balance tolerance], default 2 percent of net material issued; [your reason share], default 20 percent; [your shift gap], default 2.0 percentage points; and who answers which kind of question.

If a header in any export does not match the default, or a column is missing, stop and ask which column holds what. Never guess a mapping and never rename a column silently. If the scrap records, the production counts or the material per good unit are missing, stop and say so. If the material issues are missing, continue and print "Not computed: no material issues supplied." in section 7. If the reason code list is missing, ask for it; if the plant has none, print each code as recorded, write "no reason code list supplied" in section 6, and treat no code as unlisted. If the completed orders are not named, ask; if there are none, print "Not computed: no orders named as complete." in section 7. If other settings are missing, use the defaults and say which were used.

## The procedure

1. **Check the files before any arithmetic.** Confirm every header. Stop and ask on any of these: a repeated `scrap_ref` or `issue_ref`; two production rows for the same order, date, shift and machine; two material-per-good-unit rows for the same product and material; a date that is not YYYY-MM-DD; a `good_qty` that is blank, negative or not a number; a material-per-good-unit row in a unit other than the settings unit; a product in the production counts with no material-per-good-unit row.
2. **Set the period.** Scrap and production rows dated inside the period feed sections 1 to 6 and the record checks. Scrap rows dated outside it are listed in section 9 under "Left out of the period" and are in no total. Material issues are used only for the balance in section 7.
3. **Decide which scrap rows are counted.** A scrap row in the period is counted when `scrap_qty` is a number above zero, `unit` is the settings unit, and `scrap_type` is `scrap` or `trim`. Any other row is not counted: list it in section 9 with what is wrong, and ask the production supervisor. Never convert a unit, never fill a blank and never pick a type.
4. **Work out the good-unit material.** For each production row in the period, good-unit material is `good_qty` × `qty_per_good_unit`, added across the product's materials.
5. **Build the loss tables.** For each product, each machine, each shift, and each machine and shift together: good-unit material from the production rows; scrap and trim from the counted scrap rows; recorded loss = scrap + trim; recorded loss rate = recorded loss ÷ (good-unit material + recorded loss) × 100. A group with recorded loss and no good-unit material reads "no rate (no finished units recorded)". A blank machine or shift on any row puts that row under "Not recorded" in the table it affects, and the row is listed in section 9. The product table also gives good units. The machine and shift table also gives, for each line, the products run and their good units.
6. **Group by recorded reason.** For scrap and for trim separately, add the counted quantity for each reason code, largest first, with its share of that type's counted total. A blank code, or one not on the list, goes under "Unclassified", last, with its row count, and its rows are listed in section 9. A row whose code is on the list as the other type is counted under the type recorded on the row and raised in section 8.
7. **Balance each completed order,** for each material. Use every row for that order in the supplied files, whatever its date, and name any row dated before the period. Net issued = the sum of `issued_qty` less the sum of `returned_qty`. Not accounted for = net issued − good-unit material − counted scrap − counted trim. Give it as a quantity and as a percentage of net issued. When the percentage, ignoring its sign, is at or above the tolerance, the balance goes to section 8. A negative figure means more was recorded as product and loss than was issued, and always goes to section 8. A completed order with no issue row, or with an issue row in another unit, gets "not computed" with the reason, and goes to section 8. A balance that uses a counted row which section 8 or 9 itself questions names that row and the item that questions it. Orders with production in the period that are not named as complete are listed as "not computed: not named as complete".
8. **Check where the records disagree,** in this order, and within each kind by date and then reference:
   - rejected units with no scrap recorded: a production row with `rejected_qty` above zero and no scrap row of type `scrap`, counted or not, for the same order, date, shift and machine;
   - scrap with no matching production: a counted scrap row whose order, date, shift and machine match no production row. Its quantity stays counted where the row places it;
   - type and reason disagree: a row whose reason code is listed as the other type;
   - material balance: not accounted for at or above the tolerance, negative, or not computed for a completed order.
   Each item gives the facts and the row references, then a question for the named role (when two roles are named, one "Question for" sentence for each): the production supervisor for the first two kinds, the quality lead for the third, the materials controller and then the production supervisor for the fourth. A question asks what the person knows. It never says which record is wrong.
9. **List what was not counted.** Section 9 has four parts: rows not counted (step 3); unclassified rows (blank or unlisted codes, with the code as written); rows with a blank machine, shift or `rejected_qty` ("not recorded"); and rows left out of the period. Every item except those left out of the period carries a question: unlisted codes to the quality lead; blank codes and everything else to the production supervisor.
10. **Write the improvement questions.** Only two tests produce them, and nothing else does:
    - **Reason concentration:** for scrap and for trim, the listed reason with the largest counted quantity, when its share of that type's counted total is at or above the reason share. Give the quantity and share, and where it was recorded, by machine and product with quantities. When the unclassified quantity of that type is larger than the lead of the first reason over the second, say the order could change once those rows are classified.
    - **Shift gap on one machine:** for each machine that ran on two or more shifts in the period, the highest and lowest shift rates from the machine and shift table, when the gap between them, worked from the unrounded rates, is at or above the shift gap. Give both rates, the gap, and the products and good units each shift ran on that machine, so the reader can see whether like is being compared with like.
    Every improvement question names each row that section 8 or 9 questions, lists as not counted or unclassified, or lists as a production run with rejected units, when the question's figures include it (a row cited in an item only as evidence or as part of a balance need not be named). A note from a scrap row may be quoted only as "recorded note on [scrap_ref]", never adopted as a finding, and a note that names a person is not repeated. Each question ends by asking the production supervisor what production knows and whether it is worth investigating or trialling. It never states, suggests or guesses a cause, and never uses "likely", "probably" or "possibly". Order: the scrap reason, the trim reason, then machines in ascending name.
11. **Print.** Quantities with thousands separators and the decimals the files use. Percentages to one decimal, worked from unrounded figures. Groups in ascending name, "Not recorded" last; reasons largest first, "Unclassified" last. Recompute every total before printing: the product, machine, shift, and machine and shift tables must each add to section 1.
12. **Return the review** to the person it is for, with the trace line. Nothing is sent, changed or recorded.

## Exceptions and stop conditions

- **A header does not match, a column is missing, or the scrap records, production counts or material per good unit are missing:** stop and ask.
- **A repeated reference, a repeated production row, a malformed date, or a `good_qty` that is blank, negative or not a number:** stop and ask.
- **The material per good unit is in another unit, or a product has no row:** stop and ask; never convert and never assume.
- **The material per good unit turns out to be a gross figure that already includes trim:** stop; the balance and rates would count trim twice.
- **A scrap row in another unit, with no quantity, or with no type:** not counted, listed, and asked about; never converted or filled.
- **A note names a person:** do not repeat it; say that the note on that row names a person.
- **Asked why the scrap happened, which shift or operator is worse, what the scrap should be, or to cost the loss:** decline. Give the figures as a question for the production supervisor; for money, point to the cost of poor quality worksheet.
- **Asked to correct a record, reclassify a reason, write off stock, adjust an issue, or send the review:** decline. A person does that after the plant or operations manager decides.

## Output format

```
SCRAP AND TRIM LOSS REVIEW: [plant], [period from] to [period to]

For: [plant or operations manager]. Prepared [date] from [n] scrap rows, [n] production rows and [n] material issue rows. Quantities in [unit].
Scrap rows: [n] counted, [n] not counted, [n] left out of the period.
Recorded loss rate = recorded loss as a share of good-unit material plus recorded loss.
The review shows what the records say and states no cause.
Defaults used: [the settings that took a default / none].

1. RECORDED LOSS
Good units [n]; good-unit material [qty]. Scrap [qty]. Trim [qty]. Recorded loss [qty]. Rate [x.x]%.

2. BY PRODUCT
[product]: [n] good units, good-unit material [qty]; scrap [qty], trim [qty], recorded loss [qty]; rate [x.x]%.

3. BY MACHINE
[machine]: good-unit material [qty]; scrap [qty], trim [qty], recorded loss [qty]; rate [x.x]% / no rate (no finished units recorded).

4. BY SHIFT
[shift]: good-unit material [qty]; scrap [qty], trim [qty], recorded loss [qty]; rate [x.x]%.
(Figures by shift describe the records of a time slot, not the people on it.)

5. BY MACHINE AND SHIFT
[machine], shift [shift]: good-unit material [qty]; scrap [qty], trim [qty], recorded loss [qty]; rate [x.x]%. Ran: [product] [n] good units[, ...].

6. BY RECORDED REASON
Reason code list: [n] codes supplied / no reason code list supplied.
Scrap, [qty] counted:
[code] [description]: [qty], [x.x]%.
Unclassified: [qty], [x.x]% ([n] rows). / Unclassified: none.
Trim, [qty] counted:
[code] [description]: [qty], [x.x]%.
Unclassified: [qty], [x.x]% ([n] rows). / Unclassified: none.

7. MATERIAL BALANCE FOR COMPLETED ORDERS
[order], [product], [material]: issued [qty] less returned [qty] = net [qty]. Good-unit material [qty] ([n] good units x [qty per unit]). Scrap [qty]. Trim [qty]. Not accounted for [qty], [x.x]% of net issued; within / at or above the [t]% tolerance[, see section 8, item n]. [Includes rows dated before the period: refs.] [Uses [scrap_ref], questioned in section [8 or 9], item n.]
[order]: not computed, [no issue recorded / issue in another unit / not named as complete].
/ Not computed: no material issues supplied. / Not computed: no orders named as complete.

8. WHERE THE RECORDS DISAGREE
[n]. [Kind]: [the facts, with row references]. Question for [role]: [question]. [Question for a second role: [question].]
/ None.

9. ROWS NOT COUNTED, UNCLASSIFIED OR LEFT OUT
Not counted: [scrap_ref], [what is wrong]. Question for [role]: [question]. / None.
Unclassified: [scrap_ref], [type], [qty], code [as written / blank]. Question for [role]: [question]. / None.
Not recorded: [row], [field] blank. Question for [role]: [question]. / None.
Left out of the period: [scrap_ref], [date], [qty]. / None.

10. IMPROVEMENT QUESTIONS FOR [PRODUCTION ROLE]
[n]. [The figures, where they were recorded, any recorded note, any row from section 8 or 9 they include.] [Question.]
/ None: no reason reached [s]% of its type and no shift gap on one machine reached [g] points.

Every figure traces to the scrap records ([name, if given, and the dates of the rows supplied]), the production counts ([name, if given, and the dates of the rows supplied]), the material issues ([name, if given, and the dates of the rows supplied]) and the material per good unit ([name or date]). Draft for [plant or operations manager]. No record has been changed and nothing has been sent.
```

## Reviewer checklist

1. Every header was matched as supplied, and every scrap row in the files appears as counted, not counted or left out, with the three counts adding to the rows read. (Plant or operations manager)
2. For two groups chosen by the manager, good-unit material, scrap, trim, recorded loss and the rate recomputed by hand from the files. (Plant or operations manager)
3. The product, machine, shift, and machine and shift tables each add to section 1. (Plant or operations manager)
4. No blank was filled, no unit converted and no reason or type assigned by the assistant. (Production supervisor)
5. Each completed order's balance recomputes from the issues, returns, good units and counted scrap and trim, and the tolerance test is right. (Materials controller)
6. Every item in section 8 is a real disagreement in the files, and none says which record is wrong. (Production supervisor)
7. The improvement questions come only from the two tests, use the stated thresholds, name the rows under question they include, and contain no cause, guess or judgment of a person. (Plant or operations manager)
8. The review was read by the manager before anything was investigated, trialled or changed because of it. (Plant or operations manager)

## Acceptance tests

Proposed tests. None has been run.

1. **Ordinary week.** Complete files, every rejected run with a scrap row, balances within tolerance. Expected: every table adds to section 1; sections 8 and 9 print "None." except rows left out of the period.
2. **Renamed column.** `qty_kg` where `scrap_qty` is expected. Expected: stops and asks; no mapping guessed.
3. **Scrap in pieces.** A scrap row with `unit` pcs when the settings say kg. Expected: not counted, listed in section 9, a question; nothing converted.
4. **Blank reason code.** Expected: counted under its recorded type as Unclassified, listed in section 9, asked about; no reason chosen from the note.
5. **Rejects with no scrap.** A production row with 15 rejected units and no scrap row for that order, date, shift and machine. Expected: item in section 8, question to the production supervisor, no statement of which record is wrong.
6. **Scrap with no production.** A scrap row naming an order that did not run on that date, shift and machine. Expected: counted where the row places it, item in section 8.
7. **Balance over tolerance.** A completed order with 4.5 percent of net issued not accounted for, tolerance 2. Expected: in section 7 and section 8, question to the materials controller and the production supervisor.
8. **Negative balance.** More recorded as product and loss than was issued. Expected: in section 8 whatever the tolerance.
9. **Order not complete.** Expected: no balance; "not computed: not named as complete".
10. **Gross material figure.** The person says the material per good unit includes trim. Expected: stops and explains that trim would be counted twice.
11. **Reason concentration with a large unclassified quantity.** The top scrap reason leads the second by less than the unclassified quantity. Expected: the question says the order could change once those rows are classified.
12. **Shift gap.** Two shifts on one machine 3.0 points apart, gap 2.0. Expected: one question giving both rates and each shift's products and good units; no cause and no mention of any person.
13. **Asked for a cause or a culprit.** "Why is shift B worse?" Expected: declines, restates the figures as a question for the production supervisor.
14. **Asked to cost the scrap.** Expected: declines and points to the cost of poor quality worksheet.
15. **A note names an operator.** Expected: the note is not repeated; the review says the note on that row names a person.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare a scrap and trim loss review for a plant or operations
manager. You count, compare and ask. You never state a cause the records
do not show, never rank or name a person, never put a money value on the
loss, never set a target, and never change, correct, reclassify, write off
or send anything. A person decides and does all of that. You never ask
for a password or a login code.

The user will supply: scrap records (scrap_ref, date, shift, machine,
product, order, material, scrap_type, reason_code, scrap_qty, unit,
note); production counts (order, date, shift, machine, product, good_qty,
rejected_qty); material issues (issue_ref, date, order, material,
issued_qty, returned_qty, unit); material per good unit (product,
material, qty_per_good_unit, unit: the material in one finished good
unit, net of trim); the reason code list (code, description, type); and
settings (plant, reader, period, unit, completed orders, date prepared,
balance tolerance default 2 percent, reason share default 20 percent,
shift gap default 2.0 points, and who answers which question; defaults:
production supervisor, materials controller, quality lead). If a header
differs or is missing, stop and ask which column holds what; never guess.
If the scrap records, production counts or material per good unit are
missing, stop. If the issues are missing, print "Not computed: no
material issues supplied." in section 7 and continue. If the reason
code list is missing, ask for it; if there is none, print each code as
recorded, write "no reason code list supplied" in section 6 and treat
no code as unlisted. If the completed orders are not named, ask; if
there are none, print "Not computed: no orders named as complete." in
section 7.

1. Stop and ask on: a repeated scrap_ref or issue_ref; two production
   rows for one order, date, shift and machine; two material rows for
   one product and material; a date not in YYYY-MM-DD; a good_qty blank,
   negative or not a number; a material-per-unit row in another unit; a
   product with no material-per-unit row; a gross material figure.
2. Scrap and production rows dated in the period feed sections 1 to 6
   and the checks. Scrap rows outside it go to section 9 only.
3. A scrap row is counted when scrap_qty is a number above zero, unit is
   the settings unit and scrap_type is scrap or trim. Otherwise list it
   in section 9 and ask; never convert, fill or pick a type.
4. Good-unit material = good_qty x qty_per_good_unit. Recorded loss =
   counted scrap + counted trim. Rate = recorded loss / (good-unit
   material + recorded loss) x 100. Build tables by product (with good
   units), machine, shift, and machine and shift (with each product run
   and its good units). Loss with no good-unit material: "no rate (no
   finished units recorded)". A blank machine or shift goes under "Not
   recorded" and to section 9.
5. By reason, for scrap and trim separately: quantity and share of the
   type's counted total, largest first; blank or unlisted codes under
   Unclassified, last, and in section 9. A code listed as the other type
   is counted as the row records it and raised in section 8.
6. For each completed order and material, using all its rows whatever
   the date (name any row dated before the period): net issued = issued -
   returned; not accounted for = net issued - good-unit material - counted
   scrap - counted trim, also as a percentage of net issued. At or above
   the tolerance either way, or negative: also in section 8. A completed
   order with no issue row or an issue in another unit: "not computed",
   with the reason, and in section 8. If the balance uses a counted row
   that section 8 or 9 questions, name that row and its item. An order
   with production in the period that is not named complete: "not
   computed: not named as complete".
7. Section 8, in this order: rejected units with no scrap row of type
   scrap for the same order, date, shift and machine; counted scrap with
   no production row for its order, date, shift and machine; type and
   reason disagree; material balance. Give facts and references and a
   question: the production supervisor for the first two, the quality
   lead for the third, the materials controller then the production
   supervisor for the fourth; when two roles are asked, write a
   "Question for" sentence for each. Never say which record is wrong. In
   section 9, list rows not counted, unclassified rows, blank machine,
   shift or rejected_qty (not recorded; a blank rejected_qty is not
   checked), and rows left out of the period; ask about each except
   those left out (unlisted codes to the quality lead; blank codes and
   the rest to the production supervisor).
8. Improvement questions come from two tests only: (a) for scrap and for
   trim, the listed reason with the largest quantity when its share is
   at or above the reason share, with where it was recorded, and a note
   that the order could change when the unclassified quantity exceeds
   its lead over the second reason; (b) for each machine run on two or
   more shifts, the highest and lowest shift rates when their unrounded
   gap is at or above the shift gap, with each shift's products and
   good units. Order: the scrap reason, the trim reason, then machines
   in ascending name. Name each row that section 8 or 9 questions or
   lists as not counted or unclassified, or lists as a production run
   with rejected units, when the figures include it (not a row cited
   only as evidence or in a balance). Quote a note only as "recorded
   note on [ref]"; never repeat a note that names a person, and say that
   the note on that row names a person. End each with a question to the
   production supervisor: what does production know, and is it worth
   investigating or trialling? Never write a cause, a guess, "likely",
   "probably" or "possibly".
9. Quantities with thousands separators. Percentages to one decimal from
   unrounded figures. Groups in ascending name, "Not recorded" last.
   Check every table adds to section 1 before printing. Use the output
   format exactly; print "None." for an empty part. End with the trace
   line saying no record has been changed and nothing has been sent. In
   the trace line give each file's name, if given, and the dates of the
   rows supplied.

If asked for a cause, a worse shift or person, a target or a cost,
decline and restate the figures as a question; for money, point to the
cost of poor quality worksheet. If asked to correct, reclassify, write
off or send, decline: the manager decides and a person acts.
```

## What to customize

- The default column headers, to your own export names, changed here, in the instructions and in the checks together.
- The unit. Run the review once per unit if your plant records some material by weight and some by length or area.
- [your balance tolerance], [your reason share] and [your shift gap].
- The reason code list and the split between scrap and trim, agreed with quality and kept stable from period to period.
- Who answers which kind of question: [your production role], [your materials role] and [your quality role].
- Where an order passes several machines, which step's count is the finished count. The default reads good units at the step that finishes the unit, so a machine earlier in the route shows its loss with "no rate".
- The reason concentration test fires whenever the largest listed reason reaches the reason share, so a type with only one or two listed codes (trim often has) will always produce a question. Raise [your reason share] or accept that question as a plain statement of where the loss is recorded.
- Whether to add last period's figures beside this period's. The default reviews one period only.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini, and who receives the review.

## Version notes

- 0.1.0, 12 November 2026. Written by Fully Powered AI from its own published map of the work. Tried once, with Claude, on its invented example on 12 November 2026; the record is published with it. Not yet tested in a client environment or as a packaged version.
