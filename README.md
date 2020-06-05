### Why this fork?

**tl;dr** Gocycle doesn't increase complexity no more for error checking.

Gocyclo unfortunately is not maintained by over five years and it doesn't exclude error checking from cyclomatic 
complexity calculation. With this fork I added a quick check for each `if` statement. Every time the `if` will be like the one below, the complexity won't be incremented:

```go
if err != nil {
    //...
}
```

---

Gocyclo calculates cyclomatic complexities of functions in Go source code.

The cyclomatic complexity of a function is calculated according to the
following rules:

     1 is the base complexity of a function
    +1 for each 'if', 'for', 'case', '&&' or '||'

To install, run

    $ go get github.com/fzipp/gocyclo

and put the resulting binary in one of your PATH directories if
`$GOPATH/bin` isn't already in your PATH.

Usage:

    $ gocyclo [<flag> ...] <Go file or directory> ...

Examples:

    $ gocyclo .
    $ gocyclo main.go
    $ gocyclo -top 10 src/
    $ gocyclo -over 25 docker
    $ gocyclo -avg .

The output fields for each line are:

    <complexity> <package> <function> <file:row:column>

