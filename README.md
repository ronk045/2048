# 2048


A C implementation of the popular puzzle game **2048**. This version supports **variable board sizes**, directional movement, tile merging mechanics, score tracking, and game state management.

## Overview

2048 is a single-player puzzle game where numbered tiles slide across a grid and merge when equal values collide. The goal is to combine tiles until reaching **2048** while maximizing score.

Unlike the original fixed 4×4 game, this implementation supports **custom board dimensions** selected by the user at runtime.

Controls:

- `w` → move up
- `a` → move left
- `s` → move down
- `d` → move right
- `n` → start a new game
- `q` → quit

---

## Features

- Supports customizable board sizes
- Implements all 2048 movement mechanics
- Handles tile sliding and merging
- Prevents tiles from merging twice in one move
- Generates random tiles after valid moves
- Tracks score based on merges
- Detects valid and invalid moves
- Supports game reset and quitting

---

## Implemented Functions

### `make_game()`

Initializes a new game board.

Responsibilities:

- Sets board dimensions
- Initializes score
- Allocates and initializes cells
- Sets empty cells to `-1`

---

### `remake_game()`

Resets an existing game using new dimensions.

Responsibilities:

- Reuses existing game structure
- Reinitializes game data
- Clears board state
- Resets score

---

### `get_cell()`

Returns a pointer to a specific board cell.

Responsibilities:

- Converts row/column coordinates
- Performs bounds checking
- Returns `NULL` for invalid indices

---

### `move_w()`

Moves all tiles upward.

Responsibilities:

- Slides tiles upward
- Merges matching values
- Updates score
- Prevents duplicate merges
- Returns whether board state changed

---

### `move_s()`

Moves all tiles downward.

Uses movement logic similar to `move_w()` with directional modifications.

---

### `move_a()`

Moves all tiles left.

Handles sliding and merging across rows.

---

### `move_d()`

Moves all tiles right.

Handles directional movement and merge rules.

---

### `legal_move_check()`

Checks whether the game can continue.

Returns:

- `1` → legal moves exist
- `0` → game over

Checks:

- Empty spaces remaining
- Adjacent matching tiles

---

## Example Merge Behavior

Sliding left:

```text
(2, 2, 4, 8)
↓
(4, 4, 8, *)
```

Sliding:

```text
(2, 2, 2, *)
```

Left:

```text
(4, 2, *, *)
```

Right:

```text
(*, *, 2, 4)
```

A tile may merge only once during a move.

---

## Concepts Used

- C programming
- Dynamic memory allocation
- Pointer arithmetic
- 2-D board representation using 1-D arrays
- Game state management
- Grid traversal algorithms
- Boundary checking
- Simulation logic
- Debugging and testing

---

## Project Structure

```text
game.c          -> game logic implementation
game.h          -> structures and declarations
main.c          -> game loop
getch_fun.c     -> keyboard input handling
test_src/       -> test files
makefile        -> build configuration
```

---

## Build Instructions

Compile:

```bash
make
```

---

## Running the Game

Launch:

```bash
./mp8
```

Enter board dimensions:

```text
4 4
```

Example gameplay:

```text
Score: 12

+----+----+----+----+
|  2 |    |  4 |    |
|    |  2 |    |  8 |
|    |    |  2 |    |
|  4 |    |    |  2 |
+----+----+----+----+

Move: a
```

---

## Testing

Run provided tests:

```bash
./mp8_test
```

Custom tests may be added by editing:

```text
/test_src/test.c
```

---

## Skills Demonstrated

- Data structure manipulation
- Dynamic memory management
- Grid-based algorithm design
- Pointer usage in C
- Game logic implementation
- State tracking and validation
- Problem decomposition
- Testing and debugging workflows
