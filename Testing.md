- have to run `go mod init` first
- create test for `main.go` inside `main_test.go` 
- run with `go test -v *.go`
- fail the test with `t.Fatal`
```
package main 

import (
	"testing"
)

func TestMain(t *testing.T) {
	t.Run("comment", func(t *testing.T) {
		t.Run("should do this", func(t *testing.T) {
			// do something 
			if err != nil {
				t.Fatalf("Error doing this %s", err)
			}
		})
	})
}
```