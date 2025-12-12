# Mental Model Practical Questions(12-12-2025)
### The following code snippets have TypeScript errors. Fix the code without changing the core implementation of the functions until it compiles AND runs correctly (no any, no @ts-ignore allowed unless explicitly permitted). 

## 1
```
function greet(name) {
  return "Hello " + name.toUpperCase();
}

const names = ["alice", "bob", 123];
names.forEach(greet);
```

### Solution

```bash
function greet(name: string): string{
    return "Hello " + name.toUpperCase();
}
const names = ["alice", "bob", 123];

names.forEach(el =>{
    if(typeof el !== "string"){
        return `Invalid type`;
    }
    greet(el)
});
```