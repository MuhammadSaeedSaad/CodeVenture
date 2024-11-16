# Typescript

## interface
1. The power of interface is that it acts like a gate keeper for a specific function or class.
2. Another important aspect is that interfaces provide a level of abstraction or high-level understanding of a certain class. </br>
ex: if I have a class that has sorting methods to sort nunmbers, strings, etc. for instance bubble-sort. I don't need to know how the bubble-sort works if there is an interface
that tells me that if I need to use this class I need to implement a `compare` and `swap` functions and have a property called `lenght`.

## Abstract classes
1. abstract classes are much like interfaces. they provide a level of abstraction plus they can have actual implementation of certain methods.
2. Abstract classes can be better used in situations where there is a strong connections between classes.
3. On the other hand, interfaces are used where there is connection between classes but not so strong one. </br>
ex1: in the sorting example better use abstract class `Sorter` to provide the sorting algorithm and the abstraction.
ex2: for marking things on a map they have to be mappable. `Mappable` can be an interface.


## Enums
1. Primary goal of using Enums is to signal to other engineers that these are all closely related values.
2. Follows near-idential syntax rules as normal objects.
3. Creates an object with the same keys and valeus when converted from TS to JS.
4. Use whenever we have a small fixed set of values that are all closely related and know at compile time.

# Misc notes
## How to create an interface that matches any object
```Typescript
interface ClassConstructor {
    new (...args: any[]): {}
}
```