# Basics

Objectives:

* Safety
* 
## Install

```text
❯ npm install -g typescript
❯ tsc --version
Version 3.9.5
```

TypeScript is **transpiled** to JavaScript and **then interpreted** by a browser.

tsconfig.json file:

```text
{
  "compilerOptions": { 
    "target": "es2018", 
    "outDir": "./dist", 
    "rootDir": "./src", 
    "module": "commonjs"
  } 
}
```

Assuming an `index.ts` file, to transpile to a `index.js` file:

```text
tsc
```

To run:

```text
node dist/index.js
```



Run transpiler in watch mode: `tsc -w`

