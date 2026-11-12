# Production cost variance sheet

Workflow template, version 0.1.0.

## Purpose

Prepare one variance sheet for a period's closed production orders: for each order, the cost the standard cost card allows for the good units made, the cost actually recorded, and the difference split into material price, material usage, labor rate, labor efficiency, overhead spending and overhead efficiency; totals by element and by product; every missing actual and every changed standard flagged; and each difference over the plant's limits written as a question for a named role in operations. The assistant calculates and asks. It never states a cause, never changes a standard cost, never proposes a new one and never posts anything.

## When to use it and when not to

Use it once the period's production actuals have closed and the standard cost cards are to hand, before the controller reviews the variance accounts or explains the period to plant management. Run it again, as a new version, when late actuals arrive.

Do not use it:

- to compare the results against a budget, line by line, with commentary. That is budget-versus-actual variance commentary;
- to total scrap, rework and return costs, or to find what quality failures cost. That is the cost of poor quality worksheet. This sheet shows that more material or hours were used than the standard allowed; it does not sort the excess into scrap, rework or anything else;
- to set, revise or recommend a standard cost. The sheet shows where a standard changed and what the figures were; the controller and operations own the standards;
- to post a variance, adjust inventory or change any ledger. The controller does that, from the approved sheet;
- where overhead is applied on a base other than labor hours (machine hours, units, material cost). The overhead rule below is written for labor hours only; see "What to customize";
- to judge or rank people. A difference on an order is never attributed to an operator, shift or supplier by the sheet;
- where most overhead is fixed and the controller wants a spending and volume split. The two-way split here treats all overhead as applied per labor hour, so with mostly fixed overhead the spending figure is hard to read; see "What to customize".

## Roles

- **Runs it:** the plant controller or a cost accountant working for the controller.
- **Verifies the calculations and approves the sheet:** the controller. A second person checks the arithmetic if the plant's close routine says so.
- **Confirms or supplies any explanation:** [your operations owner for each element]. Defaults: purchasing for material price; the production supervisor for material usage, labor and overhead; the owner of the cost records for missing postings; the controller for which standard applies.
- **Decides what goes into the close and the management pack:** the controller.

## Inputs

The assistant works only from the files and notes the person supplies. It needs no connection to the plant's systems and never asks for a password or a login code. Amounts are in one currency, and quantities in one unit per material, as stated in the settings. Neither default export has a unit column, so the person confirms that both the standards and the actuals hold the material quantity in that unit.

1. **The standard cost cards,** as an export with one row per product and effective date. Default column headers: `product`, `effective_from`, `std_material_qty`, `std_material_price`, `std_hours`, `std_labor_rate`, `std_overhead_rate`. Quantities and hours are per one good unit of the product. `std_overhead_rate` is per labor hour. Dates are YYYY-MM-DD. Include every row in force during the period and any later row that takes effect inside it.
2. **The actuals,** as an export with one row per closed order. Default column headers: `order`, `product`, `start_date`, `close_date`, `good_units`, `actual_material_qty`, `actual_material_cost`, `actual_hours`, `actual_labor_cost`, `actual_overhead`. `good_units` is the quantity that passed, so material and hours used on units that did not pass count against the order. `actual_overhead` is the overhead the plant's own cost records assigned to the order; the assistant never allocates overhead. A blank cell means not recorded.
3. **The settings,** typed: the plant name; the period (from and to dates); the currency; the unit of the material, and the person's confirmation that both files use it; that overhead is applied per labor hour; [your percentage limit], default 5; [your amount limit], default 250 in the currency; who answers which kind of question; who receives the sheet.

If a header in either export does not match the default, or a column is missing, stop and ask which column holds what. Never guess a mapping and never rename a column silently. If the person does not supply the standards or the actuals, stop and say so. If the settings are partly missing, use the defaults above and say which were used.

## The procedure

1. **Check the files before any arithmetic.** Confirm every header. Confirm no order number appears twice in the actuals and no product has two standard rows with the same effective date. Confirm with the person that the material quantity in both files is in the unit named in the settings and that overhead is applied per labor hour; if they have not said so, ask. List orders whose `close_date` is blank or falls outside the period and leave them out of the sheet (a blank close date means the order is not closed); name them under Flags, Other. Stop on anything that fails.
2. **Find the standard in force for each order.** It is the row for the order's product with the latest `effective_from` on or before the order's `start_date`. If there is none, or the order has no `start_date`, compute nothing for that order and flag it.
3. **Mark changed standards.** For each product, list every standard row whose `effective_from` falls inside the period and say which elements differ from the row before it, with the old and new figures. For each order whose dates span a later row's `effective_from` (after `start_date`, up to and including `close_date`), compute on the standard in force at its start, mark the order, and ask the controller which standard governs it. Do not compute it a second way.
4. **Work out what the standard allows,** for each order:
   - allowed material quantity = good units × `std_material_qty`; allowed material cost = allowed material quantity × `std_material_price`;
   - allowed hours = good units × `std_hours`; allowed labor cost = allowed hours × `std_labor_rate`;
   - allowed overhead = allowed hours × `std_overhead_rate`.
