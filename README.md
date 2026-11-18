# NeggSweeper Solver

**Open it: https://fang89.github.io/neggsweeper-solver/**

A helper for Neopets' NeggSweeper that shows which neggs are safe, right on the game page.
It never clicks anything for you, and it runs entirely in your browser: nothing is sent anywhere.

## How to use

1. Open the page above and drag the orange **NeggSweeper Helper** button to your bookmarks bar
   (no bar? `Ctrl+Shift+B`, or `⌘+Shift+B` on a Mac).
2. Open NeggSweeper on neopets.com.
3. Click the bookmark once. It keeps working after every click, every win and every new game
   until you close the tab.

| Colour | Meaning |
| --- | --- |
| 🟩 Green | Safe: click any of them |
| 🟥 Red | A bad negg: leave it |
| 🟧 Orange (pulsing) | Nothing is certain: the negg least likely to be bad |

The card in the corner shows how many safe neggs there are and can print the odds on every
covered negg. Its **×** puts the game back to normal.

Works in Chrome, Edge and Firefox on Windows and Mac. Flagging a negg (Ctrl-click, or
Shift-click on a Mac) doesn't confuse it: a flagged negg still counts as covered.

## How it works

Every click reloads the game page, which would wipe a normal bookmark out. So the helper shows
the game inside a full-page frame from the same site and stays in the page around it. Every time
the frame loads it reads the board again and solves it.

The solver is exact, not a rule of thumb:

- Covered neggs next to a number are split into groups that share no number. Every way of
  hiding bad neggs in each group that fits all its numbers is counted.
- The game's **Remaining** counter fixes how many bad neggs are left in total
  (covered neggs − remaining). Each group's layouts are weighted by how many ways the untouched
  neggs can hold the rest.
- A negg that is bad in **no** layout is green, one that is bad in **every** layout is red.
  Those two calls come from the layouts themselves, never from rounded odds, so a green negg is
  never a guess.
- When nothing is certain, the orange negg has the lowest chance of being bad. Ties go to the
  negg with the fewest covered neighbours, since a corner opens the most board when it is safe.

Tested on real saved game boards and 1,000 simulated Hard games (14 × 14, 40 bad neggs), with no
wrong green or red call. A typical board solves in a few milliseconds.

---
Unofficial fan tool. Not made by or connected to Neopets.
