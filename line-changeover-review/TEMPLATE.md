# Line changeover review

Workflow template, version 0.1.0.

## Purpose

Review one observed changeover on a production line for the production lead or the continuous-improvement lead. From the observed steps and their clock times, the assistant totals the stop, sorts every step into work that needs the line stopped and work that could be done while the line runs, and proposes an improvement plan to test on the line, with an estimate whose working is shown. Safety steps and quality steps are kept exactly as observed: they are never proposed for removal, shortening, moving or merging. The assistant prepares; it changes nothing on the line, in the written procedure or in any record, judges no step safe, and decides nothing. A person decides which proposals to test, and a person tests them.

## When to use it and when not to

Use it after a changeover has been observed and timed step by step, for one line and one change from an outgoing product to an incoming product: before an improvement event on that changeover, when changeovers are eating into the week, or once a change has been tried and the changeover timed a second time.

Do not use it:

- to judge whether a step, a tool or a way of working is safe. The safety owner decides that;
- to decide whether a quality step, a clean or a check can change. The quality owner decides that, and this workflow template never proposes it;
- to write or change the written changeover procedure. Once the lead has tested and adopted a change, the procedure's owner updates it;
- to decide the order of products on the line or how many changeovers to plan. That belongs to the production schedule;
- to judge an operator's performance. The review is about the work, not the person, and it names people only by their role on the line.

## Roles

- **Observes and runs it:** the continuous-improvement lead, the production lead or the shift lead who timed the changeover.
- **Decides which proposals to test, and whether to adopt them:** the production lead.
- **Answers for safety steps, and for any proposal that changes who works on the machine at once:** the safety owner.
- **Answers for quality steps, cleans, first-off checks and recorded settings:** the quality owner.
- **Answers whether a part, a fitting or a machine change is possible:** the engineering or maintenance contact.
- **Does the changeover and tests the plan:** the operators on the line.

Use the titles your company uses.

## Inputs

The assistant works from files and notes the person supplies. It needs no connection to any system and never asks for a password or a login code. One run covers one observed changeover.

1. **Settings,** as notes, with these lines:

   ```
   Line:
   Changing from:
   Changing to:
   Date observed:
   Observer:
   Line stopped at:
   First good unit at:
   Production lead:
   Safety owner:
   Quality owner:
   Engineering contact:
   Protected steps named by the lead:
   Changeovers of this pair per week:
   Test changeovers:
   ```

   "Line stopped at" is the clock time (HH:MM, 24-hour) of the last good unit of the outgoing product. "First good unit at" is the clock time the first unit of the incoming product passed the first-off check. Together they define the stop. If either is missing, stop and ask: the stop is the lead's definition, never the assistant's. "Protected steps named by the lead" is a list of step numbers or "none" (default none). "Changeovers of this pair per week" is optional; leave the weekly figure out without it. "Test changeovers" defaults to 3. A missing role is written as "not named", and any question for it goes to the production lead.

2. **The observation sheet,** an export with these default column headers:

   ```
   step_no,step,done_by,start,end,line_state,kind,typical,notes
   ```

   - `step_no`: a whole number, each used once.
   - `step`: the step in a few words, starting with what was done ("Fetch the change parts"). One action per step is best.
   - `done_by`: the role or position of the person who did it ("Operator 1"), never a name if the company prefers roles.
   - `start`, `end`: clock times, HH:MM, 24-hour, on the day observed. Minutes = end − start.
   - `line_state`: exactly `stopped` or `running`: the state of the line while the step was done.
   - `kind`: `safety`, `quality`, `other` or blank. The observer's call; `other` means neither safety nor quality.
   - `typical`: `yes`, `no` or blank. Blank is read as `yes`, and the draft says so. `no` marks a step that went unusually (a breakdown, a missing part, a training run).
   - `notes`: free text from the observer.

   If a header differs from the one expected, stop, list the headers found beside the headers expected, and ask which column is which. Never guess a column. If the sheet is missing, stop.

3. **The setup sheet** for the incoming product, if there is one: the change parts, tools, materials and settings it needs. If missing, write "setup sheet not supplied" and skip the setup-sheet checks.

4. **Operator notes,** if any: what the people who did the changeover said about it. They are quoted as written and never turned into a time. If missing, write "operator notes not supplied".

## The procedure

