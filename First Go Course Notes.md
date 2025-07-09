- array: fixed size `var a [2]string`
- slice: dynamically sized array `cards := []string`

#### Slice functions
- append: `s = append(s, 1)`

#### Looping
- `for i, value := range slice {}`

#### Define types
- `type deck []string`

#### Receiver 
- `func (d deck) print() {}`
- any var of type "deck" now has access to print method

#### Slice range
- `slice[a:b]` 
- gets elements from index to up to, not including, b

#### Type conversion
- `[]byte("Hello,World!")`
- casts string to slice of bytes

#### Make 
- slices have length and capacity 
- length = number of elements in the slice
- capacity = number of elements the slice can hold 
- to create a slice with given capicity and length, use make
- `newSlice := make(type, length, capacity)`

#### Go Routines
- independantly scheduled flow of control
- very lightweight
- since v1.22, go fixed "loop-variable capture" issue
- before v1.22, common approach was anonymous functions with closure
```
for _, customer := range customers {
  go func(customer Customer) {
    registerCustomer(ctx, customer)
  }(customer)
}
```

#### Go Routine vs Thread
- thread is:
  - managed by OS
  - microsecond-millisecond creation (expensive system call)
  - fixed size (1MB on linux/macOS, 2MB on Windows)
  - max threads = 1000
- go routine is:
  - managed in user space by Go's runtime 
  - tens of nanoseconds creation 
  - starts at 2 kB and grows/shrinks on demand
  - max go routines = 100s of thousands

#### Channels 
- communicate between go routines
- receiving messages is blocking 

#### Commands
###### go build
compiles 

###### go run 
compiles + runs

###### go fmt 
formats 

###### go install
compiles + installs 

###### go get 
downloads raw package

###### go test
runs tests

#### Packages
- started with `package main` for example
- groups files together (like js module)
- 2 types: 
  - executable: generates executable file (has to be `main`)
  - reusable: code used as helpers  
- if `package main`:
  - we must have a public function called `main`

#### Import keyword
- bring exported identifiers available in current scope

#### Type Assertion 
- `x.(T)` asks at run time:
  - does the value stored in `x` implement the interface/concrete type `T`? 
- `v, ok := x.(T)`:
  - doesn't panic if `x` doesn't implement `T` - `v` is just zero value of `T` and `ok` is `false` (this is `comma-ok` idiom)

#### How to Use Interfaces
- in go, types don't have to implement interfaces directly
- variables of a given type can be passed to functions that expect an argument of interface type, and it'll work so long as the variables satisfy the interface 
- interfaces only accept methods 
- i.e. it's only about behaviour

#### Typing Compared to Java
- Java has nominal typing:
```
class Circle implements Geometry {...}
```
- Go has structual typing 
- the method signature matter

#### Pass by Value
- Go is a pass by value language

#### References
- & reference operator (address of)
  - ptr := &x
- \* dereference operator (value at)
  - value := *ptr

#### Type vs Operator
- `ptr *person` this is type description (pointer to person)
- `*ptr` this is operator

#### Automatic method receiver adjustment 
- `func (p *person) updateName(updatedName string) {}` 
- but we can still call:
```
jim := person{firstName: "jim"}
jim.updateName("jimmy")
```
- because go treats it like: `(&jim).updateName("jimmy")`
- similalry the actual function body: 
- `p.firstName = updatedName` is just syntactic sugar for
- `(*p).firstName = updatedName`

#### Functions that accepts slices 
- slice has `length`, `capacity` and `ptr to array`
- a function that accepts a slice as an argument does pass by value
- however the thing it copies is the `ptr to array` 
- therefore modifying the slice inside the function will affect the original slice

#### Value vs Reference types
- value types:
  - int
  - float
  - string
  - bool
  - structs
- reference types:
  - slices
  - maps
  - channels 
  - pointers 
  - functions 


