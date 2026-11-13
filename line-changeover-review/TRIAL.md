# Line changeover review: one run on the invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-12

The inputs are the invented example in [the worked example](example.md): the settings, the observation sheet, the setup sheet and the three operator notes for "Company D", Line 2. No client data was used. The run was made once. The model read the template and the inputs first, produced the output, and only then read the example's published output to compare. The model did not write the template.

## What came out

The run did not stop. Every header matched, no time or value was out of order, and the check lines tied. The full output follows.

```
LINE CHANGEOVER REVIEW: Line 2, Sauce A 500 ml to Sauce B 250 ml

For: Production lead. Observed Tuesday 10 November 2026 by Continuous-improvement lead. Based on one observed changeover; timings vary from one changeover to the next.
Inputs: observation sheet line2_changeover_2026-11-10.csv, 15 steps; settings; setup sheet Line 2, Sauce B 250 ml; operator notes 3 notes. Steps with typical left blank are read as typical (all 15).
The stop: 10:00 to 11:10, 70 minutes, from the last good unit of Sauce A 500 ml to the first unit of Sauce B 250 ml accepted at the first-off check.

1. Timings
Stop minutes covered by recorded steps: 67. Not recorded: 3 (10:57 to 11:00).
Work with the line stopped: 113 person-minutes. Operator 1 57; Operator 2 46; Shift lead 10.
Work with the line running: 13 person-minutes, 8 before the stop and 5 after restart.

2. Each step, sorted
1. Print the Sauce B batch paperwork | Shift lead | 09:50-09:58, 8 min | running | Already done while running | before the stop
2. Lock out and isolate the filler, capper and labeller | Operator 1 | 10:00-10:05, 5 min | stopped | Protected: safety | kind safety
3. Clear all Sauce A bottles, caps and labels from the line | Operator 2 | 10:00-10:08, 8 min | stopped | Protected: quality | kind quality
4. Walk to the parts store and fetch the 250 ml change parts | Operator 1 | 10:05-10:13, 8 min | stopped | Move before the stop | verbs walk, fetch
5. Flush and clean the filler bowl and nozzles | Operator 2 | 10:08-10:23, 15 min | stopped | Protected: quality | kind quality
6. Search for the 250 ml star wheel | Operator 1 | 10:13-10:19, 6 min | stopped | Move before the stop | verb search
7. Remove the 500 ml guide rails and star wheels | Operator 1 | 10:19-10:29, 10 min | stopped | Line stopped, needed | verb remove
8. Wait for the Sauce B label reels to arrive from the warehouse | Operator 2 | 10:23-10:28, 5 min | stopped | Move before the stop | verb wait
9. Fit the 250 ml guide rails and star wheels | Operator 1 | 10:29-10:41, 12 min | stopped | Line stopped, needed | verb fit
10. Load the Sauce B label reel and enter the Sauce B date code on the coder | Operator 2 | 10:28-10:34, 6 min | stopped | Line stopped, needed | verb load
11. Remove the lockout and check the guards are closed | Operator 1 | 10:41-10:45, 4 min | stopped | Protected: safety | kind safety
12. Adjust the fill volume and run trial bottles until the fill weight is right | Operator 1 | 10:45-10:57, 12 min | stopped | Line stopped, needed | verb adjust
13. Wash the removed 500 ml parts and return them to the store | Operator 2 | 10:34-10:46, 12 min | stopped | Move after restart | verb return (wash is in no list); kind other, see Q4
14. First-off check of Sauce B: fill weight, cap torque, label and date code | Shift lead | 11:00-11:10, 10 min | stopped | Protected: quality | kind quality
15. Write the changeover in the line log | Shift lead | 11:10-11:15, 5 min | running | Already done while running | after restart

3. Totals by sort
Protected: 5 steps, 42 min. Line stopped, needed: 4 steps, 40 min. Move before the stop: 3 steps, 19 min. Move after restart: 1 step, 12 min. Lead to decide: 0 steps, 0 min. Already done while running: 2 steps, 13 min.

4. Protected steps, kept exactly as observed
2. Lock out and isolate the filler, capper and labeller, 5 min. Protected: safety
3. Clear all Sauce A bottles, caps and labels from the line, 8 min. Protected: quality
5. Flush and clean the filler bowl and nozzles, 15 min. Protected: quality
11. Remove the lockout and check the guards are closed, 4 min. Protected: safety
14. First-off check of Sauce B: fill weight, cap torque, label and date code, 10 min. Protected: quality

5. Not typical
None marked.

6. Improvement plan to test
P1. Step 13, Wash the removed 500 ml parts and return them to the store (Operator 2, 12 stopped min). Move after restart: do it once Sauce B is running instead of during the stop. Setup sheet: not applicable (move after restart). Operator note: none on this step; the sheet note says "Done during the stop because Operator 2 was free." Checks before testing: production lead, quality owner (Q4). Stopped minutes moved: 12 (Operator 2).
P2. Step 4, Walk to the parts store and fetch the 250 ml change parts (Operator 1, 8 stopped min). Move before the stop: fetch the change parts while Sauce A 500 ml is still running, so they are at the line when it stops. Setup sheet: lists it (change parts: 250 ml guide rails (2); 250 ml star wheels (2)). Checks before testing: production lead. Stopped minutes moved: 8 (Operator 1).
P3. Step 6, Search for the 250 ml star wheel (Operator 1, 6 stopped min). Move before the stop: find the star wheel while the line is running, so no search is needed at the stop. Setup sheet: lists it (250 ml star wheels (2)). Operator note: "The 250 ml star wheel is meant to live on shelf 3 in the parts store. After the last 250 ml run it went to the wash area and stayed there." (Operator 1). Checks before testing: production lead. Stopped minutes moved: 6 (Operator 1).
P4. Step 8, Wait for the Sauce B label reels to arrive from the warehouse (Operator 2, 5 stopped min). Move before the stop: have the reels at the line before it stops. Setup sheet: lists it (Materials: Sauce B labels, 2 reels). Operator note: "The label reels normally arrive at the line at the start of the shift. Today the warehouse was short-handed." (Operator 2). Checks before testing: production lead; observer (Q2). Stopped minutes moved: 5 (Operator 2).
P5. Steps 7 and 9, Remove the 500 ml guide rails and star wheels; Fit the 250 ml guide rails and star wheels (Operator 1, 22 stopped min). Shorten: Operator 2 is freed by P1 and P4 (17 stopped min) and could take part of these two steps, so two people work on the machine at once. Checks before testing: production lead, engineering contact and safety owner (Q3). Minutes: none estimated.
P6. Step 12, Adjust the fill volume and run trial bottles until the fill weight is right (Operator 1, 12 stopped min). Shorten: at the next changeover, record the fill volume that passes the first-off check on the setup sheet, so later changeovers start from it. Setup sheet: "Settings: fill volume, not recorded". Operator note: "We adjust the fill volume by trial every time. Nobody writes the setting down." (Operator 1). Checks before testing: production lead, quality owner (Q5). Minutes: none estimated.

7. Estimate to test
Operator 1: 57 stopped min, 14 of them in moves (P2, P3). Stop as observed 70 min; if those moves work as planned, up to 14 min shorter, about 56 min. Others' stopped minutes after their moves: Operator 2 29; Shift lead 10. At 3 changeovers of this pair a week, up to 42 minutes of line time a week.
This estimate is to be tested on Line 2, not a result: the review cannot see which steps wait on another person's work.

8. How to test it on the line
On the next 3 changeovers of Sauce A 500 ml to Sauce B 250 ml on Line 2, with the same observation sheet: time the stop and steps 4, 6, 7, 8, 9, 12, 13. Protected steps 2, 3, 5, 11, 14 are done exactly as now. The Production lead compares each test with this observation and decides what to adopt; the owner of the written procedure updates it after that.

9. Questions before testing
For the Continuous-improvement lead (observer):
Q1. No step was recorded from 10:57 to 11:00, between the end of step 12 and the start of step 14; the note on step 14 says the Shift lead arrived from the office at 11:00. What happened in those 3 minutes, and was anyone waiting?
Q2. Operator 2's note says the label reels normally arrive at the start of the shift and the warehouse was short-handed today (step 8, 5 min). Should step 8 be marked not typical on the next sheet?
For the Operations manager (safety owner):
Q3. P5 would have Operator 1 and Operator 2 work on the machine at the same time during steps 7 and 9. Is that allowed, and under what conditions? The Maintenance lead (engineering contact) is asked whether the machine allows it.
For the Quality lead (quality owner):
Q4. Step 13, Wash the removed 500 ml parts and return them to the store, is marked other, but its wording names washing. Is it neither a safety nor a quality step, before P1 is tested?
Q5. P6 would record the fill volume that passes the first-off check. Does the quality lead agree it may be written on the setup sheet?

10. Decisions for the Production lead: 2
1. Which of P1 to P6 to test on the next 3 changeovers, and who prepares each.
2. Operator 1 says the 250 ml star wheel is meant to live on shelf 3 in the parts store and, after the last 250 ml run, went to the wash area and stayed there (step 6, 6 min). How is that cause to be removed?

Check lines
Stop: 11:10 - 10:00 = 70 min = covered 67 + not recorded 3.
Stopped person-minutes: Operator 1 57 + Operator 2 46 + Shift lead 10 = 113 = sorted totals 42 + 40 + 19 + 12 + 0 = 113.
Steps: 15 on the sheet = 5 + 4 + 3 + 1 + 0 + 2.
Estimate: 70 - 14 = 56.

Draft for the Production lead's decision. Nothing on Line 2, in the procedure or in any record has been changed.
```