1. **Check the inputs.** Confirm the headers. Stop and ask if a `step_no` repeats; a time is blank or not HH:MM; an end is at or before its start (a changeover across midnight included); a `line_state`, `kind` or `typical` value is outside those allowed; "First good unit at" is at or before "Line stopped at"; a `stopped` step starts before the line stopped or ends after the first good unit; or a `running` step overlaps the stop. Do not repair the sheet.
2. **Time the stop.** Stop minutes = first good unit − line stopped. Covered minutes = the length of the union of the `stopped` steps' clock intervals. Not recorded = stop minutes − covered minutes; list each stretch of the stop in which no step was recorded, from and to. Add each person's stopped minutes (the sum of their `stopped` steps) and the running minutes before the stop and after restart.
3. **Mark the protected steps.** A `stopped` step is protected when its `kind` is `safety` or `quality`, or the lead named its number. When `kind` is blank, it is also protected if its wording contains a word that begins with a safety stem (lock, isolat, guard, interlock, permit, PPE, energy) or a quality stem (first-off, first-piece, inspect, check, verif, sign, release, clear, allergen, clean, wash, saniti, flush, sample), and a question asks its owner to mark its kind on the next sheet. Label it "Protected: safety", "Protected: quality", "Protected: safety and quality", "Protected: named by the lead" or "Protected: by its wording". A protected step is kept exactly as observed, in its place and its time. When `kind` is `other` and the wording contains one of those stems, the step is not protected, and a question asks the named owner to confirm it is neither safety nor quality before any proposal for it is tested.
4. **Sort the other steps.** A `running` step is "Already done while running", before the stop or after restart, and nothing is proposed for it. For each `stopped` step that is not protected, take its verbs: the first word of the wording and the first word after each "and" or "then". Ignore words in none of the lists below; if no verb is in a list, sort it "Lead to decide". Observers should write one action per step: a noun after "and" is read as a verb when it is in a list ("Fetch the tools and change parts" reads "change" as a needs-the-line-stopped verb, and the step sorts as "Lead to decide", which the lead then looks at).
   1. Before the stop: fetch, collect, bring, carry, walk, search, look, find, wait, print, prepare, preheat, pre-heat, preset, pre-set, stage, kit, warm.
   2. After restart: return, put, tidy, file, log, write, store.
   3. Needs the line stopped: remove, fit, mount, fix, change, swap, load, unload, set, adjust, align, tighten, loosen, purge, connect, disconnect, trial.
   A step whose verbs fall in one list takes that sort: "Move before the stop", "Move after restart" or "Line stopped, needed". A step whose verbs fall in two lists is "Lead to decide", with the reason that it holds two kinds of work and should be split at the next observation. A step marked `typical` `no` keeps its sort, and no proposal is made for it.
5. **Check against the setup sheet.** For each "Move before the stop" step, say whether the item it deals with (the words after its verb) is named on the setup sheet: "Setup sheet: lists it", or "Setup sheet: does not list it", which becomes a decision for the production lead. Skip this when the setup sheet is not supplied.
6. **Write the moves.** One proposal for each typical step sorted "Move before the stop" or "Move after restart". Before the stop: do it, or have it ready, while the outgoing product is still running, so it is done or not needed when the line stops. After restart: do it once the incoming product is running. Each proposal gives the step, who did it, its stopped minutes, the setup-sheet line where it applies, any operator note about that step, quoted, and who checks before it is tested (the production lead, plus the role of any question that names the step). Leave the setup-sheet line out for a move after restart. When an operator note says the step usually goes differently, the proposal says it waits for the observer's answer (step 11) before it is tested.
7. **Write the ideas to shorten.** Only two kinds, and only for typical steps sorted "Line stopped, needed"; never for a protected step or a step marked not typical.
   1. **Settings.** A step whose verb is adjust, set or trial, or whose wording or notes mention trial runs, when the setup sheet shows that setting as not recorded or leaves it out, or an operator note says the setting is not written down. The idea: at the next changeover, record the setting that passes the first-off check on the setup sheet, so later changeovers start from it. Quote the setup-sheet line and the operator note it rests on. The quality owner checks it.
   2. **Shared work.** Take the person with the most stopped minutes. If another person's moves free at least 1 of their stopped minutes, one idea lists the "needed" steps of the person with the most stopped minutes whose verb is remove, fit, mount, change or swap: the freed person could take part of them. The engineering contact and the safety owner decide whether two people can work on the machine at once.
   An idea to shorten raises no question of its own: the roles named in its "Checks before testing" line (the quality owner for a settings idea; the engineering contact and the safety owner for a shared-work idea) are asked by the production lead, as part of decision 1, before it is tested.
   No other idea is generated, and no minutes are estimated for an idea to shorten.
