# Scrap and trim loss review: an invented example

*Illustrative example with invented data.* The plant, products, orders, codes and every figure below are made up for this page. They stand for a small metal-stamping plant reviewing one week in November 2026, and describe nothing that happened anywhere.

## What the plant manager supplies

**Scrap records** (default headers; quantities in kg):

```
scrap_ref,date,shift,machine,product,order,material,scrap_type,reason_code,scrap_qty,unit,note
S-01,2026-11-02,A,Press 1,BR-40,WO-501,CR-15,trim,SKL,360,kg,
S-02,2026-11-02,A,Press 1,BR-40,WO-501,CR-15,scrap,SET,24,kg,first-off parts
S-03,2026-11-02,B,Press 1,BR-40,WO-501,CR-15,trim,SKL,330,kg,
S-04,2026-11-02,B,Press 1,BR-40,WO-501,CR-15,scrap,DIM,48,kg,oversize after die change
S-05,2026-11-03,A,Press 1,BR-40,WO-501,CR-15,trim,SKL,220,kg,
S-06,2026-11-03,A,Press 1,BR-40,WO-501,CR-15,trim,END,40,kg,coil tail
S-07,2026-11-03,A,Press 2,PN-60,WO-502,CR-15,trim,SKL,300,kg,
S-08,2026-11-03,A,Press 2,PN-60,WO-502,CR-15,scrap,SUR,25,kg,
S-09,2026-11-03,B,Press 2,PN-60,WO-502,CR-15,trim,SKL,290,kg,
S-10,2026-11-03,B,Press 2,PN-60,WO-502,CR-15,scrap,,62,kg,
S-11,2026-11-04,A,Press 2,PN-60,WO-502,CR-15,trim,SKL,210,kg,
S-12,2026-11-05,A,Press 2,BR-40,WO-503,CR-15,trim,SKL,280,kg,
S-13,2026-11-05,A,Press 2,BR-40,WO-503,CR-15,scrap,DIM,16,kg,
S-14,2026-11-05,B,Press 2,BR-40,WO-503,CR-15,trim,SKL,200,kg,
S-15,2026-11-05,B,Press 2,PN-60,WO-502,CR-15,scrap,SET,35,kg,
S-16,2026-11-05,A,Press 2,BR-40,WO-503,CR-15,scrap,DIM,12,pcs,
S-17,2026-10-30,B,Press 1,BR-40,WO-499,CR-15,trim,SKL,150,kg,
```

**Production counts** (default headers; good units counted at the press, which finishes each part):

```
order,date,shift,machine,product,good_qty,rejected_qty
WO-501,2026-11-02,A,Press 1,BR-40,2000,30
WO-501,2026-11-02,B,Press 1,BR-40,1800,60
WO-501,2026-11-03,A,Press 1,BR-40,1200,0
WO-502,2026-11-03,A,Press 2,PN-60,800,10
WO-502,2026-11-03,B,Press 2,PN-60,700,25
WO-502,2026-11-04,A,Press 2,PN-60,500,0
WO-503,2026-11-05,A,Press 2,BR-40,1500,20
WO-503,2026-11-05,B,Press 2,BR-40,1000,15
```

**Material issues** (default headers):

```
issue_ref,date,order,material,issued_qty,returned_qty,unit
I-01,2026-11-02,WO-501,CR-15,4500,0,kg
I-02,2026-11-03,WO-501,CR-15,600,30,kg
I-03,2026-11-03,WO-502,CR-15,6200,0,kg
I-04,2026-11-05,WO-503,CR-15,4000,0,kg
```

**Material per good unit,** from the plant's specification sheet for steel coil CR-15 (the steel left in one finished part, not the steel drawn for it):

```
product,material,qty_per_good_unit,unit
BR-40,CR-15,0.80,kg
PN-60,CR-15,2.50,kg
```

**Reason code list:**

```
code,description,type
SET,setup and first-off parts,scrap
DIM,out of dimension,scrap
SUR,surface damage,scrap
SKL,blanking skeleton,trim
END,coil head and tail ends,trim
```

**Settings:** Plant C (invented); for the plant manager; period 2026-11-02 to 2026-11-06; unit kg; completed orders WO-501 and WO-502 (WO-503 is still running); prepared 2026-11-09; balance tolerance 2 percent; reason share 20 percent; shift gap 2.0 points. Questions on scrap records, production counts and improvement go to the production supervisor, on issues to the materials controller, and on reason codes to the quality lead.

