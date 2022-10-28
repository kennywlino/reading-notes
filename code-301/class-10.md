# The JavaScript Call Stack and JavaScript Error Messages

## Why this topic matters

Knowing how the JavaScript call stack functions is important as we want to be able to clearly see what order code is executed. This is especially important when we use callbacks and asynchronous functions.

Understanding errors is also significant as we want to be able to quickly grasp what's impacting our code and think of ways to fix them. 

## Understanding the JavaScript Call Stack

1. What is a ‘call’?

    A call is just when we invoke a function.

2. How many ‘calls’ can happen at once?

    Only one call can happen at a time.

3. What does LIFO mean?

    LIFO stands for **L**ast **I**n **F**irst **O**ut

4. Draw an example of a call stack and the functions that would need to be invoked to generate that call stack.

    If we had the following functions:

    ```javascript
   def functionA(){
        console.log('A there!');  
    }

    def functionB(){
        functionA();
        console.log('B yourself!');
    }

    functionB();
    ```

    Then the call stack would look like: 

    ```javascript
    // functionB() is called.

    1. |             |
       |             | 
       |             |
       | functionB() |
    
    // functionA() is called next.

    2. |             |
       |             | 
       | functionA() |
       | functionB() |

    // console.log('A there') 

    3. |             |
       |             | 
       |*functionA()*|
       | functionB() |

   // console.log('B yourself!');

    4. |             |
       |             | 
       |             |
       |*functionB()*| 

   // empty stack

    5. |             |
       |             | 
       |             |
       |             |  

    ```


5. What causes a Stack Overflow?

    A stack overflow is caused when a function is called repeatedly without an exit condition. The JavaScript runtime can only accommodate X amount of calls before it crashes.

## JavaScript error messages

Based on this [article](https://codeburst.io/javascript-error-messages-debugging-d23f84f0ae7c).

1. What is a ‘reference error’?

    A reference error is when we try to call a variable that hasn't been declared.

    For example:

    ```javascript
    let f00 = 'foo';
    print(foo); // Uncaught ReferenceError: 'foo' is not defined
    ```

2. What is a ‘syntax error’?

    A syntax error is when there is a typo in the syntax of the code.

    ```javascript
    def obj = {; // Uncaught SyntaxError Unexpected identifier 'obj'
    ```

3. What is a ‘range error’?

    A range error occurs when we refer to an invalid index on any object with length.

    ```javascript
    let arr = [1, 2, 3];

    console.log(arr[3]); // Uncaught RangeError
     ```

4. What is a ‘type error’?

    A type error is when there is a mismatched element type or something we're trying to do is incompatible.

    ```javascript
    let num = 1;
    test.toUppercase(); // Uncaught TypeError: test.toUppercase is not a function

    ```

5. What is a breakpoint?

    A breakpoint is a line where we ask the debugger to stop running the code in order to inspect what's going on.

6. What does the word ‘debugger’ do in your code?

    The debugger helps us find the sources of our bugs by using breakpoints to show the state of the code at that point in time.

## Things I want to know more about
