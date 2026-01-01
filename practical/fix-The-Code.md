# TypeScript Practical

## Q1
```TypeScript
function greet(name) {
  return "Hello " + name.toUpperCase();
}

const names = ["alice", "bob", 123];
names.forEach(greet);
```
## Q2
```TypeScript
const scores: number[] = [95, "100", 87];
scores.push(82);
console.log(scores.reduce((a, b) => a + b));
```
## Q3
```TypeScript
function printUser(user) {
  console.log(user.name.toUpperCase());
  console.log(user.age + 1);
}

printUser({ name: "Sara", age: "25" });
```