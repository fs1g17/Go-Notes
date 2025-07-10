- lightweight unit of execution 
- called with `go` keyword 

### WaitGroup 
- built around atomic counter
- funcs:
	- `wg.Add(n)`: adds n to internal 64 bit counter (panics if counter goes negative)
	- `wg.Done()`: shorthand for `wg.Add(-1)`
	- `wg.Wait()`: waits for the counter to reach 0
```
package main 

import (
	"fmt"
	"sync"
)

func main() {
	var wg sync.WaitGroup
	for i := 0; i <= 5; i++ {
		wg.Add(1)

		go func() {
			defer wg.Done()
			// do something
		}()
	}

	wg.Wait() // waits here until all go routines are complete
}
```

### Defer
- schedules a function call to run after surrounding function has finished
- kind of like a `finally` mechanism