# 📝 OOP 2024 Final Exam — Answers

---
## Question 1: MCQ Answers

| #   | Answer | Sentence                       | Exceplanition                                                                                                                    |
| --- | ------ | ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| 1   | A      | .class                         | Java source files (.java) are compiled into bytecode files with the .class extension.                                            |
| 2   | D      | All of them                    | Default methods must have a body, can be overridden, and are public by default. So all statements are correct.                   |
| 3   | B      | Via interfaces only            | Java does not support multiple inheritance of classes (to avoid diamond problem), but a class can implement multiple interfaces. |
| 4   | D      | public static final            | Fields in interfaces are implicitly public, static, and final.                                                                   |
| 5   | A      | Value                          | Java is always pass-by-value. For objects, the value of the reference is passed.                                                 |
| 6   | A      | Comparable                     | To enable sorting (e.g., in Collections.sort() or Arrays.sort()), a class should implement Comparable (or use a Comparator).     |
| 7   | C      | They extend RuntimeException   | Unchecked exceptions are subclasses of RuntimeException; they do not need to be declared or caught                               |
| 8   | B      | final                          | A final method cannot be overridden.                                                                                             |
| 9   | C      | .html                          | Javadoc tool generates HTML documentation files.                                                                                 |
| 10  | B      | abstract classes or interfaces | Abstract methods can be declared in both abstract classes and interfaces.                                                        |

---
## Question 2: Code Output
``
### 1 ->(b)
```text
2
```

### 2 -> (a)
```text
World
```
### 3 -> (a)
```text
CLASS B
```
### 4 -> (b)
```text
2
```
### 5 -> (d)
```text
B
```
---
## Question 3
```java
// Fix no.1
import java.util.Arrays;

public class TestApp {
	static class Time implements Comparable<Time> {
		int hour;
		int minute;
		
		public Time(int hour, int minute) {
			this.hour = hour;
			this.minute = minute;
		}
		
		// Fix no.2
		public int compareTo(Time other) {
			if (this.hour != other.hour) {
				return Integer.compare(this.hour, other.hour);
			}
			return Integer.compare(this.minute, other.minute);
		}
		
		// Fix no.3
		@Override
		public String toString() {
			return String.format("%02d:%02d", hour, minute);
			}
		}
	}
	public static void main(String[] args) {
		Time[] arr = new Time[2];
		arr[0] = new Time(12, 5);
		arr[1] = new Time(5, 5);
		Arrays.sort(arr);
		for (Time time : arr) {
			System.out.println(time.toString());
		}
	}
}
```

---
## Question 4
```java
public class TestApp {

    public interface Polygon {
        default float getPerimeter() {
            return -1.0f;
        }
    }

    public interface PolygonInfo {
        String getPolygonInfo();
    }

    class Triangle implements Polygon, PolygonInfo {
        private float side1, side2, side3;

        public Triangle(float side1, float side2, float side3) {
            this.side1 = side1;
            this.side2 = side2;
            this.side3 = side3;
        }

        @Override
        public float getPerimeter() {
            return side1 + side2 + side3;
        }

        @Override
        public String getPolygonInfo() {
            return "Triangle with sides " + side1 + ", " + side2 + ", " + side3
                    + ". Perimeter = " + getPerimeter();
        }
    }

    class Rectangle implements Polygon, PolygonInfo {
        private float length;
        private float width;

        public Rectangle(float length, float width) {
            this.length = length;
            this.width = width;
        }

        @Override
        public float getPerimeter() {
            return 2 * (length + width);
        }

        @Override
        public String getPolygonInfo() {
            return "Rectangle with length " + length + " and width " + width
                    + ". Perimeter = " + getPerimeter();
        }
    }
}
```