# Repository Status

Last updated: 2026-03-16

## InjectaVox-web
- **Status:** Active development — ClinicFlow feature set in production, ICD-10 Wave 1 in progress
- **Open issues (medomatic-ai/.github):** #5 (Wave 1B: types/reducer/protocol), #6 (Wave 1C: Icd10CodeList UI), #9 (Wave 2C: ClinicFlowPage integration)
- **Open PRs:** 0
- **Key files confirmed present:** `app/src/types/clinicflow.ts`, `app/src/hooks/useClinicFlowSession.ts`, `app/src/services/keystream/protocol.ts`

## InjectaVox-native
- **Status:** Active development — ICD-10 Wave 1 in progress
- **Open issues (medomatic-ai/.github):** #4 (Wave 1A: types/store/compiler), #7 (Wave 2A: edge function), #8 (Wave 2B: sendNoteToPA payload)
- **Open PRs:** 0

## KeyStream (inside InjectaVox-native)
- **Status:** Active — no changes required for ICD-10 Wave 1 or Wave 2 (relays note_complete as raw JSON)
- **Open issues:** 0
- **Open PRs:** 0

## Active Epic Issues (medomatic-ai/.github)
| Issue | Title | Status |
|-------|-------|--------|
| #3 | ICD-10 Automated Diagnosis Code Selection — Epic | Parent, open |
| #4 | Wave 1A: Native types, store, compiler | Open — integration-review |
| #5 | Wave 1B: Web types, reducer, protocol | Open — integration-review, clinical-review |
| #6 | Wave 1C: Icd10CodeList UI component | Open |
| #7 | Wave 2A: Edge Function ICD-10 extraction | Open, blocked on Wave 1 |
| #8 | Wave 2B: sendNoteToPA payload | Open, blocked on Wave 1 |
| #9 | Wave 2C: ClinicFlowPage + PatientCard integration | Open, blocked on Wave 1 |

---

*This file is updated by the Architect role and `/popebot sync-kb` command.*
