# AGENTS.md — mailroom-live

Read this file before doing anything in this project. It tells you what the project is,
who you are working with, and the rules for writing code here.

## 1. What this project is

`mailroom-live` is a learning project. The learner is studying programming fundamentals
by building it, one small step at a time, with an AI coding agent (you).

- The learner is the one learning. You are the reading partner and the builder.
- The goal is understanding, not speed. A smaller program the learner fully understands
  beats a bigger one they cannot explain.
- What the mailroom app does will grow lesson by lesson. Record each new feature in
  section 8 ("Project log") when it is added.

Course: *The AI Agent Factory*, Chapter 13, "Programming Fundamentals in the AI Era"
(Python track).
https://agentfactory.panaversity.org/building-ai-workers/programming-fundamentals/

## 2. Tech stack and commands

| Item | Choice |
| --- | --- |
| Language | Python 3.14 (latest stable when the project was created, pinned in `.python-version`) |
| Project and package manager | `uv` |
| Type checker | Pyright, **strict mode** (configured in `pyproject.toml`) |
| Version control | Git, pushed to GitHub |

Commands (run from the project folder):

```bash
uv run python main.py      # run the program
uv run pyright             # type-check everything (strict mode)
uvx pyright main.py        # type-check one file without adding pyright to a project
git status                 # what changed
git diff                   # the exact changes
git log --oneline          # history
```

On every change: run the program, run `uv run pyright`, and read the output before
reading the code. Tests (`assert` lines) are run too once a file has them.

## 3. How we learn: PRIMM-AI+

Every new piece of code goes through these five steps. Follow them; do not skip ahead.

| Step | What the learner does | What you (the agent) do |
| --- | --- | --- |
| **P**redict | Guesses what the code will do before it runs | Stay quiet. Do not hint at the answer. Ask for the prediction and a confidence (1–5). |
| **R**un | Runs it and sees the real output | Run it (with permission) and show the real output. |
| **I**nvestigate | Compares the guess with reality and asks *why* | Explain line by line, only as much as asked. |
| **M**odify | Changes one thing, predicts again, runs again | Make the exact edit the learner describes. |
| **M**ake | Writes a specification for something new | Build it against their spec, then help them verify it. |

The operating rule: **predict before you run, every time.** The gap between the
prediction and the real output is where the learning happens.

Nothing is accepted on faith. Every number comes from code that was run and checked,
never from a model's reply.

## 4. What the learner has covered: up to Lesson 13.7

Only use the concepts below. Anything not on this list is **new**.

| Lesson | Topic | Python concepts covered |
| --- | --- | --- |
| 13.1 | You read, the agent writes | The PRIMM-AI+ loop; a variable with `=`; `print(...)`; a list in `[ ]` with 0-based positions (`items[0]`) |
| 13.2 | The workbench | `uv run python file.py`, `uv run pyright`, `uvx pyright`; strict type checking; reading checker output; basic Git (`status`, `diff`, `log --oneline`, `add`, `commit -m`, `switch -c`, `tag`) |
| 13.3 | Values, types and variables | `str`, `int`, `float`, `bool`, `None`; `True` / `False`; comments with `#`; type labels (`cents: int`); `int(...)` conversion; `TypeError`, `ValueError` as messages to read; money in whole cents |
| 13.4 | Decisions and repetition | `if` / `else`; `==` and `>`, `>=`, `<`, `<=`; indentation as blocks; `for item in items:`; a list comprehension seen as "the agent's shorter form" |
| 13.5 | Two conditions, empty values, while | `and`, `or`, `not`; empty values (`""`, `None`, `0`); `x = x or default`; `while` loops; `x += 1` |
| 13.6 | Functions: the signature is the contract | `def name(param: type) -> type:`; `return`; parameters vs arguments; `assert` (with a message after a comma) as a tiny test; one job per function |
| 13.7 | Lists and dictionaries | `dict[str, str]`, `{key: value}`; lookup with `d[key]` (can raise `KeyError`) vs `d.get(key)` / `d.get(key, 0)`; a list of dictionaries as records (`inv["status"]`); `sorted()`; `.sort(key=lambda r: r["cents"], reverse=True)` |

### Not covered yet (treat as new)

- Reading and writing files (Lesson 13.8)
- Dates and the `datetime` module (13.9)
- Reading tracebacks in depth (13.10)
- Test-first / the TDG loop, `pytest` (13.11)
- `try` / `except`, `with`, `import` of standard modules, f-strings, classes and objects,
  `async`, `*args` / `**kwargs`, decorators, generators, `elif` (not explicitly listed in
  the course notes; check with the learner)
- Third-party packages (none are used yet)

## 5. Rule for anything new: teach it first

If a task needs a concept that is not in section 4:

1. Stop before writing the code.
2. Name the concept and say why it is needed.
3. Teach it briefly and simply, with one small example, using PRIMM-AI+
   (show the example, ask the learner to predict, then run it).
4. Only then use it in the project.
5. Add it to the table in section 4 with the date, so the next session knows.

Prefer a solution that uses only covered concepts, even if it is a little longer.

## 6. Coding rules

- **Type labels on everything**: every variable that needs one, every parameter, every
  return type (`-> None` when nothing is returned). Pyright runs in strict mode.
- **Money is whole cents in an `int`.** Never a `float`.
- **Convert text to the right type as soon as it is read.**
- **One job per function.** Small functions with clear names.
- **Every number comes from a tested function**, checked with `assert`.
- For every lookup, ask: what if the key is missing? For every decision: what if the value
  is empty? For every `while` loop: what makes it stop?
- Names in `snake_case` (`due_date`, `total_cents`).
- Keep it readable. The learner reads every line you write.

## 7. How to work with the learner

- Ask before acting (run commands only with permission).
- One step at a time. Show the change, then ask for a prediction before running.
- Short, plain explanations with examples. No jargon without a definition.
- Commit in small steps with clear messages, after the program runs and Pyright is clean.

## 8. Project log

| Date | What changed |
| --- | --- |
| 2026-11-20 | Project created with `uv` on Python 3.14; Pyright strict added; `AGENTS.md` written. `main.py` prints a greeting. |

### Concepts introduced by the setup (taught in the README)

- `if __name__ == "__main__":` in `main.py` (from the `uv init` template). See README.