## What was observed

**Every required part was produced.** All ten numbered sections and the four check lines came out, in the order of the output format. The stop was 70 minutes. The plan held four moves and two ideas to shorten. The estimate was 56 minutes, up to 14 minutes shorter, which is up to 42 minutes of line time a week at three changeovers. The check lines tied on the first pass.

**Against the published example.** The sorts, the totals, the protected steps, the order of the plan (P1 to P6), the estimate, the weekly figure and the check lines were the same as the example's. The differences were in wording and in a few places where the template leaves a choice:

- The example gives fuller wording for the "Already done while running" steps and shorter reasons for the other steps. The model's reasons were similar but not word for word.
- The model added a parenthetical quoting the setup-sheet line on each move before the stop. The example says only "Setup sheet: lists it."
- On P1 (a move after restart) the model wrote "Setup sheet: not applicable", and quoted the sheet's note on step 13 as if it were an operator note. The example leaves both out. The model's version adds text the template does not ask for.
- The example puts nothing under the safety owner's questions. The model added a question to the safety owner (Q3) and one to the quality owner (Q5) for the two ideas to shorten, because the template says those owners decide them. The example names them only in the "Checks before testing" lines.
- The last decision differs. The template says to ask how the cause of a search is to be removed, and the model asked exactly that. The example asks where washed change parts are to go and who checks that they are there, which goes a step past the template's rule to recommend nothing beyond the plan.
- Question 1 differs. The model asked what happened in the 3 unrecorded minutes and whether anyone was waiting. The example asks whether the line was waiting for the first-off check, which is a guess the inputs do not support. The inputs say only that the shift lead arrived at 11:00.

