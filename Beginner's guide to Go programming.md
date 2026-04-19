# Go Language Notes

A concise reference for getting started with Go — covering program structure, compilation, and standard output.

---

## Table of Contents

- [First Go Program](#first-go-program)
- [Program Structure & Syntax](#program-structure--syntax)
- [Running a Go Program](#running-a-go-program)
- [Common `fmt` Functions](#common-fmt-functions)

---

## First Go Program

Create a file named `helloWorld.go`:

```bash
touch helloWorld.go
```

```go
package main

import "fmt"

func main() {
    fmt.Println("hello, world")
}
```

Run it:

```bash
go run helloWorld.go
# Output: hello, world
```

| Line | Purpose |
|---|---|
| `package main` | Declares this file belongs to the executable `main` package |
| `import "fmt"` | Imports the standard formatting/IO package |
| `func main()` | Entry point — execution starts here |
| `fmt.Println(...)` | Prints text to stdout with a trailing newline |

---

## Program Structure & Syntax

### Packages

Every Go file starts with a `package` declaration. `package main` marks the entry point of an executable program.

### Imports

```go
import "fmt"
```

Go has a rich standard library. Packages are imported by their path string. Unused imports cause a **compile error**.

### Functions

```go
func main() {
    // code
}
```

- All functions start with `func`.
- The opening brace `{` **must** be on the same line as `func` — this is enforced by the compiler.

> ⚠️ **Common mistake:** Placing `{` on a new line causes a syntax error:
> ```
> syntax error: unexpected semicolon or newline before {
> ```

---

## Running a Go Program

Go is a compiled language. `go run` compiles and executes in one step.

```bash
go run helloWorld.go
```

This is equivalent to:

```bash
go build helloWorld.go   # produces a binary: ./helloWorld
./helloWorld             # runs the binary
```

Use `go build` when you want a standalone executable (e.g., for deployment or performance benchmarking).

### Example — Multiple Print Statements

```go
// helloGopher.go
package main

import "fmt"

func main() {
    fmt.Println("hello Gopher.")
    fmt.Println("hello Gopher.")
    fmt.Println("hello Gopher.")
}
```

```bash
go build helloGopher.go
./helloGopher
# hello Gopher.
# hello Gopher.
# hello Gopher.
```

---

## Common `fmt` Functions

The `fmt` package provides three primary output functions:

| Function | Prints Text | Newline | Format Verbs |
|---|:---:|:---:|:---:|
| `fmt.Print()` | ✅ | ❌ | ❌ |
| `fmt.Println()` | ✅ | ✅ | ❌ |
| `fmt.Printf()` | ✅ | ❌ | ✅ |

### Example

```go
package main

import "fmt"

func main() {
    fmt.Print("hello")
    fmt.Print("world")       // prints on same line → helloworld

    fmt.Println()            // inserts a blank line
    fmt.Println("labex")     // prints with newline → labex

    fmt.Printf("%s\n", "London")  // formatted output → London
}
```

### Common `Printf` Verbs

| Verb | Meaning |
|---|---|
| `%s` | String |
| `%d` | Integer |
| `%f` | Float |
| `%v` | Default format (any value) |
| `%T` | Type of the value |
| `\n` | Newline character |

---

> 💡 **Tip:** `fmt` also provides functions for reading input (`fmt.Scan`, `fmt.Scanf`) and error formatting (`fmt.Errorf`) — covered in later sections.