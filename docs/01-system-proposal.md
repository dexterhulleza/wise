# WISE — System Proposal

**WorldSkills Philippines Integrated Administrative System**
Proposed for: WorldSkills Philippines Secretariat (TESDA)
Document status: Draft v0.1 for validation

---

## 1. Purpose

WISE replaces paper routing and separate spreadsheets with **one document chain you can trace**,
from the budget line (PAP/UACS) to the final payment and audit closure. Three rules shape it:

1. **Nothing moves without its prior document.** A PR cannot exist without an APP
   line, a PO cannot be signed without a certified ORS and CAF, and a DV cannot be
   created without an accepted IAR (or, for non-procurement items, the document that gives the legal basis).
2. **Every document type has a versioned checklist.** The checklist covers required fields,
   attachments, linked prior documents, and signatories, and it cites its legal basis.
   A document cannot be submitted until its checklist passes. A reviewer can only
   return it with a reason code.
3. **Performance and money are tied together.** Every peso obligated and disbursed
   traces back to a PAP, a WFP line, and an OPCR/IPCR success indicator. Every
   reported accomplishment links to its means of verification (MOV).

## 2. Corrected end-to-end process

The reference 10-stage flow has been checked against current rules (RA 12009 and
its IRR, PD 1445, the GAM, COA Circ. 2012-001, CSC SPMS). The changes are listed in
[`03-legal-basis-and-corrections.md`](03-legal-basis-and-corrections.md). The
**corrected flow** has 11 stages over two tracks:

```
                     ┌──────────────────────────────────────────────────────────────┐
 STAGE 0             │ Budget Preparation: Tier 1/Tier 2 proposal, Indicative PPMP, │
                     │ Indicative APP, GAD Plan & Budget                            │
                     └──────────────────────────────┬───────────────────────────────┘
                                                    ▼ (GAA enacted)
 STAGE 1  Performance & Financial Planning: PAP (GAA/PREXC) → WFP/Financial Plan → OPCR → DPCR → IPCR
                                                    ▼
 STAGE 2  Procurement Planning: Market Scoping → Final PPMP → APP (HoPE-approved, posted) + APP-CSE
                                                    ▼
          ┌──────────── PROCUREMENT TRACK ────────────┐   ┌──── NON-PROCUREMENT TRACK ────┐
 STAGE 3  │ Request Prep: PR + TOR/Specs + ABC        │   │ N1 Request: Travel Order,     │
 STAGE 4  │ Review: completeness → APP/PPMP match →   │   │    honoraria, allowance, WSI  │
          │   fund earmark → approval                 │   │    fee, cash advance request  │
 STAGE 5  │ Procurement: mode → solicitation (PhilGEPS)│  │ N2 Fund earmark → approval    │
          │   → evaluation → post-qual → BAC Res →    │   │ N3 ORS/BURS                   │
          │   HoPE approval → Notice of Award         │   │ N4 DV / Cash advance release  │
 STAGE 6  │ Obligation: ORS/BURS + CAF  ◄── GATE      │   │ N5 Liquidation (deadline-     │
          │   → PO/Contract signing → NTP → COA copy  │   │    enforced)                  │
 STAGE 7  │ Delivery → Inspection → Acceptance (IAR)  │   └───────────────┬───────────────┘
          │   → PAR / ICS / RIS                       │                   │
 STAGE 8  │ Billing (invoice) → DV → Accounting (Box C)│                  │
          │   → Approval (Box D) → LDDAP-ADA / check  │                   │
          └─────────────────────┬─────────────────────┘                   │
                                ▼                                         ▼
 STAGE 9  Monitoring: accomplishment reports + MOV → OPCR/DPCR/IPCR rating → BARs/FARs → PMR → reconciliation
                                ▼
 STAGE 10 Audit & Closure: records verification → COA audit/AOM response → warranty expiry → release of
          retention/securities → project closure → records disposition
```

### 2.1 Stage detail

