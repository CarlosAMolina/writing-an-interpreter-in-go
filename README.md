## Introduction

In this project I run the code of the Thorsten Ball's book Writing An Interpreter In Go.

## Requirements

- Go >= 1.13 (recommended).

## Run

### Tests

```bash
cd src/monkey/
go test ./lexer
```

### REPL

```bash
cd src/monkey/
go run main.go
# >> let add = fn(x, y) { x + y; };
```

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

#### Parser. What is it?

Converts the source code input (input as text or tokens) into a data structure that represents the input, normally called `syntax tree` or `Abstract Syntax Tree` (AST).

The AST format changes between program languages.

Parser is also called `syntactic analysis` because while building up the data structure, the input is analyzed to check that respects the expected structure.

#### Parser strategies

There are two main parser strategies:

- Top down parser: first the root node fo the AST is constructed and then descends.
- Bottom up parser: the opposite of the previous one.

#### Statements

A program is formed by statements.

Example of 2 let statements:

```bash
let x = 10;
let add = fn (a, b) {
    return a + b
}
```

Let statements bind a value to a given name. Their form is:

```bash
let <identifier> = <expression>
```

##### Statement VS expression

- Expression: produces values. Example:

    ```bash
    5
    ```

    ```bash
     add (5,5)
    ```

- Statement: does not produces values. Example:

    ```bash
    let x = 5
    ```

    ```bash
    return 5
    ```

What is an expression or an statement depends on the programming language as some programs allow to use function literals in places where any expression is allowed and other languages no.

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