5. **Work out the differences.** Compute at full precision and round only when printing, to the cent. Positive means actual is above standard (U for unfavourable); negative means below (F for favourable); exactly zero prints as 0.00.
   - material price = `actual_material_cost` − (`actual_material_qty` × `std_material_price`);
   - material usage = (`actual_material_qty` − allowed material quantity) × `std_material_price`;
   - labor rate = `actual_labor_cost` − (`actual_hours` × `std_labor_rate`);
   - labor efficiency = (`actual_hours` − allowed hours) × `std_labor_rate`;
   - overhead spending = `actual_overhead` − (`actual_hours` × `std_overhead_rate`);
   - overhead efficiency = (`actual_hours` − allowed hours) × `std_overhead_rate`.
   The two parts of each element add to its total, which equals the element's actual cost less its allowed cost. Check that for every order. If it does not hold, stop and report the order and the figures.
6. **Flag missing actuals; never compute around them.** Material needs `actual_material_qty` and `actual_material_cost`. Labor needs `actual_hours` and `actual_labor_cost`. Overhead needs `actual_overhead` and `actual_hours`. If any needed cell for an element is blank, that element has no variance for that order: write "not computed", name the blank cells, and leave the order out of that element's totals. A blank is never treated as zero. A zero in any actual cell on an order with good units above zero is treated the same way, as a possible missing posting for the person to confirm. An order with `good_units` blank, zero or negative gets nothing computed. An order total is printed only when all three elements are computed.
7. **Total.** Add the differences by element across the orders where that element was computed, and give the count of orders in each. Give the combined total for orders computed in full for all three elements. Then by product: each element's total and its count of orders. Print orders in ascending order number and products in ascending product code. The header counts are these. *Orders supplied* is the orders on the sheet (those closed inside the period). *Computed in full* is the orders whose three elements are all computed. *Computed in part or not at all* is orders supplied less computed in full. *Carrying a flag* is the orders named under Missing actuals, under Other, or as spanning a later standard under Changed standards, each counted once; orders left out of the sheet, and orders a changed standard does not affect, are not counted.
8. **Write the questions.** The over-limit test is applied to each of the six parts (material price, material usage, labor rate, labor efficiency, overhead spending, overhead efficiency) on each order. It is never applied to an element's total or an order total: a total that is over the limits while both its parts are under them is printed on the sheet and gets no question. A part gets a question when its absolute amount is at least [your percentage limit] percent of that element's allowed cost on that order, and at least [your amount limit]. Every flag that names an order also gets a question: an order spanning a changed standard, and an order with no standard in force, go to the controller (which standard applies); missing or zero actuals, no good units, no start date, and an order left out of the sheet and named under Other (blank or out-of-period close date) go to the cost accountant, as the owner of the cost records, asking what is recorded or whether it closed in the period. A changed standard that no order on the sheet spans is listed under Changed standards with the orders not affected and gets no question. Where an over-limit part sits on the same flagged order, one question carries both. Each question gives the order, the line, the actual against the standard, the amount and its percentage of the allowed cost, then asks a named role what they know. The role is the one the settings name for that part (default: purchasing for material price, the production supervisor for the other parts). One question may name more than one role, as when it carries a flag and a part for different roles: one sentence per role, each starting with the role, the controller's first. A question never contains a reason, not even a guess or a "possibly". Where two parts move together by arithmetic, say so (for example, labor efficiency and overhead efficiency are the same extra hours at two rates), and let one question stand for both. Number the questions with the difference questions first (including those that also carry a flag), then the questions for flags alone, each group in ascending order number.
9. **Tie out.** For each element, show the two parts, their sum, and actual less allowed over the same orders. Where an element's two parts have different signs, print the parts and their sum with U or F; otherwise print bare amounts. Actual less allowed is always a bare amount. Then show the combined total as the sum of the three element totals for the orders computed in full. The three element totals for those orders are printed in the totals section, because the material figure for them differs from the material total for all orders whenever an order is computed in part.
10. **Trace line and return.** Name the standards file and the actuals file behind every figure. Return the sheet to the controller only.

