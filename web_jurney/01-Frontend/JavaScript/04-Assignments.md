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