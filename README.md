# JavaScript Closure Issue in setTimeout Loop

This repository demonstrates a common closure issue in JavaScript when using `setTimeout` within a loop.  The expected behavior is to log numbers 0 through 9, each after a 1-second delay.  However, due to the way closures work, the loop completes before the `setTimeout` callbacks execute, resulting in all callbacks logging the final value of `i` (which is 10).

## Bug Description
The problem stems from the fact that the `setTimeout` callbacks don't capture the value of `i` at the time of their creation; instead they capture the reference to the variable 'i'. By the time the `setTimeout` callbacks finally execute, the loop has already finished and 'i' is equal to 10. This leads to all callbacks logging the same value. 

## Solution
To fix this, create a closure for each iteration of the loop by using an immediately invoked function expression (IIFE) to capture the current value of `i`.

## How to Run

1. Clone this repository.
2. Open `bug.js` to see the buggy code and `bugSolution.js` to view the corrected code.
3. Run `bug.js` and `bugSolution.js` in a browser's console, or via Node.js, to observe the difference in output.