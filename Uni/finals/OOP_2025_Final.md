# 📝 OOP 2025 Final Exam — Answers

---
## Question 1: MCQ Answers

| #   | Answer | Answer                 |
| --- | ------ | ---------------------- |
| 1   | D      | Private members        |
| 2   | D      | `toString()`           |
| 3   | C      | `equals()`             |
| 4   | B      | Overridable by default |
| 5   | A      | Value                  |
| 6   | A      | `final`                |
| 7   | A      | They must be checked   |
| 8   | D      | `long`                 |
| 9   | D      | Both A and B           |
| 10  | D      | `finally`              |

---
## Question 2: Code Output

### 1 -> (a)
```text
From Super Class
```

### 2 -> (b)
```text
4
```
### 3 -> (b)
```text
false
```
### 4 -> (d)
```text
Exception is caught
```
### 5 -> (c)
```text
0
```
---
## Question 3
```java
// fix no.1
import java.util.ArrayList;

// fix no.2
@Override
public boolean equals(Object obj) {
	Student otherStudent = (student) obj;
	if(this.id == otherStudent.id) { 
		return true;
	}
	return false;
}
```
---
## Question 4

```java
public class TestApp {

    public interface Movable {
        void moveUp();
        void moveRight();
    }

    public class Point {
        private int x;
        private int y;

        public Point(int x, int y) {
            this.x = x;
            this.y = y;
        }

        public int getX() {
            return x;
        }

        public void setX(int x) {
            this.x = x;
        }

        public int getY() {
            return y;
        }

        public void setY(int y) {
            this.y = y;
        }
    }

    public class MovableRectangle implements Movable {
        private Point upperLeft;
        private Point lowerRight;
        private int xShift = 0, yShift = 0;

        public MovableRectangle(Point lowerRight, Point upperLeft) {
            this.lowerRight = lowerRight;
            this.upperLeft = upperLeft;
        }

        public Point getLowerRight() {
            return lowerRight;
        }

        public void setLowerRight(Point lowerRight) {
            this.lowerRight = lowerRight;
        }

        public Point getUpperLeft() {
            return upperLeft;
        }

        public void setUpperLeft(Point upperLeft) {
            this.upperLeft = upperLeft;
        }

        public int getxShift() {
            return xShift;
        }

        public int getyShift() {
            return yShift;
        }

        public void updatexShift(int xShift) {
            this.xShift += xShift;
        }

        public void updateyShift(int yShift) {
            this.yShift += yShift;
        }

        @Override
        public void moveUp() {
            this.updateyShift(1);
        }

        @Override
        public void moveRight() {
            this.updatexShift(1);
        }
    }
}
---