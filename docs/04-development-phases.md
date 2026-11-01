# WISE — Development Phases

**Approach:** *track first, then digitize, then automate.*
Phase 1 does **not** replace paper. Signed physical documents stay the official
record. WISE gives each one a tracking number, records every hand-off, stores a scanned copy, checks
it against its document-type checklist, and links it to the office and individual
targets it supports. Later phases replace the paper forms with documents created in the system
and enforce hard gates.

```
Phase 1  Tracking & Monitoring Foundation   ← physical docs scanned, tracked, checked; monthly/semestral monitoring
Phase 2  Planning Linkage                   ← OPCR/IPCR, WFP, PPMP, APP encoded; documents linked to plan lines
Phase 3  Born-digital Procurement & Budget  ← PR, ORS, PO/Contract, IAR created in WISE with system gates
Phase 4  Disbursement & WSP Operations      ← DV, LDDAP-ADA, travel, cash advance, liquidation, honoraria
Phase 5  E-signature, Integration, Closure  ← PNPKI, PhilGEPS/DBM/COA outputs, audit & records disposition
```

---

## Phase 1 — Tracking & Monitoring Foundation (≈ 3–4 months)

### 1.1 Objectives

1. **Know where every document is.** Each physical document gets a tracking number and a QR
   routing slip. Every receive and release is logged, along with how long it sat at each desk.
2. **Keep a scanned copy of everything.** Scans are uploaded at each signature milestone, so the
   file has the full signed history even when the original is with COA or the supplier.
3. **Check completeness against the document-type checklist.** When a document is registered,
   its checklist appears (from [`02-document-checklists.md`](02-document-checklists.md)).
   The receiving desk ticks what is attached and what is missing. The system **flags** gaps but does not block yet.
4. **Monitor performance every month.** Staff record monthly outputs against their IPCR
   targets and upload MOV. The outputs roll up to the OPCR. The semestral review draws on this data.

### 1.2 Scope

| Feature | Description |
|---|---|
| **Master data (minimal)** | Offices/units, users and roles, document types (from `config/document-types.yaml`), PAP list, FY. Enough to tag documents, without full budget tables yet |
| **Document registration** | Choose document type → enter key metadata (title, reference no., date, amount, PAP, supplier/payee, originating office) → upload scan → system issues a **Tracking No.** (e.g., `WSP-2027-000123`) |
| **QR routing slip** | Printable slip stapled to the physical document. Scanning the QR with a phone or webcam opens the record, so receive/release takes one tap |
| **Receive / release log** | Every hand-off is logged: from, to, date/time, action taken (for signature, for review, returned, filed). The document's **current location** and **custodian** are always visible |
| **Version uploads** | New scan at each milestone (e.g., "PR – signed by requesting officer", "PR – approved"). Each upload is hashed (SHA-256) and stamped with the uploader and time. Earlier versions are kept |
| **Checklist-based completeness check** | Each document type shows its checklist. The desk marks items *present / missing / not applicable* with remarks. Status: **Complete / Incomplete – returned / Complete with remarks** |
| **Linking documents** | Manually link related documents (PR ↔ RFQ ↔ Abstract ↔ PO ↔ ORS ↔ IAR ↔ DV) into one **transaction folder**, so the chain can be viewed end to end |
| **Monthly accomplishment monitoring** | Encode the IPCR targets/success indicators for the semester (simple form, no workflow yet). Each month staff enter outputs and upload MOV (photos, attendance sheets, reports, or a link to a tracked document). Supervisor confirms |
| **Semestral OPCR/IPCR review support** | Generates draft IPCR/OPCR accomplishment columns from the monthly entries and MOV, ready for rating under TESDA's SPMS (rating is still done on paper or in the existing form in Phase 1) |
| **Dashboards** | (a) Documents per desk with aging and SLA status (RA 11032); (b) incomplete/returned documents by reason; (c) transactions by stage; (d) monthly accomplishment vs. target per person and office; (e) MOV completeness % |
| **Search & retrieval** | Search by tracking no., reference no., payee/supplier, amount, PAP, date, document type, or text (OCR, if enabled) |
| **Notifications** | Email/in-app alerts: document arrives at your desk, document overdue, monthly accomplishment due, MOV missing |
| **Audit log & security** | Log that cannot be altered, role-based access, MFA for admins, restricted access for sensitive personal data (competitor passports, minors) |

**Out of scope for Phase 1:** creating forms in the system, e-signatures, hard
blocking gates, budget balances/earmarks, accounting entries, external integrations.

### 1.3 Physical-document tracking flow

```
Originator prepares and signs paper document
        │
        ▼
Records/Secretariat desk ── Register in WISE: choose type, metadata, scan, checklist tick
        │                   → Tracking No. + QR slip printed and attached
        ▼
Each next desk ── scan QR → "Receive" ── act (sign/review) ── upload new scan if signed
        │                                   └─ "Release to <next desk>"  or  "Return" (reason code)
        ▼
Final action (e.g., approved, paid, filed) ── upload final signed copy ── status CLOSED
        │
        ▼
Original filed / sent to COA ── location recorded ("Original with COA Audit Team, transmittal no. …")
```

