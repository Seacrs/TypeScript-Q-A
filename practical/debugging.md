# TypeScript Practical Questions

## Q1
```tsx
type ID = string | number;

function getLength(id: ID) {
  return id.length;
}

getLength(123);
getLength("abc");
```
## Q2
```tsx
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
## Q3
```tsx
type Admin = { role: "admin"; permissions: string[] };
type Guest = { role: "guest"; sessionId: string };
type User = Admin | Guest;

function greet(user: User) {
  if (user.role === "admin") {
    console.log("Welcome admin, permissions:", user.sessionId);
  }
}
```
## Q4
```tsx
type Result = "pending" | "approved" | "rejected";

function evaluateScore(score: number): Result {
  if (score > 90) return "approved";
  if (score > 70) return "pending";
  return "denied"; 
}
```
## Q5
```tsx
type Value = string | null | undefined;

function logLength(value: Value) {
  if (value) {
    console.log(value.length);
  }
}
```

## Q6
```tsx
type ApiResponse = { success: true; data: string } | { success: false; error: string };

async function fetchData(id: number): Promise<ApiResponse> {
  const res = await fetch(`/api/data/${id}`);
  const json = await res.json();
  return json; 
}
```

## Q7
```tsx
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

## Q8
```tsx
type Action = 
  | { type: "ADD_TODO"; text: string }
  | { type: "TOGGLE_TODO"; id: number }
  | { type: "DELETE_TODO"; id: number };

const action = { type: "ADD_TODO", text: 123 } as Action; 
dispatch(action); 
```