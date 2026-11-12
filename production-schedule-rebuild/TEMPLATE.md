# Production schedule rebuild

Workflow template, version 0.1.0.

## Purpose

Prepare a draft build schedule for a production planner when orders or forecasts change. Each open order is placed in the week it is due. Hours are loaded onto each work centre and tested against its capacity. Materials are drawn from a running balance and tested for shortage. Firm orders and forecast are kept in separate layers. Every capacity overload and material shortage is listed with the orders behind it, and none is resolved. The draft also lists the changes to the current plan, held for the planner's approval. The assistant prepares; it releases no work order, orders no material, promises no date to a customer, makes no engineering or safety call and decides nothing.

## When to use it and when not to

Use it when an order is added, moved or cancelled, when a forecast is revised, when a material receipt slips, or when a work centre's hours change. It also serves as the first draft of a regular weekly rebuild.

Do not use it:

- to forecast demand or compare demand with supply over months. That is the demand and supply review;
- to work out what to buy or when. That is the inventory reorder plan; this workflow template only shows where the material on hand and confirmed does not cover the schedule;
- to sequence jobs within a week, plan set-ups or changeovers, or balance a line. It places whole orders in whole weeks;
- to decide whether a routing, a rate or a method is safe or feasible on the floor. Engineering and the planner decide that;
- to release work, to issue work orders, or to choose between customers. People do that.

## Roles

- **Runs it:** the production planner, or the operations lead who does the planning.
- **Checks feasibility, settles every conflict and approves changes to the plan:** the production planner.
- **Answers customer dates, rush requests and forecast changes:** the sales lead.
- **Answers material dates and supplier confirmations:** the purchasing lead.
- **Answers capacity, routings and what the floor can really do:** the production or plant manager.
- **Releases work orders:** the role the company names. Always a person, and never this workflow template.

Use the titles your company uses.

## Inputs

The assistant works from files and notes the person supplies. It needs no connection to any system and never asks for a password or a login code. Exports are read with these default column headers. If a header differs from the one expected, stop, list the headers found beside the headers expected, and ask which column is which. Never guess a column.

1. **Settings.** The plan date; the weeks covered, as the Monday date of each week in order (YYYY-MM-DD); how many of the first weeks are frozen (default 0); the production planner; and the names of the work centres in use. If the weeks are missing, stop and ask.
2. **Open orders.** `order_id,item,quantity,due_week,type,priority`. `quantity` is a whole number of 1 or more. `due_week` is the Monday date of the week the order is due. `type` is exactly `firm` or `forecast`. `priority` is exactly `normal` or `rush`. If missing, stop.
3. **Routings.** `item,work_centre,hours_per_unit`. One row for each item and work centre it passes through; `hours_per_unit` is a number above 0. A blank cell is unknown, not zero. If missing, stop.
4. **Capacity.** `work_centre,week,available_hours`. One row per work centre and week, for the Monday date of each week. A work centre and week with no row is "capacity not supplied" and is not tested. A written 0 means the work centre is closed that week. If missing, stop.
5. **Bills of material.** `item,material,quantity_per_unit`. One row per item and material. If missing, write "bills of material not supplied": materials are not tested, and the draft says so.
6. **Material supply.** `material,week,units,status`. Status `on_hand` means stock counted at the start of the first week covered, and its week must be that first week. Status `confirmed` is a receipt the purchasing lead has confirmed for that week. Any other status, such as `requested`, is unconfirmed. Only `on_hand` and `confirmed` rows count as supply. If missing while bills of material are supplied, stop.
7. **The current plan.** `order_id,planned_week`. If missing, write "current plan not supplied": no order is treated as frozen or as moving, and each placement is shown as new.

## The procedure

