# Dart OOP Assignment: Kigali Bus Card

**Name:** Ahmed Elsiddig  
**Student ID:** 26034

---

## My Numbers

- D = 34
- L = 4
- Starting balance = 1000 + (34 × 10) = **1340 RWF**
- Bus fare = 200 + 34 = **234 RWF**
- Student discount = 10 + 4 = **14%**

---

## Part 1, 2 and 3: BusCard and StudentCard

### Output of main.dart

```text
Error: name too short
Owner: Ama | Balance: 1340 RWF
Owner: Ahmed Elsiddig | Balance: 1340 RWF
Error: top-up must be 500 to 50000 RWF
Topped up 2000 RWF
Paid 234 RWF
Paid 234 RWF
Owner: Ahmed Elsiddig | Balance: 2872 RWF
Student discount: 32 RWF
Paid 202 RWF
Owner: Ahmed Elsiddig | Balance: 1138 RWF
Student card: 14% off
```

### How the Numbers Work

1. Starting balance: 1340 RWF.
2. After top-up: 1340 + 2000 = 3340 RWF.
3. After two bus fares: 3340 - 234 - 234 = 2872 RWF.
4. Student discount: 234 × 14 ~/ 100 = 32 RWF.
5. Student fare: 234 - 32 = 202 RWF.
6. Student balance: 1340 - 202 = 1138 RWF.

### Why Is There No Setter for Balance?

The balance should only change through the `topUp()` and `pay()` methods. This ensures that the top-up limit and sufficient-balance rules are enforced.

A setter would allow someone to assign an arbitrary balance directly, which could cause incorrect values.

### What Does `~/` Do?

`~/` is integer division. It divides two numbers and removes the decimal part.

Example:

```dart
print(237 * 17 / 100);
```

Output:

```text
40.29
```

Using integer division:

```dart
print(237 * 17 ~/ 100);
```

Output:

```text
40
```

---

## Part 4: Bug Hunt

### Bug Table

| Bug | Original code | Why it is wrong | Fix |
|---|---|---|---|
| 1 | `String _brand;` and `int _battery;` | Non-nullable fields have no initial values. | Initialize them with `String _brand = '';` and `int _battery = 0;`. |
| 2 | SmartPhone constructor without parent initializer | Parent constructor parameters are not passed. | Add `: super(brand, battery)`. |
| 3 | `@override void restart()` | The parent class does not have a restart method. | Add `restart()` to the Phone class. |
| 4 | `p.battery = 100;` | There is no battery setter. | Add a setter accepting values from 0 to 100. |
| 5 | `print(p.battery());` | Battery is a getter, not a method. | Use `print(p.battery);`. |

### Not a Bug

```dart
Phone p = new Phone('Tecno', 50);
```

The `new` keyword is valid Dart syntax. It is optional, so it can be removed, but it is not an error.

### Fixed Program Output

```text
100
```

---

## Part 5: Bag and BigBag

### My Prediction

```text
1
5
```

### Real Output

```text
1
5
```

### Was My Prediction Correct?

Yes, my prediction was correct.

The first Bag becomes 1 after calling `add()`.

The setter rejects the value -5, so the value remains 1.

For BigBag, each `add()` call executes the parent `add()` method twice. Two calls produce 4, and adding 1 produces 5.

---

## How to Run the Programs

### Run the Main Assignment

```bash
dart run main.dart
```

### Run the Bug Hunt Program

```bash
dart run bug_hunt.dart
```

### Analyze the Dart Files

```bash
dart analyze main.dart bug_hunt.dart
```

Expected analysis result:

```text
No issues found!
```

---

## GitHub Repository

**Repository name:** `dart-oop-26034`

**GitHub username:** `elsiddiga63-ai`

**Repository URL:** https://github.com/elsiddiga63-ai/dart-oop-26034

The assignment requires five separate commits:

1. `Part 1: BusCard`
2. `Part 2 and 3: StudentCard and main`
3. `Part 4: bug hunt fixed`
4. `Part 5: prediction`
5. `Part 5: real output and README`

The Part 5 prediction should be committed before running the Bag and BigBag program, followed by a separate commit containing the real output.

The repository should be private, and the lecturer should be added as a collaborator.

---

## Final Testing Results

The assignment programs were tested successfully.

- Main program: Passed.
- Bug hunt program: Passed.
- Dart analyzer: No issues found.
- Main program calculations: Verified.
- Student discount: 14%.
- Final regular card balance: 2872 RWF.
- Final student card balance: 1138 RWF.

All assignment files are included in this repository.

---

**Student:** Ahmed Elsiddig  
**Student ID:** 26034  
**Course Assignment:** Dart OOP – Kigali Bus Card