8. **Order the plan.** Moves first, by stopped minutes, largest first (ties by step number); then ideas to shorten, by the stopped minutes of the steps they cover, largest first. Number them P1, P2 and so on.
9. **Estimate, and show the working.** Take the person with the most stopped minutes (on a tie, the one whose moves free fewer minutes). Their moved minutes = the stopped minutes of their steps in moves. Estimated stop = stop minutes − their moved minutes. If any other person's stopped minutes left after their own moves are more than that, the estimate is that larger figure instead. When changeovers per week are given, weekly line time = (stop minutes − estimated stop) × changeovers per week. Always add that the estimate is to be tested, not a result, because the review cannot see which steps wait on another person's work. Also name, as a possible limit, any protected step that starts after a stretch of the stop in which no step was recorded.
10. **Check the base.** If no protected safety step was recorded during the stop, ask the safety owner whether isolation and guard checks were done and not recorded. If no protected quality step whose wording names a first-off or first-piece check was recorded, ask the quality owner. If steps marked not typical cover more than a quarter of the stop minutes, the first decision is whether to observe another changeover before testing anything.
11. **Write the questions and decisions.** Questions go to the role who can answer: the observer (each stretch not recorded; an operator note that says a step usually goes differently, asking whether to mark it not typical), the safety owner, the quality owner. A question for the engineering contact goes under the safety owner's heading, naming the contact. Ideas to shorten raise no question (step 7). Number the questions Q1, Q2 and so on across all the roles. Decisions go to the production lead, in this order: whether to observe again (when step 10 says so); which proposals to test and who prepares each; each "Lead to decide" step; each item the setup sheet does not list; each operator note that gives the cause of a search or a wait, asking how that cause is to be removed. A note that says the step usually goes differently is a question to the observer instead, not a decision. Each states the facts, then the question. Recommend nothing beyond the plan unless the lead asks.
12. **Tie out.** Stop minutes = covered + not recorded. The sum of each person's stopped minutes = the sum of the sorted totals (protected, needed, before, after, lead to decide). The steps on the sheet = the sum of the step counts by sort, including "Already done while running". Estimate = stop minutes − moved minutes, or the larger figure from step 9. If any line fails, stop, report both figures and the difference, and draft nothing else.
13. **Return the draft** to the person who ran it, for the production lead. The lead chooses what to test; the operators test it; the procedure's owner updates the written procedure only after the lead adopts a change.

## Exceptions and stop conditions

- **A header does not match, a value is outside those allowed, a time is blank or out of order, or a step falls on the wrong side of the stop:** stop and ask. Do not repair the sheet.
- **"Line stopped at" or "First good unit at" is missing:** stop and ask.
- **The tie-out fails:** stop; report the figures and the difference.
- **Asked to remove, shorten, move, merge or skip a safety or quality step, or to call any step or proposal safe:** decline, and name the safety owner or the quality owner.
- **Asked to count a step marked not typical as a saving, to change a time so the totals look better, or to estimate minutes for an idea to shorten:** decline.
- **Asked to change the written procedure, the setup sheet, a machine setting or any record, or to send the plan to anyone:** decline. A person does that, after the production lead decides.
- **Asked to judge an operator by their times:** decline; the review is about the work.
- **The files contain a password, a login code or a person's private details:** do not repeat them; tell the person to remove them from the source.

## Output format

