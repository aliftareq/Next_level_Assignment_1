# Behind the scene of TypeScript Compiler & the role of tsconfig
## Introduction

Our typical Browsers and Node.js cannot run TypeScript directly. They only understand JavaScript. So we use a tool called `tsc`, the TypeScript compiler, to change our code into JavaScript. In this post, we will see what `tsc` does and why `tsconfig.json` matters.

## What tsc Does

When you run `tsc`, it does three main jobs. First, it reads your code and builds a tree of it. Second, it checks the types and shows errors. Third, it removes the types and writes plain JavaScript.

If the types are wrong, `tsc` shows an error.

```typescript
let name: string = 5; // Error: number is not assignable to string
```

If everything is correct, `tsc` creates a new file.

```typescript
// index.ts
let age: number = 20;
```

```javascript
// index.js
let age = 20;
```

The type `number` is gone, because JavaScript does not need it.

## The Role of tsconfig.json

The `tsconfig.json` file tells `tsc` how to compile your project. Without this file, `tsc` uses its default settings.

```json
{
  "compilerOptions": {
    "target": "ES2017",
    "module": "commonjs",
    "strict": true,
    "outDir": "dist"
  }
}
```

- `target` picks the JavaScript version of the output.
- `module` picks the module style.
- `strict` turns on safer type checks.
- `outDir` is the folder for the new files.

## Conclusion

The `tsc` compiler checks your types and then turns TypeScript into JavaScript. The `tsconfig.json` file controls how this happens. When you set it up well, your code is safer and works in more places. Learn these two tools well, and fixing bugs becomes much easier.