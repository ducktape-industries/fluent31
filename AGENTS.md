# AGENTS.md

## Code says it, not comments

Code churns; a comment doesn't age with it, and an incident record in a comment traps the next
reader. So the code alone must say what happens (orthory, dm-15-17 305/309, #duckpond 271). This
holds for new and changed lines; don't sweep untouched code for it.

- A name says exactly what it holds or does, however long it gets: `blocks_behind_the_writer`,
  not `lag`.

### Checked by the lint

tools' `agents-lint.py` reads these on the lines a change adds or changes, and quotes the rule a
line breaks.

- `comments`: No comments, except `// SAFETY:`, a short doc on a type and on each enum variant
  (what it is, one line), and a brief header of one to three lines at the top of a file saying
  what the file is for. No incident history, no job numbers, no "why we once did X" in code.
- `conditions`: No `&&` or `||` chained in an `if` or `else if` condition (let chains included).
  Name each piece first, then branch on the names (`let is_ducktape_network = …;`, then
  `if is_ducktape_network`); `&&` inside a closure or a `let` binding is fine.
