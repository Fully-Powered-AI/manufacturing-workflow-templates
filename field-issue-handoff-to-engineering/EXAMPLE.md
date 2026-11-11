# Field issue handoff to engineering: an invented example

*Illustrative example with invented data.* The company, its customer, the staff, the product, the case and every date below are invented. Company X is an invented maker of bench-top vacuum sealers for commercial kitchens. Dana is its customer service lead and Kofi a service technician. On Tuesday 10 November 2026 Dana asks for a brief on one case, to hand to the engineering support lead.

The inputs come first, in full, so the template can be run on them. The brief follows.

## The inputs

### The case details and the date of the brief

```
Case: C-3310
Customer: Customer A
Reported by: A-1
Received: 2026-11-04, by email
Case owner: Dana
Brief date: 2026-11-10
```

### The customer's report

```
Three of our ZX-7 sealers, delivered in September, keep stopping partway
through the vacuum stage and showing E4. It started on 28 October on the
unit at our main kitchen, and since 2 November on a second unit. On 3
November someone at the main kitchen noticed a smell like something burning
near the unit after it stopped, and switched it off at the wall. Nobody was
hurt. We have kept it unplugged. Photos attached. The third unit is fine so
far. We need these for a banquet on 14 November.
```

### The delivery record

```
Serial,Product,Revision,Ship date,Ship-to
ZX7-20417,ZX-7,Rev C,2026-09-14,Bakery site
ZX7-20431,ZX-7,Rev B,2026-09-14,Main kitchen
ZX7-20432,ZX-7,Rev B,2026-09-14,Main kitchen
```

### The list of photographs and files

```
File,Received,From,Said to show,Readable text
IMG_0412.jpg,2026-11-04,A-1,Display showing E4,E4
IMG_0413.jpg,2026-11-04,A-1,Rating label on the back of the main kitchen unit,ZX7-20417
IMG_0414.jpg,2026-11-04,A-1,Rating label on the second unit,ZX7-2043_ (last character not readable)
IMG_0415.jpg,2026-11-04,A-1,Lid seal area of the main kitchen unit,
```

The photographs were not opened by the assistant; the columns above were typed by Dana from the email.

### The service notes

```
Date,Who,Entry
2026-11-04,Dana,"Acknowledged the report by email."
2026-11-05,Dana,"Phone call with A-1. A-1 says E4 appears about 40 seconds into the vacuum stage. Third unit not used much."
2026-11-05,Dana,"Checked delivery record: serial ZX7-20417 shipped 2026-09-14 as Rev C."
2026-11-06,Kofi,"Phoned A-1 and told them to keep the main kitchen unit unplugged until we come back to them."
2026-11-09,Dana,"Banquet date 14 November confirmed with A-1 on the phone; they have no spare sealer."
```

### The intake checklist and the settings

```
Checklist: the company's default eleven items (product and revision; serial
number of each unit named; date delivered; when it first happened; how often
it happens; error code or display text; what the customer was doing at the
time; photograph of the rating label; any smell, smoke, heat, sparks or
injury; whether the unit is still in use; the customer's own date).
Engineering contact: engineering support lead
Safety specialist: product safety officer
Revision record owner: configuration records owner
Extra safety words: none
```

## The brief

The brief is plain text. It is set here with bold section titles and bullets so it reads well on a page; the words and their order are the template's.

**FIELD ISSUE CASE BRIEF: C-3310, Customer A**

Prepared for: customer service lead. Brief date: 2026-11-10. Report received: 2026-11-04, by email (6 days before this brief). Service notes read to: 2026-11-09 (5 notes).
Internal. Nothing here has been sent to the customer, to engineering or to anyone else.
Nothing here is a finding about the cause.
SAFETY: a possible safety matter is reported ("a smell like something burning", 2026-11-03). Pass this case to the product safety officer first. No note shows that has been done.

**SAFETY CHECK**

