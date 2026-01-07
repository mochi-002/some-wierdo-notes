# Weekly Assignments
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
```JavaScript
let myNumbers = [1, 2, 3, 4, 5];
let [a, , , , e] = myNumbers
console.log(a * e);
```
#### Assignment -> 02
```JavaScript
let mySkills = ["HTML", "CSS", "JavaScript", ["PHP", "Python", ["Django", "Laravel"]]];
let [a, b, c, [d, e, [f, g]]] = mySkills
console.log(`My Skills: ${a}, ${b}, ${c}, ${d}, ${e}, ${f}, ${g}`);
```
#### Assignment -> 03
```JavaScript
let arr1 = ["Ahmed", "Sameh", "Sayed"];
let arr2 = ["Mohamed", "Gamal", "Amir"];
let arr3 = ["Haytham", "Shady", "Mahmoud"];

let [c, ,] = arr1;
let [, ,] = arr2
let [, a, b] = arr3

console.log(`My Best Friends: ${a}, ${b}, ${c}`);
```
#### Assignment -> 04
```JavaScript
const member = {
age: 30,
working: false,
country: "Egypt",
hobbies: ["Reading", "Swimming", "Programming"],
};
let { age: a, working: w, country: c, hobbies: [h1, , h3] } = member
console.log(`My Age Is ${a} And Iam ${w ? "" : "Not"} Working`);
console.log(`I Live in ${c}`);
console.log(`My Hobbies: ${h1} And ${h3}`);
```
#### Assignment -> 05
```javascript
const game = {
	title: "YS",
	developer: "Falcom",
	releases: {
		"Oath In Felghana": ["USA", "Japan"],
		"Ark Of Napishtim": {
			  US: "20 USD",
			  JAP: "10 USD",
		},
	    Origin: "30 USD",
	},
};

let {
	title: t,
	developer: d,
	releases: {
		["Oath In Felghana"]: [u, j],
		["Ark Of Napishtim"]: { US: u_price, JAP: j_price },
		Origin: or
	}
} = game
const [o, a] = ["Oath In Felghana", "Ark Of Napishtim"]

console.log(`My Favourite Games Style Is ${t} Style`);
console.log(`And I Love ${d} Games`);
console.log(`My Best Release Is ${o} It Released in ${u} & ${j}`);
console.log(`Although I Love ${a}`);
console.log(`${a} Price in USA Is ${u_price}`);
console.log(`${a} Price in Japan Is ${j_price}`);
console.log(`Origin Price Is ${or}`);
```
#### Assignment -> 06
```JavaScript
let chosen = 1;

let myFriends = [
	{ title: "Osama", age: 39, available: true, skills: ["HTML", "CSS"] },
	{ title: "Ahmed", age: 25, available: false, skills: ["Python", "Django"] },
	{ title: "Sayed", age: 33, available: true, skills: ["PHP", "Laravel"] },
];

for (chosen = 1; chosen <= myFriends.length; chosen++) {
	let {
		title: t,
		age: a,
		available: v,
		skills: [, sTwo]
	} = myFriends[chosen - 1];
	console.log(`${t}\n${a}\n${v ? "Available" : "Not Available"}\n${sTwo}`);
}
```
## Maps & Sets
### [123 => 133](https://elzero.org/javascript-bootcamp-assignments-lesson-from-123-to-133/)
#### Assignment -> 01
```JavaScript
let setOfNumbers = new Set([10]);
setOfNumbers.add(20).add(setOfNumbers.size);
console.log(setOfNumbers)
// make the set into array then access the last element
console.log([...setOfNumbers][setOfNumbers.size - 1])
```
#### Assignment -> 02
```JavaScript
let myFriends = ["Osama", "Ahmed", "Sayed", "Sayed", "Mahmoud", "Osama"];
console.log([...new Set(myFriends)].sort())
```
#### Assignment -> 03
```JavaScript
let myInfo = {
	username: "Osama",
	role: "Admin",
	country: "Egypt",
};
  
let myMap = new Map(
	Object.entries(myInfo).map(([key, value]) => [String(key), value])
);
console.log(myMap);
console.log(myMap.size);
console.log(myMap.has("role"));
```
#### Assignment -> 04
```JavaScript
let theNumber = 100020003000;

let res = Number(
	[...new Set(String(theNumber))]
		.filter((a) => a !== "0")
		.map((a) => Number(a))
		.join("")
);

console.log(res);
```
#### Assignment -> 05
```JavaScript
let theName = "Elzero";
console.log([...theName]);
console.log(theName.split(''))
console.log(Array.from(theName));
console.log([...new Set(theName)]);
console.log([...new Array(...theName)]);
```
#### Assignment -> 06
```JavaScript
```
#### Assignment -> 07
```JavaScript
let numsOne = [1, 2, 3];
let numsTwo = [4, 5, 6];

console.log([...numsOne, ...numsTwo])

console.log(numsOne.concat(numsTwo));

let mySet = new Set(numsOne)
	numsTwo.forEach(element => {
	mySet.add(element)
});
console.log([...mySet])
```
#### Assignment -> 08
```JavaScript
console.log(210);
```
---
## Regular Expression
### [134 => 146](https://elzero.org/javascript-bootcamp-assignments-lesson-from-134-to-146/)
#### Assignment -> 01
```JavaScript
let reg = /\d{4}:\w{2}\d:(\d{4}:*){6}/ig
```
#### Assignment -> 02
```JavaScript
let reg = /\bOs\d*O\b/g;
```
#### Assignment -> 03
```JavaScript
const phoneRe = /\+\(\d{3}\)-\d{3}\s\(\d{4}\)/ig;
```
#### Assignment -> 04
```JavaScript
let re = /https?:\/\/(?:[-\w]+\.)?([-\w]+)\.\w+(?:\.\w+)?\/?.*/i;
/*
	* https? -> it can has s after http or not
	* :\/\/ -> contains ://
	* (?:[-\w]+\.)? -> may have subdomain or not (www. mail.)
	* ([-\w]+) -> has one or more characters (domain name)
	* /. -> has a dot
	* \w+ -> has one or more character (com org net)
	* (?:\.\w+)? -> may have another --> (.eg .uk)
	* /\/? -> may have \ after the domain
	* .* -> doesn't contain or contains . (one or more)
	* /i -> case-insensitive
*/
```
#### Assignment -> 05
```JavaScript
let re = /\d+\s?\-?\s?\/?\d+\s?\-?\s?\/?\d+/;
```
#### Assignment -> 06
```JavaScript
let re = /(https?:\/\/)?([-\w]+\.)?([-\w]+)\.\w+(?:\.\w+)?\/?.*/gi;
```
---
## OOP
### [147 => 158](https://elzero.org/javascript-bootcamp-assignments-lesson-from-147-to-158/)
#### Assignment 01
```js
class Car {
  constructor(name, model, price) {
    this.name  = name;
    this.model = model;
    this.price = price;
  }

  run() {
    console.log("Car Is Running Now");
  }

  stop() {
    console.log("Car Is Stopped");
  }
}

const car1 = new Car("MG", 2022, 420000);
const car2 = new Car("MG", 2022, 420000);
const car3 = new Car("MG", 2022, 420000);

console.log(
  `Car One Name Is ${car1.name} And Model Is ${car1.model} And Price Is ${car1.price}`
);
```

