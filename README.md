# xfail

[![Go Reference](https://pkg.go.dev/badge/github.com/AlekSi/xfail.svg)](https://pkg.go.dev/github.com/AlekSi/xfail)

Go package providing testing helpers for expected tests failures.

## Examples

### Simple

```go
func TestParseDuration(tt *testing.T) {
	t := XFail(tt, "https://github.com/golang/go/issues/67076")

	if _, err := time.ParseDuration("3.336e-6s"); err != nil {
		t.Fatal(err)
	}
}
```

## License

Copyright 2021 FerretDB Inc. Licensed under Apache License v2.0.
