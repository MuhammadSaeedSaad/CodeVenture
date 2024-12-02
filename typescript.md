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

## Generics
### Type inference in generics
```typescript
class ArrayOfAnything<T> {
    constructor(public collection: T[]) {}

    get(index: number): T {
        return this.collection[index];
    }
}

const arr = new ArrayOfAnything(['a', 'b', 'c']); // type of arr is string[]
```
```typescript
function printAnything<T>(arr: T[]): void {
    for(let i=0; i < arr.length; i++) {
        console.log(arr[i]);
    }
}

// both below are equal
printAnything<string>(['a', 'b', 'c']);
printAnything(['a', 'b', 'c']);
```

### Generic Constraints
```typescript
class car {
    print(): void {
        console.log('I am a car');
    }
}

class House {
    print(): void {
        console.log('I am a house');
    }
}

interface Printable {
    print(): void;
}

function printHousesOrCars<T extends Printable>(arr: T[]): void {
    for(let i=0; i < arr.length;  i++) {
        arr[i].print();
    }
}

printHousesOrCars<House>([new House(), new House()]); // func definition with 'extends' like above or you will get error here
printHousesOrCars<Car>([new Car(), new Car()]);
```

## Composition vs. Inheritance
| Composition | Inheritance |
|-------------|-------------|
| Has a | Is a |
| more reusable | more rigid and straight forward |
1. There is a huge misconception in the javascript community about around 'Favor object composition over class inheritance'.
2. Concatinative composition or literal composition (composition as it is in dictionary. like composing) or multiple inheritance is very different than the composition design pattern.

### Resouces
1. [Composition vs Inheritance](https://dev.to/hassam7/composition-vs-inheritance-4oo2) daily.dev.
# Misc notes
## Weird type annotations
1. define a type for a callback.
```typescript
type Callback = () => {} // this is the type for a function

on(eventName: string, callback: Callback) {
        
}
```
2. When the properties of an object is unknown.
```typescript
const someObject: { [key: string]: string[] }
```

1. Ensure correct assignment
```typescript
// someObject: string[] || undefined
const someArray = someObject || [];
```

## How to create an interface that matches any object
```Typescript
interface ClassConstructor {
    new (...args: any[]): {}
}
```