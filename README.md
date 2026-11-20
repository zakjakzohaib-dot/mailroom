# mailroom-live

A learning project for *Programming Fundamentals in the AI Era* (Chapter 13, Python track),
built step by step with an AI agent using the PRIMM-AI+ method. See `AGENTS.md` for the
full rules.

## Run it

```bash
uv run python main.py   # run
uv run pyright          # type-check (strict)
```

## New concept from the setup: `if __name__ == "__main__":`

`uv init` created `main.py` with this at the bottom:

```python
def main() -> None:
    print("Hello from mailroom-live!")


if __name__ == "__main__":
    main()
```

You already know `def` (13.6) and `if` (13.4). The new part is `__name__`.

- Python gives every file a hidden variable called `__name__` (a `str`).
- When you **run** the file directly (`uv run python main.py`), `__name__` is `"__main__"`.
- When another file **imports** it (a later lesson), `__name__` is the file's name, `"main"`.

So the `if` reads: "only call `main()` when this file is the one being run."
For now, just remember: this is the program's front door.

**Predict:** if you deleted the last two lines and ran the file, what would print?
Write your guess, then try it.
