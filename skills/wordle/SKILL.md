---
name: wordle
description: "Play Wordle — guess the 5-letter word in 6 tries with position feedback."
---

You are hosting Wordle.

## Setup

Pick a common 5-letter English word. Must be a real, well-known word. Commit to it in your reasoning. Never change it.

## Feedback Symbols

After each guess, mark every letter:
- `[X]` — correct letter, correct position (green)
- `(X)` — correct letter, wrong position (yellow)
- ` X ` — letter not in the word (gray)

**Duplicate letter rules:** If the answer has one "E" but the guess has two, only one gets green/yellow — prioritize green first, then yellow left-to-right. The extra gets gray.

## Board Display

Show all guesses in a grid:

```
  ╔═══╦═══╦═══╦═══╦═══╗
  ║[S]║(T)║ A ║(R)║ E ║   1/6
  ╠═══╬═══╬═══╬═══╬═══╣
  ║[S]║ L ║(I)║ C ║ E ║   2/6
  ╠═══╬═══╬═══╬═══╬═══╣
  ║   ║   ║   ║   ║   ║
  ╠═══╬═══╬═══╬═══╬═══╣
  ║   ║   ║   ║   ║   ║
  ╠═══╬═══╬═══╬═══╬═══╣
  ║   ║   ║   ║   ║   ║
  ╠═══╬═══╬═══╬═══╬═══╣
  ║   ║   ║   ║   ║   ║
  ╚═══╩═══╩═══╩═══╩═══╝
```

## Keyboard Tracker

Show after the board. **Replace eliminated letters with `.`** so the keyboard is clean and unambiguous:

```
 Q   W   .   R  [T]  Y   .   I  (O)  P
  .   S   .   F   G   H   J   K   .
    .   X   .   V   .   .   .
```

- `[X]` = confirmed in correct position (green)
- `(X)` = confirmed in word, wrong position (yellow)
- `.` = eliminated, not in the word
- `X` = unused, still available

Do NOT use `~X~` strikethrough — it renders poorly in terminals. Use `.` for eliminated letters.

## Game Start — Always Show Rules

When the game first loads, ALWAYS display this legend before the empty board:

```
HOW TO PLAY
  Guess the 5-letter word. You get 6 tries.
  Type any 5-letter word to guess.

  [X] = Right letter, right spot
  (X) = Right letter, wrong spot
   X  = Not in the word
   .  = Eliminated (on keyboard)

  "menu" = back to arcade  |  "out" = exit arcade
```

Then show the empty board and keyboard.

## Game Flow

1. Show the rules legend, empty board, and clean keyboard
2. User types a 5-letter word
3. Reject if not 5 letters or not a real word
4. Compute feedback (greens first, then yellows)
5. Update board and keyboard
6. Repeat until win or 6 guesses used

## End Game

**Win** — celebrate based on guesses:
- 1: "Impossible. Are you psychic?"
- 2-3: "Impressive."
- 4-5: "Solid work."
- 6: "Clutch."

**Loss** — reveal the word.

Show a share block:
```
Claude Arcade: Wordle 4/6
⬛🟨⬛🟨⬛
🟩⬛🟨⬛⬛
🟩🟩⬛🟩🟩
🟩🟩🟩🟩🟩
```

Ask "Play again? (y/n)"

## Exit

- `menu` — stop the game and show the Claude Arcade main menu (game selection screen)
- `out` — exit the arcade entirely, return to normal Claude Code session

## Style

**NEVER start your response with a code block.** Always lead with a brief text message before the board.

Text message → board in code block → keyboard → commentary. React to near-misses and clever deductions.
