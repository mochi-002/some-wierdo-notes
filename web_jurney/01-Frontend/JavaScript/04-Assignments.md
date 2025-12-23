## BOM
### [102 => 110](https://elzero.org/javascript-bootcamp-assignments-lesson-from-102-to-110/)
#### Assignment -> 01
```javascript
function printRange() {
	let numbers = window
	.prompt("Enter numbers to print From - To", "Example: 5-20")
	.split('-');
	
	for (let start = Math.min(numbers[0], numbers[1]); start <= Math.max(numbers[0], numbers[1]); start++) {
		console.log(start);
	}
}
```
---
#### Assignment -> 02
```HTML
<div class="popup-overlay" id="myPopup">
	<div class="popup-content">
		<button class="close-button" onclick="closePopup()">×</button>
		<h1>Welcome</h1>
		<p>Welcome To Elzero Web School</p>
	</div>
</div>
```

```CSS
.popup-overlay {
	background-color: #e8e8e8;
	border-radius: 8px;
	padding: 40px;
	max-width: 600px;
	width: 100%;
	position: relative;
	visibility: hidden;
}
  
.popup-content {
	background-color: #f0f0f0;
	border: 2px solid #d0d0d0;
	border-radius: 6px;
	padding: 60px 40px;
	text-align: center;
	position: relative;
}
  
.close-button {
	position: absolute;
	top: -15px;
	right: -15px;
	width: 35px;
	height: 35px;
	background-color: #ff0000;
	color: white;
	border: none;
	border-radius: 50%;
	font-size: 18px;
	font-weight: bold;
	cursor: pointer;
	display: flex;
	align-items: center;
	justify-content: center;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
	transition: background-color 0.3s;
}

.close-button:hover {
	background-color: #cc0000;
}

h1 {
	font-size: 32px;
	margin-bottom: 20px;
	color: #333;
}

p {
	font-size: 16px;
	color: #666;
}
```

```JavaScript
function openPopup(timeout) {
	let popup = document.getElementById("myPopup");
	setTimeout(() => {
	popup.style.visibility = 'visible';
	}, timeout);
}

function closePopup() {
	document.getElementById("myPopup").style.visibility = 'hidden';
}

```
---
#### Assignment -> 03
```JavaScript
function countDown(interval) {
	const div = document.getElementById("div");
	const timer = setInterval(() => {
		let value = Number(div.textContent);
		if (value <= 0) {
			div.textContent = "🔴 BOOM!";
			clearInterval(timer);
		return;
		}
		div.textContent = value - 1;
	}, interval);
	return timer;
}
```
---
#### Assignment -> 04
```JavaScript
function countDown(interval) {
	const div = document.getElementById("div");
	const timer = setInterval(() => {
		let value = Number(div.textContent);
		if (value <= 0) {
			div.textContent = "🔴 BOOM!";
			window.open(
				"https://elzero.org/",
				 "_blank"
			 );
			clearInterval(timer);
		return;
		}
		div.textContent = value - 1;
	}, interval);
	return timer;
}
```
---
#### Assignment -> 05
```HTML
<div class="div">
<p id="div">1</p>
</div>
```

```JavaScript
function countDown(interval) {
	const div = document.getElementById("div");
	const timer = setInterval(() => {
		let value = Number(div.textContent);
		if (value <= 0) {
			div.textContent = "🔴 BOOM!";
			window.open(
				"https://elzero.org/",
				"_blank",
				"width=200,height=200"
			);
			clearInterval(timer);
		return;
		}
		div.textContent = value - 1;
	}, interval);
	return timer;
}
```

---
### [111 => 114](https://elzero.org/javascript-bootcamp-assignments-lesson-from-111-to-114/)
#### Assignment -> 01
```HTML
<div class="container">
  <h2>Simple Selection</h2>

  <div class="select-container">
    <div class="select-wrapper">
      <label for="font-family-select">Font Family</label>
      <select id="font-family-select">
        <option value="" hidden>Choose...</option>
      </select>
    </div>

    <div class="select-wrapper">
      <label for="font-color-select">Font Color</label>
      <select id="font-color-select">
        <option value="" hidden>Choose...</option>
      </select>
    </div>

    <div class="select-wrapper">
      <label for="font-size-select">Font Size</label>
      <select id="font-size-select">
        <option value="" hidden>Choose...</option>
      </select>
    </div>
  </div>

  <div class="text-section">
    <p class="text">
      This is a clean and modern design featuring three select boxes arranged horizontally. The layout
      emphasizes simplicity and usability.
    </p>

    <p class="text">
      The aesthetic approach uses a gradient background with soft shadows and rounded corners to create a
      contemporary look. Each element is carefully spaced for optimal visual balance.
    </p>

    <p class="text">
      Feel free to customize the colors, fonts, and content to match your specific needs and preferences.
    </p>
  </div>
</div>
```

