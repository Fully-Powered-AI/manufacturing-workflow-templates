# RFQ clarification list: an invented example

*Illustrative example with invented data.* The company, the people, the suppliers, the part numbers and every figure below are made up. It shows the inputs a buyer supplies and the list that comes out.

## The situation

Quillfeather Assemblies, an invented maker of enclosures, has sent a request for quotation, RFQ-2611-04, for four sheet-metal and turned parts to three suppliers. The buyer is Priya. The responsible engineer is Tomas. Today is Monday 16 November 2026. Priya runs the capability to see where the request stands. The working days are Monday to Friday and no day is closed.

## What the buyer supplies

**Request cover details**

- Reference RFQ-2611-04, issued Friday 6 November 2026.
- Quote due: Friday 20 November 2026.
- Delivery location: Quillfeather Assemblies, Unit 4 goods-in.
- Currency: blank.
- How long a quote must stand: blank.
- Certificates or inspection: "Material certificates required."
- Suppliers: Supplier A, Supplier B, Supplier C.

**Request lines**

```
Line | Part number | Description    | Revision | Quantity | Unit | Material                     | Finish              | Delivery date | Drawing
1    | QA-1042     | Mounting bracket | C      | 500      | ea   | 5052-H32 aluminium, 3 mm     | Clear anodize       | 2027-01-18    | QA-1042
2    | QA-1043     | Hinge plate    | B        | 250      | ea   | 304 stainless, 2 mm          |                     | 2027-01-18    | QA-1043
3    | QA-2210     | Shaft collar   | A        |          | ea   | 1045 steel                   | Black oxide         | 2027-02-01    | QA-2210
4    | QA-3305     | Cover panel    | D        | 100      | ea   | 5052-H32 aluminium, 2.5 mm   | Powder coat to PS-07| 2027-02-01    | QA-3305
```

**Document register**

```
Document | Title                  | Revision | Date       | Used by lines
QA-1042  | Mounting bracket       | D        | 2026-10-02 | 1
QA-1043  | Hinge plate            | B        | 2026-08-14 | 2
QA-2210  | Shaft collar           | A        | 2026-06-30 | 3
QA-3305  | Cover panel            | D        | 2026-09-21 | 4
PS-07    | Powder coat finish spec| 3        | 2026-05-11 | 4
```

**Drawing text, typed in from the title blocks and notes**

- QA-1042, title block Rev D. Material 5052-H32, 3 mm. Finish: clear anodize. General tolerance: ±0.2 unless stated. View 1 shows hole spacing 60 ±0.05. Note 3: "Hole spacing ±0.1."
- QA-1043, title block Rev B. Material 304 stainless, 2 mm. Note 1: "Deburr and passivate." Dimensions shown: overall length 75, width 40, hole centres 55. No tolerance on any of them. No general tolerance note.
- QA-2210, title block Rev A. Material 1045 steel. Finish: black oxide. General tolerance: ±0.1 unless stated. Note 2: "Bore to give a close running fit on shaft."
- QA-3305, title block Rev D. Material 5052-H32, 3 mm. General tolerance: ±0.3 unless stated. Note 1: "Powder coat to PS-07 rev 2."

**The buyer's notes**

- 10 November 2026: sent clarification 1 to Supplier A, Supplier B and Supplier C by email, asking each to state what it had assumed for the currency, the quote validity, the finish on line 2 and the quantity on line 3. Reply requested within three working days.

**The engineer's rulings**

- 13 November 2026, Tomas, on L4-SPEC: "PS-07 revision 3 applies to line 4. The drawing note citing revision 2 is out of date."

**Supplier answers**

```
Date received | Supplier   | Item ID | Answer
2026-11-12    | Supplier A | RFQ-CUR | USD.
2026-11-12    | Supplier A | L3-QTY  | Assumed 300 pieces.
2026-11-13    | Supplier B | RFQ-CUR | GBP.
2026-11-13    | Supplier B | L2-FIN  | Passivation assumed, per the drawing note.
2026-11-13    | Supplier B | L1-REV  | Quoting to the drawing as attached, Rev D.
2026-11-13    | Supplier A | L2-TOL1 | We would apply ±0.1 to dimensions without a tolerance.
```

## What comes out

