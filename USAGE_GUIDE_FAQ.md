# Pairwise Exchange Teaching App - User Guide and FAQ

## Overview
This app demonstrates the Pairwise Exchange Method for facility layout design.
You can:
- Generate random flow and (optionally) distance matrices
- Enter your own values and apply edits
- Run the algorithm step-by-step or to completion
- Visualize layout changes and total cost
- Export iteration history

---

## Quick Start (5 minutes)
1. Set **n** (number of departments) in the Problem panel.
2. (Optional) Adjust **Rows** and **Cols** so Rows*Cols >= n.
3. Click **Generate Random Problem**.
4. Click **Next Step** a few times.
5. Click **Run to End** to finish.

---

## Core Concepts

### Departments vs. Positions
- Departments are D1, D2, ... (items to place).
- Positions are P0, P1, ... (grid cells).
- The layout is a mapping: **Department -> Position**.

### Cost
Total cost is:
Sum over all pairs: **F[i][j] * D[layout[i]][layout[j]]**

---

## Panels and Functions

### Problem
Purpose: Define size and geometry.
Controls:
- **n (3..12)**: number of departments.
- **Rows / Cols**: grid shape; must satisfy Rows*Cols >= n.
- **Metric**: Manhattan or Euclidean (used only when Custom Distance is OFF).
- **Force symmetric flows**: mirror F[i][j] with F[j][i].
- **Use custom distance matrix**: enables distance editing and random distance generation.
- **Force symmetric distances**: mirror D[p][q] with D[q][p].

### Random Generator
Purpose: Create random inputs for Flow and Distance.
Blocks:
- **Flow**: Min, Max, Sparsity, Seed.
- **Distance**: Min, Max, Sparsity, Seed.
Behavior:
- If **Custom Distance** is ON, distance matrix is randomized using Distance settings.
- If **Custom Distance** is OFF, distance matrix is computed from grid geometry.

### Algorithm Controls
Purpose: Run or step through the algorithm.
Buttons:
- **Run to End**: apply best improving swaps until no improvement or max iterations.
- **Next Step**: apply one best improving swap.
- **Previous Step**: undo the last swap.
- **Reset to Initial**: undo all swaps.
Other:
- **Show swaps / Top-K**: controls how many candidate swaps are listed.
- **Max iterations**: maximum steps when running to end.

### Logging / Export
Purpose: Save results and validate calculations.
Buttons:
- **Export CSV**: export iteration history as CSV.
- **Export TXT**: export a readable report.
- **Validate dC**: compare efficient delta vs full recompute for the best swap.

### Layout Visualization
Purpose: Show layout and allow drag-and-drop swapping.
Features:
- Department labels inside occupied cells.
- Light P# labels to show position index.
- Drag one occupied cell onto another to swap departments.

### Matrices
Purpose: Show and edit Flow and Distance.
Behavior:
- **Apply Flow Edits**: commit flow changes.
- **Apply Distance Edits**: commit distance changes (only when Custom Distance is ON).
- Distance matrix:
  - Custom ON: editable P# x P#.
  - Custom OFF: read-only in current layout order.
Tips:
- Use scrollbars and resize panes for large n.

### Quick Guide Button
Purpose: Short, in-app help.
Location: bottom-left of the left panel.

### Info Buttons (i)
Purpose: Hover help for each panel.
Behavior: Shows a short popup when hovered.

---

## Common Workflows

### 1) Random Demo
1. Set n.
2. Generate random problem.
3. Run steps or run to end.
4. Export results.

### 2) Manual Data Entry
1. Enter Flow and/or Distance values.
2. Click Apply buttons.
3. Run steps.

### 3) Custom Distance Model
1. Turn ON Custom Distance.
2. Edit distances or randomize distance.
3. Apply Distance Edits.

---

## FAQ

**Q: Why can not I reduce Rows or Cols?**  
A: The grid must satisfy Rows*Cols >= n. Invalid values are rejected.

**Q: Why is the distance matrix read-only?**  
A: If Custom Distance is OFF, distances are computed from grid geometry and editing is disabled.

**Q: I changed the metric but the distance matrix did not update.**  
A: The distance matrix updates only when Custom Distance is OFF. If it is ON, you are editing custom values.

**Q: I changed n but the UI did not update.**  
A: After typing a new n, press Enter or click outside the input.

**Q: Why does cost change when I drag departments?**  
A: Dragging swaps departments and changes their positions in the layout.

**Q: Can I drop onto empty cells?**  
A: Drag-and-drop currently swaps only between occupied cells.

**Q: Why do I see P# inside cells?**  
A: P# is the position index for reference.

**Q: How do Apply buttons work?**  
A: They commit changes in the matrix editors to the internal model.

**Q: What does Validate dC do?**  
A: It compares the efficient delta computation with a full cost recompute.

---

## Tips
- Use seeds for reproducible random problems.
- Keep distances symmetric unless you need a directional model.
- Resize panes and use scrollbars for large n.
