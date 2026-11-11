# Production cost variance sheet: an invented example

*Illustrative example with invented data.* The plant, products, orders and every figure below are made up for this page. They stand for a small metal-parts plant closing October 2026, and describe nothing that happened anywhere.

## What the controller supplies

**Standard cost cards** (default headers; per good unit; overhead rate per labor hour):

```
product,effective_from,std_material_qty,std_material_price,std_hours,std_labor_rate,std_overhead_rate
B-100,2026-01-01,2.5,4.00,0.40,30.00,20.00
H-200,2026-01-01,6.0,5.00,0.75,30.00,20.00
H-200,2026-10-15,6.0,5.50,0.75,30.00,20.00
```

**Actuals for the closed orders** (a blank cell means not recorded):

```
order,product,start_date,close_date,good_units,actual_material_qty,actual_material_cost,actual_hours,actual_labor_cost,actual_overhead
WO-1001,B-100,2026-10-01,2026-10-06,1000,2600,10660.00,430,13115.00,8300.00
WO-1002,B-100,2026-10-08,2026-10-13,1200,2985,11940.00,470,14100.00,9300.00
WO-2001,H-200,2026-10-05,2026-10-12,400,2450,12495.00,310,9300.00,6200.00
WO-2002,H-200,2026-10-13,2026-10-20,500,3020,16610.00,372,11160.00,7400.00
WO-1003,B-100,2026-10-20,2026-10-27,800,2010,8040.00,,,
```

**Settings:** Plant A (invented); period 2026-10-01 to 2026-10-31; currency in the plant's own units; material unit kg, with both files confirmed as holding material quantities in kg; overhead applied per labor hour; percentage limit 5; amount limit 250. Questions: material price to purchasing; everything else to the production supervisor; missing postings to the cost accountant; which standard governs an order to the controller. Sheet goes to the controller.

## What comes out

