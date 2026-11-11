# Production schedule rebuild: tried once on its example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in [example.md](example.md): the seven input blocks (settings, open orders, routings, capacity, bills of material, material supply and current plan). No client data was used. The run followed the fenced instruction block and the output format in the template, using the inputs only. The example's own draft was not read until after this output was written.

**Edited after this run, 10 November 2026.** Following an independent review, the template and the published example were edited after the run recorded here, and the run was not repeated. The output and the observations below are left as recorded, so where they describe the template or the example they describe them as they stood at the time of the run. The edits are listed under "Edited after this run" at the end.

## What came out

```
PRODUCTION SCHEDULE REBUILD: plan of 2026-11-16

For: Production planner. Weeks covered: 2026-11-16 to 2026-12-07. Frozen: 2026-11-16. Hours to one decimal; materials in the units supplied.
Inputs: open orders open_orders.csv; routings routings.csv; capacity capacity.csv; bills of material bom.csv; material supply material_supply.csv; current plan current_plan.csv.
Orders: 10 open rows. 7 placed (6 firm, 1 forecast). 2 not placed. 1 beyond the horizon.

Draft build schedule
2026-11-16 (frozen)
O-5101 S1 x 200, firm, due 2026-11-16
2026-11-23
O-5102 S2 x 80, firm, due 2026-11-23
O-5103 S3 x 100, firm, due 2026-11-23
2026-11-30
O-5104 S2 x 60, firm, due 2026-11-30
F-01 S2 x 100, forecast, due 2026-11-30
2026-12-07
O-5106 S3 x 50, firm, due 2026-12-07
O-5107 S2 x 40, firm, due 2026-12-07

Load by work centre (hours: firm / firm plus forecast / available)
Cutting: 2026-11-16 20.0 / 20.0 / 50.0; 2026-11-23 44.0 / 44.0 / 50.0; 2026-11-30 18.0 / 48.0 / 50.0; 2026-12-07 22.0 / 22.0 / 50.0
Welding: 2026-11-16 40.0 / 40.0 / 60.0; 2026-11-23 80.0 / 80.0 / 70.0; 2026-11-30 30.0 / 80.0 / 70.0; 2026-12-07 40.0 / 40.0 / capacity not supplied

Capacity conflicts
Welding, 2026-11-23: load 80.0 (80.0 firm + 0.0 forecast), available 70.0, over by 10.0. Over on firm orders. Orders: O-5102 40.0; O-5103 40.0. Room in other weeks, firm plus forecast: 2026-11-16 20.0 (frozen); 2026-11-30 0.0; 2026-12-07 capacity not supplied.
Welding, 2026-11-30: load 80.0 (30.0 firm + 50.0 forecast), available 70.0, over by 10.0. Over only with forecast. Orders: O-5104 30.0; F-01 50.0. Room in other weeks, firm plus forecast: 2026-11-16 20.0 (frozen); 2026-11-23 0.0; 2026-12-07 capacity not supplied.

Material balances and shortages
Fastener kit
Firm orders: 2026-11-16 600; 2026-11-23 380; 2026-11-30 140; 2026-12-07 80
Firm plus forecast: 2026-11-16 600; 2026-11-23 380; 2026-11-30 -260; 2026-12-07 -320
Firm: covered. Firm plus forecast: first short 2026-11-30, largest shortfall 320 in 2026-12-07.
Short in 2026-11-30, used by: O-5104 240; F-01 400.
Short in 2026-12-07, used by: O-5106 100; O-5107 160.
Unconfirmed supply: none supplied.
Steel strip
Firm orders: 2026-11-16 600; 2026-11-23 320; 2026-11-30 -40; 2026-12-07 -180
Firm plus forecast: 2026-11-16 600; 2026-11-23 320; 2026-11-30 -640; 2026-12-07 -780
Firm: first short 2026-11-30, largest shortfall 180 in 2026-12-07. Firm plus forecast: first short 2026-11-30, largest shortfall 780 in 2026-12-07.
Short in 2026-11-30, used by: O-5104 360; F-01 600.
Short in 2026-12-07, used by: O-5106 200; O-5107 240.
Unconfirmed supply: 800 requested for 2026-11-30. Largest firm-plus-forecast shortfall if all were confirmed: none.

Orders not placed
O-5105 S1 x 300, firm, due 2026-11-16, RUSH: due in a frozen week. Would need: Cutting 30.0, Welding 60.0; Steel strip 600, Fastener kit 300.
O-5108 S1 x 50, firm, due 2026-11-09: due before the plan starts. Would need: Cutting 5.0, Welding 10.0; Steel strip 100, Fastener kit 50.

Beyond the horizon
F-02 S1 x 400, forecast, due 2026-12-14.

Changes to the current plan, held for approval
O-5103: moves from 2026-11-30 to 2026-11-23.
O-5107: new, placed 2026-12-07.
F-01: new, forecast placed 2026-11-30.
O-5099: in the current plan for 2026-11-23 and not in the open orders; its load is not counted.

Not tested
Welding, 2026-12-07: capacity not supplied; its load of 40.0 is shown but not tested.

Decisions for the planner: 7
1. O-5105 (300 S1, RUSH, firm) is due in the frozen week of 2026-11-16 and is not in the current plan, so it was not placed. It would need Cutting 30.0 and Welding 60.0 hours, Steel strip 600 and Fastener kit 300. The planner may need to ask the sales lead. Is the order to be placed, and in which week?
2. O-5108 (50 S1, firm) is due 2026-11-09, before the plan starts, so it was not placed. It would need Cutting 5.0 and Welding 10.0 hours, Steel strip 100 and Fastener kit 50. The planner may need to ask the sales lead. Is the order still wanted, and in which week?
3. Welding is over by 10.0 hours in the week of 2026-11-23, on firm orders O-5102 (40.0) and O-5103 (40.0). Room in other weeks is 20.0 hours in the frozen week of 2026-11-16, 0.0 in 2026-11-30, and 2026-12-07 has no capacity row. The planner may need to ask the plant manager and the sales lead. How is the overload to be settled?
4. Welding is over by 10.0 hours in the week of 2026-11-30 only with forecast F-01 (50.0). Firm load is 30.0 against 70.0 available. The planner may need to ask the sales lead. Is F-01 to stay in the schedule in that week?
5. Fastener kit is short only with forecast: 260 in 2026-11-30 and 320 at its largest in 2026-12-07, with the confirmed receipts counted (300 and 200). Firm orders are covered. The planner may need to ask the purchasing lead and the sales lead. How is the shortage to be settled if F-01 is built?
6. Steel strip is short on firm orders from 2026-11-30 (40) and by 180 at its largest in 2026-12-07. A receipt of 800 for 2026-11-30 is requested and not confirmed, and is not counted. The planner may need to ask the purchasing lead. How is the shortage to be settled if the 800 is not confirmed?
7. O-5099 is in the current plan for 2026-11-23 and is not among the open orders, so its load and materials are not counted. The planner may need to ask the sales lead. Is O-5099 cancelled, or missing from the open orders?

Check lines
Cutting, firm: weekly loads 104.0 = orders 104.0. Firm plus forecast: 134.0 = 134.0.
Welding, firm: weekly loads 190.0 = orders 190.0. Firm plus forecast: 240.0 = 240.0.
Fastener kit, firm: opening 800 + confirmed receipts 500 - use 1220 = 80, the closing balance. Firm plus forecast: 800 + 500 - 1620 = -320.
Steel strip, firm: opening 1000 + confirmed receipts 900 - use 2080 = -180, the closing balance. Firm plus forecast: 1000 + 900 - 2680 = -780.
Open order rows 10 = placed 7 + not placed 2 + beyond the horizon 1.

Draft for the Production planner's approval. No work order has been released, no material ordered and no record changed.
```

