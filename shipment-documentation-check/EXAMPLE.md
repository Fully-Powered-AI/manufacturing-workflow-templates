# Shipment documentation check: an invented example

*Illustrative example with invented data.* The business, the customer, the item codes, the lot numbers, the quantities and every date below are invented. The business is an invented small metal fabricator, called the Shop here. Its shipping lead asks for the check on the morning of Tuesday 10 November 2026, for one finished order that is due to ship on 12 November. The customer is Customer A; people are referred to by role.

The inputs come first, in full, so the template can be run on them. The check follows.

## The inputs

### 1. Settings (typed by the shipping coordinator)

```
Business: the Shop
Today: 2026-11-10
Quality lead: the quality lead
Shipping lead: the shipping lead
All other settings: use the defaults
```

### 2. Order lines

```
order_number,line,item_code,description,qty_ordered,unit,revision,ship_date
PO-7781,1,BRK-210,Mounting bracket,200,each,C,2026-11-12
PO-7781,2,BRK-215,Side bracket,120,each,B,2026-11-12
PO-7781,3,PLT-40,Base plate,50,each,A,2026-11-12
PO-7781,4,SHF-08,Drive shaft,30,each,D,2026-11-12
```

### 3. Required documents (the Shop's own list for this order)

```
requirement_id,document_type,applies_to,source
R1,Material certificate,1,Order note
R2,Material certificate,3,Order note
R3,Material certificate,4,Order note
R4,Coating certificate,2,Order note
R5,Packing list,ALL,Shipping procedure SP-3
```

### 4. Inspection records

```
record_id,line,item_code,lot,qty_inspected,qty_accepted,qty_rejected,record_date,result
I-301,1,BRK-210,L-5501,120,120,0,2026-11-06,accepted
I-302,1,BRK-210,L-5502,80,78,2,2026-11-07,accepted
I-303,2,BRK-215,L-6120,120,120,0,2026-11-07,accepted
I-304,3,PLT-40,L-7001,50,50,0,2026-11-08,accepted
```

### 5. Documents on file

```
document_id,document_type,applies_to,item_code,lot,revision,document_date,signed
D-1,Material certificate,1,BRK-210,L-5501,,2026-10-20,yes
D-2,Coating certificate,2,BRK-251,,A,2026-10-22,yes
D-3,Material certificate,3,PLT-40,L-7001,,2026-10-28,no
D-4,Packing list,ALL,,,,2026-11-10,yes
```

### 6. Packing details

```
package_id,line,item_code,lot,qty_packed,unit
P-1,1,BRK-210,L-5501,120,each
P-2,1,BRK-210,L-5502,80,each
P-3,2,BRK-215,L-6120,120,each
P-4,3,PLT-40,L-7001,55,each
P-5,4,SHF-08,L-8002,30,each
```

## The check

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
Line 4 SHF-08 revision D: ordered 30 each; no inspection record; packed 30 (P-5). Lot L-8002: packed 30, no inspection record. See decision 4.

Missing records
1. Material certificate naming lot L-5502 on line 1 BRK-210, 80 packed (R1).
2. Material certificate for line 4 SHF-08 (R3).
3. Inspection record for line 4 SHF-08, lot L-8002, 30 packed.

Differences between files
1. Line 1, lot L-5502: packed 80 (P-2), accepted 78 (I-302); 2 more packed than accepted.
2. Line 2: D-2 shows item code BRK-251; the order line shows BRK-215.
3. Line 2: D-2 shows revision A; the order line shows revision B.
4. Line 3: packed 55 (P-4); ordered 50; 5 more than ordered.
5. Line 3, lot L-7001: packed 55 (P-4), accepted 50 (I-304); 5 more packed than accepted.
6. Line 3: D-3 is not shown as signed.

Documents on file that no requirement names
None.

Decisions for the quality lead and the shipping lead
1. Line 1 BRK-210. Lot L-5502 has 80 packed (P-2) against 78 accepted on I-302, which records 2 rejected. D-1 names lot L-5501 only, so no material certificate on file names L-5502. Is the lot L-5502 count of 80 right, and are the 2 rejected pieces among them? Is there a material certificate for lot L-5502?
2. Line 2 BRK-215. D-2 shows item code BRK-251 and revision A; the order line is BRK-215 revision B. Is D-2 the coating certificate for this line? Is there another coating certificate for this line?
3. Line 3 PLT-40. 55 are packed (P-4) against 50 ordered and 50 accepted on I-304. D-3 is not shown as signed. Is the extra 5 intended? Is a signed copy of D-3 on file elsewhere?
4. Line 4 SHF-08. There is no inspection record and no material certificate on file; 30 are packed (P-5) from lot L-8002. Do these records exist outside the files supplied?

Draft for the quality lead and the shipping lead. Nothing has been certified, signed, released, sent or changed, and no conformity or export judgment has been made. Counts are taken from the files supplied on 2026-11-10.
```
