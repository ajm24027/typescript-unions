# typescript-unions

### What are Unions?

Unions are a way to combine multiple types into a singular type. Some contextual uses might include "Interfaces" which essentailly tells classes should behave.

How we've known types to operate - below is a value variable which is assigned to the type "number", in the future a number must be assigned to the variable for typescript to be satisfied:

```typescript
let value: number
```

Now however, we can assign multiple types to a singluar variable using union, as we use pipes (|), we can tack on new types to variables.

```typescript
let value: number | boolean | string
```

#### Now for the interface -

Say that we have two interfaces which have their own properties (kind, size, & radius):

```typescript
interface Square {
  kind: 'square'
  size: number
}

interface Circle {
  kind: 'circle'
  radius: number
}
```

We can use Unions to create a variable that accepts both types of interfaces:

```typescript
let myShape: Square | Circle
```

I can't show the dynamic nature of the code, but as we assign various properties to the newly created myShape variable, Typescript will narrow down or offer guidelines for how we should create the rest of the variable because it knows for example, that if my kind is === "square" not to allow me to assign a radius to it, because radius only exists in the Circle interface.

To correctly use this in Typescript, we even have to use conditionals to correctly guide Typescripts logic so that our functions and code can run. This is because it wants us to follow the previously defined logic from before. If I try to access radius or size (which are specific to a specific interface) before defining what interface was passed in as a parameter, the code will not work.

```typescript
const displayShape = (shape: Square | Circle): void => {
  console.log('Kind', shape.kind)
  if (shape.kind === 'circle') {
    console.log('Radius', shape.radius)
  } else {
    console.log('Size', shape.size)
  }
}
```

### Unions in Arrays

To correctly use Unions in arrays use the following syntax:

```typescript
let array: (number | string | (Square | Circle))[] = [myShape, myShape]
```