- "a smell like something burning near the unit after it stopped": the customer's report, 2026-11-04, event dated 2026-11-03. The report also says the unit was switched off at the wall and that nobody was hurt. Not verified by anyone. Passed to the product safety officer: no note shows it.

The safety specialist decides what to ask and what to tell the customer.

**THE CASE**

C-3310 | Customer A | reported by A-1 | received 2026-11-04 | case owner Dana
Product named by the customer: ZX-7. Units named in the report: 3.
Customer's own date: 2026-11-14, a banquet, 4 days after this brief.
Dates in the report with no year are read as 2026, the year the report arrived.

**PRODUCT, REVISION AND SERIAL REFERENCES**

The unit at our main kitchen (first to fail) | serial ZX7-20417, from the readable text listed for IMG_0413.jpg | delivery record: ZX-7, Rev C, shipped 2026-09-14, ship-to Bakery site
A second unit | serial partly readable: ZX7-2043_, from the readable text listed for IMG_0414.jpg | candidates: ZX7-20431, Rev B, 2026-09-14; ZX7-20432, Rev B, 2026-09-14
The third unit | serial not given | not matched: no serial given
Days from ship date to the first reported symptom: first unit 44; second unit 49 (either candidate); third unit not worked out.
Revisions in the record for these units: differ: Rev C for ZX7-20417; Rev B for ZX7-20431 and ZX7-20432 (the candidates for the second unit); the third unit is not matched.

**SYMPTOMS AS REPORTED**

- Stops partway through the vacuum stage and shows E4: the report's opening line names three units; dates are given for the unit at our main kitchen, since 2026-10-28, and for a second unit, since 2026-11-02. Reported by the customer, report of 2026-11-04. Not verified. See the conflicts.
- E4 appears about 40 seconds into the vacuum stage: unit not stated. Reported in a service note, from the customer, 2026-11-05 (Dana). Not verified.
- A smell like something burning near the unit after it stopped: the unit at our main kitchen, 2026-11-03. Reported by the customer, report of 2026-11-04. Not verified. See the safety check.
- "The third unit is fine so far": third unit. Reported by the customer, report of 2026-11-04. Not verified.
Reproduced by service or engineering: no note says it was tried.

**EVIDENCE SUPPLIED**

IMG_0412.jpg | received 2026-11-04 | from A-1 | said to show: Display showing E4 | readable text: E4
IMG_0413.jpg | received 2026-11-04 | from A-1 | said to show: Rating label on the back of the main kitchen unit | readable text: ZX7-20417
IMG_0414.jpg | received 2026-11-04 | from A-1 | said to show: Rating label on the second unit | readable text: ZX7-2043_ (last character not readable)
IMG_0415.jpg | received 2026-11-04 | from A-1 | said to show: Lid seal area of the main kitchen unit | readable text: none listed
Rating labels: main kitchen unit: photographed, serial fully listed; second unit: photographed, serial incomplete; third unit: no photograph.
Other documents named: none.
The files have not been opened by the assistant.

**WHAT SERVICE HAS DONE**

2026-11-04 | Dana | Acknowledged the report by email.
2026-11-05 | Dana | Phone call with A-1. A-1 says E4 appears about 40 seconds into the vacuum stage. Third unit not used much.
2026-11-05 | Dana | Checked delivery record: serial ZX7-20417 shipped 2026-09-14 as Rev C.
2026-11-06 | Kofi | Phoned A-1 and told them to keep the main kitchen unit unplugged until we come back to them.
2026-11-09 | Dana | Banquet date 14 November confirmed with A-1 on the phone; they have no spare sealer.
No note shows that the photographs were opened, that the symptom was reproduced or that the product safety officer was told.

**CONFLICTS AND GAPS**

