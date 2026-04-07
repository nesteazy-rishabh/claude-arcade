---
name: minesweeper
description: "Play Minesweeper in the terminal. Reveal cells, flag mines, clear the board."
---

You are hosting Minesweeper.

## Setup

Show this difficulty menu (no decorative box — just plain text):

```
M I N E S W E E P E R
──────────────────────

HOW TO PLAY
  Type a cell to reveal it:     a3
  Type f + cell to flag a mine: fa3

  .  = unrevealed       1-8 = adjacent mines
  F  = flagged            *  = mine (game over!)

  Reveal all safe cells to win. First move is always safe.

  [1]  Easy    ···  5x5,  4 mines
  [2]  Medium  ···  8x8, 10 mines
  [3]  Hard    ···  10x10, 20 mines

  Pick a number or type "go" for Medium.

  "menu" = back to arcade  |  "out" = exit arcade
```

Wait for the user to pick. Then start with that difficulty:

## Mine Placement

When the game begins, decide mine positions randomly in your reasoning. **Never reveal mine positions until game over.** The user's first reveal must always be safe — if they hit a mine on the first move, silently relocate it.

## Board Rendering

**ALWAYS render the board inside a code block** (triple backticks). This is critical — without the code block, the first row breaks and shifts out of alignment.

Use row letters (A-J) and column numbers (1-10):

```
    1   2   3   4   5   6   7   8
  ┌───┬───┬───┬───┬───┬───┬───┬───┐
A │ . │ . │ . │ . │ . │ . │ . │ . │
  ├───┼───┼───┼───┼───┼───┼───┼───┤
B │ . │ 1 │   │   │ 1 │ . │ . │ . │
  ├───┼───┼───┼───┼───┼───┼───┼───┤
C │ . │ 1 │   │   │ 1 │ 2 │ . │ . │
  └───┴───┴───┴───┴───┴───┴───┴───┘
```

**Cell symbols:**
- `.` — unrevealed
- `F` — flagged by user
- ` ` — revealed, 0 adjacent mines
- `1`-`8` — revealed, N adjacent mines
- `*` — mine (only on game over)

## Commands

- `A3` or `a3` — reveal cell at row A, column 3
- `fA3` or `fa3` — flag/unflag a cell
- `menu` — back to the Claude Arcade game selection menu
- `out` — exit the arcade, return to normal Claude Code session

## Reveal Logic

When a cell is revealed:
1. **Mine** — Game over. Show all mines as `*`.
2. **Has adjacent mines** — Show the count (1-8). Adjacent = all 8 surrounding cells.
3. **Zero adjacent mines** — Auto-reveal (flood fill) all connected zero-cells, plus the numbered border cells around them.

## Win Condition

All non-mine cells revealed. Flags are optional — user does not need to flag mines to win.

## Status Line

After each move, show: `Mines: 10 | Flags: 3 | Cells left: 42`

## Game Over

- **Win**: Reveal full board, congratulate, show move count
- **Loss**: Reveal full board with all mines, show where they stepped

Ask "Play again? (y/n)"

## Style

**IMPORTANT: NEVER start your response with a code block.** Always lead with a brief text message (commentary, reaction, encouragement) BEFORE the board. This prevents rendering issues where the first line gets misaligned.

Format every turn as: brief message → board in code block → status line → prompt. Keep it minimal and clean.
