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
let aNumber = 42;       //aNumber is inferred to be of type 'number'
aNumber = "forty two";  //Error: aNumber is of type number
```

