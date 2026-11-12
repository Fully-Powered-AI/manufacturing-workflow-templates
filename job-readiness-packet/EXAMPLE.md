# Job readiness packet: an invented example

*Illustrative example with invented data.* The firm, the people, the documents, the part numbers, the dates and the quantities below are all invented. The firm is an invented 40-person machine shop whose production planner prepares a packet before job J-2043 is released to the floor. First come the inputs the planner supplied, in full, then the packet the workflow template returned.

## The inputs

### 1. Settings

```
Site: Firm A, Plant 1
Job number: J-2043
Check date: 2026-11-09
Production owner role: Production manager
Quality owner role: Quality lead
```

### 2. Order lines

```
job_no,line_no,part_no,qty,due_date
J-2043,1,BRK-110,200,2026-11-30
J-2043,2,HSG-220,50,2026-12-07
J-2043,3,CLP-305,100,2026-12-07
```

### 3. Requirements

```
job_no,line_no,req_type,doc_id,revision_called,source
J-2043,1,drawing,DWG-BRK-110,C,Customer order
J-2043,1,specification,PS-ANOD-02,B,Drawing note
J-2043,1,inspection,IP-BRK-110,A,Order routing
J-2043,1,material,MS-AL6061,,Drawing note
J-2043,2,drawing,DWG-HSG-220,D,Customer order
J-2043,2,drawing,DWG-HSG-220,E,Customer email
J-2043,2,specification,PS-WELD-07,A,Drawing note
J-2043,2,inspection,IP-HSG-220,B,Order routing
J-2043,2,material,MS-SS304,C,Drawing note
J-2043,3,drawing,DWG-CLP-305,B,Customer order
J-2043,3,specification,PS-HT-11,A,Drawing note
```

### 4. Document register

```
doc_id,title,revision,status,approved_date,approved_by
DWG-BRK-110,Bracket BRK-110,B,Superseded,2025-09-02,Engineering lead
DWG-BRK-110,Bracket BRK-110,C,Approved,2026-03-16,Engineering lead
PS-ANOD-02,Anodizing process,A,Superseded,2024-05-20,Process engineer
PS-ANOD-02,Anodizing process,B,Approved,2025-10-06,Process engineer
IP-BRK-110,Bracket inspection plan,A,Approved,2025-09-09,Quality lead
MS-AL6061,Aluminum bar material specification,A,Approved,2024-02-12,Quality lead
DWG-HSG-220,Housing HSG-220,D,Approved,2026-01-19,Engineering lead
DWG-HSG-220,Housing HSG-220,E,Draft,,
PS-WELD-07,Welding process,A,Approved,2024-08-01,Process engineer
PS-WELD-07,Welding process,B,Approved,2026-10-26,Process engineer
IP-HSG-220,Housing inspection plan,B,Superseded,2025-04-14,Quality lead
IP-HSG-220,Housing inspection plan,C,Approved,2026-10-13,Quality lead
MS-SS304,Stainless bar material specification,C,Approved,2025-03-03,Quality lead
DWG-CLP-305,Clamp CLP-305,B,Approved,2025-12-01,Engineering lead
```

### 5. Material lines

Quantities are in kilograms.

```
job_no,line_no,doc_id,qty_needed,qty_allocated,qty_on_order,expected_date,cert_on_file
J-2043,1,MS-AL6061,220,220,0,,yes
J-2043,2,MS-SS304,180,60,150,2026-11-27,no
```

## The output

The output below is shown with bold type and bullets for reading; the template's output format is plain text with the same content, order and wording.

**JOB READINESS PACKET: Firm A, Plant 1, job J-2043, check date 2026-11-09**

- **For:** Production manager and Quality lead.
- **Prepared:** 2026-11-09, from order lines (3), requirements (11), document register (14 rows, 9 documents), material lines (2).

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
2. **Line 3, PS-HT-11.** The specification is called at revision A and is not in the register. Where is the approved specification, and does it need to be added to the register?
3. **Line 2, PS-WELD-07.** The order calls revision A. The register shows two approved revisions, A approved 2024-08-01 and B approved 2026-10-26. Which revision applies to this order, and does the register need to change?
4. **Line 1, MS-AL6061.** The Drawing note calls no revision. The register's approved revision is A. Which revision does the order require?
5. **Line 2, IP-HSG-220.** The order routing calls revision B, which the register shows as Superseded. The approved revision is C. Which revision does the order require?
6. **Line 2, MS-SS304.** 60 of 180 are allocated and 150 are on order, expected 2026-11-27, 10 days before the due date. Does the job wait for the delivery, or is it handled another way?
7. **Line 2, MS-SS304.** The certificate is not on file. Who obtains it, and is it needed before work starts?
8. **Line 3, CLP-305.** No inspection requirement was supplied. Does the part have an inspection plan, and should it be added to the requirements?

**Not proven:** The packet compares only the lists supplied. It does not show that the register is right, that the drawing at the machine is the approved revision, that the material held is the grade the specification calls for, or that a requirement has not been left off the order. Specification and material requirements are checked only where the order lists them, and a document called at different revisions on different lines is not compared.

Draft for the decision of the Production manager and the Quality lead. No drawing, revision, process or material has been approved, no job has been released, and no record has been changed.
