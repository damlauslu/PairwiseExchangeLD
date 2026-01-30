# Pairwise Exchange Teaching App — User Guide & FAQ

## Overview
This app demonstrates the Pairwise Exchange Method for facility layout design. You can:
- Generate random flow and (optionally) distance matrices
- Edit matrices manually
- Run step-by-step or to the end
- Visualize layout changes and cost
- Export results

---

## Quick Start (5 minutes)
1. **Set n** (number of departments) in the Problem panel.
2. **Generate Random Problem** in Random Generator.
3. **Check the layout** in the visualization grid.
4. Click **Next Step** to apply the best improving swap.
5. Click **Run to End** to finish automatically.

---

## Core Concepts

### Departments vs. Positions
- **Departments**: D1, D2, ... (the items to place)
- **Positions**: P0, P1, ... (grid cells)
- The layout is a mapping: **Department -> Position**

### Cost
Total cost is computed by:

Sum over all pairs **F[i][j] × D[layout[i]][layout[j]]**

---

## Panels & Controls

### Problem
- **n (3..12)**: number of departments.
- **Rows / Cols**: grid shape. Must satisfy **Rows × Cols ≥ n**.
- **Metric**: Manhattan or Euclidean (used when *not* using custom distance).
- **Force symmetric flows**: mirror flow values.
- **Use custom distance matrix**: enables editing distances and using random distance settings.
- **Force symmetric distances**: mirror distance values.

### Random Generator
Separated into **Flow** and **Distance** blocks.
- **Min / Max**: range for random values.
- **Sparsity**: fraction of zero entries.
- **Seed**: optional; repeatable randomness.

When **Use custom distance matrix** is ON:
- Distance matrix is randomized using Distance settings.
When OFF:
- Distance matrix is computed from grid geometry.

### Algorithm Controls
- **Run to End**: repeats best improving swap until no improvement or max iterations.
- **Next Step**: apply one best improving swap.
- **Previous Step**: undo last swap.
- **Reset to Initial**: undo all swaps.

### Logging / Export
- **Export CSV / TXT**: save iteration history.
- **Validate ΔC**: compare efficient vs. full recompute for the best swap.

### Layout Visualization
Grid display:
- Department labels inside occupied cells.
- Light P# labels indicate position index.
- Drag and drop between occupied cells swaps departments.

### Matrices
Two editable matrices with scrollbars:
- **Flow matrix**: F[i][j]
- **Distance matrix**:
  - **Custom ON**: editable P# × P#
  - **Custom OFF**: read-only view in current layout order

Apply buttons stay visible above the matrices.

---

## Common Workflows

### 1) Standard Demo
1. Set n = 8 or 9
2. Generate random problem
3. Click Next Step a few times
4. Run to End
5. Export TXT

### 2) Manual Editing
1. Enter values in Flow or Distance matrix
2. Click **Apply Flow Edits** / **Apply Distance Edits**
3. Run steps

### 3) Custom Distance Model
1. Enable **Use custom distance matrix**
2. Edit distances or randomize using Distance settings
3. Apply Distance Edits

---

## FAQ

**Q: Why can’t I reduce Rows or Cols?**  
A: The grid must always satisfy Rows × Cols ≥ n. Invalid values are rejected.

**Q: Why is the distance matrix read-only?**  
A: If “Use custom distance matrix” is OFF, distances are computed from grid geometry, so editing is disabled.

**Q: Why does the cost change when I drag departments?**  
A: Dragging swaps departments, changing their positions and therefore the total cost.

**Q: I changed n but the UI didn’t update.**  
A: After typing a new n, press Enter or click outside the input to apply.

**Q: Can I swap with empty cells?**  
A: Currently, drag-and-drop only swaps between occupied cells.

**Q: Why do I see P# inside cells?**  
A: P# is the grid position index for reference.

---

## Tips
- Use seeds when you want reproducible results.
- Keep distances symmetric unless you have a specific directional model.
- For larger n, use scrollbars and resize panes to see full matrices.

