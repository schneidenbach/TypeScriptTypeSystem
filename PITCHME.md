![TypeScript Logo](https://cloud.githubusercontent.com/assets/3449303/18765110/8c5c603e-8114-11e6-9166-554b0face27b.png)

## Deconstructing TypeScript's Type System

#### Spencer Schneidenbach

@schneidenbach

---

## What is TypeScript?

![TypeScript Logo](https://cloud.githubusercontent.com/assets/3449303/18765110/8c5c603e-8114-11e6-9166-554b0face27b.png)

--- 

## Why TypeScript?

Future of JavaScript, Today  
Better Tooling  
It's JavaScript That Scales

---

## Best Thing about TypeScript

> It doesn't try to not be JavaScript - it just tries to make JavaScript better

?

---

## Best Thing about TypeScript

> It doesn't try to not be JavaScript - it just tries to make JavaScript better

Me

---

## Major Companies Are Using TypeScript

Google  
Slack

---

## What TypeScript Isn't

"C# All The Things"

---

## What TypeScript Isn't

> **TypeScript is manifestly not about turning JavaScript into C#.** You’ll never be best of breed in one ecosystem by attempting to retrofit another ecosystem.

Anders Heljsberg

---

## Everyone Talks About

async/await  
classes  
arrow functions  
basic type usage

---

![TypeScript Logo](https://cloud.githubusercontent.com/assets/3449303/18765110/8c5c603e-8114-11e6-9166-554b0face27b.png)

These are great reasons to use TypeScript

---

![TypeScript Logo](https://cloud.githubusercontent.com/assets/3449303/18765110/8c5c603e-8114-11e6-9166-554b0face27b.png)

Equally good - TypeScript's awesome type system

---

## Let's Dive In

---

## Let's Talk Basics

`number`, `string`, `boolean`, `array`  
`null`, `undefined`  
`any`

---

## Implicit Types

Variables and functions will be given types by TypeScript where possible

```typescript
let aNumber = 42;   //aNumber is inferred to be type 'number'
```

If you mix types, TypeScript will show an error

```typescript
let aNumber = 42;
aNumber = "forty two";  //Error: aNumber is of type number
```

---

## Explicit Types

You can add type annotations to your variables

```typescript
let aNumber: number = 42;
```

Explicitly marks variable as a type  
Useful when you don't know value ahead of time

---

## Functions

In JavaScript, it's a free-for-all

```typescript
function printNameAndAge(name, age) {
    console.log(`Hello ${name}!`);
    console.log(`You are ${age} years old.`);
}

printNameAndAge("Spencer", 30);
printNameAndAge();  //totally valid
printNameAndAge("Jeff", "Jon", "Jay", "old");
```

---

## Functions

In TypeScript, it's better enforced

```typescript
function printNameAndAge(name: string, age: number) {
    console.log(`Hello ${name}!`);
    console.log(`You are ${age} years old.`);
}

printNameAndAge("Spencer", 30);                 //ok
printNameAndAge();                              //error
printNameAndAge("Jeff", "Jon", "Jay", "old");   //def nope
```

---

## Functions

In addition to parameters...

```typescript
function printNameAndAge(name, age) : void {
    console.log(`Hello ${name}!`);
    console.log(`You are ${age} years old.`);
}
```

You can add type annotations to functions to explicitly set a return type

---

## Functions

This is compile-time enforced

```typescript
function operate(num1: number, num2: number, op: string) : number {
    if (op === "add") {
        return num1 + num2;
    }
    //ERROR: return missing
}
```

---

## Interfaces

The types you will use the most  
They are similar, but not the same as .NET interfaces!

---

## Duck typing

If it quacks like a duck, walks like a duck, and looks like a duck, it's a duck

---

## Duck typing

![PHP? No thanks!](assets/duck.jpg)

---

## Here's an interface

```typescript
interface Person {
    firstName: string;
    lastName; string;
}
```

---

## Interfaces define structure

The "shape" of the object is what counts

```typescript
interface Person {
    firstName: string;
    lastName: string;
}

function addPerson(newPerson: Person) {
    //do some stuff
}

addPerson({
    firstName: "John",
    lastName: "Lackey"
});     //totally valid
```

---

## Interfaces define structure

The "shape" of the object is what counts

```typescript
interface Person {
    firstName: string;
    lastName: string;
}

function addPerson(newPerson: Person) {
    //do some stuff
}

addPerson({
    firstName: "Matt"
})      //fails
```

---

## Optional properties

```typescript
interface Person {
    firstName: string;
    lastName?: string;
}
```

---

## Optional properties

```typescript
interface Person {
    firstName: string;
    lastName?: string;
}

function addPerson(newPerson: Person) {
    //do some stuff
}

addPerson({
    firstName: "Matt"
})      //valid!
```

---

## But that's not all

> “Interfaces are capable of describing the wide range of shapes that JavaScript objects can take”
TS docs

---

## Function types

```typescript
interface Logger {
    (message: string, severity: string): void;
}
```

---

## Function types

```typescript
interface Logger {
    (message: string, severity: string): void;
}

let aLogger: Logger = (message, severity) => {
    //log to console?
}
```

---

## Index types

Specifies a type as "indexable"

```typescript
interface NumberDictionary {
    [index: string]: number;
}
```

The index type must be a number or string  
Useful for enforcing the return type of an indexed type

---

## We'll revisit index types

---

![Alton Brown](assets/alton.jpg)

---

## What's the runtime impact of interfaces?

---

Interfaces don't compile down to anything

```typescript
////Person.ts
interface Person {
    firstName: string;
    lastName: string;
}

////Person.js
//nothing here!
```

Use them to give meaning to your code

---

## Generics

Allows you to define reusable constraints on types

```typescript
let thePersons: Array<Person> = [];

thePersons.push({
    firstName: "John",
    lastName: "Lackey"
});
```

---

## Generics: TODO

generic constraints

---

## Classes

Groups of data and actions, like C#/VB.NET classes

```typescript
class Animal {
    string: name;
    
    move() : void {
        console.log(`${this.name} moved.`);
    }
}
```

---

## Classes

Classes can implement interfaces

```typescript
interface Person {
    firstName: string;
    lastName: string;
}

class Employee implements Person {
    firstName: string;
    lastName: string;
    dateHired: Date;
}
```

---

## Classes

Classes can inherit from other classes

```
class SalesRepresentative inherits Employee {
    salesCode: string;
}
```

---

## Classes

Strongest use cases are inheritance and code reuse

---

## Enums

Enums are just like enums in C# and VB.NET  
Number based

```typescript
enum Suit { 
    Heart,
    Spade,
    Diamond,
    Club
}

let aSuit: Suit = Suit.Club;
```

---

## const Enums

Inlines use of the enum

```typescript
const enum Suit { 
    Heart,
    Spade,
    Diamond,
    Club
}

let aSuit: Suit = Suit.Club;
```

Compiles to:

```typescript
let aSuit = 3;
```

A little more performant

---

## Enum tip

When using enums, start the enum with number 1

```typescript
enum Suit { 
    Heart = 1,
    Spade,
    Diamond,
    Club
}
```

This allows you to assert an enum value as truthy

---

## String literal types

Ooh, new syntax

```typescript
type Suit = "Heart" | "Diamond" | "Spade" | "Club";

let aSuit: Suit = "Heart";
```

---

As far as the `type` syntax goes...

---

![Alton Brown](assets/alton.jpg)

---

## Enums vs string literals

I prefer string literals, but you might like enum

---

## Enums vs string literals

Real world:

```csharp
enum SecurityClearance { TopSecret, Lowest }

class Person
{
    [JsonConverter(typeof(StringEnumConverter))]
    public SecurityClearance SecurityClearance { get; set; }
}
```

If you deserialize enums as string, use string literals  
Otherwise use enums

---

## Tuples

Arrays are commonly used as tuples in JavaScript

```typescript
let numberPair = [123, "one hundred twenty three"];
```

---

## Tuples

You can add type annotations to enforce the "tuple" type

```typescript
function printNumbers(aNumberTuple: [number, string]) {
    console.log(`${aNumberTuple[0]}` `${aNumberTuple[1]}`);
}

let numberPair = [123, "one hundred twenty three"];
printNumbers(numberPair);   //ok
printNumbers(["two", 2]);   //error
```

---

## Type assertions and type guards

