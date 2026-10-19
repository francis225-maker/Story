# COMPILER_GROUP_8

## Compiler Construction Project

**Course:** Introduction to Compiler   
**Project Type:** Group Project  
**Implementation Language:** Python  
**Repository:** Group-8

## 1. Project Overview

COMPILER_GROUP_ONE is a university group project focused on designing and implementing a mini compiler for a small C-like programming language using Python.

A compiler is a program that translates source code written in a programming language into another representation that can be processed or executed by a computer. A compiler typically performs several stages of processing, including lexical analysis, syntax analysis, semantic analysis, code generation, and optimization.

This project is divided into five phases. Each phase will be developed, tested, documented, and integrated into the same GitHub repository.

The group will use Git and GitHub to collaborate, share code, review changes, track development progress, and maintain a visible history of contributions.

**Current Phase:** Phase 1 — Scanner (Lexical Analyzer)

**Project Status:** In progress

---

## 2. Project Objectives

The objectives of this project are to:

- Understand the fundamental principles of compiler construction.
- Design a small C-like programming language with clearly defined rules.
- Implement a scanner that converts source code into tokens.
- Implement a parser that checks the grammatical structure of programs.
- Perform semantic analysis to identify meaning-related errors.
- Generate an intermediate representation of the source program.
- Generate target code from the intermediate representation.
- Apply code optimization techniques where appropriate.
- Test the compiler components using valid and invalid input.
- Develop practical skills in Python programming, debugging, documentation, and software testing.
- Practice collaborative software development using Git and GitHub.
- Maintain incremental commits that demonstrate the group's actual progress.

---

## 3. Project Phases and Deadlines

The project will be completed in five phases.

| Phase | Component | Deadline | Status |
|---|---|---|---|
| 1 | Scanner (Lexical Analyzer) | 25 October 2026 | In progress |
| 2 | Parser | 8 November 2026 | Not started |
| 3 | Semantic Analysis and Intermediate Representation (IR) | 22 November 2026 | Not started |
| 4 | Code Generation | 6 December 2026 | Not started |
| 5 | Code Optimization and Final Demonstration | 13 December 2026 | Not started |

The status of each phase will be updated as development progresses. A phase should only be marked complete after its required functionality has been implemented, tested, and integrated.

---

## 4. Technology Stack

| Technology | Purpose |
|---|---|
| Python 3.8 or newer | Implementation of the compiler |
| Git | Version control |
| GitHub | Shared repository and collaboration |
| Python standard library | Core functionality without mandatory third-party dependencies |
| `unittest` or `pytest` | Automated testing, depending on the group's decision |

The group will agree on consistent coding conventions, file interfaces, and testing procedures.

---

## 5. Project Structure

The project will use a modular structure. Each compiler phase will have its own directory, and the scanner will be divided into smaller components to help organize the Phase 1 work.

```text
COMPILER_GROUP_ONE/
├── README.md
├── .gitignore
├── main.py
├── scanner/
│   ├── __init__.py
│   ├── tokens.py
│   ├── identifiers.py
│   ├── numbers.py
│   ├── operators.py
│   ├── punctuation.py
│   ├── strings.py
│   ├── positions.py
│   ├── errors.py
│   └── scanner.py
├── parser/
├── semantic_analysis/
├── code_generator/
├── optimizer/
└── tests/
    └── test_scanner.py
```

This is the planned structure. Files and directories will be added as the relevant work begins. Empty directories may not appear on GitHub until they contain files.

### File Responsibilities

| File or Directory | Responsibility |
|---|---|
| `README.md` | Project documentation and instructions |
| `.gitignore` | Specifies files Git should normally ignore |
| `main.py` | Entry point for running the compiler demonstration |
| `scanner/__init__.py` | Makes the scanner directory importable as a Python package |
| `scanner/tokens.py` | Defines token types, token representation, and shared token definitions |
| `scanner/identifiers.py` | Handles identifier and keyword recognition |
| `scanner/numbers.py` | Handles numeric literal recognition |
| `scanner/operators.py` | Handles operators such as `+`, `==`, and `=` |
| `scanner/punctuation.py` | Handles punctuation such as parentheses, commas, and semicolons |
| `scanner/strings.py` | Handles string literals, character literals, and supported escape sequences |
| `scanner/positions.py` | Tracks source line and column positions |
| `scanner/errors.py` | Represents and reports lexical errors |
| `scanner/scanner.py` | Coordinates scanning and combines the scanner components |
| `parser/` | Will contain the parser implementation in Phase 2 |
| `semantic_analysis/` | Will contain semantic analysis and related functionality in Phase 3 |
| `code_generator/` | Will contain code generation functionality in Phase 4 |
| `optimizer/` | Will contain optimization functionality in Phase 5 |
| `tests/test_scanner.py` | Contains automated tests for the scanner |

