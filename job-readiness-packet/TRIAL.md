# Job readiness packet: one trial on its example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in `public/example.md` (settings, order lines, requirements, document register and material lines). No client data was used. The assistant was given the template's fenced instruction block and output format and the example's inputs, and produced the packet below before comparing it with the example's published output.

One slip in method: the first read of the example file was cut at a character limit and showed the start of the published output, up to the second decision, before the packet was worked out. The packet was still built from the inputs by the template's steps, and the later parts (material, certificates, missing requirements, decisions 3 to 8) were not seen until after.

## What came out

**JOB READINESS PACKET: Firm A, Plant 1, job J-2043, check date 2026-11-09**

- **For:** Production manager and Quality lead.
- **Prepared:** 2026-11-10, from order lines (3), requirements (11), document register (14 rows, 9 documents), material lines (2).

**Order lines:** 3. Quantity in all: 350.

- Line 1: BRK-110, quantity 200, due 2026-11-30.
- Line 2: HSG-220, quantity 50, due 2026-12-07.
- Line 3: CLP-305, quantity 100, due 2026-12-07.

**Requirements checked:** 11. Matched 5. Conflicting calls 2. Not in register 1. No approved revision 0. Two approved revisions 1. Revision not called 1. Called revision not approved 1. Tie-out: 5 + 2 + 1 + 0 + 1 + 1 + 1 = 11.

**Matched: 5 requirements**

- Line 1 drawing DWG-BRK-110 Bracket BRK-110, revision C, approved 2026-03-16 by Engineering lead. Called by Customer order.
- Line 1 specification PS-ANOD-02 Anodizing process, revision B, approved 2025-10-06 by Process engineer. Called by Drawing note.
- Line 1 inspection IP-BRK-110 Bracket inspection plan, revision A, approved 2025-09-09 by Quality lead. Called by Order routing.
- Line 2 material MS-SS304 Stainless bar material specification, revision C, approved 2025-03-03 by Quality lead. Called by Drawing note.
- Line 3 drawing DWG-CLP-305 Clamp CLP-305, revision B, approved 2025-12-01 by Engineering lead. Called by Customer order.

**Conflicting revisions: 1 conflict (2 requirements)**

- Line 2 drawing DWG-HSG-220 Housing HSG-220: revision D called by Customer order; revision E called by Customer email. Register: approved revision D, approved 2026-01-19; E is Draft.

**Document gaps: 4 requirements**

- Line 3 specification PS-HT-11: not in the register. Called: revision A by Drawing note.
- Line 2 specification PS-WELD-07 Welding process: two approved revisions in the register, A (approved 2024-08-01) and B (approved 2026-10-26). Called: revision A by Drawing note.
- Line 1 material MS-AL6061 Aluminum bar material specification: no revision called by Drawing note. Register: approved revision A, approved 2024-02-12.
- Line 2 inspection IP-HSG-220 Housing inspection plan: revision B called by Order routing; B is Superseded in the register. Approved revision C, approved 2026-10-13.

**Material:** 2 materials. Available 1. On order 1. Short 0. No material line supplied 0. Tie-out: 1 + 1 + 0 + 0 = 2.

- Line 1 MS-AL6061 Aluminum bar material specification: needed 220, allocated 220, on order 0. Available. Certificate: on file.
- Line 2 MS-SS304 Stainless bar material specification: needed 180, allocated 60, on order 150, expected 2026-11-27 (10 days before the due date of 2026-12-07). On order; short on hand by 120. Certificate: not on file.

**Certificates:** on file 1, not on file 1, not stated 0. Tie-out: 1 + 1 + 0 = 2.

**Material lines matching no requirement:** (none)

**Requirements not supplied**

- Line 3 CLP-305: no inspection requirement supplied.

**Decisions for Production manager and Quality lead: 8**

1. **Line 2, DWG-HSG-220.** Two sources call different revisions: D by the Customer order and E by the Customer email. The register approves D, and E is a Draft. Which revision does the order require, and does anything in the register or the order need to change?
2. **Line 3, PS-HT-11.** The specification is called at revision A and is not in the register. Is there an approved specification for it, and does it belong in the register?
3. **Line 2, PS-WELD-07.** The order calls revision A. The register holds two approved revisions, A (approved 2024-08-01) and B (approved 2026-10-26). Which revision applies to this order, and which approved row is correct?
4. **Line 1, MS-AL6061.** The Drawing note calls no revision. The register's approved revision is A, approved 2024-02-12. Which revision does the order require?
5. **Line 2, IP-HSG-220.** The Order routing calls revision B, which the register shows as Superseded. The approved revision is C. Which revision does the order require?
6. **Line 2, MS-SS304.** 60 of 180 are allocated and 150 are on order, expected 2026-11-27, 10 days before the due date. Short on hand by 120. How is the gap covered before work starts?
7. **Line 2, MS-SS304.** The certificate is not on file. Who obtains it, and is it needed before work starts?
8. **Line 3, CLP-305.** No inspection requirement was supplied. Is there an inspection plan for this part, and should it be added to the order's requirements?