| Stage | Steps | Key documents | Responsible | Gate (must be true before exit) |
|---|---|---|---|---|
| **0 Budget Preparation** | Prepare the budget proposal for the coming FY; Indicative PPMP; Indicative APP; GAD tagging | BP forms, Indicative PPMP, Indicative APP, GAD Plan & Budget | WSP Secretariat, Planning, Budget | Indicative PPMP total ≤ proposal for each PAP/object of expenditure |
| **1 Performance & Financial Planning** | Load GAA PAPs (PREXC/UACS); prepare WFP/Financial Plan; cascade targets OPCR → DPCR → IPCR | WFP, BED forms (Financial Plan, Physical Plan, Monthly Disbursement Program), OPCR, DPCR, IPCR | Secretariat, Planning, Budget, HR/PMT | WFP total = allotment. OPCR targets map to PAP physical targets. Every IPCR success indicator maps to a DPCR/OPCR indicator |
| **2 Procurement Planning** | Market scoping; Final PPMP per end-user; consolidation; APP approval by HoPE; posting; APP-CSE to PS-DBM; supplemental APP as needed | Market Scoping Report, PPMP, APP, APP-CSE | End-user, Procurement Unit, BAC Secretariat, HoPE | Every PPMP line is tied to a WFP line and UACS code. APP is approved and posted |
| **3 Request Preparation** | Draft TOR/specs; compute ABC from market scoping; PR citing the APP line | PR, TOR/Technical Specs, ABC computation, Market Scoping Report | Requesting Officer, TWG/Committee Chair | PR quantity/amount ≤ remaining APP line balance |
| **4 Review & Approval** | Completeness check; APP/PPMP verification; fund availability and earmark; approval | PR (approved), Fund Earmark record | Secretariat, Procurement Unit, Budget, Approving Official | Earmark created. PR approved under the delegated authority limit |
| **5 Procurement Processing** | Mode determination; pre-procurement conference (where required); solicitation through PhilGEPS; bid opening/RFQ; evaluation; post-qualification; BAC Resolution; HoPE approval; NOA | ITB/RFQ, Bid/Quotation docs, Abstract, Post-qual report, BAC Resolution, NOA | Procurement Unit, BAC, TWG, HoPE | NOA issued. Winning bid ≤ ABC. Required postings made |
| **6 Budget Obligation** | ORS/BURS certified by Budget (allotment); CAF by Chief Accountant; PO/Contract signed; performance security; NTP; COA copy | ORS/BURS, CAF, PO/Contract, Performance Security, NTP | Budget, Accounting, HoPE, Supplier | **ORS and CAF certified before the PO/contract is signed.** Contract copy sent to COA within the prescribed period |
| **7 Implementation & Acceptance** | Delivery/service; inspection; acceptance; property recording; liquidated damages if late | DR, Invoice, IAR, PAR/ICS/RIS, property cards | Supplier, End-user, Inspection Committee, Supply/Property | IAR complete (inspected and accepted). Property document issued where applicable |
| **8 Accounting & Payment** | Billing; DV with COA 2012-001 attachments; Accounting review (Box C); approval (Box D); LDDAP-ADA/check; withholding tax; retention | DV, LDDAP-ADA/Check, BIR 2307, JEV | Accounting, Approving Official, Cash/Disbursing | DV checklist passes. Amount ≤ obligation balance |
| **9 Monitoring** | Accomplishment reports with MOV; semestral SPMS ratings; BAR/FAR submission; PMR; reconciliation | Accomplishment Report, MOV, rated OPCR/DPCR/IPCR, BARs/FARs, PMR | Secretariat, Planning, HR/PMT, Budget, Accounting, BAC Sec | Every reported accomplishment has MOV attached. Budget and Accounting balances reconcile |
| **10 Audit & Closure** | Records verification; respond to AOMs; settle NS/ND; warranty expiry; release retention and securities; closure report; archive under the RDS | Project Completion Report, Release of Retention, AOM replies, Records Transmittal | Records, Internal Audit, COA, Accounting | No open AOM/ND. Warranty expired. Retention released. Records indexed |

### 2.2 Non-procurement track (WorldSkills-specific)

A large part of WSP spending is not procurement and must not be forced through
the BAC. WISE handles these as typed transactions with their own checklists:

| Transaction | Typical WSP use | Core prior documents | Basis (verify current) |
|---|---|---|---|
| **Local travel** | NSC/regional competitions, expert meetings | Approved Travel Order, Itinerary, ORS | EO 77 s. 2019; COA 2012-001 |
| **Foreign travel** | ASEAN Skills Competition, WorldSkills Competition, WSI General Assembly | Foreign Travel Authority (proper approving level), Travel Order, Itinerary, ORS | EO 77 s. 2019; OP/DBM foreign-travel rules |
| **Cash advance** | Delegation expenses abroad, competition operations | Approved CA request, bonded Special Disbursing Officer, no unliquidated prior CA | COA Circ. 97-002, as amended |
| **Liquidation** | After travel or an event | Liquidation Report, receipts/invoices, Certificate of Travel Completed, RER where allowed | COA Circ. 97-002; COA 2012-001 |
| **Honoraria** | Experts, judges, chief experts, resource persons | Office Order/designation, legal basis, attendance/output proof, approved rates | Applicable DBM Budget Circulars on honoraria |
| **Competitor allowances / incentives** | Training allowance, cash incentives for medalists | Legal/charter basis (GAA, TESDA Board resolution or policy), approved list, ID and bank details | Agency-specific — **confirm with Legal** |
| **Membership / participation fees** | WorldSkills International, WorldSkills Asia, ASEAN fees | Membership basis, WSI invoice, FX computation, approval | Not procurement. Foreign remittance per Accounting rules |
| **Fund transfers / MOAs** | Co-hosting with LGUs, schools, industry | MOA, legal basis, recipient accreditation | COA rules on fund transfers |

Every transaction still passes **N2 fund earmark → N3 ORS/BURS → N4 DV**, with the same gates as the procurement track.

## 3. Document Flow Engine (the core of the system)

### 3.1 Document lifecycle (same for every type)

```
DRAFT ─► SUBMITTED ─► COMPLETENESS CHECK ─► IN REVIEW (step 1..n) ─► APPROVED ─► RELEASED ─► CLOSED ─► ARCHIVED
            ▲                │                      │
            └──── RETURNED ◄─┴──────────────────────┘   (return requires a reason code + comment)
                                                    └─► CANCELLED (with authority + reason; frees earmark)
```

* **Submit** is allowed only when the automatic checklist checks pass (fields, attachments, linked documents, amounts).
* **Completeness check** is a person confirming the manual checklist items (e.g., "specs are not brand-specific").
* **Review steps** come from the document type's routing definition, can depend on amount or mode, and each has an SLA (RA 11032).
* **Approved/certified** documents are locked. Changes need an *amendment* document that links to the original.
* Each transition records who did it, when, which checklist version applied, and a hash of the attachments.

### 3.2 Checklist model

Each **document type** defines:

| Element | Example (Purchase Request) |
|---|---|
| `required_fields` | PR no., date, office, PAP/UACS, APP line ref, items, unit, qty, unit cost, total, purpose |
| `prerequisites` | Approved APP line with enough balance. TOR/specs attached. ABC computation attached |
| `attachments` | TOR/Technical Specs, Market Scoping Report, ABC computation |
| `auto_validations` | `pr.total <= app_line.remaining`, `pr.uacs == ppmp_line.uacs`, specs contain no brand names (keyword flag) |
| `manual_checks` | Specs are performance-based. Quantity matches the actual need. Delivery schedule is realistic |
| `signatories` | Requested by (End-user) → Funds available (Budget) → Approved by (per Delegation of Authority) |
| `routing_rules` | Amount bands and fund source pick the approver from the Delegation of Authority table |
| `sla_days` | Classification per Citizen's Charter (simple/complex/highly technical) |
| `legal_basis` | RA 12009 IRR; COA 2012-001; TESDA DOA |
| `retention` | Records Disposition Schedule item and years |
| `version` / `effective_date` | Versioned, so an old document is always judged against the checklist that applied when it was created |

Full checklists are in [`02-document-checklists.md`](02-document-checklists.md), and the machine-readable
form is in [`../config/document-types.yaml`](../config/document-types.yaml).

### 3.3 Traceability key

Every document carries the **chain key**:

```
FY ─ Fund ─ PAP (PREXC/UACS) ─ WFP line ─ PPMP line ─ APP line ─ PR ─ NOA ─ ORS ─ PO/Contract ─ IAR ─ DV ─ LDDAP/Check
                                  └─ OPCR SI ─ DPCR SI ─ IPCR SI ─ Accomplishment ─ MOV
```

One click from any DV goes back to the APP, the PAP, and the performance target it
served. This answers the usual COA and PBB question: *"what did this money accomplish?"*

### 3.4 Hard gates (system-enforced)