## What comes out

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
WO-502, PN-60, CR-15: issued 6,200 less returned 0 = net 6,200. Good-unit material 5,000 (2,000 good units x 2.50). Scrap 122. Trim 800. Not accounted for 278, 4.5% of net issued; at or above the 2% tolerance, see section 8, item 3. Uses S-10, questioned in section 9, and S-15, questioned in section 8, item 2.
WO-503: not computed, not named as complete.

8. WHERE THE RECORDS DISAGREE
1. Rejected units with no scrap recorded: the production count for WO-503 on 2026-11-05, shift B, Press 2, shows 15 rejected units, and no scrap row of type scrap names WO-503 on that date, shift and machine (the only scrap row there for WO-503 is S-14, trim). Question for the production supervisor: what happened to the 15 rejected BR-40 units, and is there a scrap record for them?
2. Scrap with no matching production: S-15 (2026-11-05, shift B, Press 2, WO-502, PN-60, scrap, SET, 35) names an order that the production counts do not show on that date, shift and machine; they show WO-503, BR-40, on Press 2 that shift. S-15 is counted under PN-60, Press 2 and shift B, as recorded. Question for the production supervisor: which order and product does S-15 belong to?
3. Material balance: WO-502 has 278 of its net 6,200 issued not accounted for as good-unit material, scrap or trim, 4.5% against a 2% tolerance (I-03; S-07 to S-11 and S-15, of which S-10 is questioned in section 9 and S-15 in item 2; three production rows). Question for the materials controller: are all issues and returns for WO-502 in the export? Question for the production supervisor: is any scrap or trim from WO-502 not yet recorded?

9. ROWS NOT COUNTED, UNCLASSIFIED OR LEFT OUT
Not counted: S-16, unit pcs where the settings say kg (2026-11-05, shift A, Press 2, WO-503, scrap, DIM, 12 pcs). Question for the production supervisor: what weight of material do the 12 pieces on S-16 come to?
Unclassified: S-10, scrap, 62, code blank. Question for the production supervisor: which reason on the list applies to S-10?
Not recorded: None.
Left out of the period: S-17, 2026-10-30, 150.

10. IMPROVEMENT QUESTIONS FOR THE PRODUCTION SUPERVISOR
1. DIM (out of dimension) is the largest listed scrap reason: 64, 30.5% of the 210 scrap counted. Recorded on Press 1 for BR-40 (48, S-04) and on Press 2 for BR-40 (16, S-13). Recorded note on S-04: "oversize after die change". Unclassified scrap (62, S-10, section 9) is larger than DIM's lead of 5 over SET, so the order could change once S-10 is classified. What does production know about the out-of-dimension scrap on BR-40, and is it worth investigating or trialling?
2. SKL (blanking skeleton) is the largest listed trim reason: 2,190, 98.2% of the 2,230 trim counted. Recorded on Press 1 for BR-40 (910), on Press 2 for BR-40 (480) and on Press 2 for PN-60 (800). What does production know about the skeleton loss on each product, and is it worth investigating or trialling?
3. Press 2: shift B rate 18.7% against shift A 15.7%, a gap of 3.0 points against a threshold of 2.0. Shift A ran BR-40 1,500 good units and PN-60 1,300; shift B ran BR-40 1,000 and PN-60 700. Shift B's figures include S-10 (section 9) and S-15 (section 8, item 2), and its good units include the WO-503 run in section 8, item 1. What does production know about the difference between the two shifts on Press 2, and is it worth investigating or trialling?

Every figure traces to the scrap records (2026-11-02 to 2026-11-06, with S-17 from the week before), the production counts (2026-11-02 to 2026-11-05), the material issues (2026-11-02 to 2026-11-05) and the material per good unit (specification sheet, CR-15). Draft for the plant manager. No record has been changed and nothing has been sent.
```

## How to read it

The tables say where the steel went, and they agree with each other: products, presses, shifts, and presses by shift all add to the same 2,440 kg recorded loss against 11,000 kg in good parts. Most of it is trim, the skeleton left after blanking, so one improvement question is about skeleton loss on each product and not about rejected parts.

Three things in the records do not line up, and each is put to the person who keeps that record rather than settled on the page. The 15 rejected BR-40 parts on shift B of 5 November have no scrap entry. One setup entry names an order that was not on the press that shift. And 278 kg of the steel issued to WO-502 does not appear as good parts, scrap or trim. The Press 2 shift gap is shown with the product mix beside it and with the two questioned rows named, so nobody reads it as a verdict on a crew. The review gives no reason for any of it; the plant manager and production decide what is worth a closer look.