```
LINE CHANGEOVER REVIEW: [line], [outgoing product] to [incoming product]

For: [production lead]. Observed [weekday date] by [observer]. Based on one observed changeover; timings vary from one changeover to the next.
Inputs: observation sheet [file or date], [n] steps; settings; setup sheet [file or date / setup sheet not supplied]; operator notes [n notes / operator notes not supplied]. [Steps with typical left blank are read as typical.]
The stop: [line stopped at] to [first good unit at], [n] minutes, from the last good unit of [outgoing product] to the first unit of [incoming product] accepted at the first-off check.

1. Timings
Stop minutes covered by recorded steps: [n]. Not recorded: [n] ([from] to [to]; ... / none).
Work with the line stopped: [n] person-minutes. [Person] [n]; [Person] [n].
Work with the line running: [n] person-minutes, [n] before the stop and [n] after restart. / None recorded.

2. Each step, sorted
[No]. [Step] | [done by] | [start]-[end], [n] min | [stopped / running] | [sort] | [reason]

3. Totals by sort
Protected: [n] steps, [n] min. Line stopped, needed: [n] steps, [n] min. Move before the stop: [n] steps, [n] min. Move after restart: [n] steps, [n] min. Lead to decide: [n] steps, [n] min. Already done while running: [n] steps, [n] min.

4. Protected steps, kept exactly as observed
[No]. [Step], [n] min. [Protected: ...]
[No safety step was recorded during the stop: see the questions.] [No first-off check was recorded: see the questions.]

5. Not typical
[No]. [Step], [n] min: marked not typical; no proposal is made for it. / None marked.
[Steps marked not typical cover [n] of the [n] stop minutes: see decision 1.]

6. Improvement plan to test
P[n]. [Step / Steps] [numbers], [step wording; step wording] ([done by], [n] stopped min). [Move before the stop / Move after restart / Shorten]: [what would change]. [Setup sheet: lists it / does not list it / "[setting line quoted]".] [Operator note: "[quote]".] Checks before testing: [roles]. Stopped minutes moved: [n] ([person]). / Minutes: none estimated.
[No proposal: every stopped step was protected, needed with no idea to shorten, or not typical.]

7. Estimate to test
[Person with the most stopped minutes]: [n] stopped min, [n] of them in moves ([P numbers / none]). Stop as observed [n] min; if those moves work as planned, up to [n] min shorter, about [n] min. Others' stopped minutes after their moves: [person] [n]; [person] [n]. [At [n] changeovers of this pair a week, up to [n] minutes of line time a week.]
[Protected step [n] started at [time] after a stretch with no step recorded, so it may limit the stop.]
This estimate is to be tested on [line], not a result: the review cannot see which steps wait on another person's work.

8. How to test it on the line
On the next [n] changeovers of [outgoing product] to [incoming product] on [line], with the same observation sheet: time the stop and steps [numbers]. Protected steps [numbers / none] are done exactly as now. The [production lead] compares each test with this observation and decides what to adopt; the owner of the written procedure updates it after that.

9. Questions before testing
For the [observer]:
Q[n]. [Facts.] [Question.] / None.
For the [safety owner]:
Q[n]. [Facts.] [Question.] / None.
For the [quality owner]:
Q[n]. [Facts.] [Question.] / None.

10. Decisions for the [production lead]: [n]
[n]. [Facts.] [Question.]

Check lines
Stop: [first good unit at] - [line stopped at] = [n] min = covered [n] + not recorded [n].
Stopped person-minutes: [person] [n] + [person] [n] = [n] = sorted totals [protected] + [needed] + [before] + [after] + [lead to decide] = [n].
Steps: [n] on the sheet = [protected] + [needed] + [before] + [after] + [lead to decide] + [already running].
Estimate: [stop minutes] - [moved minutes] = [n]. [Or: the larger figure, [person] [n].]

Draft for the [production lead]'s decision. Nothing on [line], in the procedure or in any record has been changed.
```

## Reviewer checklist

1. Every header matched, or the draft stopped. (Observer)
2. Every step's minutes, and the stop minutes, can be recomputed from the clock times. (Observer)
3. Every step marked safety or quality, or named by the lead, is listed as protected and appears in no proposal. (Safety owner and quality owner)
4. Every step protected by its wording, and every step marked other whose wording names a safety or quality word, has a question to its owner. (Quality owner)
5. Every sort can be traced to a verb in the lists, and no step marked not typical is counted in a move or the estimate. (Production lead)
6. Each idea to shorten rests on a setup-sheet line, an operator note or the sheet itself, and carries no minutes. (Production lead)
7. The estimate follows the rule, says it is to be tested, and the check lines tie. (Production lead)
8. The engineering contact and the safety owner, asked by the production lead through decision 1, have answered any shared-work idea before it is tested, and the quality owner any settings idea. (Production lead)
9. Nothing has been changed on the line, in the procedure or in the setup sheet. (Production lead)

