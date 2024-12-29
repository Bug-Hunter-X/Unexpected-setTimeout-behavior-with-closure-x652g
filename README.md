# Unexpected setTimeout Behavior with Closures

This example demonstrates a common issue in JavaScript involving closures and the `setTimeout` function.  The expected output might be the numbers 0 through 9 printed sequentially with a one-second delay. However, due to how closures work with asynchronous operations, the output is consistently 10 across all iterations.

## Problem

The `for` loop iterates and schedules multiple `setTimeout` calls. By the time these callbacks finally execute, the loop has completed, and the value of `i` has become 10. Thus, the closure captures the final value of `i`, not its value at each iteration.

## Solution

The solution involves using an immediately invoked function expression (IIFE) or `let` to create a new scope for each iteration, preserving the correct value of `i` within each timeout callback.