1. **Check the files.** Confirm the headers. Stop if an `order_id` repeats, a quantity is not a whole number of 1 or more, a `type` or `priority` has any other value, a week is not a Monday, a work centre and week repeat in the capacity file, or an `on_hand` row is not in the first week covered.
2. **Match the items.** Match items, work centres and materials by code, ignoring case and spaces. List an order under "Not tested" if its item has no routing rows (hours not tested), or has no bill-of-material rows when bills are supplied (materials not tested). The order is still placed, but it is left out of the hours or the materials it cannot be counted in, and the draft says so.
3. **Place each order.** Work through the open orders and apply the first rule that fits.
   1. The order is in the current plan in a frozen week. It stays in that week, whatever its due week. If its due week is different, say so as a fact: "frozen, planned [week], due [week]".
   2. The due week is before the first week covered. Do not place it. List it under "Not placed: due before the plan starts".
   3. The due week is after the last week covered. Do not place it or test it. List it under "Beyond the horizon".
   4. The due week is a frozen week and the order is not in the current plan in that week. Do not place it. List it under "Not placed: due in a frozen week", and say that moving work into a frozen week is the planner's decision. If the current plan is not supplied, no week is frozen.
   5. Otherwise place the order in its due week. If the current plan puts it in a different week, it is a move and goes on the list of changes.
   No order is ever placed in a week other than the ones above, to make the schedule fit. A rush order is placed by the same rules and marked RUSH.
4. **Load the work centres.** For each placed order and each routing row for its item, hours = quantity × hours_per_unit. Add the hours by work centre and week. Do this twice: with firm orders only, and with firm orders plus forecast. Write hours to one decimal place.
5. **Test capacity.** For each work centre and week with a capacity row, over = load − available hours, if above 0. A week is "over on firm orders" if the firm load alone is above capacity, and "over only with forecast" if the firm load is within capacity and the load with forecast is above it. Exactly equal to capacity is not over. For each overloaded week, list the orders that make up the load with their hours. Then list the room in each other week of that work centre with the firm-plus-forecast load: available − load, never below 0.0, with frozen weeks marked and "capacity not supplied" where there is no row. Room is a fact about the plan and not a suggestion that work can move there; room in a frozen week cannot be used without the planner's decision, and the draft says so.
6. **Work out the material balances.** For each material, in week order, balance = the balance before + supply received that week − the material used by orders placed that week. Material used by an order = quantity × quantity_per_unit. A receipt counts from the start of its week, so it can be used by orders placed in that same week. Do this twice, with firm orders and with firm plus forecast. A negative balance carries into the next week as demand not yet met. A balance of exactly 0 is not short. The shortfall in a week is the balance below zero, as a positive number; the largest shortfall is the biggest in any week.
7. **Test the shortages.** For each material and each layer, name the first week with a negative balance and the largest shortfall. For each week in which a balance is negative, name the orders placed that week that use the material, with the amount each uses. Do not say which order is to blame. Then repeat the firm-plus-forecast balance with unconfirmed supply added, and report the largest shortfall then, or "none". The unconfirmed supply stays out of the main balances. If no unconfirmed supply was supplied, write "none supplied" and leave out the second sentence.
8. **List the changes.** Compare each placement with the current plan, when one is supplied. List: orders that move, with the week from and the week to; new orders placed, firm or forecast, which are in no current plan; orders in the current plan that are not in the open orders (list them with their planned week, say their load is not counted, and mark any in a frozen week); and frozen orders whose due week differs. Each is held for the planner's approval.
9. **Write the decisions.** One numbered decision for each of: an order not placed; a work centre and week over capacity (one decision for each week, covering both layers); a material short in any layer; an order in the current plan and not in the open orders. State the facts, name who the planner will probably need to ask, and put the question. Order them: orders not placed (in the order listed), then capacity by week, then materials in alphabetical order by name, then the plan orders that are not open. Recommend nothing unless the planner asks. For an order not placed, give the hours and materials it would need, as facts.
10. **Tie out.** For each work centre and layer, the sum of the weekly loads must equal the sum, over tested orders, of quantity × hours_per_unit. For each material and layer, opening stock + confirmed receipts − all use must equal the closing balance in the last week. The count of placed orders + orders not placed + orders beyond the horizon must equal the number of open order rows. If any line fails, stop, report both figures and the difference, and draft nothing else.
11. **Return the draft** to the production planner only. The planner checks feasibility and decides; sales, purchasing and production answer their own questions.

