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