```
RFQ CLARIFICATION LIST: RFQ-2611-04

For: Priya, with Tomas (responsible engineer). Run on 2026-11-16. Quote due 2026-11-20 (4 working days left). Suppliers: Supplier A, Supplier B, Supplier C.
Package read: 4 lines; 5 documents in the register; drawing text read for 4 of 4 drawings.

Summary: 10 items. Waiting for the buyer's value: 4. Waiting for the engineer: 5. Settled by the engineer: 1. Closed by the buyer: 0.

1. Missing details
RFQ-CUR Request: the currency is blank. No other document states it. Why it matters: quotes in different currencies cannot be set side by side. Settled by: the buyer. Status: Waiting for the buyer's value.
RFQ-VAL Request: how long a quote must stand is blank. No other document states it. Why it matters: the buyer cannot tell how long a price stands. Settled by: the buyer. Status: Waiting for the buyer's value.
L2-FIN Line 2, QA-1043: the finish is blank. Drawing QA-1043, note 1, says "Deburr and passivate." Why it matters: the finish sets the price and the process route. Settled by: the buyer. Status: Waiting for the buyer's value.
L3-QTY Line 3, QA-2210: the quantity is blank. No other document states it. Why it matters: there is no quantity to price. Settled by: the buyer. Status: Waiting for the buyer's value.

2. Conflicts between documents (for the responsible engineer)
L1-REV Line 1: the request line, Revision, says "C"; the document register, QA-1042 Revision, says "D"; and the QA-1042 title block says "Rev D". Why it matters: the supplier may price a different revision. Settled by: the responsible engineer. Status: Waiting for the engineer.
L4-MAT Line 4: the request line, Material, says "5052-H32 aluminium, 2.5 mm"; drawing QA-3305, material, says "5052-H32, 3 mm". Why it matters: material and thickness set the price. Settled by: the responsible engineer. Status: Waiting for the engineer.
L4-SPEC Line 4: drawing QA-3305, note 1, says "Powder coat to PS-07 rev 2"; the document register, PS-07 Revision, says "3". Why it matters: the supplier may work to a different revision of the specification. Settled by: the responsible engineer. Status: Settled by the engineer (note of 2026-11-13).

3. Ambiguous tolerances (for the responsible engineer)
L1-TOL1 Line 1, QA-1042, view 1 and note 3: "60 ±0.05" and "Hole spacing ±0.1." Kind: (b) stated twice. Why it matters: the supplier cannot meet both. Settled by: the responsible engineer. Status: Waiting for the engineer.
L2-TOL1 Line 2, QA-1043, dimensions: "75", "40" and "55" are shown with no tolerance, and the drawing has no general tolerance note. Kind: (a) none stated. Why it matters: the supplier has to guess how closely to make it. Settled by: the responsible engineer. Status: Waiting for the engineer.
L3-TOL1 Line 3, QA-2210, note 2: "Bore to give a close running fit on shaft." Kind: (c) words only. Why it matters: the requirement cannot be measured. Settled by: the responsible engineer. Status: Waiting for the engineer.

4. Supplier answers record
Messages sent, as the buyer reported: clarification 1, 2026-11-10, Supplier A, Supplier B, Supplier C, items RFQ-CUR, RFQ-VAL, L2-FIN, L3-QTY, reply date 2026-11-13.
RFQ-CUR, Supplier A, 2026-11-12: "USD." Reading: answers the question asked; differs from Supplier B.
RFQ-CUR, Supplier B, 2026-11-13: "GBP." Reading: answers the question asked; differs from Supplier A.
L3-QTY, Supplier A, 2026-11-12: "Assumed 300 pieces." Reading: answers the question asked.
L2-FIN, Supplier B, 2026-11-13: "Passivation assumed, per the drawing note." Reading: answers the question asked.
Unprompted statements: L1-REV, Supplier B, 2026-11-13: "Quoting to the drawing as attached, Rev D." Reading: volunteered, not asked.
Unprompted statements: L2-TOL1, Supplier A, 2026-11-13: "We would apply ±0.1 to dimensions without a tolerance." Reading: volunteered, not asked.
Unanswered past the reply date: Supplier A: RFQ-VAL, L2-FIN. Supplier B: RFQ-VAL, L3-QTY. Supplier C: RFQ-CUR, RFQ-VAL, L2-FIN, L3-QTY.

5. Draft message (not sent; the buyer approves and sends)
To: Supplier A, Supplier B, Supplier C, sent separately. Subject: RFQ-2611-04 clarification 2.
Addenda: PS-07 revision 3 applies to line 4. The drawing note citing revision 2 is out of date.
Please state: none new; every missing detail was put in clarification 1.
Reminders (each supplier receives only its own): Supplier A: "Please still state what you have assumed for how long a quote must stand on the request, or tell us you cannot quote it without it (RFQ-VAL)." "Please still state what you have assumed for the finish on line 2, or tell us you cannot quote it without it (L2-FIN)." Supplier B: "Please still state what you have assumed for how long a quote must stand on the request, or tell us you cannot quote it without it (RFQ-VAL)." "Please still state what you have assumed for the quantity on line 3, or tell us you cannot quote it without it (L3-QTY)." Supplier C: "Please still state what you have assumed for the currency on the request, or tell us you cannot quote it without it (RFQ-CUR)." "Please still state what you have assumed for how long a quote must stand on the request, or tell us you cannot quote it without it (RFQ-VAL)." "Please still state what you have assumed for the finish on line 2, or tell us you cannot quote it without it (L2-FIN)." "Please still state what you have assumed for the quantity on line 3, or tell us you cannot quote it without it (L3-QTY)."
Reply by: three working days after the day the buyer sends it. If sent today (2026-11-16), that is 2026-11-19.

6. Needs a person
Nothing.

Every item traces to the lines and cover details of RFQ-2611-04, the register of 5 documents, the drawing text for lines 1 to 4, the buyer's note of 2026-11-10, Tomas's ruling of 2026-11-13 and the six supplier answers received to 2026-11-13. The list changes no record, interprets no tolerance and sends nothing.
```

## Checking the figures

- Items: four missing, three conflicts and three tolerances make 10. Four wait for the buyer's value, five wait for the engineer and one is settled, which also make 10.
- Next reply date: if the buyer sent the draft message today, Monday 16 November, three working days would give Thursday 19 November. The buyer has not said when it will be sent, so the list prints the rule and that one worked date.
- Earlier reply date: clarification 1 went out on Tuesday 10 November, so three working days gives Friday 13 November. Today is Monday 16 November, so the unanswered items are past the date.
- Unanswered: of 12 answers asked for (four items, three suppliers), 4 arrived, so 8 are outstanding: 2 from Supplier A, 2 from Supplier B and 4 from Supplier C.
- Working days left: Tuesday 17 to Friday 20 November, counting the due date, is 4.
- The one item kept for line 2 QA-1043 covers all three untoleranced dimensions, because kind (a) is one item for each drawing.
- The two volunteered statements are not among the 12 and change no status.
