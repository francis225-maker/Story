# COMPILER_GROUP_ONE

A term project: a mini compiler for a small C-like language, written in **Python**. All five phases of the compiler live in this single repository.

## Team Members

| # | Name        | GitHub Username | Role / Responsibility |
|---|------       |-----------------|-----------------------|
| 1 | francis     |                 |                       |
| 2 | kofi     |                 |                       |
| 3 |  ama    |                 |                       |
| 4 |  dsds    |                 |                       |
| 5 |    sd  |                 |                       |
| 6 |   das   |                 |                       |
| 7 |   ad   |                 |                       |
| 8 |   da   |                 |                       |
| 9 |  da    |                 |                       |
| 10 | add    |                 |                       |

## Project Phases and Deadlines

| Phase | Deliverable                 | Deadline         | Status      |
|-------|-----------------------------|------------------|-------------|
| 1     | Scanner                     | 25 October 2026  | In progress |
| 2     | Parser                      | 8 November 2026  | Not started |
| 3     | Semantic Analysis / IR      | 22 November 2026 | Not started |
| 4     | Code Generation             | 6 December 2026  | Not started |
| 5     | Optimizer + Final Demo      | 13 December 2026 | Not started |

## Tech Stack

- **Language:** Python 3.8 or newer
- **Dependencies:** none (standard library only)
- **Version control:** Git and GitHub (private repository)

## Project Structure

```
COMPILER_GROUP_ONE/
├── README.md
├── .gitignore
├── main.py                  # Entry point / demo runner
└── minicompiler/
    ├── __init__.py          # Package exports
    ├── token.py             # Phase 1: token types, keywords, operator tables
    ├── scanner.py           # Phase 1: lexical analyzer
    ├── ast_nodes.py         # Phase 2: AST node classes (planned)
    ├── parser.py            # Phase 2: parser (planned)
    ├── semantic.py          # Phase 3: semantic analyzer (planned)
    ├── ir.py                # Phase 3: intermediate representation (planned)
    ├── codegen.py           # Phase 4: code generator (planned)
    └── optimizer.py         # Phase 5: optimizer (planned)
```

## Getting Started

```bash
# 1. Clone the repository
git clone https://github.com/<ORGANIZATION-OR-USERNAME>/COMPILER_GROUP_ONE.git
cd COMPILER_GROUP_ONE

# 2. Check your Python version (3.8+ required)
python --version

# 3. Run the demo from the project root
python main.py
```

> **Important:** Always run from the repository root. Do **not** run `python minicompiler/scanner.py` directly, because the relative imports will fail.

## Phase 1: Scanner

The scanner (lexical analyzer) reads source code as text and converts it into a list of tokens.

### Usage

```python
from minicompiler import tokenize

tokens, errors = tokenize('var x = 5 + 3;')

for tok in tokens:
    print(tok.type, tok.lexeme, tok.value)

for err in errors:
    print(err)
```

### Token fields

| Field    | Description                                                 |
|----------|-------------------------------------------------------------|
| `type`   | A `TokenType` enum member (e.g. `TokenType.IDENTIFIER`)     |
| `lexeme` | The exact source text that was matched                      |
| `value`  | The parsed value (`int`, `float`, `str`, `bool`) or `None`  |
| `line`   | Line number, starting at 1                                  |
| `column` | Column number, starting at 1                                |

### Supported language features

- **Keywords:** `if else while for return func var const true false null int float bool string void break continue print`
- **Integers:** decimal, hex (`0xFF`), binary (`0b1010`), underscores (`1_000`)
- **Floats:** `3.14`, `.5`, `1e10`, `2.5E-3`
- **Strings and chars:** `"hello\n"`, `'a'`, with escapes `\n \t \r \0 \\ \' \"`, `\xHH`, `\uHHHH`
- **Operators:** `+ - * / %`, `= += -= *= /=`, `== != < <= > >=`, `&& || !`, `& | ^ << >>`, `++ --`
- **Punctuation:** `( ) { } [ ] , ; : . ->`
- **Comments:** `// line` and `/* block */`

### Error handling

The scanner never crashes on bad input. It records a `LexError` with the line and column, emits an `ERROR` token, and keeps scanning. Detected errors include unexpected characters, unterminated strings and block comments, malformed numbers (`12abc`), and invalid escape sequences.

```
[Lexical error at 15:11] Malformed number '12abc'
[Lexical error at 15:17] Unexpected character '@'
[Lexical error at 15:19] Unterminated string literal
```

### Note on the `token.py` filename

Python's standard library already has a module called `token`. Our `token.py` is safe **only** because it lives inside the `minicompiler` package and is imported as `minicompiler.token`. Never place it next to the script you run.

## Git Workflow

The course requires a **visible, incremental commit history**. A single last-minute commit does not satisfy the policy.

1. **Never commit directly to `main` for big features.** Create a branch:
   ```bash
   git checkout -b feature/short-description
   ```
2. **Commit small and often** with meaningful messages:
   ```bash
   git add <files>
   git commit -m "feat: add hex literal scanning"
   ```
3. **Push your branch and open a pull request** for review:
   ```bash
   git push -u origin feature/short-description
   ```
4. **Pull before you start work** so you do not overwrite teammates:
   ```bash
   git pull origin main
   ```

### Commit message prefixes

| Prefix   | Use for                          |
|----------|----------------------------------|
| `feat:`  | A new feature                    |
| `fix:`   | A bug fix                        |
| `docs:`  | Documentation changes            |
| `test:`  | Adding or updating tests         |
| `refactor:` | Code cleanup, no behavior change |

### Deadline rule

On each phase's deadline day, the group must have committed its first working feature **and** continue committing later increments. The deadline marks the final feature commit, not the first line of code.

## Repository Access

- Repository: private, named `COMPILER_GROUP_ONE`
- All group members are collaborators with **Write** access
- Instructor added as a collaborator: `emmanueldery31@gmail.com`

## Roadmap

- [x] Repository setup
- [ ] Phase 1: Scanner
- [ ] Phase 2: Parser
- [ ] Phase 3: Semantic Analysis / IR
- [ ] Phase 4: Code Generation
- [ ] Phase 5: Optimizer + Final Demo

## License

For educational use as part of a university course project.