The group will agree on how the scanner modules communicate with one another before integrating individual contributions.

---

## 6. Phase 1: Scanner (Lexical Analyzer)

### 6.1 Description

The scanner is the first stage of the compiler. It reads source code character by character and groups the characters into meaningful units called tokens.

For example, the following source code:

```c
var x = 5 + 3;
```

contains a keyword, an identifier, an assignment operator, numeric literals, an arithmetic operator, and a semicolon.

The scanner will identify these tokens and preserve information about their original text and positions in the source program.

### 6.2 Token Information

Each token is planned to contain:

| Field | Description |
|---|---|
| `type` | The token category |
| `lexeme` | The exact text matched in the source code |
| `value` | The interpreted value where applicable |
| `line` | The source line number, starting at 1 |
| `column` | The source column number, starting at 1 |

### 6.3 Planned Scanner Features

The following list describes the intended language features. Actual support will be confirmed by implementation and testing.

**Keywords**

`if`, `else`, `while`, `for`, `return`, `func`, `var`, `const`, `true`, `false`, `null`, `int`, `float`, `bool`, `string`, `void`, `break`, `continue`, `print`

**Identifiers**

Names used for variables and functions, according to the identifier rules defined by the group.

**Numeric literals**

- Decimal integers, such as `25`.
- Hexadecimal integers, such as `0xFF`.
- Binary integers, such as `0b1010`.
- Underscores in numeric literals, such as `1_000`.
- Floating-point numbers, such as `3.14`.
- Scientific notation, such as `1e10` and `2.5E-3`.

**Strings and character literals**

Examples include `"hello"` and `'a'`. Supported escape sequences will be defined by the agreed language specification.

**Operators**

- Arithmetic: `+`, `-`, `*`, `/`, `%`
- Assignment: `=`, `+=`, `-=`, `*=`, `/=`
- Comparison: `==`, `!=`, `<`, `<=`, `>`, `>=`
- Logical: `&&`, `||`, `!`
- Bitwise: `&`, `|`, `^`, `<<`, `>>`
- Increment and decrement: `++`, `--`
- Arrow: `->`

**Punctuation**

Parentheses, braces, brackets, commas, semicolons, colons, and periods.

**Comments**

- Single-line comments beginning with `//`.
- Block comments beginning with `/*` and ending with `*/`.

These features will be implemented and tested incrementally according to the agreed language rules.

### 6.4 Error Handling

The scanner should report lexical errors with useful line and column information.

Potential errors include:

- Unexpected characters.
- Unterminated strings.
- Unterminated block comments.
- Invalid escape sequences.
- Malformed numeric literals.

The scanner's error-recovery behavior will be tested to ensure that invalid input is handled predictably.

### 6.5 Testing

Scanner tests will cover:

- Keywords and identifiers.
- Integer and floating-point literals.
- Operators and punctuation.
- Strings and character literals.
- Whitespace and source positions.
- Comments.
- Empty input and end-of-file handling.
- Invalid characters and malformed literals.

Features will be marked as supported only after implementation and appropriate tests.

---

## 7. Integration Between Phases

The output of each phase will serve as input to the next phase.

| Phase | Input | Expected Output |
|---|---|---|
| Scanner | Source-code text | Tokens and lexical diagnostics |
| Parser | Tokens | Abstract syntax tree (AST) and syntax diagnostics |
| Semantic Analysis / IR | AST | Semantic results and intermediate representation |
| Code Generation | Intermediate representation | Target code or agreed output format |
| Optimization | Intermediate representation or generated code | Optimized output |

The group will define consistent interfaces and data structures to ensure that the components can be integrated successfully.

---

## 8. Getting Started

### Prerequisites

- Python 3.8 or newer, subject to compatibility with the implementation.
- Git installed on the development computer.
- Access to the private GitHub repository.

### Clone the Repository

Replace the placeholder below with the actual GitHub username or organization that owns the repository.

