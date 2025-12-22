## BOM
### 102 => 110
#### Asignment -> 01
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
#### Asignment -> 02
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
#### Asignment -> 03
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
#### Asignment -> 04
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
#### Asignment -> 05
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