# Explore TypeScript Type Hierarchy: any, unknown, and never

## Introduction

TypeScript types work like a family tree. The type is in the top can hold any value(like parents) and the bottom one type can't hold any value at all(the new born baby). In this post, we will learn how `any`, `unknown`, and `never` work this tree. We will also learn about why `unknown` is the safer choice.

## The Top: unknown

`unknown` is a top type. You can put any value inside it. But TypeScript will not allow you to use the value until you check what it is.

```typescript
let value: unknown = "hello";

// value.toUpperCase(); // Error!

if (typeof value === "string") {
  console.log(value.toUpperCase()); // OK
}
```

## The Unsafe Choice : any

`any` turns off type checking. You can do anything with it, even things that will crash your program.

```typescript
let data: any = 5;
data.toUpperCase(); // No error here, but it crashes when run
```

## The Bottom: never

`never` is the bottom type. A never type can't hold any value. We use it for functions that never finish, like a function that always throws an error.

```typescript
function fail(message: string): never {
  throw new Error(message);
}
```

A `never` can be used where any type is expected. But no other type can be given to a `never`.

## Why unknown Is Better

`any` hides bugs until the code runs. `unknown` makes you check the type first, so TypeScript catches your mistakes early. This keeps your code safe.

## Conclusion

Think it like that, `unknown` as the most responsible person who hold all responsibility and `never` as the less responsible one and The `any` type middle child who breaks the rules and skips safety. Whenever you do not know a type, use `unknown`. Your code will have fewer bugs.