**Not proven:** The packet compares only the lists supplied. It does not show that the register is right, that the drawing at the machine is the approved revision, that the material held is the grade the specification calls for, or that a requirement has not been left off the order. Specification and material requirements are checked only where the order lists them, and a document called at different revisions on different lines is not compared.

Draft for the decision of the Production manager and the Quality lead. No drawing, revision, process or material has been approved, no job has been released, and no record has been changed.

## What was observed

- Every part of the output format was produced, and every tie-out held (11 requirements, 2 materials, 2 certificates). No stop condition was triggered, and nothing was declined, because the inputs were clean and the run asked for none of the refusals.
- Against the published example, the counts, classes, quantities, day count, certificate results and the number and order of decisions are the same. The differences are small:
  - The "Prepared" line. The format says "today's date", so this run wrote 2026-11-10; the example wrote 2026-11-09, the check date.
  - The wording of decisions 2, 3, 6 and 8 differs. The facts are the same. This run's decision 6 adds "Short on hand by 120" and its decision 3 asks which approved row is correct; the example asks whether the register needs to change. Decision wording is free in the template, so this is expected.
  - Small wording differences in decision 4 (this run added the approval date).
- Every fact in the output is in the inputs. The day count (10 days before) and the short-on-hand figure (120) are worked from the inputs. Neither this output nor the example adds a fact that is not in the inputs.
- Where the template left room for a guess:
  - "Prepared: [today's date]" and the check date can differ, and the template does not say which one a packet carries on a re-run. Both appear here.
  - The material line prints "[title]", but the template does not say what to print when a material specification has no register row (and so no title).
  - The format has no singular for "1 day".
  - Decision wording is not fixed, so two runs will not match word for word.
  - Within the document gaps, the order is by class and the template does not say whether each class is then ordered by line; this run did so.
- Shortcomings: this was one run, by one model, on one clean example. It does not test the acceptance tests that need bad input (a mismatched header, "Rev C" against "C", a request to say the job is ready). The reviewer checklist was applied to this output by the same model that wrote it, not by the people the checklist names, so it does not replace their review.

## Changed after the run

The output and observations above are as recorded and describe the template as it stood at the run. After an independent review on 10 November 2026 the template was changed as listed below, and it was not run again. Nothing in the recorded output was altered. The example's inputs and published output are unchanged.

- **Prepared line.** It now carries the check date from the settings, as the example does. This run wrote the day it was run (2026-11-10), so its Prepared line differs from the template as it now stands by design.
- **Material title.** A material line for a document not in the register prints the doc_id alone.
- **One day.** The format now gives "1 day" as well as "[n] days".
- **Order of gaps.** Within each class of document gap, rows go by line, then type, then document id.
- **Expected date.** The date clause is printed for On order lines only.
- **Required columns.** The inputs now name the required columns of each table and say which may be blank (the requirements' revision, the register's approved date and approver outside Approved rows, the material lines' expected date and certificate).
- **Missing requirements.** The procedure now says "no drawing requirement or no inspection requirement", as the instruction block does.
- **Requirement key.** A requirement row is keyed by line, document, revision and source; an exact duplicate stops the work.
- **Conflict count.** A conflict is counted, and given a decision, only when its rows are classed Conflicting calls; a document not in the register that is called at two revisions stays Not in register. Clarification only; this example has no such case.
- **Line missing both.** A line with no drawing and no inspection requirement is printed once as "no drawing or inspection requirement supplied". Clarification only; this example has no such case.
- **Print rules in the instruction block.** The block now carries the singular and plural forms for requirements and conflicts, the rule that a conflict counts once, and the rule that a "No material line supplied" line has no certificate sentence, which the format notes already gave. The wrapping of one long line in the block was also tidied.
- **Blind run.** This run saw the published output down to decision 2 before it worked. The next run should be blind.
