# Boards

Boards make the matrix clickable. Build them from `docs/states/<flow>.md`, never from memory.

## In Claude Design

When a Claude Design canvas is available (the person names one, or one exists for the product):

1. Read the canvas's design system (tokens, components, fonts) and an existing board of the same product, and build in that language.
2. Make one **matrix board**: the table from the doc, with each open ID tagged and a card each for Opens, Decisions and Out of scope.
3. Make one **interactive board per surface**: the real screen, with a state switcher (a segmented control labelled with the column names) that swaps the screen into each state. Put the exact copy from the doc in each state. Include the slow threshold as its own step, and play each state's motion when it is selected.
4. Add a mobile frame beside the desktop frame when the matrix has a Mobile column.
5. Name boards `<FLOW>-<NN> · <surface> · states` so they sort together, and link each surface board from its row on the matrix board.

## Without a canvas

Write one self-contained HTML file next to the doc (`docs/states/<flow>.html`): the matrix on top, then each surface with its state switcher. Use the product's CSS tokens when you can read them; otherwise use a neutral palette with light and dark modes. No build step and no external scripts, so it opens from disk.

## Board checklist

- Every non-`—` cell is reachable from a switcher.
- Copy matches the doc word for word.
- Focus lands where the doc says after an error.
- Reduced motion can be toggled on the board to preview the static version.
