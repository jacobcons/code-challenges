# Code Challenges

## How to use this resource

1. Solve problems in the order given. Feel free to paste problems into chatgpt to ask it to explain it better if you need. Remember to test different paths in the code. Remember to run through the code in your head if the output isn't what you expect to see what could of gone wrong. Also ask chatgpt about how to setup debugger tools in vscode for nodejs so you can also have the computer step through the code for you, but it's still good practise at this early stage to dry run it in your head
2. If you get stuck ask chatgpt to give you a simple hint but not to give you the actual solution
3. When solved/you give up => ask chatgpt to generate a simple solution in node.js and explain it
4. If you really struggled with making much progress on the problem at all and had to just see the solution, ask chatgpt to generate a similar problem for you to solve for extra practise

## Table Of Contents

<!-- toc -->

- [Todo](#todo)
- [Modulus Operator](#modulus-operator)
  - [Explanation](#explanation)
  - [Exercise 1: Divisibility Check](#exercise-1-divisibility-check)
  - [Exercise 2: Determine Parity](#exercise-2-determine-parity)
  - [Exercise 3: Repeating Number Sequence](#exercise-3-repeating-number-sequence)
  - [Exercise 4: Pass the Parcel](#exercise-4-pass-the-parcel)
  - [Exercise 5: Future Day of the Week (difficult)](#exercise-5-future-day-of-the-week-difficult)
- [Math functions](#math-functions)
  - [Explanation](#explanation-1)
  - [Exercise 1: Distance to Nearest Integer](#exercise-1-distance-to-nearest-integer)
  - [Exercise 2: Calculate Percentage](#exercise-2-calculate-percentage)
  - [Exercise 3: Coin Flip](#exercise-3-coin-flip)
  - [Exercise 4: Rock, Paper, Scissors Game](#exercise-4-rock-paper-scissors-game)
  - [Exercise 5: Generate Random Number](#exercise-5-generate-random-number)
  - [Exercise 6: Generate Random Integer](#exercise-6-generate-random-integer)
  - [Exercise 7: Generate Random Integer in Range](#exercise-7-generate-random-integer-in-range)
  - [Exercise 8: Number Guessing Game](#exercise-8-number-guessing-game)
- [Loops](#loops)
  - [Simple loops](#simple-loops)
    - [Exercise 1: Loop Through Range](#exercise-1-loop-through-range)
    - [Exercise 2: Countdown with Blast Off](#exercise-2-countdown-with-blast-off)
    - [Exercise 3: Print Even Numbers](#exercise-3-print-even-numbers)
    - [Exercise 4: Sum of Integers](#exercise-4-sum-of-integers)
    - [Exercise 5: Sum of Multiples](#exercise-5-sum-of-multiples)
    - [Exercise 6: Collatz Conjecture](#exercise-6-collatz-conjecture)
    - [Exercise 7: Calculate Factorial](#exercise-7-calculate-factorial)
    - [Exercise 8: Find Factors](#exercise-8-find-factors)
    - [Exercise 9: Check Prime](#exercise-9-check-prime)
    - [Exercise 10: Print Primes](#exercise-10-print-primes)
    - [Exercise 11: FizzBuzz](#exercise-11-fizzbuzz)
    - [Exercise 12: Fibonacci Sequence](#exercise-12-fibonacci-sequence)
  - [Nested loops](#nested-loops)
    - [Exercise 1: Multiplication Table](#exercise-1-multiplication-table)
    - [Exercise 2: Printing a Right-Angle Triangle](#exercise-2-printing-a-right-angle-triangle)
    - [Exercise 3: Border of a Square](#exercise-3-border-of-a-square)
    - [Exercise 4: Pyramid Pattern (difficult)](#exercise-4-pyramid-pattern-difficult)

<!-- tocstop -->

## Todo

- Loops
  - Menus
- Arrays & Strings
  - No built-in functions
  - Built-in functions
  - 2d arrays
- Objects
- Regex
- Date & Time

## Modulus Operator

### Explanation

1. **Understanding the Modulus Operator**:  
   The modulus operator (`%`) returns the remainder of a division. For example, `13 % 4` equals `1` because when you divide 13 by 4, it goes three times (4 \* 3 = 12) with a remainder of 1. This remainder is what the modulus operator provides.

2. **Divisibility Check**:  
   The modulus operator is also useful for checking if one number divides evenly into another. For instance, `35 % 7` equals `0`, which tells us that 7 divides 35 perfectly with no remainder. If the result of `a % b` is `0`, it indicates that `b` is a divisor of `a`. More examples include `12 % 4 = 0` (4 divides 12 evenly) and `20 % 5 = 0` (5 divides 20 evenly).

3. **Working with Repeating Sequences**:  
   The modulus operator is particularly handy when dealing with repeating sequences. Imagine you have a repeating string like `"abcd"` that goes on infinitely: `"abcdabcdabcd..."`. Assume it's 0 indexed so "a" is in the 0th position, "b" in the 1st and so on. If you want to find the character at an arbitrary index, the key insight is that if you start at some index say 0, for every lot of 4 you go forward you'll end up at the same character in the sequence e.g. start at index 0 "a" => for every lot of 4 you add you'll still be at "a", start at index 1 "b" => for every lot of 4 you go add you'll still be at "b" etc... so given at arbitrary index say 21, this can be expressed as a multiple of 4 add its remainder 21=5\*4 + 1 => start at index 1 "b" and go forward 5 lots of 4 (which has no affect) and hence you remain at character "b". Hence you just need to calculate position % 4 as this will shove as many 4s in as possible and give you what's left (the starting index) i.e. pos % 4 == 0 => "a", pos % 4 == 1 => "b", pos % 4 == 2 => "c", pos % 4 == 3 => "d"

   - To find the character at position `n`, calculate `n % 4`. The result will tell you where you are in the sequence because it tells how many extra are left after fitting as many chunks of 4 "abcd" into n
     - If `n % 4 = 0`, the character is `a`
     - If `n % 4 = 1`, the character is `b`
     - If `n % 4 = 2`, the character is `c`
     - If `n % 4 = 3`, the character is `d`

   So the key is that when have you a repeating sequence, a given `position` can be expressed as `starting point + length_of_repetition * n` (where you shove in as many repetitions as possible) which indicates being at starting position and going forward a bunch of repititions which doesn't change the element, hence calculating `position % length_of_repetition` will give you that initial `starting point`

### Exercise 1: Divisibility Check

write a function isDivisible(n, m) that returns true if m goes into n, otherwise false

```javascript
// Examples:
isDivisble(12, 4) -> true
isDivisble(13, 5) -> false
```

### Exercise 2: Determine Parity

write a function parity(n) that returns "even" if n is even and "odd" if n is odd

```javascript
// Examples:
parity(6) -> "even"
parity(7) -> "false"
```

### Exercise 3: Repeating Number Sequence

imagine you have a sequence of numbers that repeats forever going 5, 10, 15, 5, 10, 15 etc... write a function that takes in the position in a sequence and returns the number at that position. Assume the sequence is 0 indexed.

```javascript
// Examples:
numberAtPosition(0) -> 5
numberAtPosition(1) -> 10
numberAtPosition(2) -> 15
numberAtPosition(3) -> 5
numberAtPosition(99) -> 5
```

### Exercise 4: Pass the Parcel

6 people sit around in a circle numbered from 0 to 5 clockwise playing pass the parcel. write a function passTheParcel(currentPosition, numberOfPasses) that takes in the current person that has the parcel and the number of times the parcel is passed around clockwise. The function should return the person that has the parcel after passing it around. You should draw a diagram to help visualise this.

```javascript
// Examples:
passTheParcel(3, 2) -> 5 (person 3 has it, it gets passed 2 people along, so now person 5 has it)
passTheParcel(4, 3) -> (person 4 has it, it gets passed 3 people along so it goes to 5, back to 0 and then to 1)
```

### Exercise 5: Future Day of the Week (difficult)

Write a function that takes in the day of the week as a string (e.g., "monday", "tuesday", etc.) and the number of days in the future you want to go (e.g., 100) and returns the new day of the week.

```javascript
// Examples:
futureDay("monday", 5) -> "saturday" (Starting on Monday, 5 days later is Saturday)
futureDay("wednesday", 9) -> "friday" (Starting on Wednesday, 9 days later is Friday)
futureDay("friday", 15) -> "saturday" (Starting on Friday, 15 days later is Saturday)
futureDay("sunday", 2) -> "tuesday" (Starting on Sunday, 2 days later is Tuesday)
```

## Math functions

### Explanation

JavaScript comes with some built-in math functions, such as `Math.round()`, `Math.ceil()`, `Math.floor()`, and `Math.random()`. You can use these functions to perform various mathematical operations. Ask ChatGPT to see examples of these in use.

### Exercise 1: Distance to Nearest Integer

Write a function `distanceToClosestInteger(n)` that returns the distance to the integer closest to `n`.

```javascript
// Examples:
distanceToClosestInteger(4.3) -> 0.3
distanceToClosestInteger(5.8) -> 0.2
```

### Exercise 2: Calculate Percentage

Write a function `calculatePercentage(part, whole)` that returns the percentage of `part` out of `whole`, rounded to the nearest integer.

```javascript
// Examples:
calculatePercentage(50, 200) -> "25%"
calculatePercentage(37, 80) -> "46%"
```

### Exercise 3: Coin Flip

Write a function `coinFlip()` that returns "heads" 50% of the time and "tails" the other 50%.

```javascript
// Example:
coinFlip() -> "heads"
coinFlip() -> "tails"
```

### Exercise 4: Rock, Paper, Scissors Game

Make a rock, paper, scissors game. It should ask the user for their choice. The computer should pick a choice at random, print it, and then it should print the outcome of the game. e.g. player chooses rock, computer chooses paper at random, computer wins

### Exercise 5: Generate Random Number

Write a function `randomNumber(n)` that generates a random number between 0 (inclusive) and `n` (exclusive).

```javascript
// Examples:
randomNumber(10) -> 4.237
randomNumber(5) -> 0.876
```

### Exercise 6: Generate Random Integer

Write a function `randomInteger(n)` that generates a random integer between 0 (inclusive) and `n` (exclusive).

```javascript
// Examples:
randomInteger(10) -> 7
randomInteger(5) -> 2
```

### Exercise 7: Generate Random Integer in Range

Write a function `randomInteger(min, max)` that generates a random integer between `min` (inclusive) and `max` (inclusive).

```javascript
// Examples:
randomInteger(1, 10) -> 4
randomInteger(5, 15) -> 11
```

### Exercise 8: Number Guessing Game

Make a game where a user must make a guess between 1-10. Then the computer should generate a random number between 1-10, print it, and state whether or not the user guessed correctly. e.g. user chooses 4, computer generates 7 at random, user loses

## Loops

### Simple loops

#### Exercise 1: Loop Through Range

Write a function `loop(min, max)` that outputs all the integers between `min` and `max` (inclusive). Write two versions of the function, one using `for` loops and the other using `while` loops.

```javascript
// Examples:
loop(1, 5);
// Output:
// 1
// 2
// 3
// 4
// 5
```

#### Exercise 2: Countdown with Blast Off

Write a function `countdown(n)` that prints all the integers from `n` down to `1` and then prints "Blast off!". Write two versions of the function, one using `for` loops and the other using `while` loops.

```javascript
// Examples:
countdown(5);
// Output:
// 5
// 4
// 3
// 2
// 1
// Blast off!
```

#### Exercise 3: Print Even Numbers

Write a function `evens(n)` that prints all the integers from `1` to `n` that are even.

```javascript
// Examples:
evens(10);
// Output:
// 2
// 4
// 6
// 8
// 10
```

#### Exercise 4: Sum of Integers

Write a function `sum(n)` that returns the sum of all the integers between `1` (inclusive) and `n` (inclusive).

```javascript
// Examples:
sum(5) -> 15 (because 1 + 2 + 3 + 4 + 5 = 15)
sum(10) -> 55
```

#### Exercise 5: Sum of Multiples

Write a function `sumOfMultiples(x, n)` that returns the sum of the multiples of `x` up to `n`.

```javascript
// Examples:
sumOfMultiples(3, 10) -> 18 (because 3 + 6 + 9 = 18)

sumOfMultiples(5, 20) -> 50 (because 5 + 10 + 15 + 20 = 50)
```

#### Exercise 6: Collatz Conjecture

Write a function `collatz(n)` that prints the sequence of numbers according to the Collatz conjecture, starting from `n`. The rule is: if `n` is even, divide it by 2; if `n` is odd, multiply it by 3 and add 1. Stop when `n` reaches 1 (the conjecture claims that no matter which positive integer you start with, you will always eventually reach the number 1)

```javascript
// Examples:
collatz(6);
// Output:
// 6
// 3
// 10
// 5
// 16
// 8
// 4
// 2
// 1

collatz(3);
// Output:
// 3
// 10
// 5
// 16
// 8
// 4
// 2
// 1
```

#### Exercise 7: Calculate Factorial

Write a function `factorial(n)` that returns `n!`. `n! = n * (n - 1) * ... * 1`.

```javascript
// Examples:
factorial(5) -> 120
factorial(3) -> 6
```

#### Exercise 8: Find Factors

Write a function `factors(n)` that prints all the factors of `n`.

```javascript
// Examples:
factors(12);
// Output:
// 1
// 2
// 3
// 4
// 6
// 12
```

#### Exercise 9: Check Prime

Write a function `isPrime(n)` that returns `true` if `n` is prime, otherwise `false`.

```javascript
// Examples:
isPrime(7) -> true
isPrime(10) -> false
```

#### Exercise 10: Print Primes

Write a function `printPrimes(n)` that prints all primes less than or equal to `n`.

```javascript
// Examples:
printPrimes(10);
// Output:
// 2
// 3
// 5
// 7
```

#### Exercise 11: FizzBuzz

Write a function `fizzbuzz(n)` that prints the numbers from 1 to `n`, but for multiples of 3, print "Fizz" instead of the number, and for multiples of 5, print "Buzz". For numbers that are multiples of both 3 and 5, print "FizzBuzz".

```javascript
// Examples:
fizzbuzz(15);
// Output:
// 1
// 2
// Fizz
// 4
// Buzz
// Fizz
// 7
// 8
// Fizz
// Buzz
// 11
// Fizz
// 13
// 14
// FizzBuzz
```

#### Exercise 12: Fibonacci Sequence

Write a function `fibonacci(n)` that prints the first `n` numbers in the Fibonacci sequence.

```javascript
// Examples:
fibonacci(5);
// Output:
// 0
// 1
// 1
// 2
// 3
```

### Nested loops

#### Exercise 1: Multiplication Table

Write a function `multiplicationTable(n)` that prints an `n x n` multiplication table.

```javascript
// Example for n = 3:
multiplicationTable(3);
/*
Output:
1 2 3
2 4 6
3 6 9
*/
```

#### Exercise 2: Printing a Right-Angle Triangle

Write a function `printTriangle(height)` that prints a right-angled triangle made of asterisks (`*`). The triangle should have a height equal to the `height` parameter.

```javascript
// Example for height = 4:
printTriangle(4);
/*

Output:
*
**
***
****

*/
```

#### Exercise 3: Border of a Square

Write a function `printSquareBorder(n)` that prints the border of a square of size `n x n` using asterisks (`*`). The inside of the square should be empty.

```javascript
// Example for n = 5:
printSquareBorder(5);
/*

Output:
*****
*   *
*   *
*   *
*****

*/
```

#### Exercise 4: Pyramid Pattern (difficult)

Write a function printPyramid(levels) that prints a pyramid of asterisks (\*) with the specified number of levels.

```javascript
// Example for levels = 4:
printPyramid(4);
/*
Output:
   *
  ***
 *****
*******
*/
```