```bash
git clone https://github.com/REPLACE-THIS-USERNAME/COMPILER_GROUP_ONE.git
cd COMPILER_GROUP_ONE
```

### Check the Python Version

```bash
python --version
```

On some computers, use:

```bash
python3 --version
```

### Run the Project

Once the scanner and entry point have been implemented:

```bash
python main.py
```

The exact running instructions will be updated when the initial working implementation is available.

### Run Tests

If the group chooses Python's built-in `unittest` framework, tests can be run from the project root using:

```bash
python -m unittest discover -s tests
```

These commands describe the planned workflow. They may not work until the corresponding files and functionality have been implemented.

---

## 9. Git and GitHub Workflow

The entire project will remain in one shared private repository.

### Step 1: Update Your Local Repository

```bash
git checkout main
git pull origin main
```

### Step 2: Create a Branch

For example:

```bash
git checkout -b feature/scanner-identifiers
```

### Step 3: Stage and Commit Changes

```bash
git status
git add <file-or-files>
git commit -m "feat: recognize identifiers"
```

Replace `<file-or-files>` with the paths of the files being committed.

### Step 4: Push Your Branch

```bash
git push -u origin feature/scanner-identifiers
```

Open a pull request on GitHub and follow the group's agreed review and merge process.

### Commit Message Prefixes

| Prefix | Purpose |
|---|---|
| `feat:` | New functionality |
| `fix:` | Bug fixes |
| `docs:` | Documentation changes |
| `test:` | Tests |
| `refactor:` | Code restructuring without intended behavior changes |

### Incremental Commit Requirement

The group must maintain a visible, incremental commit history. The first working feature for each phase must be committed by the applicable deadline, with further improvements committed throughout development.

Members should use their own GitHub accounts and make commits that accurately represent their contributions.

---

## 10. Team Members and Responsibilities

Complete this table with the group's actual information.

| # | Full Name | GitHub Username | Responsibility |
|---|---|---|---|
| 1 | REPLACE THIS | REPLACE THIS | REPLACE THIS |
| 2 | REPLACE THIS | REPLACE THIS | REPLACE THIS |
| 3 | REPLACE THIS | REPLACE THIS | REPLACE THIS |
| 4 | REPLACE THIS | REPLACE THIS | REPLACE THIS |
| 5 | REPLACE THIS | REPLACE THIS | REPLACE THIS |
| 6 | REPLACE THIS | REPLACE THIS | REPLACE THIS |
| 7 | REPLACE THIS | REPLACE THIS | REPLACE THIS |
| 8 | REPLACE THIS | REPLACE THIS | REPLACE THIS |
| 9 | REPLACE THIS | REPLACE THIS | REPLACE THIS |
| 10 | REPLACE THIS | REPLACE THIS | REPLACE THIS |

Each member should have a clear responsibility and make meaningful contributions. Responsibilities may be adjusted by agreement as the project develops.

---

## 11. Repository Access

- **Repository name:** `COMPILER_GROUP_ONE`
- **Visibility:** Private
- **Programming language:** Python
- **Group members:** All members should have Write access.
- **Instructor:** The instructor should be invited using `emmanueldery31@gmail.com`, as required by the course instructions.

Repository access should be checked in GitHub's repository settings.

---

## 12. Project Roadmap

- [x] Create the shared GitHub repository.
- [ ] Verify access for all group members and the instructor.
- [ ] Finalize the scanner's language rules.
- [ ] Implement and test Phase 1: Scanner.
- [ ] Implement and test Phase 2: Parser.
- [ ] Implement and test Phase 3: Semantic Analysis and IR.
- [ ] Implement and test Phase 4: Code Generation.
- [ ] Implement and test Phase 5: Code Optimization.
- [ ] Integrate the compiler phases.
- [ ] Prepare the final demonstration.
- [ ] Complete project documentation.

The checklist should be updated to reflect actual progress.

---

## 13. Conclusion

COMPILER_GROUP_ONE is intended to provide practical experience in compiler construction, Python programming, software testing, documentation, and collaborative development.

By dividing the project into five phases, the group will build an understanding of how source code is tokenized, parsed, checked, transformed, generated, and optimized.

This repository will serve as the shared workspace and record of the group's implementation, testing, documentation, and incremental progress.

---

**Project:** COMPILER_GROUP_ONE  
**Course:** Compiler Construction  
**Implementation Language:** Python  
**Repository:** Private GitHub repository
