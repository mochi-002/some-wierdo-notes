# 📝 OOP 2023 Final Exam — Answers

---
## Question 1: MCQ Answers

| #   | Answer | Answer                       |
| --- | ------ | ---------------------------- |
| 1   | A      | Encapsulation                |
| 2   | A      | Inheritance and Polymorphism |
| 3   | A      | .class                       |
| 4   | C      | Inheritance                  |
| 5   | C      | Method Overloading           |
| 6   | C      | All of them                  |
| 7   | C      | final                        |
| 8   | B      | `equals()`                   |
| 9   | B      | `class B implements A{}`     |
| 10  | B      | throw                        |

---
## Question 2: Code Output
``
### 1 ->(c)
```text
false
```

### 2 -> (c)
```text
Compilation erroe
```
### 3 -> (a)
```text
4
```
### 4 -> (d)
```text
None of them
```
### 5 -> (d)
```text
ACD
```
---
## Question 3

| #   | Output                                |
| --- | ------------------------------------- |
| a   | Animal speed is 30                    |
| b   | Animal speed is 30<br>Dog speed is 30 |
| c   | Animal is eating                      |
| d   | Dog is eating                         |
| e   | Animal is traviling                   |
| f   | Animal is traviling                   |

---
## Question 4
```java
public class TestApp {

    public interface CurrencyConvert {
        float fromEGP(float amount);
        float toEGP(float amount);
    }

    public class DollarCurrencyConverter implements CurrencyConvert {
        private float amount;

        public DollarCurrencyConverter(float amount) {
            this.amount = amount;
        }

        @Override
        public float fromEGP(float amount) {
            return amount / 19;
        }

        @Override
        public float toEGP(float amount) {
            return amount * 19;
        }

        public float getAmount() {
            return amount;
        }

        public void setAmount(float amount) {
            this.amount = amount;
        }
    }

    public class EuroCurrencyConverter implements CurrencyConvert {
        private float amount;

        public EuroCurrencyConverter(float amount) {
            this.amount = amount;
        }

        @Override
        public float fromEGP(float amount) {
            return amount / 20;
        }

        @Override
        public float toEGP(float amount) {
            return amount * 20;
        }

        public float getAmount() {
            return amount;
        }

        public void setAmount(float amount) {
            this.amount = amount;
        }
    }
}
```