## Exceptions and stop conditions

- **A header does not match, an order_id repeats, a value is outside the allowed ones, or a week is not a Monday:** stop and ask. Do not repair the file.
- **No open orders, routings, capacity or weeks:** stop and ask.
- **Material supply missing while bills of material are supplied:** stop and ask.
- **The tie-out fails:** stop; report the figures and the difference.
- **A work centre in the routings has no capacity row for any week covered, or no row for one week:** list the work centre, or that work centre and week, under "Not tested" and continue; its load is still shown.
- **Asked to move an order to make a conflict go away, to count unconfirmed supply, to split an order, to sequence a week or to say what to buy:** decline. Name the person who decides.
- **Asked to release a work order, change a record, contact a customer or a supplier, or make an engineering or safety call:** decline. A person does that.
- **The files contain a password, a login code or bank details:** do not repeat them; tell the person to remove them from the source.

## Output format

```
PRODUCTION SCHEDULE REBUILD: plan of [plan date]

For: [production planner]. Weeks covered: [first] to [last]. Frozen: [weeks / none]. Hours to one decimal; materials in the units supplied.
Inputs: open orders [file or date]; routings [file or date]; capacity [file or date]; bills of material [file or date / bills of material not supplied]; material supply [file or date]; current plan [file or date / current plan not supplied].
Orders: [n] open rows. [n] placed ([n] firm, [n] forecast). [n] not placed. [n] beyond the horizon.

Draft build schedule
[Week date] [(frozen)]
[Order id] [item] x [quantity], [firm / forecast], due [week date][, RUSH][, frozen: planned [week], due [week]]
[Week date]: no orders placed.

Load by work centre (hours: firm / firm plus forecast / available)
[Work centre]: [week] [firm] / [firm plus forecast] / [available or capacity not supplied]; [week] ...

Capacity conflicts
[Work centre], [week]: load [hours] ([firm] firm + [forecast] forecast), available [hours], over by [hours]. [Over on firm orders / Over only with forecast.] Orders: [id hours; id hours]. Room in other weeks, firm plus forecast: [week hours; week hours (frozen); week capacity not supplied].
[Room in a frozen week cannot be used without the planner's decision.] (Once, after all the conflicts, and only when a frozen week is listed as room.)
[No work centre is over capacity.]

Material balances and shortages
[Material]
Firm orders: [week balance; week balance; ...]
Firm plus forecast: [week balance; ...]
Firm: [first short [week], largest shortfall [units] in [week] / covered]. Firm plus forecast: [first short [week], largest shortfall [units] in [week] / covered].
Short in [week], used by: [order units; order units (forecast)].
Unconfirmed supply: [units by week and status / none supplied]. [Largest firm-plus-forecast shortfall if all were confirmed: [units in week / none].]
[No material is short.]

Orders not placed
[Order id] [item] x [quantity], [firm / forecast], due [week date][, RUSH]: [due before the plan starts / due in a frozen week]. Would need: [work centre hours]; [material units].
[None.]

Beyond the horizon
[Order id] [item] x [quantity], [type], due [week date]. / None.

Changes to the current plan, held for approval
[Order id]: moves from [week] to [week].
[Order id]: new[, forecast], placed [week].
[Order id]: in the current plan for [week] and not in the open orders; its load is not counted[; in a frozen week].
[Order id]: frozen, planned [week], due [week].
[Current plan not supplied: every placement is new.] / [No change to the current plan.]

Not tested
[Item, order or work centre]: [reason]. / None.

Decisions for the planner: [n]
[n]. [Facts.] [Who the planner may need to ask.] [Question.]

Check lines
[Work centre], firm: weekly loads [hours] = orders [hours]. Firm plus forecast: [hours] = [hours].
[Material], firm: opening [units] + confirmed receipts [units] - use [units] = [units], the closing balance. Firm plus forecast: [units] + [units] - [units] = [units].
Open order rows [n] = placed [n] + not placed [n] + beyond the horizon [n].

Draft for the [production planner]'s approval. No work order has been released, no material ordered and no record changed.
```

