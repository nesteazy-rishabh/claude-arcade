# Claude Arcade

Retro terminal games for Claude Code. Play while you wait for builds, tests, and long-running tasks.

## Games

| Game | Description |
|------|-------------|
| **Tic-Tac-Toe** | Classic 3x3 grid, X vs O against Claude |
| **Minesweeper** | Reveal cells, flag mines, clear the board (Easy/Medium/Hard) |
| **Hangman** | Guess the hidden word one letter at a time |
| **Wordle** | 5-letter word, 6 guesses, with position feedback |
| **2048** | Slide and merge tiles to reach 2048 |
| **Chess** | Full chess with Unicode pieces against Claude |

## Install

Inside Claude Code, run:

```
/plugin marketplace add nesteazy-rishabh/claude-arcade
/plugin install claude-arcade
```

Then restart your Claude Code session for the skills to load.

Or test locally:

```bash
claude --plugin-dir ./claude-arcade
```

## Usage

Type `/games` to open the arcade menu:

```
[1]  Tic-Tac-Toe    ...  Classic X vs O
[2]  Minesweeper    ...  Don't go boom
[3]  Hangman        ...  Guess the word
[4]  Wordle         ...  5 letters, 6 tries
[5]  2048           ...  Slide & merge
[6]  Chess          ...  Battle of minds
```

Or jump straight to a game:

```
/games tictactoe
/games chess
/games wordle
```

## Controls

Every game supports:
- `menu` -- back to the arcade game selection
- `out` -- exit the arcade, return to Claude Code

## Tip

For the best experience, background your long-running task with **Ctrl+B** before starting a game. Your task keeps running while you play.

## License

MIT
