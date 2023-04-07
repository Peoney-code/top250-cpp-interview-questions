<details>
<summary>   What is exeption?</summary>

execution of a program and disrupts its normal flow. It could be anything from an out-of-range array index to a runtime error. When an exception occurs, it is said to be "thrown" by the program, and the C++ runtime system attempts to find a handler for the exception.

C++ provides a built-in mechanism for handling exceptions, known as "exception handling". This mechanism allows a program to respond to exceptions by catching and handling them in a structured way. When an exception is thrown, the program can "catch" the exception and handle it appropriately, rather than simply crashing or exiting. This makes C++ code more robust and reliable.
</details>

<details>
<summary>   What is a try-catch block?</summary>

In C++, a try-catch block is a mechanism used to handle exceptions that may occur during program execution. The try block is used to enclose a block of code that might generate an exception, while the catch block is used to handle the exception if it occurs.

Here is a basic syntax for a try-catch block in C++:
```cpp
try {
    // code that might generate an exception
}
catch (exception_type exception_object) {
    // code to handle the exception
}
```

In the try block, if an exception is thrown, the control is transferred to the corresponding catch block. The catch block takes an exception object as a parameter, which holds information about the exception that occurred. Multiple catch blocks can be used to handle different types of exceptions. If none of the catch blocks matches the thrown exception, the program terminates abnormally.
</details>

<details>
<summary>   What is a throw keyword?</summary>

In C++, throw is a keyword that is used to throw an exception. When an exception is thrown using throw, it means that an error has occurred during the execution of a program and the program cannot continue as expected. The throw keyword can be followed by any expression or object that represents the exception that has occurred.

For example, consider the following code:
```cpp
double divide(double x, double y) {
  if (y == 0) {
    throw "Divide by zero error!";
  }
  return x / y;
}
```

In this code, the throw keyword is used to throw a string "Divide by zero error!" when the denominator y is equal to zero. This means that if a user calls this function with y equal to zero, the function will throw an exception and the program will stop executing unless the exception is caught and handled by a try-catch block.
</details>

<details>
<summary>   What is a catch keyword?</summary>

The catch keyword is used in C++ along with the try block to handle exceptions. When an exception is thrown from the try block, the program jumps to the catch block to handle the exception. The catch block must specify the type of exception it is designed to catch.

Here is an example:
```cpp
try {
  // some code that might throw an exception
} catch (exception_type e) {
  // code to handle the exception
}
```

In this example, if an exception of type exception_type is thrown within the try block, the program will jump to the catch block and execute the code to handle the exception.
</details>

<details>
<summary>   What is a throw exception?</summary>

In C++, a "throw" statement is used to indicate that an exception has occurred during the execution of a program. When a "throw" statement is encountered, the control of the program is transferred to the nearest enclosing "try" block that has a matching "catch" block to handle the thrown exception.

An exception can be any object or data type. When an exception is thrown, it can be caught and handled by an appropriate "catch" block in the program. If no appropriate "catch" block is found to handle the thrown exception, the program will terminate and display an error message.

The "throw" keyword can be followed by any expression that evaluates to a data type or object, which is used to represent the exception that occurred. For example, in the following code snippet, an exception is thrown when the input is negative:
```cpp
int x;
cin >> x;
if (x < 0) {
   throw "Negative input not allowed!";
}
```

Here, if the user enters a negative number, the program will throw a C-style string "Negative input not allowed!" as an exception. This exception can then be caught and handled appropriately by a "catch" block.
</details>

<details>
<summary>   What is a catch exception?</summary>
A catch block is a C++ language construct used to handle exceptions that are thrown during runtime by a try block. When an exception is thrown inside a try block, the program's execution is transferred to the catch block. The catch block contains the code that handles the exception, and it is executed only when an exception is thrown in the corresponding try block. The catch block takes an argument that specifies the type of exception that can be caught. If the thrown exception is of that type or a derived type, the catch block is executed. If not, the program's execution continues outside the catch block, searching for the next appropriate catch block.
</details>