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
## 2
```
const scores: number[] = [95, "100", 87];
scores.push(82);
console.log(scores.reduce((a, b) => a + b));
```
### Solution

```bash
const scores: number[] = [95, "100", 87].map(Number);
scores.push(82);
console.log(scores.reduce((a, b) => a + b));
```
## 3
```
function printUser(user) {
  console.log(user.name.toUpperCase());
  console.log(user.age + 1);
}

printUser({ name: "Sara", age: "25" });
```
### Solution
```bash
type User={
    name: string
    age: string
}

function printUser(user: User): void {
    console.log(user.name.toUpperCase());
    console.log(Number(user.age) + 1);
}

printUser({ name: "Sara", age: "25" });
```
## 4
```
type ID = string | number;

function getLength(id: ID) {
  return id.length;
}

getLength(123);
getLength("abc");
```
### Solution
```bash
type ID = string | number;

function getLength(id: ID) {
    return String(id).length;
}

getLength(123);
getLength("abc");
```
## 5
```
type User = {
  id: number;
  name: string;
  isAdmin: boolean;
};

function getCurrentUser(): User {
  if (Math.random() > 0.5) {
    return { id: 1, name: "Alice", isAdmin: true };
  }
}
```
### Solution
```bash
type User = {
    id: number;
    name: string;
    isAdmin: boolean;
};

function getCurrentUser(): User | undefined{
    if (Math.random() > 0.5) {
        return { id: 1, name: "Alice", isAdmin: true };
    }
}
```
## 6
```
type Admin = { role: "admin"; permissions: string[] };
type Guest = { role: "guest"; sessionId: string };
type User = Admin | Guest;

function greet(user: User) {
  if (user.role === "admin") {
    console.log("Welcome admin, permissions:", user.sessionId);
  }
}
```
### Solution
```bash
type Admin = { role: "admin"; permissions: string[] };
type Guest = { role: "guest"; sessionId: string };
type User = Admin | Guest;

function greet(user: User) {
    if (user.role === "admin") {
        console.log("Welcome admin, permissions: ", user.permissions);
    }
}
```
## 7
```
type Result = "pending" | "approved" | "rejected";

function evaluateScore(score: number): Result {
  if (score > 90) return "approved";
  if (score > 70) return "pending";
  return "denied"; 
}
```
### Solution
```bash
type Result = "pending" | "approved" | "rejected";

function evaluateScore(score: number): Result {
    if (score > 90) return "approved";
    if (score > 70) return "pending";
    return "rejected"; 
}
```
## 8
```
type Value = string | null | undefined;

function logLength(value: Value) {
  if (value) {
    console.log(value.length);
  }
}
```
### Solution
```bash

```
## 9
```
type ApiResponse = { success: true; data: string } | { success: false; error: string };

async function fetchData(id: number): Promise<ApiResponse> {
  const res = await fetch(`/api/data/${id}`);
  const json = await res.json();
  return json; 
}
```
### Solution
```bash
type ApiResponse = { success: true; data: string } | { success: false; error: string };

async function fetchData(id: number): Promise<ApiResponse> {
    try{
        const res = await fetch(`/api/data/${id}`);
        if(!res.ok){
            throw new Error(`HTTP error! status: ${res.status}`);
        }
        const json = await res.json();
        return {
            success: true,
            data: json
        };
    }
    catch(err){
        return{
            success: false,
            error: err instanceof Error ? err.message : String(err)
        }
    }
}
```
## 10
```
type Profile = {
  name: string;
  settings?: {
    theme: "dark" | "light";
    notifications: boolean;
  };
};

const profiles: Profile[] = [
  { name: "Bob" },
  { name: "Carla", settings: { theme: "dark", notifications: true } }
];

profiles.forEach(p => {
  console.log(p.settings.theme.toUpperCase());
});
```
### Solution
```bash

```