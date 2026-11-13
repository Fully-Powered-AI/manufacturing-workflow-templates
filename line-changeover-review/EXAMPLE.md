# Line changeover review: an invented example

*Illustrative example with invented data.* The company, the line, the products, the people and every time below are invented. "Company D" is an invented maker of bottled sauces with two filling lines. Its continuous-improvement lead timed one changeover on Line 2, from Sauce A in 500 ml bottles to Sauce B in 250 ml bottles, and ran the review for the production lead. People are named only by their position on the line. First come the inputs the continuous-improvement lead supplied, in full, then the draft the workflow template returned.

## The inputs

### 1. Settings

```
Line: Line 2
Changing from: Sauce A 500 ml
Changing to: Sauce B 250 ml
Date observed: Tuesday 10 November 2026
Observer: Continuous-improvement lead
Line stopped at: 10:00
First good unit at: 11:10
Production lead: Production lead
Safety owner: Operations manager
Quality owner: Quality lead
Engineering contact: Maintenance lead
Protected steps named by the lead: none
Changeovers of this pair per week: 3
Test changeovers: 3
```

### 2. Observation sheet (line2_changeover_2026-11-10.csv)

```
step_no,step,done_by,start,end,line_state,kind,typical,notes
1,Print the Sauce B batch paperwork,Shift lead,09:50,09:58,running,,,
2,"Lock out and isolate the filler, capper and labeller",Operator 1,10:00,10:05,stopped,safety,,
3,"Clear all Sauce A bottles, caps and labels from the line",Operator 2,10:00,10:08,stopped,quality,,
4,Walk to the parts store and fetch the 250 ml change parts,Operator 1,10:05,10:13,stopped,,,
5,Flush and clean the filler bowl and nozzles,Operator 2,10:08,10:23,stopped,quality,,
6,Search for the 250 ml star wheel,Operator 1,10:13,10:19,stopped,,,Not on its shelf.
7,Remove the 500 ml guide rails and star wheels,Operator 1,10:19,10:29,stopped,,,
8,Wait for the Sauce B label reels to arrive from the warehouse,Operator 2,10:23,10:28,stopped,,,
9,Fit the 250 ml guide rails and star wheels,Operator 1,10:29,10:41,stopped,,,
10,Load the Sauce B label reel and enter the Sauce B date code on the coder,Operator 2,10:28,10:34,stopped,,,
11,Remove the lockout and check the guards are closed,Operator 1,10:41,10:45,stopped,safety,,
12,Adjust the fill volume and run trial bottles until the fill weight is right,Operator 1,10:45,10:57,stopped,,,Four rounds of trial bottles.
13,Wash the removed 500 ml parts and return them to the store,Operator 2,10:34,10:46,stopped,other,,Done during the stop because Operator 2 was free.
14,"First-off check of Sauce B: fill weight, cap torque, label and date code",Shift lead,11:00,11:10,stopped,quality,,Shift lead arrived from the office at 11:00.
15,Write the changeover in the line log,Shift lead,11:10,11:15,running,,,
```

### 3. Setup sheet

```
Setup sheet: Line 2, Sauce B 250 ml
Change parts: 250 ml guide rails (2); 250 ml star wheels (2)
Materials: Sauce B labels, 2 reels; 38 mm caps
Tools: 10 mm hex key; star-wheel puller
Settings: fill volume, not recorded; capper torque, as set by the quality lead
```

### 4. Operator notes

```
Operator 1: The 250 ml star wheel is meant to live on shelf 3 in the parts store. After the last 250 ml run it went to the wash area and stayed there.
Operator 2: The label reels normally arrive at the line at the start of the shift. Today the warehouse was short-handed.
Operator 1: We adjust the fill volume by trial every time. Nobody writes the setting down.
```

## The draft

