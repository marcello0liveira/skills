# Motion

Motion explains a change of state. It runs **once and stops**.

1. **Use the design system's motion.** Read its duration, easing and keyframe tokens and use only those. When the product has none, use this small declared set and say so in the doc:
   - enter: 160 ms, `cubic-bezier(.2,.8,.2,1)`, fade plus 4 px rise;
   - confirm: 240 ms check drawn once, or a single scale pop (1 → 1.06 → 1);
   - exit: 120 ms fade.
2. **Loop only while something is really waiting.** A spinner may turn while a request is in flight and stops when it settles. Decorative pulses, shimmer on loaded content, and breathing badges on a static screen are out.
3. **Respect reduced motion.** Under `prefers-reduced-motion: reduce`, replace every movement with an instant change of state. The state must read the same without the motion.
4. **Keep the trigger stable.** A button in progress keeps its text and its width; only its icon becomes a spinner.

Record the motion for each cell in the matrix: what moves, its token, and what replaces it under reduced motion.