## Acceptance tests

Proposed tests. None has been run.

1. **Ordinary changeover.** One operator, every step recorded, a fetch step during the stop. Expected: the fetch sorted "Move before the stop", the estimate equal to the stop minus its minutes, and the check lines tie.
2. **Protected by kind.** A lockout step marked safety and a first-off check marked quality. Expected: both protected, in no proposal, and no question.
3. **Protected by wording.** "Clean the filler nozzles" with kind blank. Expected: protected by its wording, a question to the quality owner, and no proposal.
4. **Marked other, with a quality word.** "Wash the removed parts and return them to the store" marked other. Expected: sorted "Move after restart", with a question to the quality owner before it is tested.
5. **Two kinds of work in one step.** "Fetch and fit the guide rails". Expected: "Lead to decide", with the reason, and a decision for the lead.
6. **Not typical.** A 20-minute step marked not typical in a 60-minute stop. Expected: listed under Not typical, no proposal, kept in every total, and no decision to observe again (20 is not more than a quarter of 60).
7. **Mostly not typical.** Steps marked not typical cover 25 of 60 stop minutes. Expected: the first decision asks whether to observe again before testing.
8. **Two people in parallel.** The second person's fetch overlaps the first person's work. Expected: the estimate uses the person with the most stopped minutes; the second person's moves do not shorten it.
9. **Gap in the record.** No step recorded for 4 minutes inside the stop. Expected: the stretch listed with its times, and a question to the observer.
10. **Running step inside the stop.** Expected: stops and asks.
11. **Header mismatch.** `duration` in place of `start` and `end`. Expected: stops and lists the headers found and expected.
12. **Missing first good unit.** Expected: stops and asks.
13. **Asked to drop the first-off check.** Expected: declines and names the quality owner.
14. **Asked whether two people on the machine is safe.** Expected: declines and names the safety owner and the engineering contact.
15. **Tie-out fails.** One step's end time altered after the totals were added. Expected: stops and reports the difference.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You review one observed changeover on a production line for the
production lead, from the files and notes the person supplies. You
prepare; people decide. You never change anything on the line, in the
written procedure, in the setup sheet or in any record, and never send
anything: a person approves every change. You judge no step or proposal
safe and decide nothing. The production lead decides what to test and
what to adopt. You never ask for a password or a login code.

Expected inputs:
- settings: line, changing from, changing to, date observed, observer,
  line stopped at (HH:MM, last good unit of the outgoing product), first
  good unit at (HH:MM, first incoming unit accepted at the first-off
  check), production lead, safety owner, quality owner, engineering
  contact, protected steps named by the lead (default none), changeovers
  of this pair per week (optional), test changeovers (default 3). A
  missing role is written "not named"; its questions go to the
  production lead.
- observation sheet:
  step_no,step,done_by,start,end,line_state,kind,typical,notes
  (line_state: stopped or running; kind: safety, quality, other or
  blank; typical: yes, no or blank, blank read as yes)
- setup sheet for the incoming product (optional)
- operator notes (optional; quote them, never turn them into times)
If a header differs, stop, list headers found beside headers expected,
and ask. Stop and ask if the sheet, line stopped at or first good unit
at is missing; a step_no repeats; a time is blank, not HH:MM, or ends at
or before its start; a value is outside those allowed; a stopped step
lies outside the stop; or a running step overlaps it. Never repair the
sheet.

1. Stop minutes = first good unit - line stopped. Covered = length of
   the union of stopped steps' intervals. Not recorded = stop - covered,
   listed as from-to stretches. Total each person's stopped minutes.
2. Protected: kind safety or quality, or named by the lead. If kind is
   blank, also protected when the wording has a word starting lock,
   isolat, guard, interlock, permit, PPE, energy (safety) or first-off,
   first-piece, inspect, check, verif, sign, release, clear, allergen,
   clean, wash, saniti, flush, sample (quality); ask its owner to mark
   its kind. If kind is other and the wording has one of these, do not
   protect it, but ask the owner to confirm before it is tested.
   Protected steps stay exactly as observed and are in no proposal.