#### Assignment 02
```js
class Tablet extends Phone {
  constructor(name, serial, price, size) {
    super(name, serial, price);
    this.size = size || "Unknown";
  }

  fullDetails() {
    return `${this.name} -> serial is ${this.serial}, price is ${this.price} and size is ${this.size}`;
  }
}
```

#### Assignment 03
```js
class User {
  #card;

  constructor(username, card) {
    this.username = username;
    this.#card = this.#formatCard(card);
    this.showData = `Hello ${this.username} Your Credit Card Number Is ${this.getCard()}`;
  }

  #formatCard(card) {
    return String(card)
      .replace(/\D/g, "")
      .match(/.{1,4}/g)
      ?.join("-") || "";
  }

  getCard() {
    return this.#card;
  }
}
```

#### Assignment 04
```js
String.prototype.addLove = function() {
  return `I Love ${this} Web School`;
};
```

#### Assignment 05 
```js
Object.defineProperties(myObj, {
  score: {
    value: 1000,
    writable: false,   
    enumerable: true,
    configurable: false
  },
  
  id: {
    enumerable: false,  
    configurable: false
  },
  
  country: {
    enumerable: false,  
    configurable: true  
  }
});

delete myObj.country;
```

---
## Date, Generators, Modules
### [159 => 168](https://elzero.org/javascript-bootcamp-assignments-lesson-from-159-to-168/)
#### Assignment 01
```js
const birthDate = new Date(2006, 5, 4);
const now = new Date();

const diffMs = now - birthDate;

const time = {
  seconds: Math.floor(diffMs / 1000),
  minutes: Math.floor(diffMs / (1000 * 60)),
  hours:   Math.floor(diffMs / (1000 * 60 * 60)),
  days:    Math.floor(diffMs / (1000 * 60 * 60 * 24)),
};

function diffInYearsAndMonths(start, end) {
  let years = end.getFullYear() - start.getFullYear();
  let months = end.getMonth() - start.getMonth();
  let days = end.getDate() - start.getDate();

  if (days < 0) months--;
  if (months < 0) {
    years--;
    months += 12;
  }

  return { years, months };
}

const { years, months } = diffInYearsAndMonths(birthDate, now);

console.log(`Seconds: ${time.seconds}`);
console.log(`Minutes: ${time.minutes}`);
console.log(`Hours:   ${time.hours}`);
console.log(`Days:    ${time.days}`);
console.log(`Months:  ${years * 12 + months}`);
console.log(`Years:   ${years}`);

```
#### Assignment 02
```js
const now = new Date(0);
const next10Years = new Date(now);

next10Years.setFullYear(now.getFullYear() + 10);
next10Years.setHours(0);
next10Years.setMinutes(0);
next10Years.setSeconds(1);

console.log(next10Years);
```
#### Assignment 03
```js
const now = new Date();
const lastMonth = new Date(now.getFullYear(), now.getMonth(), 0);
console.log(lastMonth)
const monthName = lastMonth.toLocaleDateString("en-US", {month : "long"});
console.log(
	`Previous Month Is ${monthName} And Last Day Is ${lastMonth.getDate()}`
);
```
#### Assignment 04
```js
const birth1 = new Date("2006-06-04T10:30:15");
const birth2 = new Date(2006, 5, 4, 10, 30, 15);
const birth3 = new Date();

birth3.setFullYear(2006);
birth3.setMonth(5);
birth3.setDate(4);
birth3.setHours(10);
birth3.setMinutes(30);
birth3.setSeconds(15);
birth3.setMilliseconds(0);
```
#### Assignment 05
```js
const start = performance.now();
for (let num = 0; num < 99999; num++) {
	console.log(num);
}
const end = performance.now();
console.log(`Execution time: ${(end - start)} ms`);
```
#### Assignment 06
```js
function* gen() {
	let value = 14;
	let step = 140;
	
	while (true) {
		yield value;
		value += step;
		step += 200;
	}
}
```
#### Assignment 07
```js
function* genAll() {
	yield* [...new Set(genNumbers())];
	yield* [...new Set(genLetters())];
}
```
#### Assignment 08
>mod-one.js
```js
export default function (x, y, z) {
	return x + y + z;
}
```
>mod-two.js
```js
let a = 10, b = 20, c = 30;
export const numOne = a;
export const numTwo = b;
export const numThree = c;
```
>main.js
```js
import calc from "./mod-one.js";
import * as modOne from "./mod-two.js";
console.log(calc(modOne.numOne, modOne.numTwo, modOne.numThree)); // 60
```

