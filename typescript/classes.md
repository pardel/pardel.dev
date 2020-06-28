---
description: Classes are templates that describe a data type.
---

# Classes

```typescript
export class TodoItem {
  public id: number;
  public task: string;
  public complete: boolean = false;

  public constructor(id: number, task: string, complete: boolean = false) { 
    this.id = id;
    this.task = task;
    this.complete = complete; 
  }

  public printDetails() : void { 
    console.log(`${this.id}\t${this.task} ${this.complete ? "\t(complete)": ""}`);
  }
}
```

**Shortcut** for defining properties and constructor:

```typescript
export class TodoItem {
 
  constructor(
    public id: number, 
    public task: string, 
    public complete: boolean = false) {
    // no statements required
  }

  public printDetails() : void { 
    console.log(`${this.id}\t${this.task} ${this.complete ? "\t(complete)": ""}`);
  }
}
```

Include other classes:

```typescript
import { TodoItem } from "./todoItem";

export class TodoCollection { 
  public todoItems: TodoItem[] = []
  ...
}
```

