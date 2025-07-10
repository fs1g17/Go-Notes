- Context carries:
	- deadlines
	- cancellation signals
	- request-scoped values
- across API boundaries and go routines

- `context.Context` is created for each request by `net/http`
- `ctx := context.Background()` or `context.TODO()`
- context is immutable, can only copy:
	- `ctx = context.WithValue(ctx, "userID", 42)`
### Storing Values in Context
```
type contextKey string
var UserIDKey contextKey = "userID"

// somewhere later
ctx := context.Background()
ctx = context.WithValue(ctx, UserIDKey, 42)
```