| # | Gate | Basis |
|---|---|---|
| G1 | PPMP line must link to a WFP line with the same UACS object code | Budget–procurement link (RA 12009) |
| G2 | PR must cite an approved APP line with enough remaining balance | RA 12009: no procurement outside the APP |
| G3 | PR approval creates a fund earmark. Total earmarks ≤ unobligated allotment | Prevents committing funds twice |
| G4 | Award only after the GAA takes effect and the allotment is released (EPA can run until then) | RA 12009 IRR (EPA) |
| G5 | **PO/Contract cannot be signed until ORS/BURS (Budget) and CAF (Accounting) are certified** | PD 1445 Secs. 86–87 |
| G6 | Contract amount ≤ ABC; obligation ≤ allotment | RA 12009; GAA |
| G7 | DV for goods/services requires an IAR with both inspection and acceptance completed | COA 2012-001 |
| G8 | Total DV amount ≤ obligation balance. Retention is withheld where required | GAM; RA 12009 IRR |
| G9 | No new cash advance for an officer with an unliquidated CA past its deadline | COA Circ. 97-002 |
| G10 | No accomplishment can be rated without MOV attached | CSC SPMS |
| G11 | Item ≥ ₱50,000 → PAR (PPE); below → ICS (semi-expendable) | COA Circ. 2022-004 |
| G12 | A user cannot approve or certify a document they prepared (segregation of duties) | NGICS |

## 4. Modules

| Module | Main functions |
|---|---|
| **M1 Planning & Performance** | PAP/UACS master, WFP, BED forms, OPCR/DPCR/IPCR cascade, GAD tagging, SPMS rating and calibration |
| **M2 Procurement Planning** | Market scoping repository, PPMP (indicative/final/supplemental), APP consolidation, APP-CSE export, price reference library |
| **M3 Requests & Procurement** | PR, TOR/specs builder, mode determination wizard (per RA 12009), BAC calendar, RFQ/ITB, abstracts, BAC resolutions, NOA/NTP, PhilGEPS posting tracker, supplier registry |
| **M4 Budget** | Allotment register (GAA/SARO/comprehensive release), earmarks, ORS/BURS, RAOD registers, BAR/FAR generation |
| **M5 Contracts & Property** | PO/Contract register, securities, delivery schedule, liquidated damages, IAR, PAR/ICS/RIS, property cards, physical count support |
| **M6 Accounting & Disbursement** | DV, Box A–E certifications, JEV, withholding tax and BIR 2307, LDDAP-ADA batch, check register, retention ledger |
| **M7 WSP Operations (non-procurement)** | Delegation and competitor/expert registry, travel orders and authorities, cash advances and liquidation, honoraria, allowances, WSI/WS Asia fees, competition calendar |
| **M8 Monitoring & Reporting** | Dashboards, accomplishment reports with MOV, PMR, PBB evidence pack, Budget–Accounting reconciliation, Transparency Seal exports |
| **M9 Audit, Records & Closure** | COA AOM/NS/ND tracker, internal audit findings, closure checklist, Records Disposition Schedule, archive |
| **M0 Platform** | Users and roles, Delegation of Authority table, checklist/version admin, document numbering, e-signature (PNPKI), notifications, audit log |

## 5. Roles and segregation of duties

| Role | Can prepare | Can certify/approve |
|---|---|---|
| End-user / Requesting Officer | PPMP, PR, TOR, Travel requests | — |
| WSP Secretariat (completeness) | Accomplishment reports | Completeness checks |
| Planning | WFP, OPCR consolidation | Plan alignment check |
| Procurement Unit / BAC Secretariat | APP, RFQ/ITB, abstracts, resolutions (draft), PMR | APP-line verification |
| BAC / TWG | Evaluation, post-qual reports | BAC Resolution |
| HoPE | — | APP, award, contract |
| Budget Officer | Earmark, ORS/BURS | Box B of ORS (allotment available) |
| Chief Accountant | JEV, CAF, reconciliation | CAF; DV Box C |
| Approving Official (per DOA) | — | PR, DV Box D, travel, CA |
| Inspection Committee | IAR (inspection part) | Inspection |
| Supply/Property Officer | IAR (acceptance), PAR/ICS/RIS | Acceptance |
| Cashier / Disbursing Officer | LDDAP-ADA, checks | Payment release |
| PMT / HR | SPMS calibration | Ratings (per SPMS) |
| Internal Audit / Records | Audit findings, records transmittal | Closure verification |
| COA Auditor (read-only) | — | — (read-only portal access to documents) |

