
# `<script type="speculationrules">` in Next.js

## 🔍 What is `<script type="speculationrules">`?

The `<script type="speculationrules">` tag allows you to give **hints to the browser** about which pages might be navigated to next, so the browser can **preload or prerender them in advance**. This can significantly improve perceived performance and navigation speed.

It's a part of the **Speculation Rules API**, which is currently supported in **Chromium-based browsers** (like Chrome and Edge).

---

## 🚀 Purpose

To help browsers **predict user navigation** and **prerender** or **preload** the next page **before the user clicks a link** — so transitions between pages feel instantaneous.

---

## 📦 Types of Speculation

### 1. `prerender`
Loads the **entire page** in the background, including running JS and fetching data, so it can be displayed instantly.

### 2. `prefetch`
Only fetches the page's static assets (like HTML/CSS/JS) — no execution. It's lighter than prerendering.

---

## 🧱 Basic Structure

```html
<script type="speculationrules">
{
  "prerender": [
    {
      "source": "list",
      "urls": ["/about", "/contact"]
    }
  ]
}
</script>
```

---

## 🔤 Key Options

| Key     | Description |
|---------|-------------|
| `type="speculationrules"` | Tells the browser this script is for navigation speculation rules. |
| `source: "list"` | Manually provide a list of URLs to prerender. |
| `source: "document"` | Let the browser analyze the document and links. |
| `href_matches` | A regex-like pattern to match URLs (only with `document` source). |

---

## ✅ Example for `document` source

This tells the browser to prerender any link that matches `/products/...`:

```json
{
  "prerender": [
    {
      "source": "document",
      "where": {
        "href_matches": "/products/.*"
      }
    }
  ]
}
```

---

## 🧩 Using it in Next.js (App Router)

In Next.js App Router, you should inject the `<script>` tag in your `layout.tsx` (or `layout.jsx`) like this:

### Example:

```tsx
// app/layout.tsx

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="en">
      <head>
        <script
          type="speculationrules"
          dangerouslySetInnerHTML={{
            __html: JSON.stringify({
              prerender: [
                {
                  source: "document",
                  where: {
                    href_matches: "/pets/.*",
                  },
                },
              ],
            }),
          }}
        />
      </head>
      <body>{children}</body>
    </html>
  );
}
```

---

## ⚠️ Important Notes

- The browser makes the final decision — these are just **hints**, not hard rules.
- `dangerouslySetInnerHTML` is necessary in Next.js to include raw JSON inside a `<script>` tag.
- Be cautious with pages that have **side effects** (e.g., analytics or API calls) — you don't want those triggered just because the browser prerendered the page.

---

## 🔒 Security Considerations

- Don't prerender pages that make sensitive API calls or assume authenticated sessions unless you’re handling those safely.
- Ensure server-rendered content doesn’t perform destructive actions when merely **rendered**.

---

## 🌐 Browser Support

| Browser | Support |
|---------|---------|
| Chrome | ✅ Yes (v96+) |
| Edge   | ✅ Yes |
| Safari | ❌ No |
| Firefox | ❌ No |

---

## 🧠 Summary

- **What it does:** Helps browsers predict and preload pages.
- **Why it's useful:** Makes navigation super fast and seamless.
- **Where to use:** In the `<head>` of your app — ideal for frameworks like **Next.js**.
- **How to write:** Use JSON inside a `<script type="speculationrules">`.

---

Let me know if you want a reusable component or hook to generate these rules dynamically in Next.js.
