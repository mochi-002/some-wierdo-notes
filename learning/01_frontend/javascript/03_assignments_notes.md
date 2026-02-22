## 📂 File Access in the Browser

JavaScript running in the browser cannot access files directly from the user's system. Instead, it relies on **user interaction** (like selecting a file via an `<input type="file">`).

### 🔹 Example: Reading a Text File

```javascript
document.getElementById("fileInput").addEventListener("change", (event) => {
  const file = event.target.files[0];
  if (!file) return;

  console.log("Selected file:", file.name);
  console.log("File size:", file.size, "bytes");
  console.log("File type:", file.type);

  const reader = new FileReader();
  reader.onload = () => {
    analyzeText(reader.result);
  };

  reader.readAsText(file);
});
```

### 🔹 Key Concepts

- `event.target.files[0]` → gets the selected file
- `FileReader` → used to read file contents
- `readAsText(file)` → reads file as plain text
- `reader.result` → contains file content after loading

---

## 🧩 String Functions

### `.split()`

Used to divide a string into an **array** based on a separator.

**Example:**

```javascript
const lines = text.split("\n");
```

- Splits the string using the newline character
- Each array element represents **one line**

---

### `.match()`

Used to search a string using a **regular expression (regex)**.

**Example:**

```javascript
const words = text.match(/\b\w+\b/g);
```

- Returns an array of matches
- Returns `null` if no match is found
- Often used for word counting, pattern detection, etc.

---

## 🔍 Regular Expressions (Regex)

Regex is a powerful way to **search, match, or extract patterns** from text.

### 🔹 Common Patterns

|Pattern|Meaning|
|---|---|
|`\n`|New line|
|`\w`|Any word character (a-z, A-Z, 0-9, _)|
|`\d`|Any digit|
|`+`|One or more|
|`*`|Zero or more|
|`\b`|Word boundary|

### 🔹 Example Use Cases

- Count words
- Find numbers
- Validate input
- Analyze text files

---

## `performance.now()`

> **Definition:** A high-resolution, monotonic timestamp used for measuring precise time intervals in JavaScript.

**1. Quick Syntax**
```javascript
const timestamp = performance.now(); 
// Example output: 1420.300000011921 (ms)
```

**2. Why use it?**

- **High Precision:** Accurate to the microsecond level (fractions of a millisecond).
- **Monotonic:** It only ever goes forward. It is **not** affected by system clock resets or daylight savings (unlike `Date.now()`).
- **Zero Point:** It starts at `0` when the page begins to load (`timeOrigin`).

**3. Common Use Case: Benchmarking**

Use it to measure how long a specific function takes to execute:
```javascript
const start = performance.now();

// Task to measure
for (let i = 0; i < 1000000; i++) { /* logic */ }

const end = performance.now();
console.log(`Execution time: ${(end - start).toFixed(4)} ms`);
```

**4. Comparison**

|Feature|`performance.now()`|`Date.now()`|
|---|---|---|
|**Accuracy**|Microseconds|Milliseconds|
|**Stability**|Guaranteed to increase|Can jump (Clock sync)|
|**Purpose**|Performance & Animation|Timestamps & Dates|

---