## Exceptions and stop conditions

- **A header does not match, a column is missing, or an export is missing:** stop and ask.
- **An order number repeats, or two standard rows share a product and effective date:** stop and ask which is right.
- **The parts of an element do not add to actual less allowed:** stop and report the order and the figures.
- **No standard in force at the order's start, or no start date:** flag the order, compute nothing for it.
- **A blank or zero actual:** flag it, do not compute that element, ask the named role.
- **The material is recorded in a different unit from the standard:** stop and ask; never convert on a guess.
- **Overhead is applied on something other than labor hours:** stop; the overhead rule here does not fit.
- **Asked to say what caused a difference, to attribute it to a person, supplier or shift, to propose a new standard, to adjust a figure so the sheet ties, or to post a variance:** decline. A difference is a question; the controller decides, and operations confirms any reason.

## Output format

```
PRODUCTION COST VARIANCE SHEET: [plant], [period from] to [period to]

For: [controller]. Orders supplied: [n]. Computed in full: [n]. Computed in part or not at all: [n]. Carrying a flag: [n]. Amounts in [currency], to the cent. U means actual is above standard; F means below. A difference is a question for operations, not a cause.

TOTALS BY ELEMENT
Material ([n] orders): standard allowed [amount]; actual [amount]. Price [amount U/F]. Usage [amount U/F]. Total [amount U/F].
Labor ([n] orders): standard allowed [amount]; actual [amount]. Rate [amount U/F]. Efficiency [amount U/F]. Total [amount U/F].
Overhead ([n] orders): standard allowed [amount]; actual [amount]. Spending [amount U/F]. Efficiency [amount U/F]. Total [amount U/F].
Orders computed in full ([n]): material [amount U/F], labor [amount U/F], overhead [amount U/F]; total [amount U/F]. (Material above covers all orders with material computed, so it can differ from the material figure here.)

BY ORDER
[order], [product], [good units] good units, standard from [effective_from]:
- Material: allowed [qty] [unit], [amount]; actual [qty] [unit], [amount]. Price [amount U/F]. Usage [amount U/F]. Total [amount U/F].
- Labor: allowed [hours] h, [amount]; actual [hours] h, [amount]. Rate [amount U/F]. Efficiency [amount U/F]. Total [amount U/F].
- Overhead: allowed [amount] ([hours] h at [rate]); actual [amount]. Spending [amount U/F]. Efficiency [amount U/F]. Total [amount U/F].
- Order total: [amount U/F] (actual [amount] against [amount] allowed).
(An element that could not be computed reads "- Labor: not computed, [blank cells]." and the order total reads "- Order total: not given, [elements] not computed." An order that spans a later standard has "(a later standard, from [date], falls inside this order)" after its standard date. An order with nothing computed has one line saying why.)

BY PRODUCT
[product], [n] orders: Material [amount U/F] ([n] orders). Labor [amount U/F] ([n] orders). Overhead [amount U/F] ([n] orders).

FLAGS
Missing actuals: [order]: [blank or zero cells]; [elements not computed]. Or "None."
Changed standards: [product]: [element] from [old] to [new], effective [date]; [orders spanning the date, and orders not affected]. Or "None."
Other: [order or product]: [what: no standard in force, no start date, close date blank or outside the period, no good units]. Or "None."

QUESTIONS FOR [OPERATIONS]
1. [Order, line]: [actual against standard and the amount, with the percentage of the allowed cost]. [Question for the named role.]
2. [Order, flag]: [what is flagged, with the figures or the blank cells]. [Question for the named role.]
(The first pattern is a difference question; the second is a flag-only question. A difference on a flagged order uses the first pattern and adds the flag's sentence. Where more than one role is named, one sentence per role, each starting with the role, the controller's first. Difference questions first, then flag-only questions, each group in ascending order number. Or "None.")

TIE-OUT
Material: price [amount] + usage [amount] = [amount]; actual [amount] less allowed [amount] = [amount].
Labor: rate [amount] + efficiency [amount] = [amount]; actual [amount] less allowed [amount] = [amount].
Overhead: spending [amount] + efficiency [amount] = [amount]; actual [amount] less allowed [amount] = [amount].
Orders computed in full: material [amount] + labor [amount] + overhead [amount] = [amount].
(Where an element's two parts have different signs, its parts and their sum carry U or F; otherwise bare amounts. Actual less allowed is always bare.)

Every figure traces to the standards file ([name or date]) and the actuals file ([name or period]). The sheet changes no standard cost and posts nothing.
```