---
## AJAX And JSON
### [169 => 178](https://elzero.org/javascript-bootcamp-assignments-lesson-from-169-to-178/)
#### Assignment 01
```js
[
  {
    "id": 1,
    "title": "Title 1",
    "body": "Article Number 1 Body",
    "category": "All",
    "author": "Ali"
  },
  {
    "id": 2,
    "title": "Title 2",
    "body": "Article Number 2 Body",
    "category": "All",
    "author": "Mahmoud"
  },
  {
    "id": 3,
    "title": "Title 3",
    "body": "Article Number 3 Body",
    "category": "All",
    "author": "Osama"
  },
  {
    "id": 4,
    "title": "Title 4",
    "body": "Article Number 4 Body",
    "category": "All",
    "author": "Sayed"
  },
  {
    "id": 5,
    "title": "Title 5",
    "body": "Article Number 5 Body",
    "category": "All",
    "author": "Ahmed"
  }
]
```
#### Assignment 02
```js
let xhr = new XMLHttpRequest();
xhr.open("GET", "assets/data/data.json");

xhr.onreadystatechange = function () {
  if (this.readyState === 4 && this.status === 200) {
    console.log("Data Loaded");
  }
};

console.log(xhr);
xhr.send();
```
#### Assignment 03
```js
let xhr = new XMLHttpRequest();
xhr.open("GET", "assets/data/data.json");
xhr.send();

xhr.onreadystatechange = function () {
  if (this.readyState === 4 && this.status === 200) {
    console.log("Data Loaded");
    let mainData = JSON.parse(xhr.responseText);
    console.log(mainData);
  }
};

xhr.onload = function () {
  if (xhr.status === 200) {
    let data = JSON.parse(xhr.responseText);
    console.log("Length:", data.length);

    data.forEach((item, index) => {
      item.category = "notAll";
      console.log(index, item.category);
    });

    let updatedData = JSON.stringify(data);
    console.log(updatedData);
  }
};
```
#### Assignment 04
```js
xhr.onreadystatechange = function () {
  if (this.readyState === 4 && this.status === 200) {
    console.log("Data Loaded");
    let mainData = JSON.parse(xhr.responseText);
    const htmlDiv = document.getElementById("data");

    mainData.forEach((item) => {
      const div = document.createElement("div");
      div.innerHTML = `
        <h2>${item.title}</h2>
        <p>${item.body}</p>
        <p>Author: ${item.author}</p>
        <p>Category: ${item.category}</p>
      `;
      htmlDiv.appendChild(div);
    });
  }
};
```

---
## Promises
### [179 => 188](https://elzero.org/javascript-bootcamp-assignments-lesson-from-179-to-188/)
#### Assignment 01
```js

```
#### Assignment 02
```js

```

---