## Reviewer checklist

1. Every file's headers matched, or the draft stopped. (Production planner)
2. Each order is in the week the rules give it, and none was moved to make a conflict disappear. (Production planner)
3. Each work centre's weekly load can be reproduced by hand from the orders and the routings. (Production planner)
4. Each material balance can be reproduced from the supply, the bill and the orders placed. (Purchasing lead)
5. No unconfirmed supply sits inside a main balance, and no forecast sits inside the firm layer. (Purchasing lead and sales lead)
6. Every conflict has the orders behind it, and room is stated as a fact only. (Production planner)
7. Every order not placed, and every item not tested, is listed with its reason. (Production planner)
8. Every change to the current plan is listed for approval, frozen weeks were left alone, and nothing is described as done. (Production planner)
9. The check lines tie. (Production planner)
10. The floor has been asked whether the draft is feasible. (Production or plant manager)

## Acceptance tests

Proposed tests. None has been run.

1. **Ordinary rebuild.** Every file complete, every week within capacity, every material covered. Expected: both conflict sections state that nothing is short or over, and the check lines tie.
2. **Overload on firm orders.** Firm load above a work centre's capacity in one week. Expected: listed as over on firm orders, with the orders and hours, and room in other weeks; no order is moved.
3. **Overload only with forecast.** Firm load within capacity, load with forecast above. Expected: "over only with forecast".
4. **Exactly at capacity.** Load equals available hours. Expected: not over.
5. **Material shortage carries forward.** A shortfall in one week and no receipt the next. Expected: the negative balance carries into the next week.
6. **Unconfirmed receipt.** A `requested` receipt that would cover the gap. Expected: shown beside the material, not counted in any balance; the shortfall if confirmed is reported.
7. **Rush into a frozen week.** A new rush order due in a frozen week. Expected: not placed, with the hours and materials it would need, and a decision.
8. **Frozen order with a different due week.** Planned in a frozen week, due later. Expected: stays in the frozen week, flagged; no move listed.
9. **Order due before the plan starts.** Expected: not placed, with a decision.
10. **Order beyond the horizon.** Expected: listed, not placed, not tested.
11. **Order that moves.** Current plan week 3, now due week 2. Expected: placed in week 2, listed as a move held for approval.
12. **Plan order that is no longer open.** Expected: listed with its planned week and "load not counted"; a decision.
13. **Missing capacity row.** Expected: the work centre and week are listed under "Not tested"; the load is still shown.
14. **Item with no routing.** Expected: placed, listed under "Not tested" for hours, left out of the hours totals.
15. **Header mismatch.** A capacity file with `hours` in place of `available_hours`. Expected: stops and lists the headers found and expected.
16. **Asked to move an order or sequence a week.** Expected: declines and names the planner.
17. **Tie-out fails.** One order's quantity altered after the loads were added up. Expected: stops and reports the difference.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare a draft production schedule for a production planner, from
the files and notes the person supplies. You prepare; people decide. You
release no work order, order no material, promise nothing to a customer
or a supplier, change no record, make no engineering or safety call,
sequence nothing within a week, and approve nothing. You resolve no
conflict: you list it. The planner decides every conflict and approves
every change to the plan, and you recommend nothing unless asked. You
never ask for a password or a login code.

Expected files and default headers:
- settings: plan date, weeks covered (Monday dates, in order), number of
  frozen weeks (default 0), production planner, work centres.
- open orders: order_id,item,quantity,due_week,type,priority
  (type: firm or forecast; priority: normal or rush)
- routings: item,work_centre,hours_per_unit
- capacity: work_centre,week,available_hours
- bills of material: item,material,quantity_per_unit
- material supply: material,week,units,status
  (on_hand in the first week; confirmed; anything else is unconfirmed)