**Facts not in the inputs.** The model's output has no fact outside the inputs, apart from the one added line in P1 noted above, which is a quotation from the observation sheet, not an invention. In the example's output, the wording of question 1 and of decision 2 above assumes more than the inputs state. All times, minutes and counts in both outputs can be recomputed from the inputs.

**Where the instructions were ambiguous, and what the model chose.**

1. *Shared work.* The procedure says the idea lists "that person's" steps, which reads as the freed person's. The instruction block says the steps of the person with the most stopped minutes. The model followed the block (steps 7 and 9, Operator 1), which is what the example shows.
2. *Where the engineering contact and the safety owner answer.* The checklist wants both to have answered a shared-work idea before it is tested, but the output format has question sections only for the observer, the safety owner and the quality owner. The model put the safety question in the safety owner's section and named the engineering contact in the checks line.
3. *A note that a step usually goes differently.* Operator 2's note on the label reels reads as that, so the model asked the observer whether step 8 was typical. The template still makes a move proposal (P4) for that step, and says nothing about holding the proposal until the observer answers. A step that may turn out to be not typical stays in the plan.
4. *Verbs outside the lists.* Step 10, "Load the label reel and enter the date code", is sorted "needed" on the verb "load"; "enter" is in no list and is ignored. The date code might be entered while the line runs, and the rules cannot see it. Likewise "wash" in step 13 is in no list and is ignored; only "return" sorts it.
5. *What to write under "Setup sheet" for a move after restart,* and how much to quote. The format does not say.
6. *Question numbering.* The format shows Q[n] under each role. The model numbered across the roles, as the example does, but the format does not say.
7. *The estimate and the first-off check.* The estimate (56 minutes) follows the rule, but the record shows the shift lead arriving at 11:00 for the first-off check. If the check cannot start earlier, moving 14 minutes out of the first operator's work may not shorten the stop. The template says the estimate is to be tested and shows the 3 unrecorded minutes, but it does not point this dependency out.

**Anything the model was told to stop for:** nothing. No header mismatch, no missing time, no failed tie-out, no request to change a safety or quality step. None of the stop conditions or the decline rules was exercised, so this run says nothing about them.

**What was changed after the run.** The record above was not altered. After the run, the template and the example were edited, and none of the edits has been run again:

- The example's output was edited: question 1 now asks what happened in the 3 unrecorded minutes and whether anyone was waiting, without guessing the cause; the last decision now asks how the cause of the search is to be removed; and it now carries the line saying protected step 14 may limit the stop. The comparison above describes the earlier wording of the example, not the published one.
- The template was edited to say that observers write one action per step and that a noun after "and" is read as a verb if it is in a list; that an idea to shorten raises no question of its own, and the production lead asks the roles named in its checks line as part of decision 1 (the run above wrote Q3 and Q5 for them; the example writes "None."); and that the safety and quality stems are broad and only over-protect. The instruction block also gained the tie rule for plan order, the 1-minute test for shared work and the "not named" rule for a missing role. None of these changes the example's figures.
- The facts file was edited for wording only.
- Ambiguity 4 above is still open: "enter" is in no verb list, so step 10 is sorted wholly as needing the line stopped. It is a stated limit; the template's "What to customize" covers adding verbs.

**Limits of this run.** It is one run, by one model, on one invented example, from the template's instructions only. The example's output was written before this run, and the model's output was produced without reading it, but the match on every figure shows the rules are determinate on this input, not that they hold on a real sheet. The fifteen acceptance tests in the template were not run. Nothing here was tested for a client.