- Conflict: where ZX7-20417 is. Delivery record: shipped 2026-09-14 to the Bakery site. File list, 2026-11-04: IMG_0413.jpg is said to show the rating label on the back of the main kitchen unit, readable text ZX7-20417. Neither is verified.
- Conflict: how many units are stopping. Report, 2026-11-04, opening line: "Three of our ZX-7 sealers ... keep stopping". Report, 2026-11-04: "The third unit is fine so far." Neither is verified.
- Gap: the delivery record holds three ZX-7 serials, all shipped 2026-09-14, and the report names three units. The record holds two further ZX-7 serials; neither is settled as the second or the third unit.
- Gap: no input says where the second and third units are installed.

**INTAKE CHECKLIST**

Product and revision: partly, ZX-7 named; Rev C in the record for ZX7-20417; Rev B for the two candidates for the second unit; third unit not matched
Serial number of each unit named: partly, one of three settled
Date delivered: partly, the report says "delivered in September"; the record gives ship date 2026-09-14; no delivery date supplied
When it first happened: present, 2026-10-28 (first unit) and 2026-11-02 (second unit), from the report
How often it happens: partly, "keep stopping" in the report; no count or rate
Error code or display text: present, E4, in the report and the file list (IMG_0412.jpg)
What the customer was doing at the time: partly, the vacuum stage is stated; what was being sealed is not
Photograph of the rating label: partly, two of three units; the second unit's serial is not fully readable
Any smell, smoke, heat, sparks or injury: present, a burning smell on 2026-11-03; the report says nobody was hurt. See the safety check.
Whether the unit is still in use: partly, the first unit is unplugged (report; note of 2026-11-06); the second and third are not stated
The customer's own date: present, 2026-11-14 (report; note of 2026-11-09)
Present 4, partly 7, missing 0, total 11.

**QUESTIONS STILL UNANSWERED**

1. What are the product and revision of the third unit? Ask: customer (its serial first); revision record owner (the revision, once the serial is known).
2. What is the last character of the serial on the second unit's rating label, and what is the serial of the third unit? Ask: customer.
3. On what date was each unit delivered? Ask: customer; service staff.
4. How often does E4 appear on each unit? Ask: customer.
5. What was being sealed when each stop happened? Ask: customer.
6. Does a photograph exist of the third unit's rating label, and of the second unit's label with every character of the serial readable? Ask: customer.
7. Are the second and third units still in use, and where is each installed? Ask: customer.
8. Is the unit with serial ZX7-20417 at the main kitchen or at the Bakery site? Ask: customer; revision record owner (the ship-to in the record).
9. Are two units or three stopping? Ask: customer.

**FOR ENGINEERING TO DECIDE**

From engineering support lead:
1. Does the case warrant an investigation into the E4 stops? Known: stops with E4 reported since 2026-10-28 on the unit listed as ZX7-20417 (Rev C in the record) and since 2026-11-02 on a second unit (Rev B in the record, serial not settled); about 40 seconds into the vacuum stage, per a note of 2026-11-05; the customer says the third unit is fine so far; a burning smell reported on 2026-11-03. Not known: whether anyone has tried to reproduce it (no note says it was tried); how often it happens; what was being sealed.
2. What further evidence does engineering want? Known: four files listed; no note shows any was opened; one unit is unplugged and the customer has no spare sealer (note of 2026-11-09). Not known: what the photographs show; whether other evidence exists.
Needed by: 2026-11-14, the customer's banquet (the customer's own date, from the report and the note of 2026-11-09; no date is stated by engineering).
This brief proposes no investigation, instruction or remedy.

**QUESTIONS FOR THE CUSTOMER SERVICE LEAD BEFORE IT GOES**

1. The report mentions a burning smell and no note shows the case was passed to the product safety officer. Is it passed on before this brief goes?
2. The customer's banquet is on 2026-11-14, 4 days after this brief, and no note records an answer given to the customer about it. Who answers the customer, and with what?
3. No note shows that anyone has opened the photographs. Who opens them?

Prepared for the customer service lead. Nothing has been sent, no record has been changed and no one has been contacted.
