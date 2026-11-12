# States

## Core columns (every surface)

| Column | What it covers |
| --- | --- |
| **Loading** | First load and reload are separate cases. First load: skeleton shaped like the content. Reload: keep the data on screen and show a quiet indicator. |
| **Empty** | Nothing to show yet. Say why, and offer the first action. An empty list that means "something failed" is an error, not an empty state. |
| **Error** | One cell per error class that reads differently to the person (validation, not found, forbidden, conflict, server, network, timeout). Say what happened, whether anything was saved or charged, and the way out. Never fall back to a fake value (a fee of 0%, a balance of 0). |
| **Success** | Confirm in the place the person is looking, short. Announce it in a live region. A paid, sent or published state never offers the same action again. |
| **Pending · slow** | The action is in flight. The trigger keeps its label and shows a spinner in place of its icon. After a threshold (start at 8 s), add a line that says it is still working and what the person can do meanwhile. A retry repeats the last intent; it never duplicates it. |

## Axis columns (add when the flow has the dimension)

| Column | What it covers |
| --- | --- |
| **Offline** | Lost connection: what still works, what queues, how the person learns it came back. |
| **Partial** | Some data loaded, some failed. Show what loaded and mark the gap. |
| **Disabled** | Every disabled control says why, before the person has to guess. |
| **Role · plan** | One column per role or plan that changes what renders or what is allowed. |
| **Reduced motion** | What stops when `prefers-reduced-motion: reduce` is set. |
| **Mobile** | What reflows, stacks or hides below the smallest breakpoint. |

## Message tones

| Tone | Use for | Placement |
| --- | --- | --- |
| **info** | Neutral facts that help the next step. | Inline, near the thing it describes. |
| **warning** | Something will happen or may go wrong if the person continues. | Inline or banner, before the action. |
| **error** | Something failed. Always paired with a way out. | Inline at the field or section that failed; banner for page-wide failures. |
| **success** | Something finished. Short, then gone. | Toast or inline confirmation where the action happened. |

Use a toast only for outcomes the person does not need to act on. A failure that needs action stays on the page until it is resolved. Never show a toast and an inline message for the same event.

Write copy that is plain and specific: what happened, then what to do. Prefer "Couldn't save the plan. Try again" over "Error saving plan!".
