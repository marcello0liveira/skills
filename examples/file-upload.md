# File upload · state matrix

An example output of `ui-state-matrix` for a fictional "Attach documents" step. Try it as an interactive board: <https://marcello0liveira.github.io/skills/>.

Scope: the documents step of a form (`/apply/documents`). Date: 2026-11-12.
Global handling: offline banner from the app shell; failed writes outside this step show a toast with "Try again".

## Truths

| Surface | Source | Outcomes |
| --- | --- | --- |
| Document list | `GET /documents` | 200 with items · 200 empty · 5xx · network |
| Upload | `POST /uploads` (multipart) | 201 · 413 too large · 415 wrong type · 5xx · network · in flight > 8 s |
| Continue | `POST /apply/step` | 200 · 409 missing required document · 5xx |

## Matrix

| Surface | Loading | Empty | Error | Success | Pending · slow | Reduced motion | Mobile |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Document list | First load: 3 skeleton rows. Reload: rows stay. | Drop zone: "No documents yet. Drop a PDF or image, up to 10 MB." | Inline: "Couldn't load your documents." · **Try again** | — list renders | — | skeleton is static | rows stack name over size |
| Upload | — | — | 413: "This file is over 10 MB. Compress it or pick another." · 415: "Use a PDF, JPG or PNG." · 5xx or network: "Upload failed. Your other files are safe." · **Retry this file** (UP-E02) | Row check drawn once; live region: "receipt.pdf uploaded" | Progress bar; after 8 s: "Still uploading. You can keep filling the form." | bar jumps, no check animation | full-width drop zone, "Choose file" button |
| Continue | — | Disabled with "Add your ID to continue" under it | 409: "Add your ID to continue" with focus moved to the drop zone · 5xx: "Couldn't save this step. Try again." | goes to the next step | Button keeps "Continue", icon becomes spinner | spinner replaced by "Saving…" | sticky bottom button |

## Opens

| ID | Severity | Evidence | Fix |
| --- | --- | --- | --- |
| UP-E01 | high | `UploadRow.tsx:42` retries create a second upload | Retry reuses the upload id (idempotency key). |
| UP-E02 | medium | `useUpload.ts:18` network error shows a generic toast | Inline error on the row with "Retry this file". |
| UP-E03 | low | `Continue.tsx:9` disabled with no reason | Show the reason under the button. |

## Decisions

### D1 · Keep failed files in the list?
Keep them with the error and a retry, or remove them and show a toast.
Recommend: keep them, because the person sees exactly which file failed and retries in one click.

## Out of scope

- Virus scanning states (handled by the backend after submit).
