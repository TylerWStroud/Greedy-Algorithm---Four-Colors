# US Map Graph Coloring – Greedy Algorithm

A Python implementation of the **four-color theorem** applied to the 48 contiguous US states using a greedy graph coloring algorithm.

---

## Overview

The four-color theorem states that no more than four colors are needed to color any planar map such that no two adjacent regions share the same color. This program models the US state map as an undirected graph and greedily assigns one of four colors to each state.

---

## How It Works

1. Each state is a **node** in the graph.
2. Two states sharing a border are connected by an **edge**.
3. The greedy algorithm iterates through each state and assigns the **lowest-numbered color** (1–4) not already used by any of its neighbors.
4. A verifier confirms no two adjacent states share the same color.

### Color Map

| Color # | Color Name |
|---------|------------|
| 1       | Red        |
| 2       | Green      |
| 3       | Blue       |
| 4       | Yellow     |

---

## Usage

Run directly in Python 3 or upload to [Google Colab](https://colab.research.google.com/).

```bash
python graph_coloring.py
```

### Example Output

```
==================================================
 Graph Coloring – State Color Lookup Table
==================================================
State    Color #    Color Name
------------------------------
AL       3          Blue
AR       3          Blue
AZ       3          Blue
CA       1          Red
...

Verification: Valid – no two adjacent states share a color.
Total colors used: 4 / 4
```

---

## Functions

### `greedy_graph_coloring(adjacency, num_colors=4)`
Assigns colors to all nodes using a greedy strategy.

| Parameter    | Type   | Description                          |
|--------------|--------|--------------------------------------|
| `adjacency`  | `dict` | `{state: [neighbor, ...]}` adjacency list |
| `num_colors` | `int`  | Maximum colors allowed (default: 4)  |

**Returns:** `dict` mapping each state to its color number.

---

### `verify_coloring(adjacency, color_map)`
Checks that no two adjacent states share a color.

**Returns:** `(bool, str)` — validity flag and a descriptive message.

---

## Complexity

| | |
|---|---|
| **Time** | O(V + E) — each node and edge is visited once |
| **Space** | O(V) — stores one color per node |

where V = number of states (48) and E = number of shared borders (~107).

---

## Limitations

- The greedy approach does **not** guarantee a globally optimal (minimum color) solution — it may use more colors than necessary on non-planar graphs.
- For the US contiguous map (a planar graph), 4 colors are always sufficient per the four-color theorem.
- Alaska and Hawaii are excluded as they share no land borders with other states.