## What was observed

- Every required part of the output format was produced, and nothing in the instructions told the run to stop: the headers, dates and values were all valid, and every check line tied.
- Compared with the published example, the figures were the same everywhere: placements, loads, both conflicts, all balances and shortfalls, the two orders not placed, the horizon order, the change list and the check lines. Nothing in either output is a fact that is not in the inputs.
- The wording differed in a few places. The example's decisions 1 and 6 offer options in the question ("moved into the frozen week, built in a later week, or taken back to the customer"; "what is to happen to O-5104, O-5106 and O-5107"). This run asked open questions instead, because the template says to recommend nothing unless asked. The example also marks forecast usage "(forecast)" in the shortage lines and writes the forecast change as "new, placed"; this run wrote "forecast placed" in the change line and did not add "(forecast)" labels.
- Places where the instructions needed a judgment:
  - The output format's "Orders not placed" line has no slot for RUSH, but the instruction says to mark rush orders. This run added RUSH, as the example does.
  - A work centre with a capacity row for some weeks but not others (Welding, 2026-12-07) is covered by the capacity-test rule and the acceptance tests, but the stop-conditions section only describes a work centre with no row in any week. This run listed the week under "Not tested", as the example does.
  - "Order the materials by name" was read as alphabetical order.
  - "New orders placed" and "forecast placed" are two kinds of change in the procedure, but the format has one "new, placed" line. This run combined them as "new, forecast placed".
  - The format does not say how to show which short-week users are forecast. This run left it out of the usage lines and said it in the decisions.
  - Where the room in a frozen week is stated (20.0 Welding hours in 2026-11-16), it sits next to an overload. It is stated as a fact and not as a suggestion, but a reader could take it as one.
- No client data, login or password was involved. The run was done once; it shows the template can be followed on this example, not how it performs in a real company. The checks by the production planner, the purchasing lead and the floor still need to happen with real files.

## Edited after this run

Made on 10 November 2026 after an independent review. None of these edits has been run. None changes a figure, a placement or a decision's facts in the example.

- **RUSH on the Orders not placed line.** The output format now has a slot for it, as the instruction block already said to mark rush orders.
- **A missing capacity row for one week.** The stop-conditions section now covers a work centre with no row for one week as well as for every week.
- **New orders and forecast.** Procedure step 8 now lists new orders, firm or forecast, on one line; the format reads "new[, forecast], placed [week]", and the example's F-01 line reads "new, forecast, placed".
- **Forecast users in the shortage lines.** The format now marks forecast orders with "(forecast)", as the example does.
- **Alphabetical order.** Decisions on materials are now stated to be in alphabetical order by name.
- **Room in a frozen week.** The format now carries a line that room in a frozen week cannot be used without the planner's decision, whenever a frozen week is listed as room; the example shows it.
- **Two example questions.** Decisions 1 and 6 in the example now ask open questions, as this run did, because the template recommends nothing unless asked.
- **Review points, second round.** Wording only, none run: decision 3 and decision 6 in the example now state room and shortage more exactly (decision 6 adds the firm-plus-forecast figures already shown in the balances); the capacity-file stop condition reads "a work centre and week repeat"; the planning-week length is no longer offered as a customization; the profile says "each order that can be placed"; the format says the frozen-room line appears once, after all conflicts.
