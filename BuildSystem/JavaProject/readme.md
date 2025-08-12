# Java Package Compilation Behavior

This example demonstrates how the **Java compiler (`javac`)** locates packages and how the folder from which you compile affects the result.

---

## 📂 Project Structure (Example)

```
JavaProject/
│
├── lib/
│   └── Utility.java
│
└── example/
    └── Main.java
```

---

## 📝 Key Concept

The Java compiler (`javac`) **can only look for classes and packages inside the current directory (compilation starting point) and its subdirectories** — it **cannot look outside or upward** from that starting point.

---

## 🔍 Case 1 – Compiling from the Root Folder

```bash
cd JavaProject
javac example/Main.java
```

**Process:**
1. It tries to find the `lib` package in the root folder (`JavaProject/lib`).
2. ✅ Found the `lib` package.
3. Compilation **succeeds**.

---

## 🔍 Case 2 – Compiling from Inside the `example` Package

```bash
cd JavaProject/example
javac Main.java
```

**Process:**
1. It tries to find the `lib` package relative to the current folder (`example/lib`).
2. ❌ No `lib` package found inside `example`.
3. Compilation **fails** due to missing package.

---

## 💡 Why This Happens

- `javac` starts searching for packages **relative to the current working directory**.
- It can **see sub-packages** (nested folders) but not packages **outside** or **above** the current directory.
- This is why you usually compile Java code from the **project root**, not from inside a package.

---

## ✅ Best Practice

- Compile from the **project root** unless you manually set the classpath.
- Example using the `-cp` (classpath) option:

```bash
cd JavaProject/example
javac -cp .. Main.java
```

---

## 📌 Summary Table

| Compilation From           | `lib` Package Found? | Result   |
|----------------------------|----------------------|----------|
| Root folder (`JavaProject`) | ✅ Yes               | ✅ Success |
| `example` folder           | ❌ No                | ❌ Fails  |

---
