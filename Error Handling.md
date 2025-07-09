### Create and check
- instead of:
```
err := someFunc()
if err != nil {
  //handle the error
}
```
- you can do:
```
if err := someFunc(); err != nil {
  //handle the error
}
```

### Error types
```
import (
    "errors"
)

var (
	ErrNotImplemented = errors.New("method not implemented")
)

// can do error matching 
err := someFunc()
if errors.is(err, ErrNotImplemented) {
	//handle the case here
}
```

