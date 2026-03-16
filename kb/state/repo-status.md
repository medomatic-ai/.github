# Repository Status

Last updated: 2026-03-16

## InjectaVox-web
- **Status:** Active development — ClinicFlow feature set in production, ICD-10 Wave 1 complete, Wave 2C in review
- **Open issues (medomatic-ai/.github):** #9 (Wave 2C: ClinicFlowPage integration — integration-review REQUEST_CHANGES)
- **Open PRs:** 0
- **Key files confirmed present:** `app/src/types/clinicflow.ts`, `app/src/hooks/useClinicFlowSession.ts`, `app/src/services/keystream/protocol.ts`, `app/src/components/clinicflow/Icd10CodeList.tsx`

## InjectaVox-native
- **Status:** Active development — ICD-10 Wave 2 in progress
- **Open issues (medomatic-ai/.github):** #4 (Wave 1A: types/store/compiler), #7 (Wave 2A: edge function), #8 (Wave 2B: sendNoteToPA payload)
- **Open PRs:** 0
- **Known type drift:** `src/services/compilation/types.ts` — `Icd10Code` missing `accepted` field (web has it; normalization guard added in Wave 2C plan)

## KeyStream (inside InjectaVox-native)
- **Status:** Active — no changes required for ICD-10 Wave 1 or Wave 2 (relays note_complete as raw JSON)
- **Open issues:** 0
- **Open PRs:** 0

## Active Epic Issues (medomatic-ai/.github)
| Issue | Title | Status |
|-------|-------|--------|
| #3 | ICD-10 Automated Diagnosis Code Selection — Epic | Parent, open |
| #4 | Wave 1A: Native types, store, compiler | Open — integration-review |
| #5 | Wave 1B: Web types, reducer, protocol | **CLOSED** |
| #6 | Wave 1C: Icd10CodeList UI component | **CLOSED** |
| #7 | Wave 2A: Edge Function ICD-10 extraction | Open, blocked on Wave 1 |
| #8 | Wave 2B: sendNoteToPA payload | Open, blocked on Wave 1 |
| #9 | Wave 2C: ClinicFlowPage + PatientCard integration | Open — clinical-review APPROVED, integration-review REQUEST_CHANGES |

---

*This file is updated by the Architect role and `/popebot sync-kb` command.*
