## Introduction

In this project I run the code of the Thorsten Ball's book Writing An Interpreter In Go.

## Requirements

- Go >= 1.13 (recommended).

## Theory

### Lexer

Also called `tokenizer` or `scanner`.

Takes source code as input and output tokens that represent the source code. This is the first transformation done to the source code and it's called `lexical anaysis` or `lexing`.

Tokens are small, easily categorizable data structures.

Example Lexer input:

```bash
let x = 2 + 3;
```

Example Lexer output:

```bash
[
  LET,
  IDENTIFIER("x")
  EQUAL_SIGN
  INTEGER(2)
  PLUS_SIGN
  INTEGER(3)
  SEMICOLON
]
```

A lexer also attach to a token the line number, column number and filename to create useful error messages in the parsing step, example `error: expected semicolon token. line 32, column 12, program.foo`.

The tokens are sent to the parser.

### Parser

Converts tokens into an `Abstract Syntax Tree`.

### REPL

REPL = Read Eval Print Loop.

Other names that REPL receives: console or interactive mode.

What REPL does:

1. Read input.
2. Send input to the interpreter to be evaluated.
3. Print the result.
4. Repeat the steps.

## Rerources

Book's URL: 

<https://interpreterbook.com/>

Official source code:

<https://interpreterbook.com/waiig_code_1.7.zip>

