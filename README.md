# Pairwise Exchange Teaching App

A Tkinter teaching app for the Pairwise Exchange Method in facility layout design.
It supports random and manual data, step-by-step swaps, full runs, visualization,
and exports.

---

## Features
- Random Flow and (optional) Distance matrix generation
- Manual matrix editing with Apply buttons
- Drag-and-drop swap on the layout grid
- Step, previous, reset, and run-to-end controls
- Live cost calculation and swap candidate list
- Export to CSV and TXT
- In-app Quick Guide and hover info buttons

---

## Requirements
- Python 3.11+ (standard library only)

---

## Run
```bash
python pairwise_exchange_gui.py
```

---

## UI Overview

### Left Panel (Setup and Controls)
- **Problem**: n, Rows/Cols, metric, symmetry, custom distance toggle
- **Random Generator**: Flow and Distance randomization settings
- **Algorithm Controls**: Run, Next, Previous, Reset, options
- **Logging / Export**: CSV/TXT export, dC validation
- **Quick Guide**: short usage help

### Right Panel (Visualization and Matrices)
- **Layout Visualization**: grid with departments and positions
- **Swap Candidates**: best swaps and delta costs
- **Matrices**: Flow and Distance editors with scrollbars
  - Distance is editable only when Custom Distance is ON
  - Apply buttons sit above the matrices

---

## How the Algorithm Works
The app evaluates all pairwise swaps and applies the swap with the best (most
negative) delta in total cost. It stops when no improvement is possible or
when max iterations is reached.

---

## Data Model
- **F**: flow matrix (department-by-department)
- **D**: distance matrix (position-by-position)
- **Layout**: maps each department to a position index
- **Cost**: sum of F[i][j] * D[layout[i]][layout[j]]

---

## Files
- `pairwise_exchange_gui.py`: main application
- `USAGE_GUIDE_FAQ.md`: full user guide and FAQ

---

## Notes
- Rows*Cols must always be >= n.
- When Custom Distance is OFF, the distance matrix is computed from the grid.
- Drag-and-drop swaps only between occupied cells.

---

## License
See `LICENSE`.
