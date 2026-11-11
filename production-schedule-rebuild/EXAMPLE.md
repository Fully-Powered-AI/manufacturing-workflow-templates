# Production schedule rebuild: an invented example

*Illustrative example with invented data.* The company, the items, the orders, the work centres and every figure below are invented. "Company A" is an invented 30-person maker of steel shelving. The production planner runs the rebuild after a customer pulls an order forward and a rush order arrives; the sales lead, the purchasing lead and the plant manager answer the questions that depend on them. First come the inputs the planner supplied, in full, then the draft the capability returned.

## The inputs

### 1. Settings

```
Plan date: Monday 16 November 2026.
Weeks covered: 2026-11-16, 2026-11-23, 2026-11-30, 2026-12-07
Frozen weeks: 1 (the week of 2026-11-16)
Production planner: Production planner
Work centres: Cutting, Welding
```

### 2. Open orders (open_orders.csv)

```
order_id,item,quantity,due_week,type,priority
O-5101,S1,200,2026-11-16,firm,normal
O-5102,S2,80,2026-11-23,firm,normal
O-5103,S3,100,2026-11-23,firm,normal
O-5104,S2,60,2026-11-30,firm,normal
O-5105,S1,300,2026-11-16,firm,rush
O-5106,S3,50,2026-12-07,firm,normal
O-5107,S2,40,2026-12-07,firm,normal
O-5108,S1,50,2026-11-09,firm,normal
F-01,S2,100,2026-11-30,forecast,normal
F-02,S1,400,2026-12-14,forecast,normal
```

### 3. Routings (routings.csv)

```
item,work_centre,hours_per_unit
S1,Cutting,0.10
S1,Welding,0.20
S2,Cutting,0.30
S2,Welding,0.50
S3,Cutting,0.20
S3,Welding,0.40
```

### 4. Capacity (capacity.csv)

```
work_centre,week,available_hours
Cutting,2026-11-16,50
Cutting,2026-11-23,50
Cutting,2026-11-30,50
Cutting,2026-12-07,50
Welding,2026-11-16,60
Welding,2026-11-23,70
Welding,2026-11-30,70
```

### 5. Bills of material (bom.csv)

```
item,material,quantity_per_unit
S1,Steel strip,2
S1,Fastener kit,1
S2,Steel strip,6
S2,Fastener kit,4
S3,Steel strip,4
S3,Fastener kit,2
```

### 6. Material supply (material_supply.csv)

```
material,week,units,status
Steel strip,2026-11-16,1000,on_hand
Steel strip,2026-11-23,600,confirmed
Steel strip,2026-11-30,800,requested
Steel strip,2026-12-07,300,confirmed
Fastener kit,2026-11-16,800,on_hand
Fastener kit,2026-11-23,300,confirmed
Fastener kit,2026-12-07,200,confirmed
```

### 7. Current plan (current_plan.csv)

```
order_id,planned_week
O-5101,2026-11-16
O-5102,2026-11-23
O-5103,2026-11-30
O-5104,2026-11-30
O-5106,2026-12-07
O-5099,2026-11-23
```

## The draft

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
Room in a frozen week cannot be used without the planner's decision.

Material balances and shortages
Fastener kit
Firm orders: 2026-11-16 600; 2026-11-23 380; 2026-11-30 140; 2026-12-07 80
Firm plus forecast: 2026-11-16 600; 2026-11-23 380; 2026-11-30 -260; 2026-12-07 -320
Firm: covered. Firm plus forecast: first short 2026-11-30, largest shortfall 320 in 2026-12-07.
Short in 2026-11-30, used by: O-5104 240; F-01 400 (forecast).
Short in 2026-12-07, used by: O-5106 100; O-5107 160.
Unconfirmed supply: none supplied.
Steel strip
Firm orders: 2026-11-16 600; 2026-11-23 320; 2026-11-30 -40; 2026-12-07 -180
Firm plus forecast: 2026-11-16 600; 2026-11-23 320; 2026-11-30 -640; 2026-12-07 -780
Firm: first short 2026-11-30, largest shortfall 180 in 2026-12-07. Firm plus forecast: first short 2026-11-30, largest shortfall 780 in 2026-12-07.
Short in 2026-11-30, used by: O-5104 360; F-01 600 (forecast).
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
F-01: new, forecast, placed 2026-11-30.
O-5099: in the current plan for 2026-11-23 and not in the open orders; its load is not counted.

Not tested
Welding, 2026-12-07: capacity not supplied; its load of 40.0 is shown but not tested.

Decisions for the planner: 7
1. O-5105, a rush order for 300 S1 due in the frozen week of 2026-11-16 and not in the current plan. It would need 30.0 Cutting hours, 60.0 Welding hours, 600 Steel strip and 300 Fastener kit. The planner may need to ask the sales lead. Is the order to be placed, and in which week?
2. O-5108, an order for 50 S1 due the week of 2026-11-09, before the plan starts. It would need 5.0 Cutting hours, 10.0 Welding hours, 100 Steel strip and 50 Fastener kit. The planner may need to ask the sales lead. In which week is it to be built, if at all?
3. Welding is over by 10.0 hours in the week of 2026-11-23, on firm orders O-5102 and O-5103. The only known room in another week is 20.0 hours in the frozen week of 2026-11-16; 2026-12-07 has no capacity row. The planner may need to ask the plant manager and the sales lead. What is to be done about the 10.0 hours?
4. Welding is over by 10.0 hours in the week of 2026-11-30 only if forecast F-01 is built. The planner may need to ask the sales lead. Is F-01 to stay in the schedule in that week?
5. Fastener kit is short only if forecast F-01 is built: 260 in the week of 2026-11-30, and 320 at its largest in 2026-12-07, after confirmed receipts of 300 and 200. The planner may need to ask the purchasing lead. What is to be done about the shortage if F-01 is built?
6. Steel strip is short on firm orders from the week of 2026-11-30 (40), and 180 at its largest in 2026-12-07. With the forecast it is short from the same week (640), and 780 at its largest in 2026-12-07. A receipt of 800 for 2026-11-30 is requested and not confirmed; the balances do not count it. The planner may need to ask the purchasing lead. How is the shortage to be settled if the 800 is not confirmed?
7. O-5099 is in the current plan for the week of 2026-11-23 and is not among the open orders, so its load and materials are not counted. The planner may need to ask the sales lead. Is O-5099 cancelled, or is it missing from the open orders?

Check lines
Cutting, firm: weekly loads 104.0 = orders 104.0. Firm plus forecast: 134.0 = 134.0.
Welding, firm: weekly loads 190.0 = orders 190.0. Firm plus forecast: 240.0 = 240.0.
Fastener kit, firm: opening 800 + confirmed receipts 500 - use 1220 = 80, the closing balance. Firm plus forecast: 800 + 500 - 1620 = -320.
Steel strip, firm: opening 1000 + confirmed receipts 900 - use 2080 = -180, the closing balance. Firm plus forecast: 1000 + 900 - 2680 = -780.
Open order rows 10 = placed 7 + not placed 2 + beyond the horizon 1.

Draft for the Production planner's approval. No work order has been released, no material ordered and no record changed.
```
