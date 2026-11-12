---
name: ui-state-matrix
description: Maps every UI state of a screen or flow into a state matrix (surfaces × states) and interactive design boards. Use when designing, building or reviewing a screen or flow, or when the user asks for all states, edge cases, a state matrix, or the loading / empty / error / slow / success states of something.
---

# UI state matrix

Map every state a person can meet in a screen or flow, then show each one so it can be clicked through. The rule behind everything: **one state per truth**. Every distinct thing the system can know (each API response, each pending write, each permission) gets its own state, and each state says what the person sees, the exact words, and the **way out**.

Write in the language of the product. Use the product's design system when one exists.

## Steps

1. **Scope the surfaces.** List the surfaces in scope: screens, sections, dialogs, and the actions inside them (submit, retry, skip). One row per surface. Done when every surface the flow can show is a row.

2. **Collect the truths.** For each surface, read the code, the API contract and the async work (queries, mutations, uploads, polling, websockets). List every outcome each one can produce: success, each error class (validation, 4xx by meaning, 5xx, network, timeout), pending, empty, partial, stale, and every role or plan that changes what renders. Each outcome is a truth. Done when every request and every branch in the render path maps to at least one truth.

3. **Fill the matrix.** Build the table: surfaces as rows, states as columns. Use the core columns from [STATES.md](STATES.md) on every surface, and add an axis column only when the flow has that dimension. Each cell holds:
   - what the person sees (component and placement);
   - the exact copy, with its tone (info, warning, error, success);
   - the way out (retry, edit, go back, contact) and where focus lands;
   - the motion, if any, per [MOTION.md](MOTION.md).

   A cell that does not apply says `—` and why in a few words. Done when no cell is blank and every truth from step 2 lives in a cell.

4. **Mark the opens.** Anything the current product gets wrong or leaves unhandled becomes an **open**: an ID (`<FLOW>-E01`…), a severity (high, medium, low), the evidence (file and line, or a screenshot) and the proposed fix. Mark the cell with the ID.

5. **Write the decisions.** Product questions the matrix cannot answer alone (copy that carries legal weight, whether a retry may charge twice, what a role may see) become decisions: the question, the options, and `Recommend:` with one line of why.

6. **Write the doc.** Save `docs/states/<flow>.md` using [TEMPLATE.md](TEMPLATE.md). It is the source of truth; the boards render from it.

7. **Render the boards.** Follow [BOARDS.md](BOARDS.md): in Claude Design when a design canvas is available, otherwise a single self-contained HTML page. Done when every surface has an interactive board whose state switcher reaches every non-`—` cell of its row.

## Done

The work is complete when every truth has a cell, every cell has a way out or a reason it needs none, every open has evidence, and every state is reachable on a board.