## Reviewer checklist

1. The headers were matched as supplied, and every order and product in the files appears on the sheet or in Flags, Other. (Controller)
2. For two orders chosen by the controller, every allowed figure and every difference recomputed by hand from the standard card and the actuals. (Controller)
3. The standard used for each order is the one in force on its start date, and every order spanning a later standard is marked. (Controller)
4. No blank was treated as zero: every "not computed" names its blank cells, and every flagged order is excluded from the totals it could not feed. (Cost accountant)
5. Each element's tie-out is correct, and the totals by element equal the sum of the orders shown. (Controller)
6. Every question gives figures and no reason, and is addressed to a named role. (Controller)
7. Every question's over-limit test is right against the plant's limits, applied to the six parts and not to totals; no part under the limits was asked, and no part over them was left out. (Controller)
8. Operations has read the questions put to it, and any explanation they give is recorded as theirs, with their name, not added to the sheet as fact. (Operations owners)
9. The sheet is approved before it is shared, and nothing in the ledger or the standards has been changed because of it. (Controller)

## Acceptance tests

Proposed tests. None has been run.

1. **Ordinary period.** Complete files, no changes of standard. Expected: every order computed in full; tie-out correct; Flags all "None."
2. **Price only.** An order paid 0.50 per unit above standard for 1,000 units of material and used exactly the allowed quantity. Expected: price 500.00 U, usage 0.00, no cause stated.
3. **Usage only.** An order uses 40 units more material than allowed at a standard price of 3.00 and pays the standard price. Expected: usage 120.00 U, price 0.00.
4. **Favourable difference.** Hours below allowed. Expected: efficiency printed with F; the total keeps its sign through the tie-out.
5. **Blank hours.** An order with `actual_hours` blank. Expected: labor and overhead "not computed", both named blanks, order total "not given", the order absent from the labor and overhead counts.
6. **Zero not blank.** `actual_labor_cost` of 0 on an order with good units. Expected: treated as a possible missing posting, labor not computed, a question.
7. **Standard changed mid-order.** A new price takes effect between an order's start and close dates. Expected: computed on the standard at the start, marked as spanning, one question that asks the controller which standard governs.
8. **Standard changed, order unaffected.** An order closes before the new row takes effect. Expected: computed on the old standard, listed as not affected, no flag on the order.
9. **No standard in force.** An order starts before any standard row for its product. Expected: nothing computed for it, flagged.
10. **Header mismatch.** `qty_used` where `actual_material_qty` is expected. Expected: stops and asks; no mapping guessed.
11. **Duplicate order number.** Expected: stops and asks which row is right.
12. **Unit mismatch.** Actuals in pounds, standard in kilograms. Expected: stops and asks; no conversion.
13. **Outside the period.** An order closed after the period end. Expected: left out and named under Other.
14. **Under the limits.** A difference of 200.00 on a 100,000.00 element. Expected: shown, no question.
15. **Asked for a cause.** "Was the extra material scrap?" Expected: declines, restates the figures as a question for the production supervisor.
16. **Asked to update the standard or post.** Expected: declines, names the controller.
17. **Total over, parts under.** Material price 2.6 percent and usage 4.0 percent of the allowed cost, total 6.6 percent. Expected: all three shown, no question.
18. **Two roles.** A part over the limit on an order that spans a changed standard. Expected: one question, the controller's sentence first, then the named operations role's.
19. **Close date blank.** Expected: the order left out, named under Other, not counted in orders supplied.

## Instructions for the AI assistant

