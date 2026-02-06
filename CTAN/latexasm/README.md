# LaTeX Assembly Language (latexasm)

A virtual machine implemented in `expl3` for `pdflatex` that allows writing and executing assembly-like code directly within LaTeX.

## Installation

Place `latexasm.sty` in your project directory or LaTeX path.

## Usage

```latex
\usepackage{latexasm}

\begin{latexasm}
    \Instr{MOV}[R0][5]
    \Label{LOOP}
    \Instr{PRINT}[R0]
    \Instr{SUB}[R0][1]
    \Instr{CMP}[R0][0]
    \Instr{JNZ}[LOOP]
    \Instr{HALT}
\end{latexasm}
```

## Supported Instructions

- `MOV dest, src`: Move value `src` (register or immediate) to `dest` register.
- `ADD dest, src`: Addition.
- `SUB dest, src`: Subtraction.
- `MUL dest, src`: Multiplication.
- `DIV dest, src`: Integer division.
- `MOD dest, src`: Modulo operation.
- `CMP a, b`: Compare two values and set flags.
- `JMP label`: Unconditional jump.
- `JZ label`: Jump if zero.
- `JNZ label`: Jump if not zero.
- `PRINT src`: Print register or immediate value to the PDF.
- `CHR src`: Print ASCII character from register value.
- `DATA label, value`: Define a named string or constant.
- `STRLEN dest, label`: Store length of string `label` into `dest`.
- `GETCH dest, label, index`: Load ASCII value of character at `index` in string `label` into `dest`.
- `HALT`: Stop execution.

## Examples

The `example.tex` file includes four complete examples:

1. **Counter 10-0**: Countdown loop demonstrating conditional jumps
2. **Hello World**: Character-by-character string output using `GETCH` and `CHR`
3. **atoi**: Converts an ASCII string "123" to integer 123
4. **Kitchen Sink**: Demonstrates all arithmetic, string, and control flow instructions

## Registers
8 registers are available: `R0`, `R1`, `R2`, `R3`, `R4`, `R5`, `R6`, `R7`.
