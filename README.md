# Variables 1: Name the Slot, Not the Value

**Time:** 60 minutes

**Files in this repo**

| File                      | Used in            |
| ------------------------- | ------------------ |
| `receipts.py`             | Parts 1–3          |
| `bagel_trace.py`          | Part 3, exercise 3 |
| `laundromat.py` (empty)   | Part 4             |
| `bus_schedule.py` (empty) | Independent Check  |

## How this activity works

You'll predict what code does, run it, figure out why, change it, and then build something of your own. Wrong predictions are expected. They show you exactly which idea to look at next.

### When you're stuck

Raise your hand when either of these is true:

- You've been stuck on one step for **5 minutes**, or
- You've tried **two different things** and neither worked.

Look for the 🙋 symbol in this guide. It marks the places where fellows most often get stuck, and asking for help there is the right move.

**When you ask for help, come with:**

1. The line of code you're stuck on
2. What you predicted
3. What actually happened
4. What you've tried so far

Engineers ask for help this way every day. Writing it down often helps you find the answer yourself.

The ✅ symbol marks a checkpoint where you show an instructor your work before moving on.

---

## The big ideas (come back to this table)

| #   | Idea                                                                                                                                       | Try it in the REPL                                                              |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------- |
| 1   | Text typed directly into a string never changes. Only the parts that come from names or expressions change.                                | `latte = 12`, `f"lattes cost ${latte}"`, `latte = 4`, `f"lattes cost ${latte}"` |
| 2   | Python doesn't read meaning into names. A name holds whatever was assigned to it.                                                          | `tea = "coffee"`, `tea`                                                         |
| 3   | A program only uses the names it actually refers to.                                                                                       | `price = 4`, `latte = 12`, `f"${latte}"`                                        |
| 4   | Two programs can print the same thing for one set of values and different things for another. One run can't prove a program is right.      | `quantity = 2`, `quantity * 12`, `24`, then `quantity = 3` and try both again   |
| 5   | A program can pause and get a value from the person running it. The code can only refer to that value by its name.                         | `item_name = input("Item: ")`, type something, then `item_name`                 |
| 6   | An expression inside `{}` in an f-string is worked out when that line runs.                                                                | `price = 4`, `quantity = 3`, `f"${price * quantity}"`                           |
| 7   | Referencing a variable evaluates to the value held in that variable at that time. Reassigning it later does not affect earlier references. | `price = 4`, `print(price)`, `price = 10`                                       |
| 8   | When possible, generalize variables to avoid having multiple variables that share the same subject                                         | `tea_price = 4` and `latte_price = 12` -> `price = 10`                          |

## Habits for today

**Coding habit:** Anything that would change for a different case (a different order, customer, or day) gets a name, and your message uses the name, not the value typed out. Name the slot by its role (`item_name`), not by what's in it today (`latte`). Test with a second case before you call it done.

**Working habit: Name a value by what it holds.**

- Before naming a value, say in plain words what it holds ("the price of one ticket"), then turn those words into the name (`ticket_price`).
- Avoid placeholder names (`x`, `num`, `thing`) and names that describe the math rather than the meaning (`a_times_b`).
- A name is clear when someone else can say what it holds without running the code.

---

## Part 1: Predict & Run (10 minutes)

Open `receipts.py`. It has an order at the top and three programs that each print a receipt line for it. **Don't run it yet.**

1. Fill in the data types comment and each `# Prediction (latte order):` line.
2. Run `python3 receipts.py`.
3. Change **only the three order lines at the top** to:
   ```python
   item_name = "tea"
   quantity = 3
   price = 4
   ```
4. Fill in each `# Prediction (tea order):` line, then run it again and fill in `# Actual (tea order):` and `# Explanation:`. Use the big ideas table.

Answer these as comments at the bottom of `receipts.py`:

1. What are the data types of `item_name`, `quantity`, `price`, and `latte`?
2. For the latte order, did all three programs print the same thing? Which would you trust?
3. For the tea order, which programs were right? For each wrong one, which part of the message didn't change, and why?