The same user can never both prepare and certify one document (G12).

## 6. Architecture

* **Web application** (responsive, so it works on mobile for approvals and inspections) with a **workflow engine driven by configuration**:
  document types, checklists, and routing live in versioned YAML/DB records (`config/document-types.yaml`), not in code.
* **Suggested stack:** PostgreSQL; a mainstream backend framework (e.g., Django or Laravel, common among PH gov developers, which helps with maintenance); a BPMN-style
  state machine; object storage for attachments with SHA-256 hashing; PDF generation that matches the official GAM/COA form layouts.
* **Hosting:** DICT GovCloud or an accredited CSP (Cloud First Policy), with backups and DR plan per DICT standards.
* **E-signature:** DICT **PNPKI** certificates, signed PDFs, and timestamping. Wet-signature fallback until COA accepts each form electronically.
* **Integrations (phased):** PhilGEPS (posting references or API as available), PS-DBM Virtual Store (APP-CSE export),
  DBM reporting templates (BAR/FAR in the official format), eNGAS/agency accounting system (JEV export), bank LDDAP-ADA file format,
  TESDA HRIS (employee master), and TESDA's existing financial systems to avoid entering data twice.
* **Security & privacy:** role-based access, MFA for certifying roles, encryption at rest and in transit, a PIA for competitor/minor data,
  NPC registration of the system, audit log that cannot be altered.
* **Numbering:** official series per document type and FY (e.g., `PR-2027-01-0001`, `ORS-101-2027-01-0001`) configured to match Budget/Accounting conventions.

## 7. Dashboards (examples)

* Budget utilization per PAP: allotment vs. earmarked vs. obligated vs. disbursed.
* APP implementation: APP lines with no PR yet, procurements past their planned schedule, failed biddings.
* Documents waiting at each desk with SLA age (ARTA compliance).
* Unliquidated cash advances by officer and age.
* OPCR/IPCR accomplishment vs. target, with MOV completeness %.
* Open COA findings and settlement status.
* WSP competition readiness: delegation travel docs, CA status, and procurement for each event.

## 8. Implementation roadmap

Phases are detailed in [`04-development-phases.md`](04-development-phases.md). The approach is *track first, then digitize, then automate*:

| Phase | Duration (indicative) | Scope |
|---|---|---|
| **1 Tracking & Monitoring Foundation** | 3–4 months | Register and scan physical documents, QR routing slips, receive/release tracking, checklist completeness checks per document type, transaction folders, monthly IPCR accomplishment + MOV, semestral OPCR/IPCR compilation, aging/SLA dashboards |
| **2 Planning Linkage** | 2–3 months | PAP/UACS, WFP, OPCR→DPCR→IPCR workflow and SPMS rating, PPMP/APP/APP-CSE; tracked documents linked to plan lines |
| **3 Born-digital Procurement & Budget** | 3 months | PR → NOA → ORS/BURS + CAF → PO/Contract → IAR created in WISE; hard gates G1–G8, G11, G12 switched on |
| **4 Disbursement & WSP Operations** | 3 months | DV, LDDAP-ADA, withholding tax, retention; travel, cash advance/liquidation, honoraria, allowances, WSI fees |
| **5 E-signature, Integration, Closure** | 3 months | PNPKI, BAR/FAR/PMR outputs, PhilGEPS/PS-DBM/accounting integration, COA tracker and portal, records disposition |

Before Phase 1: a 1-month validation of this process model, the checklists, the Delegation of Authority, and the RA 12009 IRR thresholds, plus ISSP inclusion and a PIA.
Paper stays the official record until the COA Audit Team agrees to accept each form electronically.

## 9. Open items requiring agency decision

1. Current **peso thresholds** for each procurement mode and posting rule under the RA 12009 IRR (keep as config).
2. **TESDA Delegation of Authority** amounts and signatories for PR, contracts, DVs, travel and CAs.
3. Fund sources WSP uses (regular agency fund, trust funds, donations/sponsorships). These decide ORS vs. BURS and the reporting.
4. Legal basis and approval route for **competitor allowances and cash incentives**.
5. Whether CSE must be bought from PS-DBM under the current IRR and DBM circulars.
6. Which documents the COA Audit Team will accept in electronic form with PNPKI signatures.
7. SPMS rating periods and the PMT calibration workflow under TESDA's approved SPMS.