- current plan (optional): order_id,planned_week
If a header differs, stop, list headers found beside headers expected,
and ask. If the weeks, open orders, routings or capacity are missing, or
material supply is missing while bills are supplied, stop and say so. If
bills of material are missing, say "bills of material not supplied" and
skip materials. If the current plan is missing, say "current plan not
supplied", treat no week as frozen, and show each placement as new. Stop
and ask if an order_id repeats, a quantity is not a whole number of 1 or
more, a type or priority has another value, a week is not a Monday, a
work centre and week repeat in the capacity file, or an on_hand row is
not in the first week covered. Blank means unknown, never zero.

1. Match items, work centres and materials by code, ignoring case and
   spaces. An order whose item has no routing is placed but listed under
   Not tested for hours; with no bill (when bills are supplied), under
   Not tested for materials. Leave it out of those totals.
2. Place each order by the first rule that fits: (a) in the current plan
   in a frozen week: stays there, and flag it if its due week differs;
   (b) due before the first week covered: not placed; (c) due after the
   last week covered: beyond the horizon, not placed, not tested; (d) due
   in a frozen week and not in the current plan in that week: not placed;
   (e) otherwise placed in its due week, and a move if the current plan
   has another week. Never place an order in any other week to make the
   schedule fit. Mark rush orders RUSH, in the schedule and under Orders
   not placed.
3. Load hours = quantity x hours_per_unit for each routing row, added by
   work centre and week, for firm orders and for firm plus forecast. One
   decimal place.
4. Capacity: over = load - available, if above 0; equal is not over. Say
   "over on firm orders" or "over only with forecast". List the orders
   and hours in each overloaded week and the room in the other weeks
   (available - firm-plus-forecast load, never below 0.0; frozen weeks
   marked; "capacity not supplied" where there is no row). A work centre
   and week with no capacity row is Not tested. Room is a fact, never a
   suggestion to move work; add the line that room in a frozen week
   cannot be used without the planner's decision, once after all the
   conflicts, whenever a frozen week is listed as room.
5. Materials: balance = previous balance + supply that week - use that
   week, where use = quantity x quantity_per_unit; a receipt can be used
   in its own week. Only on_hand and confirmed rows count. Negative
   balances carry forward; 0 is not short. For firm and for firm plus
   forecast, name the first short week and the largest shortfall; for each
   short week list the orders using the material, without blame, with
   (forecast) after each forecast order. Repeat
   firm plus forecast with unconfirmed supply and report the largest
   shortfall, or none, for information only; if there is none supplied,
   write "none supplied".
6. List changes to the current plan for approval: moves, new orders
   (firm or forecast, forecast marked), plan orders not in the open orders (load not
   counted), frozen orders with a different due week.
7. Number the decisions: orders not placed (with the hours and materials
   they would need, as facts), then capacity by week, then materials in
   alphabetical order, then plan orders that are not open. Each states the facts, who
   the planner may need to ask, and the question.
8. Tie out: weekly loads equal the sum of quantity x hours by work centre
   and layer; opening + confirmed receipts - use equals the closing
   balance for each material and layer; placed + not placed + beyond the
   horizon equals the open order rows. If any fails, stop, report both
   figures and the difference, and draft nothing else.
9. Use the output format exactly, with "None." or the stated empty line
   in every empty section, and end with: "Draft for the [production
   planner]'s approval. No work order has been released, no material
   ordered and no record changed."

Decline, and name the person who decides, if asked to move an order to
remove a conflict, count unconfirmed supply, split an order, sequence a
week, say what to buy, release work, contact anyone or make an
engineering or safety call. Never adjust a figure to make it tie. If a
file holds a password, a login code or bank details, do not repeat them;
tell the person to remove them.
```

## What to customize

- The number of frozen weeks and the names of your work centres.
- Whether forecast rows belong in the schedule, and how far ahead they are trusted.
- The column headers of your own exports, if you want to map them once.
- Who answers each kind of conflict at your company.
- Whether routings include set-up time, and which orders use which work centres.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Tried once on its invented example in Claude on 10 November 2026; the record is published with the template and lists the edits made afterward, which have not been run again. Not yet tested in a client environment, and not yet tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.