**Swap with a partner.** Read each other's answers to the three questions and compare.

🙋 **Ask for help if:** you and your partner can't agree on the right answer to any question.

---

## Part 2: Investigate (10 minutes)

Open the REPL (`python3`). Predict each result before you press Enter.

```
latte = 12
f"lattes cost ${latte}"
latte = 4
f"lattes cost ${latte}"
tea = "coffee"
tea
```

Write down: what changed when `latte` changed, and what didn't?

✅ **Checkpoint:** Tell an instructor, in one sentence, why Program B looked right for the latte order but wasn't.

---

## Part 3: Modify (13 minutes)

Keep the tea order in `receipts.py`.

### 1. Fix the error

Change **only Program B's `print()` line** so it prints the tea order correctly.

Self-check: run it. Programs B and C should both print `3 teas cost $12`.

Then answer: is `latte = 12` still needed? How can you tell?

🙋 **Ask for help if:** you've tried two versions of the line and B still doesn't match C.

### 2. Variation (new tool: `input()`)

`input()` pauses your program, shows a message, and waits for the person to type something and press Enter. Whatever they type becomes the value. You'll learn it fully in 1.6, so this is a preview.

Replace `item_name = "tea"` with:

```python
item_name = input("Item: ")
```

Run it and type `muffin`. Then answer as comments:

1. You didn't know the item when you wrote this line. How did the program still print it correctly?
2. Could this variable be named `tea` or `latte` now? Why not?

🙋 **Ask for help if:** your program seems frozen. Check whether it's waiting for you to type. If it's still stuck after that, raise your hand.

### 3. Trace

Open `bagel_trace.py`. Pretend the person types `bagel`. **Before running**, write the output on paper.

Then trace it step by step as comments. Write what each name holds, then how the message gets built, piece by piece. The first step is done for you:

> 1. The program pauses, the person types `bagel`, and `item_name` now holds `"bagel"`.

Run it, type `bagel`, and compare with your prediction.

---

## Part 4: Make (12 minutes, including a 4-minute name review)

**Task: Laundromat ready message.** In `laundromat.py`, print the message a laundromat texts each customer when their wash starts.

**Requirements**

1. Write the message for one customer. Every part that would change for a different customer gets a name that describes its role.
2. The customer's name comes from `input()`.
3. The minutes until ready are computed from the number of loads and the minutes per load (25), stored in an `ALL_CAPS` constant. Never type the minutes into the message.
4. Test with a second customer (Priya, 2 loads) by changing only assignment lines and what you type. The output must be correct both times.
5. Every name says what it holds.
6. The program must run without crashing.

**Check your output.** For Bo with 3 loads, then Priya with 2 loads:

```
Customer name: Bo
Bo, your 3 loads will be ready in 75 minutes.
```

```
Customer name: Priya
Priya, your 2 loads will be ready in 50 minutes.
```

If Priya's message still says 75 minutes, reread big idea 1.

🙋 **Ask for help if:** your second customer's message is wrong and you can't find which piece didn't change, or your program crashes and you can't tell which line the error points to.

### Name review (4 minutes)

1. Swap code with a partner. **Don't run their code.**
2. For each name in your partner's code, write down what you think it holds.
3. Swap back. Compare your partner's guesses with what each name actually holds.
4. Rename any name your partner guessed wrong, then run your code again to make sure it still works.

Keep the feedback about the names, not the person. "I guessed `total` was the price" is useful. "This is confusing" isn't.

✅ **Checkpoint:** Show an instructor your final code, and tell them which name (if any) you changed after the review and why.

---

## Part 5: Independent check (10 minutes)

Your instructor will hand this out. Work alone, with no AI and no notes, and write your prediction on paper before you run anything.

---

## Going further (optional)

Use one new tool, `int(input())`. Make `laundromat.py` ask for the number of loads too.

1. First try `loads = input("Loads: ")` and type `3`. Look closely at the minutes. What happened, and what type did `input()` give back?
2. Fix it with `loads = int(input("Loads: "))`.
