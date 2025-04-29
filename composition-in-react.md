
# Composition in React

## ✅ What is Composition?

**Composition** in React means:  
> **Combining multiple smaller components** together to build a **larger, more complex component**.

Instead of writing everything inside one big component, you **split your UI into small, manageable pieces** and then **assemble them together like Lego blocks**.

---

## 🧠 Why is Composition important?

- Your code becomes cleaner and easier to understand.
- Components are easier to test and refactor.
- You increase **reusability** across your project.
- It prevents your code from becoming "spaghetti code" 🍝.

---

## 🔥 Simple Example of Composition

Imagine you want to create a user's profile card.

Instead of putting everything into one file, you can split it:

```tsx
// Avatar.tsx
export function Avatar({ src, alt }: { src: string; alt: string }) {
  return <img src={src} alt={alt} className="rounded-full w-16 h-16" />;
}

// UserInfo.tsx
export function UserInfo({ name, email }: { name: string; email: string }) {
  return (
    <div>
      <h2 className="font-bold">{name}</h2>
      <p className="text-gray-500">{email}</p>
    </div>
  );
}

// ProfileCard.tsx
import { Avatar } from './Avatar';
import { UserInfo } from './UserInfo';

export function ProfileCard() {
  return (
    <div className="flex items-center space-x-4 p-4 border rounded">
      <Avatar src="/avatar.png" alt="User Avatar" />
      <UserInfo name="Kasra" email="kasra@example.com" />
    </div>
  );
}
```

✅ Here, **ProfileCard** is composed of **Avatar** and **UserInfo** components.

---

## ✨ Composition Using `children`

You can also compose components dynamically using the `children` prop:

```tsx
// Card.tsx
export function Card({ children }: { children: React.ReactNode }) {
  return (
    <div className="border p-4 rounded-lg shadow">
      {children}
    </div>
  );
}
```

Usage:

```tsx
<Card>
  <h1>Hello</h1>
  <p>This is a card</p>
</Card>
```

The **Card** component doesn’t care about its content — it simply displays whatever is passed inside it.  
**This is also a form of Composition.**

---

## 🎯 Quick Comparison

| Approach | Description |
|:---|:---|
| Props | Passing smaller, defined components like Avatar, UserInfo |
| Children | Passing dynamic content inside a component |
| Compound Components | (Advanced) Multiple components work together under a parent component |

---

## 🚀 In Short:

> **Composition** is about building complex UIs by **combining small, reusable pieces together**.

---