```
LINE CHANGEOVER REVIEW: Line 2, Sauce A 500 ml to Sauce B 250 ml

For: Production lead. Observed Tuesday 10 November 2026 by Continuous-improvement lead. Based on one observed changeover; timings vary from one changeover to the next.
Inputs: observation sheet line2_changeover_2026-11-10.csv, 15 steps; settings; setup sheet Line 2, Sauce B 250 ml; operator notes 3 notes. Steps with typical left blank are read as typical.
The stop: 10:00 to 11:10, 70 minutes, from the last good unit of Sauce A 500 ml to the first unit of Sauce B 250 ml accepted at the first-off check.

1. Timings
Stop minutes covered by recorded steps: 67. Not recorded: 3 (10:57 to 11:00).
Work with the line stopped: 113 person-minutes. Operator 1 57; Operator 2 46; Shift lead 10.
Work with the line running: 13 person-minutes, 8 before the stop and 5 after restart.

2. Each step, sorted
1. Print the Sauce B batch paperwork | Shift lead | 09:50-09:58, 8 min | running | Already done while running, before the stop | observed running
2. Lock out and isolate the filler, capper and labeller | Operator 1 | 10:00-10:05, 5 min | stopped | Protected: safety | marked safety
3. Clear all Sauce A bottles, caps and labels from the line | Operator 2 | 10:00-10:08, 8 min | stopped | Protected: quality | marked quality
4. Walk to the parts store and fetch the 250 ml change parts | Operator 1 | 10:05-10:13, 8 min | stopped | Move before the stop | verbs walk, fetch: before-the-stop list
5. Flush and clean the filler bowl and nozzles | Operator 2 | 10:08-10:23, 15 min | stopped | Protected: quality | marked quality
6. Search for the 250 ml star wheel | Operator 1 | 10:13-10:19, 6 min | stopped | Move before the stop | verb search: before-the-stop list
7. Remove the 500 ml guide rails and star wheels | Operator 1 | 10:19-10:29, 10 min | stopped | Line stopped, needed | verb remove: needs-the-line-stopped list
8. Wait for the Sauce B label reels to arrive from the warehouse | Operator 2 | 10:23-10:28, 5 min | stopped | Move before the stop | verb wait: before-the-stop list
9. Fit the 250 ml guide rails and star wheels | Operator 1 | 10:29-10:41, 12 min | stopped | Line stopped, needed | verb fit: needs-the-line-stopped list
10. Load the Sauce B label reel and enter the Sauce B date code on the coder | Operator 2 | 10:28-10:34, 6 min | stopped | Line stopped, needed | verb load: needs-the-line-stopped list
11. Remove the lockout and check the guards are closed | Operator 1 | 10:41-10:45, 4 min | stopped | Protected: safety | marked safety
12. Adjust the fill volume and run trial bottles until the fill weight is right | Operator 1 | 10:45-10:57, 12 min | stopped | Line stopped, needed | verb adjust: needs-the-line-stopped list
13. Wash the removed 500 ml parts and return them to the store | Operator 2 | 10:34-10:46, 12 min | stopped | Move after restart | verb return: after-restart list; marked other, but its wording names washing: see Q3
14. First-off check of Sauce B: fill weight, cap torque, label and date code | Shift lead | 11:00-11:10, 10 min | stopped | Protected: quality | marked quality
15. Write the changeover in the line log | Shift lead | 11:10-11:15, 5 min | running | Already done while running, after restart | observed running

3. Totals by sort
Protected: 5 steps, 42 min. Line stopped, needed: 4 steps, 40 min. Move before the stop: 3 steps, 19 min. Move after restart: 1 step, 12 min. Lead to decide: 0 steps, 0 min. Already done while running: 2 steps, 13 min.

4. Protected steps, kept exactly as observed
2. Lock out and isolate the filler, capper and labeller, 5 min. Protected: safety.
3. Clear all Sauce A bottles, caps and labels from the line, 8 min. Protected: quality.
5. Flush and clean the filler bowl and nozzles, 15 min. Protected: quality.
11. Remove the lockout and check the guards are closed, 4 min. Protected: safety.
14. First-off check of Sauce B: fill weight, cap torque, label and date code, 10 min. Protected: quality.

5. Not typical
None marked.

6. Improvement plan to test
P1. Step 13, Wash the removed 500 ml parts and return them to the store (Operator 2, 12 stopped min). Move after restart: wash and return the 500 ml parts once Sauce B is running. Checks before testing: Production lead; Quality lead (Q3). Stopped minutes moved: 12 (Operator 2).
P2. Step 4, Walk to the parts store and fetch the 250 ml change parts (Operator 1, 8 stopped min). Move before the stop: bring the 250 ml change parts to the line while Sauce A is still running. Setup sheet: lists it. Checks before testing: Production lead. Stopped minutes moved: 8 (Operator 1).
P3. Step 6, Search for the 250 ml star wheel (Operator 1, 6 stopped min). Move before the stop: have the 250 ml star wheels with the other change parts before the line stops, so no search is needed. Setup sheet: lists it. Operator note: "The 250 ml star wheel is meant to live on shelf 3 in the parts store. After the last 250 ml run it went to the wash area and stayed there." Checks before testing: Production lead. Stopped minutes moved: 6 (Operator 1).
P4. Step 8, Wait for the Sauce B label reels to arrive from the warehouse (Operator 2, 5 stopped min). Move before the stop: have the Sauce B label reels at the line before it stops, so no wait is needed. Setup sheet: lists it. Operator note: "The label reels normally arrive at the line at the start of the shift. Today the warehouse was short-handed." Waits for the Continuous-improvement lead's answer to Q2 before it is tested. Checks before testing: Production lead; Continuous-improvement lead (Q2). Stopped minutes moved: 5 (Operator 2).
P5. Steps 7, 9, Remove the 500 ml guide rails and star wheels; Fit the 250 ml guide rails and star wheels (Operator 1, 22 stopped min). Shorten: Operator 2 has 17 stopped minutes freed by P1 and P4 and could take part of the removing and fitting. Checks before testing: Maintenance lead and Operations manager decide whether two people can work on the machine at once. Minutes: none estimated.
P6. Step 12, Adjust the fill volume and run trial bottles until the fill weight is right (Operator 1, 12 stopped min). Shorten: at the next changeover, record the fill-volume setting that passes the first-off check on the setup sheet, so later changeovers start from it. Setup sheet: "fill volume, not recorded". Operator note: "We adjust the fill volume by trial every time. Nobody writes the setting down." Checks before testing: Quality lead. Minutes: none estimated.

7. Estimate to test
Operator 1: 57 stopped min, 14 of them in moves (P2, P3). Stop as observed 70 min; if those moves work as planned, up to 14 min shorter, about 56 min. Others' stopped minutes after their moves: Operator 2 29; Shift lead 10. At 3 changeovers of this pair a week, up to 42 minutes of line time a week.
Protected step 14 started at 11:00 after a stretch with no step recorded, so it may limit the stop.
This estimate is to be tested on Line 2, not a result: the review cannot see which steps wait on another person's work.

8. How to test it on the line
On the next 3 changeovers of Sauce A 500 ml to Sauce B 250 ml on Line 2, with the same observation sheet: time the stop and steps 4, 6, 7, 8, 9, 12 and 13. Protected steps 2, 3, 5, 11 and 14 are done exactly as now. The Production lead compares each test with this observation and decides what to adopt; the owner of the written procedure updates it after that.

9. Questions before testing
For the Continuous-improvement lead:
Q1. No step was recorded from 10:57 to 11:00, 3 minutes of the stop. Step 14's note says the shift lead arrived from the office at 11:00. What happened in those 3 minutes, and was anyone waiting?
Q2. Operator 2's note says the label reels normally arrive at the line at the start of the shift, and the warehouse was short-handed that day. Was step 8 typical? If not, mark it so on the sheet.
For the Operations manager:
None.
For the Quality lead:
Q3. Step 13, "Wash the removed 500 ml parts and return them to the store", is marked other, but its wording names washing. Please confirm it is not a quality step before P1 is tested.

10. Decisions for the Production lead: 2
1. The plan holds four moves (P1 to P4) and two ideas to shorten (P5, P6). Which of them are to be tested at the next 3 changeovers, and who prepares each?
2. Operator 1's note gives the cause of the search in step 6: the 250 ml star wheel went to the wash area after the last 250 ml run and stayed there. How is that cause to be removed?

Check lines
Stop: 11:10 - 10:00 = 70 min = covered 67 + not recorded 3.
Stopped person-minutes: Operator 1 57 + Operator 2 46 + Shift lead 10 = 113 = sorted totals 42 + 40 + 19 + 12 + 0 = 113.
Steps: 15 on the sheet = 5 + 4 + 3 + 1 + 0 + 2.
Estimate: 70 - 14 = 56.

Draft for the Production lead's decision. Nothing on Line 2, in the procedure or in any record has been changed.
```

Every time, minute and step in the draft traces to the observation sheet, the settings, the setup sheet or the operator notes above. The production lead chooses what to test; the operators test it on the line.
