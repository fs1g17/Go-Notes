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

