# Types

## Explicit types:

```typescript
var foo: number = 123;

foo = '456';
/*  error TS2322: Type '"456"' is not assignable 
    to type 'number'. */
```

## Own types

```typescript
interface Coordinate {
  x: number;
  y: number;
}

var a: Coordinate = { x: 1, y: 10 }
```

