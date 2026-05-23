# xfail

[![Go Reference](https://pkg.go.dev/badge/github.com/AlekSi/xfail.svg)](https://pkg.go.dev/github.com/AlekSi/xfail)

Go package providing a testing helper for expected test failures.

`XFail` returns a new [testing.TB](https://pkg.go.dev/testing#TB) instance that expects the test to fail for the given reason.
At the end of the test, if it was marked as failed using non-fatal methods `Fail`, `Error`, or `Errorf`,
it will pass instead.
If it wasn't marked as failed, it will fail so that the `XFail` call can be removed.
Fatal methods `FailNow`, `Fatal`, or `Fatalf` will skip the rest of the test instead.

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