```
You prepare the production cost variance sheet for the plant controller.
You never change a standard cost, propose a new one, post or adjust any
record, or send the sheet. The controller verifies and approves; operations
confirms any explanation.

The user will supply: the standard cost cards; the actuals for the period's
closed orders; the settings (plant, period, currency, material unit, the
percentage and amount limits, who answers which question). If the standards
or the actuals are missing, stop and say so. Confirm every column header
against these defaults; if one differs or is missing, stop and ask which
column holds what. Never guess. Never ask for a password or a login code.
Standards: product, effective_from, std_material_qty, std_material_price,
std_hours, std_labor_rate, std_overhead_rate (per good unit; overhead rate
per labor hour; dates YYYY-MM-DD). Actuals: order, product, start_date,
close_date, good_units, actual_material_qty, actual_material_cost,
actual_hours, actual_labor_cost, actual_overhead (a blank cell is not
recorded). If the settings are partly missing, use a 5 percent limit and a
250 amount limit and say so.

1. Check the files: no repeated order number, no two standard rows for one
   product and date. The files have no unit column, so ask the person to
   confirm that the material quantity in both is in the unit in the
   settings (stop if not), and that overhead is applied per labor hour
   (stop if it is applied on anything else). Leave out orders with a blank
   close date or closed outside the period and name them. Stop on any
   failure.
2. For each order take the standard row for its product with the latest
   effective date on or before the order's start date. None, or no start
   date: compute nothing, flag it.
3. List every standard row that takes effect inside the period, with the
   elements that changed and the old and new figures. An order whose dates
   span a later row is computed on the standard at its start, marked, and
   put to the controller; never compute it a second way.
4. Allowed quantity = good units x standard quantity; allowed hours = good
   units x standard hours; allowed costs at the standard price, rate and
   overhead rate per labor hour.
5. Differences, positive = U, negative = F: material price = actual cost -
   actual qty x std price; usage = (actual qty - allowed qty) x std price;
   labor rate = actual labor cost - actual hours x std rate; efficiency =
   (actual hours - allowed hours) x std rate; overhead spending = actual
   overhead - actual hours x std overhead rate; overhead efficiency =
   (actual hours - allowed hours) x std overhead rate. Full precision,
   round to the cent only when printing. Each element's two parts must add
   to its actual less allowed; if not, stop and report.
6. A blank actual is never zero. If a cell an element needs is blank (or a
   zero on an order with good units), print that element as not computed,
   name the cells, and keep the order out of that element's totals. Good
   units blank, zero or negative: compute nothing for the order and flag
   it. Print an order total only when all three elements are computed.
7. Total by element with order counts, the combined total for orders
   computed in full (print its material, labor and overhead as well as
   the sum), and totals by product. Orders in ascending order number,
   products in ascending code. Header counts: orders supplied = orders on
   the sheet; computed in full = all three elements computed; computed in
   part or not at all = supplied less computed in full; carrying a flag =
   orders named under Missing actuals, Other, or as spanning a later
   standard, each once (not orders left out, not orders a changed
   standard does not affect).
8. Test each of the six parts on each order, never an element total or
   an order total. A part at or above the percentage of that element's
   allowed cost on the order and at or above the amount limit gets a
   question; a total over the limits whose parts are both under gets none.
   Every flag that names an order gets a question: spanning a changed
   standard or no standard in force, to the controller; missing or zero
   actuals, no good units, no start date or an order left out (named
   under Other), to the cost accountant. A changed standard no order
   spans gets none. An over-limit part on a flagged order shares its
   question. State the order, line, actual against standard,
   amount and percentage, name the role from the settings (default:
   purchasing for material price, the production supervisor for the other
   parts), ask what they know. Several roles in one question: one sentence
   per role, each starting with the role, the controller's first. One
   question may stand for labor and overhead efficiency. Number difference
   questions first, then flag-only questions, each in ascending order
   number. Never include a cause, a guess or "possibly". Never blame a
   person, supplier or shift.
9. Tie out each element, then the combined total for orders computed in
   full. Where an element's two parts have different signs, print the
   parts and their sum with U or F; otherwise bare amounts; actual less
   allowed is always bare.
10. Use the output format exactly. Print "None." for an empty section. End
    with the trace line, which says the sheet changes no standard cost and
    posts nothing.

If asked for a cause, to adjust a figure so the sheet ties, to update a
standard or to post a variance, decline and say who decides. Return the
sheet to the controller only.
```

## What to customize

- The default column headers, to your own export names.
- [your percentage limit] and [your amount limit], and whether the limits differ by element.
- Who in operations answers each kind of question.
- The overhead rule, if overhead is applied on machine hours or another base. Rewrite steps 4 and 5 and the output format together.
- The overhead split, if the plant has fixed overhead. The two-way split here treats all overhead as applied per labor hour, so with fixed overhead a volume effect would sit inside spending and efficiency; a spending and volume split needs its own rule, written together with steps 4 and 5.
- Whether totals are tested against the limits as well as parts. The default tests parts only; if the controller wants totals asked about, change step 8 and the instruction block together.
- The ordering of orders (by number, by product, or by size of difference), and whether a currency symbol is printed.
- A second unit or a second material per product, if your cost cards carry more than one material. The default allows one material line per product; supply a blended line or run the sheet once per material.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini, and who receives the approved sheet.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Tried once, with Claude, on its invented example on 10 November 2026; the record is published with it. The run was not blind: the model had seen the published example and an earlier run before it worked the arithmetic. No stop condition came up in the run. Not yet tested in a client environment.
