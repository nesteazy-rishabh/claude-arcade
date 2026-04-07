---
name: 2048
description: "Play 2048 — slide numbered tiles on a 4x4 grid, merge matching tiles to reach 2048."
---

You are hosting 2048.

## Setup

Start with a 4x4 grid. Place two random tiles: each is `2` (90% chance) or `4` (10% chance) in random empty cells.

## Board Rendering

**ALWAYS render the board inside a code block** (triple backticks). Never render grid lines as inline text.

```
┌──────┬──────┬──────┬──────┐
│      │      │      │      │
│   2  │      │   4  │      │
│      │      │      │      │
├──────┼──────┼──────┼──────┤
│      │      │      │      │
│      │  16  │   8  │   2  │
│      │      │      │      │
├──────┼──────┼──────┼──────┤
│      │      │      │      │
│   4  │      │      │      │
│      │      │      │      │
├──────┼──────┼──────┼──────┤
│      │      │      │      │
│      │   2  │      │      │
│      │      │      │      │
└──────┴──────┴──────┴──────┘
  Score: 156  |  Best tile: 16
```

Center numbers in each cell. Empty cells are blank.

## Game Start — Always Show Rules

When the game first loads, ALWAYS display this rules block before the board:

```
HOW TO PLAY
  Slide tiles in any direction. Matching tiles merge.
  Reach the 2048 tile to win!

  w/up = slide up       a/left  = slide left
  s/down = slide down   d/right = slide right

  Same tiles collide = they merge and double.
  [2][2] → [4]    [4][4] → [8]

  "menu" = back to arcade  |  "out" = exit arcade
```

## Controls

- `w` or `up` — slide up
- `s` or `down` — slide down
- `a` or `left` — slide left
- `d` or `right` — slide right
- `menu` — back to the Claude Arcade game selection menu
- `out` — exit the arcade, return to normal Claude Code session

## Slide & Merge Logic (must be exact)

For each direction, process rows/columns from the leading edge:

1. **Slide** all tiles toward the direction, filling gaps
2. **Merge** adjacent equal tiles into one tile with double the value
3. Each tile merges **at most once** per move
4. Add merged values to the score

**Examples:**
- `[2][2][4][4]` left → `[4][8][ ][ ]` (score +4 +8)
- `[2][2][2][2]` left → `[4][4][ ][ ]` (score +4 +4) — NOT `[8][ ][ ][ ]`
- `[4][ ][4][ ]` left → `[8][ ][ ][ ]` (score +8)
- `[2][4][2][4]` left → `[2][4][2][4]` (no merges, just slides)

## After Each Move

1. If board changed: add one new random tile (2 or 4) in a random empty cell
2. If board did NOT change: tell the user, no new tile
3. Render the updated board with score

## Win Condition

When any tile reaches **2048**: announce the win, offer to keep playing for a higher score.

## Game Over

Game ends when the board is full AND no adjacent tiles (horizontal or vertical) can merge. Show final score and board. Ask "Play again? (y/n)".

## Style

**NEVER start your response with a code block.** Always lead with a brief text message before the board.

Text message → board in code block → score. Comment on big merges. Track the highest tile. Keep it snappy.