```JavaScript
const familyBox = document.getElementById('font-family-select');
const colorBox = document.getElementById('font-color-select');
const sizeBox   = document.getElementById('font-size-select');
const texts     = document.querySelectorAll('.text-section p');

// Populate font family options
const fontFamilies = [
  'Arial',
  'Verdana',
  'Georgia',
  'Times New Roman',
  'Courier New',
  'Comic Sans MS',
  'Impact',
  'Trebuchet MS'
];

fontFamilies.forEach(font => {
  const option = document.createElement('option');
  option.value = font;
  option.textContent = font;
  familyBox.appendChild(option);
});

// Populate font color options
const fontColors = [
  { name: 'Black',  value: '#000000' },
  { name: 'Red',    value: '#ff0000' },
  { name: 'Blue',   value: '#0000ff' },
  { name: 'Green',  value: '#008000' },
  { name: 'Purple', value: '#800080' },
  { name: 'Orange', value: '#ff8800' },
  { name: 'Pink',   value: '#ff69b4' },
  { name: 'Brown',  value: '#8b4513' }
];

fontColors.forEach(color => {
  const option = document.createElement('option');
  option.value = color.value;
  option.textContent = color.name;
  colorBox.appendChild(option);
});

// font sizes (16px → 30px)
for (let i = 16; i <= 30; i++) {
  const option = document.createElement('option');
  option.value = i;
  option.textContent = `${i} px`;
  sizeBox.appendChild(option);
}

// Load saved values from localStorage
if (localStorage.getItem('family')) {
  const savedFamily = localStorage.getItem('family');
  texts.forEach(text => text.style.fontFamily = savedFamily);
  familyBox.value = savedFamily;
}

if (localStorage.getItem('color')) {
  const savedColor = localStorage.getItem('color');
  texts.forEach(text => text.style.color = savedColor);
  colorBox.value = savedColor;
}

if (localStorage.getItem('size')) {
  const savedSize = localStorage.getItem('size');
  texts.forEach(text => text.style.fontSize = `${savedSize}px`);
  sizeBox.value = savedSize;
}

// Event listeners
familyBox.addEventListener('change', function() {
  texts.forEach(text => text.style.fontFamily = this.value);
  localStorage.setItem('family', this.value);
});

colorBox.addEventListener('change', function() {
  texts.forEach(text => text.style.color = this.value);
  localStorage.setItem('color', this.value);
});

sizeBox.addEventListener('change', function() {
  texts.forEach(text => text.style.fontSize = `${this.value}px`);
  localStorage.setItem('size', this.value);
});
```
#### Assignment -> 02
```HTML
<div class="form-container">
  <h2>Contact Form</h2>

  <div class="form-group">
    <label for="name">Full Name</label>
    <input type="text" id="name" placeholder="Enter your full name">
  </div>

  <div class="form-group">
    <label for="email">Email Address</label>
    <input type="email" id="email" placeholder="Enter your email">
  </div>

  <div class="form-group">
    <label for="phone">Phone Number</label>
    <input type="tel" id="phone" placeholder="Enter your phone number">
  </div>

  <div class="form-group">
    <label for="category">Select Category</label>
    <select id="category">
      <option value="" hidden>Choose a category...</option>
    </select>
  </div>

  <button class="submit-btn">Submit</button>
</div>
```

```JavaScript
const nameInput    = document.getElementById('name');
const emailInput   = document.getElementById('email');
const phoneInput   = document.getElementById('phone');
const categorySelect = document.getElementById('category');

const categories = [
  { name: 'General Inquiry',    value: 'General Inquiry' },
  { name: 'Technical Support',  value: 'Technical Support' },
  { name: 'Sales',              value: 'Sales' },
  { name: 'Feedback',           value: 'Feedback' },
  { name: 'Other',              value: 'Other' }
];

categories.forEach(cat => {
  const option = document.createElement('option');
  option.value = cat.value;
  option.textContent = cat.name;
  categorySelect.appendChild(option);
});

function loadFromSession(key, element) {
  const savedValue = sessionStorage.getItem(key);
  if (savedValue !== null) {
    element.value = savedValue;
  }
}

function saveToSession(key, element) {
  element.addEventListener('input', () => {
    sessionStorage.setItem(key, element.value.trim());
  });
}

loadFromSession('name', nameInput);
loadFromSession('email', emailInput);
loadFromSession('phone', phoneInput);
loadFromSession('category', categorySelect);

saveToSession('name', nameInput);
saveToSession('email', emailInput);
saveToSession('phone', phoneInput);
saveToSession('category', categorySelect);
```
---
## Destructuring & Spread
### [115 => 122](https://elzero.org/javascript-bootcamp-assignments-lesson-from-115-to-122/)
#### Assignment -> 01
#### Assignment -> 02
#### Assignment -> 03
#### Assignment -> 04
#### Assignment -> 05
#### Assignment -> 06