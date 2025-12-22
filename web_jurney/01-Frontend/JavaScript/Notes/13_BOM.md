# JavaScript – BOM (Browser Object Model)

## 1. What is BOM?

- **BOM** = Browser Object Model  
- Allows JavaScript to **talk to the browser** (outside of the page content = outside of DOM)
- The heart of BOM is the **`window`** object

### Window is the global object in browser environment

```javascript
window === this   // true (in global scope)

// All of these are the same:
window.alert()
alert()
this.alert()
```

**Window contains:**

- The **document** object (DOM)
- All global variables
- All global functions
- History, location, navigator, screen, etc.

## 2. Dialog Boxes

```javascript
alert("Message")                  // OK button only
confirm("Are you sure?")          // OK + Cancel → returns boolean
prompt("Enter your name:", "John") // returns string or null
```

```javascript
if (confirm("Delete item?")) {
  console.log("Item deleted");
} else {
  console.log("Cancelled");
}

let age = prompt("How old are you?", "18");
console.log(typeof age); // string or null
```

## 3. Timing Functions

### setTimeout – runs **once** after delay

```javascript
setTimeout(function () {
  console.log("Hello after 3 seconds");
}, 3000);

// With parameters
function greet(name, age) {
  console.log(`Hello ${name}, you are ${age}`);
}

setTimeout(greet, 2000, "Osama", 38);

// Storing ID to cancel later
const timeoutId = setTimeout(() => console.log("Never happens"), 1000);
clearTimeout(timeoutId);
```

### setInterval – runs **repeatedly**

```javascript
// Simple counter example
let counter = setInterval(() => {
  console.log("Tick");
}, 1000);

// Real countdown example
let div = document.querySelector("div");

function countdown() {
  div.textContent--;

  if (div.textContent === "0") {
    clearInterval(counter);
    div.textContent = "BOOM!";
  }
}

let counter = setInterval(countdown, 1000);
```

## 4. Location Object

Controls and gives information about current URL

```javascript
console.log(location.href);     // full URL
console.log(location.protocol); // http: or https:
console.log(location.host);     // domain + port
console.log(location.hostname);
console.log(location.pathname);
console.log(location.hash);     // #section
console.log(location.search);   // ?id=123&sort=desc

// Actions
location.reload();              // refresh page
location.replace("https://google.com");  // no history entry
location.assign("https://google.com");   // adds to history
location.href = "https://google.com";    // same as assign
```

## 5. Opening & Closing Windows

```javascript
// Open new window
window.open();                            // blank new tab
window.open("https://google.com");        // new tab
window.open("https://google.com", "_blank", "width=400,height=300,left=200,top=100");

// Special targets
window.open("...", "_self");      // current tab
window.open("...", "_parent");
window.open("...", "_top");

// Close current window (only works if opened by script)
window.close();
```

## 6. History Object

```javascript
history.length          // number of pages in history

history.back();         // ← previous page
history.forward();      // → next page
history.go(-2);         // 2 pages back
history.go(1);          // 1 page forward
history.go(0);          // refresh current page
```

**Advanced** (look later): `history.pushState()`, `history.replaceState()`

## 7. Other Useful Window Methods

```javascript
window.print();         // open print dialog
window.stop();          // stop page loading (rarely used)

window.focus();         // bring window to front (limited modern browsers)

// Scrolling
window.scrollTo(x, y);
window.scrollTo({ top: 500, left: 0, behavior: "smooth" });
window.scrollBy(0, 300);           // relative scroll
window.scrollBy({ top: 200, behavior: "smooth" });
```

## 8. Classic Practice: Scroll-To-Top Button

```javascript
const btn = document.querySelector(".scroll-to-top");

window.addEventListener("scroll", () => {
  if (window.scrollY >= 600) {
    btn.style.display = "block";
  } else {
    btn.style.display = "none";
  }
});

btn.onclick = () => {
  window.scrollTo({
    top: 0,
    left: 0,
    behavior: "smooth"
  });
};

// Useful properties
console.log(window.scrollY);      // same as pageYOffset
console.log(window.scrollX);      // same as pageXOffset
```
