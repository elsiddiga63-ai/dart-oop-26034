# Dart OOP Assignment: Kigali Bus Card

**Name:** Ahmed Elsiddig  
**Student ID:** 26034

## My numbers

- D = 34, L = 4
- Starting balance = 1340 RWF
- Bus fare = 234 RWF
- Student discount = 14%

## Output of main.dart

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

### How the numbers work

After top-up: 1340 + 2000 = 3340 RWF.  
After two fares: 3340 - 234 - 234 = 2872 RWF.  
Student discount: 234 * 14 ~/ 100 = 32 RWF.  
Student fare: 234 - 32 = 202 RWF.  
Student balance: 1340 - 202 = 1138 RWF.

## Part 1: Why no setter for balance?

The balance should only change through `topUp()` and `pay()`. This ensures the top-up limit and sufficient-balance rules are enforced. A setter would allow someone to assign an arbitrary balance directly.

## Part 2: What does ~/ do?

`~/` is integer division. It divides and removes the decimal part.

- `print(237 * 17 / 100);` prints `40.29`.
- `print(237 * 17 ~/ 100);` prints `40`.

## Part 4: Bug table

| Bug | The line | Why it is wrong | Your fix |
|---|---|---|---|
| 1 | `String _brand;` and `int _battery;` | Non-nullable fields have no initial values. | Initialize them with `String _brand = '';` and `int _battery = 0;`. |
| 2 | SmartPhone constructor without a parent initializer | The parent `Phone` fields are not initialized. | Add `: super(brand, battery)`. |
| 3 | `@override void restart()` | The parent class has no `restart()` method. | Add `restart()` to `Phone`. |
| 4 | `p.battery = 100;` | There is no battery setter. | Add a setter accepting values from 0 to 100. |
| 5 | `print(p.battery());` | `battery` is a getter, not a method. | Use `print(p.battery);`. |
| Not a bug | `Phone p = new Phone('Tecno', 50);` | `new` is optional but valid Dart syntax. | No fix. |

The fixed bug-hunt program prints `100`.

## Part 5: Predict the output

### My prediction

```text
1
5
```

### Real output

```text
1
5
```

### Was I right?

Yes. The first Bag becomes 1 after `add()`. The setter rejects -5, so it remains 1. For BigBag, each `add()` calls the parent `add()` twice. Two calls produce 4, then adding 1 gives 5.

## Git commit sequence

Commit each part separately. For Part 5, commit the prediction before running the code, then add the real output and commit again.

```bash
git init
git add .
git commit -m "Part 1: BusCard"
git branch -M main
git remote add origin https://github.com/<your-username>/dart-oop-26034.git
git push -u origin main

git add .
git commit -m "Part 2 and 3: StudentCard and main"
git push

git add .
git commit -m "Part 4: bug hunt fixed"
git push

# Commit this prediction before running Part 5
git add .
git commit -m "Part 5: prediction"
git push

# After running Part 5 and adding its real output
git add .
git commit -m "Part 5: real output and README"
git push
```

Create the repository as private and add your lecturer as a collaborator.
