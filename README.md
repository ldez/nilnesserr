# nilnesserr

nilnesserr = nilness + nilerr

`nilnesserr` is a linter for report return nil error in go. It combines the features of [nilness](https://cs.opensource.google/go/x/tools/+/refs/tags/v0.28.0:go/analysis/passes/nilness/nilness.go) and [nilerr](https://github.com/gostaticanalysis/nilerr), providing a concise way to detect return an unrelated/nil-values error.

## Simple case

case 1
```go
err := do()
if err != nil {
    return err
}
err2 := do2()
if err2 != nil {
    return err // which should return err2 after check `err2 != nil`, but return a nil value error
}
```

## Some Real Bugs

- https://github.com/alingse/sundrylint/issues/4
- https://github.com/alingse/nilnesserr/issues/1


## Installation

Install using Go modules:

```bash
go get github.com/alingse/nilnesserr@main
```

## TODO


case 2

```go
err := do()
if err != nil {
    return err
}
_, ok := do2()
if !ok {
    return err
}

```

maybe this is also a bug, should return a non-nil value error

## License

This project is licensed under the MIT License. See the LICENSE file for details.

This project incorporates source code from two different libraries:

1. [nilness](https://cs.opensource.google/go/x/tools/+/refs/tags/v0.28.0:go/analysis/passes/nilness/nilness.go) licensed under the BSD license.
2. [nilerr](https://github.com/gostaticanalysis/nilerr) licensed under the MIT license.
