# TicTacToe

A single-page Tic Tac Toe game for the browser. Play against the computer or a friend on the same device. Everything (HTML, CSS and JavaScript) lives in [`index.html`](index.html), with no build step and no dependencies.

## How to play

1. Open `index.html` in any modern browser (double-click the file, or serve the folder with e.g. `python3 -m http.server` and open `http://localhost:8000/`).
2. Pick a **Mode**:
   - **vs Computer**: choose a **Difficulty** and whether **You play** X (moves first) or O (moves second).
   - **2 Players**: take turns on the same device. The starting player alternates each round.
3. Click a square to place your mark. The first player to get three in a row (across, down or diagonally) wins, and the winning line is highlighted. If all nine squares fill up with no line, it's a draw.
4. Press **New game** (or **N**) to play again. **Reset scores** clears the scoreboard.

You can also play with the keyboard: Tab to the board, move with the arrow keys, and press Enter or Space to place a mark.

## Computer difficulty

| Level | Behaviour |
| --- | --- |
| Easy | Picks a random empty square. |
| Medium | Plays the best move most of the time, and a random move about 40% of the time. |
| Unbeatable | Uses minimax search to play perfectly. It never loses; the best you can do is a draw. |

## Scores and settings

Scores (X wins, O wins, draws), mode, difficulty and your side are saved in the browser's `localStorage` under the key `tictactoe.v1`, so they survive a page reload. Changing the mode or your side resets the scores.

## Testing

Verified with automated browser tests (Playwright driving real clicks and key presses):

- an exhaustive search over every possible human move sequence (977 finished games, with the computer playing X and O) found no game the Unbeatable computer loses;
- you cannot move while the computer is thinking, and the board locks once a game ends;
- wins, draws, winning-line highlight, scores, starter alternation in 2-player mode, keyboard navigation and saved settings after a reload all work;
- no JavaScript errors, and the layout fits a 360 px wide phone screen.
