# go-stream
Lazy stream to work with slices wich will be calculated only when terminal function called or during the mapping
## Creation
New
```
import "github.com/catmorte/go-streams/pkg/stream"
...
array := []SomeType1{...} 
...
stream := stream.New(array)
```
Mapped from another
```
import "github.com/catmorte/go-streams/pkg/stream"
...
array := []SomeType1{...} 
...
streamType1 := stream.New(array)
streamType2 := stream.Map(streamType1, func(i int, v SomeType1) []SomeType2 {
  return []SomeType2{...}
})
```
## Methods
### Non-terminal methods
`Sort(sortValues SortFunc[V]) Stream[V]` - sort values with function

`Filter(checkValues FilterFunc[V]) Stream[V]` - filter values with function

`Peek(peekValues PeekFunc[V]) Stream[V]` - peek values with function

`Limit(int) Stream[V]` - limit values to number

`Skip(int) Stream[V]` - skip values from number

`Distinct(compareValues EqFunc[V]) Stream[V]` - remove duplicates using funcition to compare 

### Terminal methods

`First() (V, bool)` - get first value (true if exists)

`Last() (V, bool)` - get last value (true if exists)

`Count() int` - get amount of values

`AllMatch(checkValues func(int, V) bool) bool` - check if all matches condition function

`AnyMatch(checkValues func(int, V) bool) bool` - check if any matches condition function

`NoneMatch(checkValues func(int, V) bool) bool` - check if none matches condition function

`ForEach(do DoFunc[V]) error` - do for each synchronously

`ForEachAsync(do DoFunc[V]) error` - do for each asynchronously

`Get() []V` - get values