### 1.4 Monthly → semestral monitoring flow

```
Semester start:  OPCR targets (office) → IPCR targets (individual) encoded and linked to OPCR success indicators
Monthly:         staff log outputs + MOV  →  supervisor confirms  →  roll-up to office dashboard
Mid-semester:    variance alerts (behind target, missing MOV)
Semester end:    system compiles accomplishments + MOV  →  rating per SPMS  →  PMT calibration (outside system in Phase 1)
```

### 1.5 Phase 1 sprint plan (2-week sprints)

| Sprint | Deliverable |
|---|---|
| 1 | Users/roles/offices, document-type registry loaded from YAML, base UI |
| 2 | Document registration, scan upload (PDF/JPG, multi-page), hashing, Tracking No. |
| 3 | QR routing slip, receive/release/return logging, current-location view |
| 4 | Checklist completeness check per document type; return reasons; version uploads |
| 5 | Transaction folders and document linking; search; optional OCR |
| 6 | IPCR/OPCR target encoding; monthly accomplishment entry with MOV |
| 7 | Dashboards (aging/SLA, completeness, accomplishment vs. target); notifications |
| 8 | Semestral compilation report; UAT with Secretariat, Budget, Accounting, BAC Sec; training; go-live |

### 1.6 Acceptance criteria

* 100% of documents entering the WSP Secretariat get a Tracking No. within one working day of receipt.
* The current location of any tracked document can be found in under 30 seconds.
* Every registered document has its checklist completed at the first receiving desk.
* At least 90% of staff submit monthly accomplishments with MOV by the 5th working day of the following month.
* The semestral accomplishment draft for each IPCR/OPCR is generated from system data with no re-encoding.

### 1.7 Phase 1 data model (core tables)

`office`, `user`, `role`, `document_type`, `checklist_template(version)`,
`document` (tracking_no, type, ref_no, date, amount, pap, payee, status, current_custodian),
`document_file` (version, sha256, uploaded_by, uploaded_at), `document_movement`
(from, to, action, timestamp, remarks), `checklist_result` (item, state, remarks),
`transaction_folder`, `folder_document`, `opcr_indicator`, `ipcr_indicator`
(links opcr_indicator), `monthly_accomplishment`, `mov_file`, `audit_log`.

These tables stay in place in later phases. Phase 3 adds structured form data to
the same `document` record, so nothing has to be migrated.

---

## Phase 2 — Planning Linkage (≈ 2–3 months)

* Full PAP/UACS master and WFP encoding (allotment by PAP and object of expenditure).
* OPCR → DPCR → IPCR cascade with approval workflow. SPMS rating and PMT calibration done in the system.
* PPMP (indicative/final/supplemental) and APP consolidation, with APP-CSE export.
* Tracked documents from Phase 1 get linked to **APP lines and WFP lines**, so spending can be monitored against the plan.
* Dashboards: APP implementation status, WFP utilization (still from encoded amounts), GAD tagging.

## Phase 3 — Born-digital Procurement & Budget (≈ 3 months)

* PR, TOR/specs, RFQ, abstract, BAC resolution, NOA, ORS/BURS, PO/Contract, NTP, and IAR are **created in WISE** using the official GAM/COA layouts.
  They are still printed for wet signature where needed.
* **Hard gates switch on:** G1–G8, G11, G12 (APP line required, fund earmark, ORS + CAF before PO, IAR before DV, and the rest).
* Budget registers: earmarks, obligations (RAOD), and balances for each PAP.
* PhilGEPS reference tracking and mode-determination wizard per the RA 12009 IRR.

## Phase 4 — Disbursement & WSP Operations (≈ 3 months)

* DV with the COA 2012-001 checklist for each transaction type, Box A–E certifications, withholding tax/BIR 2307, retention ledger, LDDAP-ADA/check register.
* WSP operations: delegation, competitor, and expert registry; travel orders and foreign travel authority; cash advance and liquidation with deadline enforcement (G9); honoraria; allowances; WSI/WS Asia fees.
* Competition readiness dashboard for each event (NSC, ASEAN Skills, WorldSkills).

## Phase 5 — E-signature, Integration, Audit & Closure (≈ 3 months)

* DICT **PNPKI** digital signatures for each form type COA has agreed to accept electronically.
* Outputs and integrations: BAR/FAR in the DBM format, GPPB PMR, PhilGEPS, PS-DBM, accounting system/eNGAS JEV export, HRIS.
* COA AOM/NS/ND tracker, internal audit findings, closure checklist, read-only portal for the COA Audit Team.
* Records Disposition Schedule (NAP), archive, retention alerts. Security assessment, then turnover.

---

## Why this order

* **Quick wins.** Tracking and visible aging cut lost documents and follow-up calls within weeks, without changing any approved form.
* **Low regulatory risk.** Phase 1 keeps paper as the official record, so it needs no COA approval for electronic documents.
* **Clean data later.** Checklist results and hand-off logs from Phase 1 show the real bottlenecks and missing documents, so Phase 3 gates can be tuned to evidence.
* **PBB and SPMS value early.** Monthly accomplishment and MOV records start in Phase 1, so the first semestral review is already backed by system data.
