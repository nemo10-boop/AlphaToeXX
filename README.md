# ♟️ AlphaToe — Unbeatable Tic-Tac-Toe AI

**Google Colab Project | Minimax + Alpha-Beta Pruning | No API Required**

---

## What is AlphaToe?

AlphaToe is an unbeatable Tic-Tac-Toe AI built entirely in Google Colab using pure Python — no APIs, no machine learning, no external infrastructure. Click a cell on the interactive board and the AI instantly responds with the mathematically optimal move, every single time.

---

## Novelty

Most Tic-Tac-Toe bots are either hardcoded rule tables or overkill neural networks. AlphaToe sits in the middle — intelligence through algorithm, not data.

The AI never trains, never learns, and is unbeatable from its very first move. It explores every possible future state of the game, scores each outcome, and picks the provably best move. No guessing. No heuristics. No data required.

---

## How the AI Works

### The Game Tree

Every board position branches into possible future states — moves, counter-moves, and eventual outcomes. The AI builds this tree mentally, scores every terminal state, and works backwards to pick the best move.

| Outcome | Score |
|---|---|
| AI wins | +1 |
| Draw | 0 |
| Human wins | -1 |

---

### Minimax

Two roles alternate through the tree:

- **Maximizer (AI)** — always picks the highest scoring move
- **Minimizer (Human)** — always picks the lowest scoring move

The AI calls Minimax for every available move, picks the one with the highest returned score, and plays it. Since every possible future is explored without exception, the result is provably optimal. On an empty board, Minimax evaluates **255,168 game states**.

---

### Alpha-Beta Pruning

Alpha-Beta produces the **exact same move** as Minimax — it just skips branches that can never affect the final decision, making it up to 97% faster.

It tracks two values while searching:

- **Alpha (α)** — best score the AI has guaranteed so far
- **Beta (β)** — best score the Human has guaranteed so far

When **β ≤ α**, the current branch is dead — one side already has a better option elsewhere. The algorithm stops exploring it immediately. This is a **prune ✂️**.

---

### Performance: Minimax vs Alpha-Beta

| Moves Played | Minimax Nodes | Alpha-Beta Nodes | Pruned |
|---|---|---|---|
| 0 — empty board | 255,168 | ~6,000 | ~97% |
| 1 | 59,000 | ~2,000 | ~96% |
| 2 | 13,000 | ~800 | ~93% |
| 3 | 2,800 | ~300 | ~89% |
| 4 | 500 | ~100 | ~80% |

Cell 9 of the notebook generates a **3D matplotlib surface plot** of this comparison.

---

## Notebook Structure

| Cell | Contents |
|---|---|
| Cell 1 | Imports |
| Cell 2 | Game constants |
| Cell 3 | `Board` class — grid, move, undo, winner detection |
| Cell 4 | `minimax()` — exhaustive recursive search |
| Cell 5 | `alphabeta()` — pruned search |
| Cell 6 | `get_best_move()` — picks best move for AI |
| Cell 7 | `ipywidgets` visual board |
| Cell 8 | Game controller + interactive play loop |
| Cell 9 | 3D performance analysis plot |

Run cells top to bottom. The interactive board appears at Cell 8.

---

## How to Play

- You are **✕** — you go first
- The AI is **◯**
- Click any empty cell to make your move
- Click **🔄 Reset** to start over
- Scoreboard tracks results across sessions

---

## Dependencies

Everything is pre-installed in Colab — nothing to pip install.

| Package | Use |
|---|---|
| `ipywidgets` | Interactive game board |
| `matplotlib` | 3D analysis plot |
| `numpy` | Analysis chart data |
| `math` | Infinity values for Minimax |
| `random` | Tiebreak between equal moves |

---

## Key Concepts Demonstrated

| Concept | Where |
|---|---|
| Recursive tree search | `minimax()` — Cell 4 |
| Backtracking | `make_move()` / `undo_move()` — Cell 3 |
| Alpha-Beta Pruning | `alphabeta()` — Cell 5 |
| Game state management | `Board` class — Cell 3 |
| Algorithm analysis | 3D surface plot — Cell 9 |

---

## Note

This is **Classical AI**, not Machine Learning. There is no training, no weights, no data. The AI is unbeatable because the algorithm is exhaustive — not because it studied thousands of games. The best a human can achieve is a draw, provided they play perfectly.

---