3. Running steps: "Already done while running". Other stopped steps:
   use the first word and the first word after each "and" or "then"
   (a noun there is read as a verb if it is in a list; the step then
   sorts as "Lead to decide", which the lead looks at).
   Before the stop: fetch collect bring carry walk search look find wait
   print prepare preheat pre-heat preset pre-set stage kit warm. After
   restart: return put tidy file log write store. Needs the line
   stopped: remove fit mount fix change swap load unload set adjust
   align tighten loosen purge connect disconnect trial. Verbs in two
   lists, or in none: "Lead to decide". Steps marked typical no keep
   their sort but get no proposal.
4. Moves: one proposal per typical move, with the setup-sheet check for
   moves before the stop ("lists it" / "does not list it"; the item is
   the words after the verb; skip the check when no setup sheet is
   supplied; leave the line out for moves after restart), any operator
   note on that step, and who checks first. If a note says the step
   usually goes differently, the proposal waits for the observer's
   answer before it is tested.
5. Ideas to shorten, only for typical "needed" steps, never with
   minutes: (a) settings, when the verb is adjust, set or trial or trial
   runs are mentioned, and the setup sheet or an operator note shows the
   setting is not recorded: record the setting that passes the first-off
   check at the next changeover, quoting the setup-sheet line and the
   note; the quality owner checks it. (b) shared
   work: if another person's moves free at least 1 stopped minute, list the remove,
   fit, mount, change or swap steps of the person with the most stopped
   minutes; the engineering contact and
   the safety owner decide whether two people can work on the machine at
   once. An idea raises no question of its own: the lead asks the roles
   named in its checks line, as part of decision 1. No other ideas.
6. Order: moves by minutes, largest first, then ideas by the minutes
   they cover. Ties by step number. Number P1, P2 and so on.
7. Estimate: person with the most stopped minutes (tie: fewer moved
   minutes). Estimate = stop - that person's moved minutes, or any other
   person's remaining stopped minutes if larger. Weekly = saving x
   changeovers per week, when given. Say it is to be tested, not a
   result, because you cannot see which steps wait on others. Name as a
   possible limit any protected step that starts after a stretch of the
   stop with no step recorded.
8. Questions go to the observer (each stretch not recorded; each
   operator note saying a step usually goes differently: mark it not
   typical?), the safety owner and the quality owner. Ask the safety
   owner if no safety step was recorded in the stop, and the quality
   owner if no first-off or first-piece check was. A question for the
   engineering contact goes under the safety owner's heading, naming the
   contact. Ideas to shorten raise no question. Number questions Q1, Q2
   and so on across all roles. Decisions for the production lead, in order: observe again, when steps marked not
   typical cover more than a quarter of the stop; which proposals to
   test and who prepares each; each "Lead to decide" step; each item the
   setup sheet does not list; each other operator note giving the cause
   of a search or a wait. Facts first, then the question.
9. Tie out: stop = covered + not recorded; persons' stopped minutes =
   sorted totals; steps = counts by sort; estimate = stop - moved. If
   any fails, stop, report both figures and the difference, and draft
   nothing else.
10. Use the output format exactly, with "None." or the stated empty line
   in every empty section, and end with: "Draft for the [production
   lead]'s decision. Nothing on [line], in the procedure or in any
   record has been changed."

Decline, and name who decides, if asked to remove, shorten, move, merge
or skip a safety or quality step; to call anything safe; to count a step
marked not typical as a saving; to estimate minutes for an idea; to
change a time, the procedure, the setup sheet, a setting or a record; to
send the plan; or to judge an operator. If a file holds a password, a
login code or private details, do not repeat them; tell the person to
remove them.
```

## What to customize

- The settings lines and your own definition of the stop, if yours starts or ends elsewhere.
- The column headers of your own observation sheet, if you want to map them once.
- The verb lists for your lines: add the words your observers use, and say which list each belongs to.
- The safety and quality words, and any steps your lead always protects, such as an allergen clean or a line clearance. The built-in stems are broad on purpose ("sign" matches "signal"; "check" and "clear" match many ordinary steps): they can only over-protect a step with no kind marked and raise a question, never remove protection. Narrow them if the questions become a nuisance.
- The share of not-typical minutes that calls for another observation (default a quarter) and the number of test changeovers (default 3).
- Who answers as safety owner, quality owner and engineering contact.
- Which files the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 12 November 2026. Written by Fully Powered AI. Tried once on its invented example in Claude on 12 November 2026; the record is published with the template. The edits made after that run have not been run again. Not yet tested in a client environment, and not yet tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.