```
PRODUCTION COST VARIANCE SHEET: Plant A, 2026-10-01 to 2026-10-31

For: the controller. Orders supplied: 5. Computed in full: 4. Computed in part or not at all: 1. Carrying a flag: 2. Amounts in the plant's currency, to the cent. U means actual is above standard; F means below. A difference is a question for operations, not a cause.

TOTALS BY ELEMENT
Material (5 orders): standard allowed 57,000.00; actual 59,745.00. Price 2,015.00 U. Usage 730.00 U. Total 2,745.00 U.
Labor (4 orders): standard allowed 46,650.00; actual 47,675.00. Rate 215.00 U. Efficiency 810.00 U. Total 1,025.00 U.
Overhead (4 orders): standard allowed 31,100.00; actual 31,200.00. Spending 440.00 F. Efficiency 540.00 U. Total 100.00 U.
Orders computed in full (4): material 2,705.00 U, labor 1,025.00 U, overhead 100.00 U; total 3,830.00 U. (Material above covers all orders with material computed, so it can differ from the material figure here.)

BY ORDER
WO-1001, B-100, 1,000 good units, standard from 2026-01-01:
- Material: allowed 2,500 kg, 10,000.00; actual 2,600 kg, 10,660.00. Price 260.00 U. Usage 400.00 U. Total 660.00 U.
- Labor: allowed 400.00 h, 12,000.00; actual 430.00 h, 13,115.00. Rate 215.00 U. Efficiency 900.00 U. Total 1,115.00 U.
- Overhead: allowed 8,000.00 (400.00 h at 20.00); actual 8,300.00. Spending 300.00 F. Efficiency 600.00 U. Total 300.00 U.
- Order total: 2,075.00 U (actual 32,075.00 against 30,000.00 allowed).

WO-1002, B-100, 1,200 good units, standard from 2026-01-01:
- Material: allowed 3,000 kg, 12,000.00; actual 2,985 kg, 11,940.00. Price 0.00. Usage 60.00 F. Total 60.00 F.
- Labor: allowed 480.00 h, 14,400.00; actual 470.00 h, 14,100.00. Rate 0.00. Efficiency 300.00 F. Total 300.00 F.
- Overhead: allowed 9,600.00 (480.00 h at 20.00); actual 9,300.00. Spending 100.00 F. Efficiency 200.00 F. Total 300.00 F.
- Order total: 660.00 F (actual 35,340.00 against 36,000.00 allowed).

WO-1003, B-100, 800 good units, standard from 2026-01-01:
- Material: allowed 2,000 kg, 8,000.00; actual 2,010 kg, 8,040.00. Price 0.00. Usage 40.00 U. Total 40.00 U.
- Labor: not computed, actual_hours and actual_labor_cost blank.
- Overhead: not computed, actual_overhead and actual_hours blank.
- Order total: not given, labor and overhead not computed.

WO-2001, H-200, 400 good units, standard from 2026-01-01:
- Material: allowed 2,400 kg, 12,000.00; actual 2,450 kg, 12,495.00. Price 245.00 U. Usage 250.00 U. Total 495.00 U.
- Labor: allowed 300.00 h, 9,000.00; actual 310.00 h, 9,300.00. Rate 0.00. Efficiency 300.00 U. Total 300.00 U.
- Overhead: allowed 6,000.00 (300.00 h at 20.00); actual 6,200.00. Spending 0.00. Efficiency 200.00 U. Total 200.00 U.
- Order total: 995.00 U (actual 27,995.00 against 27,000.00 allowed).

WO-2002, H-200, 500 good units, standard from 2026-01-01 (a later standard, from 2026-10-15, falls inside this order):
- Material: allowed 3,000 kg, 15,000.00; actual 3,020 kg, 16,610.00. Price 1,510.00 U. Usage 100.00 U. Total 1,610.00 U.
- Labor: allowed 375.00 h, 11,250.00; actual 372.00 h, 11,160.00. Rate 0.00. Efficiency 90.00 F. Total 90.00 F.
- Overhead: allowed 7,500.00 (375.00 h at 20.00); actual 7,400.00. Spending 40.00 F. Efficiency 60.00 F. Total 100.00 F.
- Order total: 1,420.00 U (actual 35,170.00 against 33,750.00 allowed).

BY PRODUCT
B-100, 3 orders: Material 640.00 U (3 orders). Labor 815.00 U (2 orders). Overhead 0.00 (2 orders).
H-200, 2 orders: Material 2,105.00 U (2 orders). Labor 210.00 U (2 orders). Overhead 100.00 U (2 orders).

FLAGS
Missing actuals: WO-1003: actual_hours, actual_labor_cost and actual_overhead blank; labor and overhead not computed.
Changed standards: H-200: material price from 5.00 to 5.50, effective 2026-10-15; WO-2002 (2026-10-13 to 2026-10-20) spans the date and is computed on 5.00; WO-2001 closed 2026-10-12 and is not affected.
Other: None.

QUESTIONS FOR OPERATIONS
1. WO-1001, labor efficiency: 430.00 h worked against 400.00 h allowed for 1,000 good units, 900.00 U, 7.5% of the 12,000.00 allowed. Production supervisor: what does production know about the hours on this order? Overhead efficiency on the same order (600.00 U, 7.5% of 8,000.00) is the same 30.00 hours at the overhead rate of 20.00, so this question stands for both.
2. WO-2002, material price: actual 16,610.00 for 3,020 kg, an average of 5.50 per kg, against a standard of 5.00; 1,510.00 U, 10.1% of the 15,000.00 allowed. The standard for H-200 material price changes to 5.50 on 2026-10-15, inside the order's dates. Controller: which standard governs this order? Purchasing: what does purchasing know about the price paid?
3. WO-1003, missing actuals: actual_hours, actual_labor_cost and actual_overhead are blank on an order closed 2026-10-27 with 800 good units. Cost accountant: have these been posted, and when will they be?

TIE-OUT
Material: price 2,015.00 + usage 730.00 = 2,745.00; actual 59,745.00 less allowed 57,000.00 = 2,745.00.
Labor: rate 215.00 + efficiency 810.00 = 1,025.00; actual 47,675.00 less allowed 46,650.00 = 1,025.00.
Overhead: spending 440.00 F + efficiency 540.00 U = 100.00 U; actual 31,200.00 less allowed 31,100.00 = 100.00.
Orders computed in full: material 2,705.00 + labor 1,025.00 + overhead 100.00 = 3,830.00.

Every figure traces to the standards file (standard cost cards, rows effective 2026-01-01 and 2026-10-15) and the actuals file (closed orders, October 2026). The sheet changes no standard cost and posts nothing.
```

## How to read it

Two things stand out, and both are questions rather than answers. WO-2002 shows a large material price difference, but a new standard price took effect partway through that order, so the controller has to decide which standard applies before the number means anything. WO-1003 has no labor or overhead figures yet, so the sheet shows nothing for them instead of a zero, and the totals say how many orders each line covers. The questions are asked of the six parts (material price and usage, labor rate and efficiency, overhead spending and efficiency), not of totals: WO-1001 material totals 660.00 U, 6.6% of its allowed cost, but its price (2.6%) and usage (4.0%) are each under the limit, so it is shown and not asked about. The sheet gives no reason for any difference. The controller verifies the arithmetic, and operations confirms any explanation.
