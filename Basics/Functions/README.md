<details>
<summary>   What is a functor?</summary>
A functor is a function object in C++. It is an instance of a class that behaves like a function, meaning that it can be called using the function call operator ().

Functors are often used as a more flexible alternative to function pointers. They can be used to encapsulate a specific function or behavior, and they can be passed as arguments to other functions or algorithms.

Here's an example of a simple functor that multiplies a given value by a factor:
```cpp
class Multiplier {
public:
    Multiplier(int factor) : factor_(factor) {}

    int operator()(int x) const {
        return x * factor_;
    }

private:
    int factor_;
};
```
In this example, we define a class named Multiplier that has a single member function named operator(). This function takes an integer argument and returns the product of the argument and a factor that is set during construction of the functor.

To use the Multiplier functor, we can create an instance of the Multiplier class and call it like a regular function:
```cpp
Multiplier times2(2);
int result = times2(5); // result = 10
```
By using functors, you can write code that is more flexible and reusable than traditional functions, as you can pass functors as arguments to other functions and algorithms. For example, the standard library algorithm std::transform takes a functor as an argument and applies it to a range of elements:
```cpp
std::vector<int> numbers = {1, 2, 3, 4};
std::vector<int> doubles;
std::transform(numbers.begin(), numbers.end(), std::back_inserter(doubles), Multiplier(2));
```
In this example, we use an instance of the Multiplier class as the functor to double each element in the numbers vector and store the result in the doubles vector.
</details>


<details>
<summary>   What is the difference between a function and a functor?</summary>

A function is a piece of code that is called by name. It can be passed data to operate on (i.e. the parameters) and can optionally return data (the return value). All data that is passed to a function is explicitly passed.

A functor is an object that can be treated like a function or function pointer. In C++, this is achieved by overloading the function call operator (). The type of a functor is a class or struct, which defines the function call operator.

The main difference between a function and a functor in C++ is that a function is not an object, while a functor is. Functions are stateless, meaning they cannot store data between calls, while functors can have state by storing data in their member variables. Additionally, functors can be customized with their own member functions and member variables, while functions cannot.

Functors are often used in generic programming and algorithms, as they provide a way to encapsulate complex behavior in a reusable and customizable way. Functions, on the other hand, are more commonly used for simple tasks that do not require state or customization.

In summary, while both functions and functors are used to encapsulate behavior in C++, functors are objects that can store data and be customized, while functions are stateless and cannot be customized beyond their arguments and return types.
</details>


<details>
<summary>   What is a lambda function?</summary>
A lamda function is an unnamed function object capable of capturing variables in scope. Lambda functions are defined using the following syntax:
```cpp
[capture list](parameters) -> return type { body }
```
Here, the capture-list is an optional list of variables that are captured by the lambda function. The arguments are the input arguments for the lambda function, and the return-type is the return type of the function. The function body is enclosed in curly braces {}. The return type is optional, and if not specified, the compiler will deduce the return type based on the return statements in the function body.

For example, a lambda function that adds two numbers can be defined as follows:
```cpp
auto add = [](int x, int y) -> int {
    return x + y;
};
```
Lambda functions are commonly used in algorithms, such as std::transform() and std::sort(), as they provide a convenient way to define and pass functions without the need for a named function. For example, the following code sorts a vector of integers in descending order:
```cpp
std::vector<int> numbers = {1, 2, 3, 4};
std::sort(numbers.begin(), numbers.end(), [](int x, int y) { return x > y; });
```
</details>

<details>
<summary>   What is a capture list?</summary>
A capture list is an optional list of variables that are captured by the lambda function. The capture list is enclosed in square brackets [] and can contain one or more of the following items:
- A variable name, which captures the variable by value.
- A reference to a variable, which captures the variable by reference.
- The special keyword this, which captures the current object by reference.
- The special keyword & to capture all local variables by reference.
- The special keyword = to capture all local variables by value.
For example, consider the following lambda function:
```cpp
int x = 10;
auto add = [x](int y) { return x + y; };
```
In this example, the lambda function captures the variable x by value. This means that the value of x is copied into the lambda function, and any changes to x will not affect the value of x inside the lambda function.

Capture lists are a powerful feature of lambda functions in C++, as they allow you to access variables from the enclosing scope within the lambda function, and can be used to customize the behavior of the lambda function.
</details>


<details>
<summary>   What is a closure?</summary>
C++ does not have closures in the same way that some other programming languages do, such as JavaScript or Python. However, C++ does have the ability to create objects that behave similarly to closures by using lambda expressions and capturing variables by reference.

A lambda expression is a way to define a function inline, without needing to declare it separately. When a lambda expression is defined within another function, it can capture variables from the outer function's scope by reference. This means that the lambda function will have access to those variables even after the outer function has completed execution.

Here's an example:
```cpp
void outerFunction() {
    int x = 10;
    auto lambdaFunction = [&]() {
        std::cout << "x = " << x << std::endl;
    };
    lambdaFunction();
}

int main() {
    outerFunction();
    return 0;
}
```
In this example, outerFunction defines a variable x and then creates a lambda function lambdaFunction that captures x by reference using the & symbol. The lambda function then prints the value of x. When outerFunction is called, it creates the lambda function and immediately calls it, resulting in the output "x = 10".

So while C++ doesn't have closures in the same way that some other languages do, it does have the ability to create objects that behave similarly by using lambda expressions and capturing variables by reference.
</details>


<details>
<summary>   What is a unary function?</summary>
In C++, a unary function is a function object that takes a single argument and returns a single value. It is typically used with the <algorithm> library to perform operations on containers such as std::vector and std::list.

Unary functions in C++ are defined using function objects or lambda expressions that accept a single argument of any data type and return a value of any data type. The standard library provides a number of unary functions, including mathematical functions such as std::sqrt and string functions such as std::toupper.

Here's an example of using a unary function to transform a std::vector<int> container:
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <functional>

int main() {
    std::vector<int> v = {1, 2, 3, 4, 5};

    std::transform(v.begin(), v.end(), v.begin(), std::negate<int>());

    for (auto i : v) {
        std::cout << i << " ";
    }

    return 0;
}
```
In this example, the std::transform function takes an input vector v, a destination vector v, and a unary function object std::negate<int>(). The std::transform function applies the unary function std::negate<int>() to each element of v, and stores the result in the corresponding element of v.

The output of this program will be -1 -2 -3 -4 -5, which is the result of negating each element of the input vector v.
</details>

<details>
<summary>   What is a binary function?</summary>
In C++, a binary function is a type of function object that takes two arguments and returns a single value. It is typically used with the <algorithm> library to perform operations on containers such as std::vector and std::list.

Binary functions in C++ are defined using function objects or lambda expressions that accept two arguments of any data type and return a value of any data type. The standard library provides a number of binary functions, including comparison functions such as std::less and arithmetic functions such as std::plus.

Here's an example of using a binary function to perform addition on two std::vector<int> containers:
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <functional>

int main() {
    std::vector<int> v1 = {1, 2, 3};
    std::vector<int> v2 = {4, 5, 6};
    std::vector<int> v3(v1.size());

    std::transform(v1.begin(), v1.end(), v2.begin(), v3.begin(), std::plus<int>());

    for (auto i : v3) {
        std::cout << i << " ";
    }

    return 0;
}
```
In this example, the std::transform function takes two input vectors v1 and v2, a destination vector v3, and a binary function object std::plus<int>(). The std::transform function applies the binary function std::plus<int>() to each element of v1 and v2, and stores the result in the corresponding element of v3.

The output of this program will be 5 7 9, which is the result of adding each pair of elements from v1 and v2.
</details>


<details>
<summary>   What is a function object?</summary>
A function object, also known as a functor, is an object that behaves like a function in C++. A function object is an instance of a class that defines the operator() function, which allows it to be called like a regular function.

Here's an example of a simple function object that adds two integers:
```cpp
class Adder {
public:
    int operator()(int x, int y) const {
        return x + y;
    }
};
```
In this example, we define a class named Adder that has a single member function named operator(). This function takes two integer arguments and returns their sum. The const qualifier after the function declaration indicates that the function does not modify the state of the Adder object.

To use the Adder function object, we can create an instance of the Adder class and call it like a regular function:
```cpp
Adder adder;
int sum = adder(3, 4); // sum = 7
```
By using function objects, you can write code that is more flexible and reusable than traditional functions, as you can pass function objects as arguments to other functions and algorithms. For example, the standard library algorithm std::transform takes a function object as an argument and applies it to a range of elements:
```cpp
std::vector<int> numbers = {1, 2, 3, 4};
std::vector<int> squares;
std::transform(numbers.begin(), numbers.end(), std::back_inserter(squares), [](int x) { return x * x; });
```
In this example, we use a lambda function as the function object to compute the square of each element in the numbers vector and store the result in the squares vector
</details>

<details>
<summary>   What is a default parameter?</summary>
A default parameter is a parameter in a function's parameter list that has a default value assigned to it. If a default value is provided for a parameter, then the function can be called without providing an argument for that parameter, and the default value will be used instead.

For example, consider the following function declaration:
```cpp
void printMessage(std::string message, int count = 1);
```
In this declaration, the second parameter "count" has a default value of 1. This means that if the function is called without providing a value for "count", it will default to 1:
```cpp
printMessage("Hello"); // will print "Hello" once
```
Alternatively, if a value is provided for "count", it will override the default value:
```cpp
printMessage("Hello", 3); // will print "Hello" three times
```
Default parameters are a useful feature in C++ because they allow functions to have a simpler interface and reduce the amount of code that needs to be written by providing sensible default values for parameters that are not always needed.
</details>

<details>
<summary>   What is an inline function?</summary>
An inline function is a C++ function that is expanded in place at the point where it is called, rather than being called through a function call mechanism. This means that the code of the function is inserted directly into the calling code, as if it were part of the caller.

The keyword "inline" is used to declare a function as inline, like this:
```cpp
inline int add(int x, int y) {
    return x + y;
}
```
When an inline function is called, the compiler replaces the function call with the actual code of the function, which is copied directly into the compiled program. This can result in faster code execution, because it eliminates the overhead of a function call.

However, there are some cases where the inline function may not be expanded, and instead behaves like a regular function. This can happen if the function is too large to be inlined, or if the function has a complex control flow that the compiler cannot easily optimize.

It is important to note that the decision of whether or not to inline a function is ultimately up to the compiler. The "inline" keyword is a suggestion to the compiler, but it is not a guarantee that the function will be inlined.
</details>

<details>
<summary>   What is a constexpr function?</summary>
A constexpr function is a C++ function that can be evaluated at compile-time, allowing the result to be used in constant expressions. This means that the function is guaranteed to produce the same result every time it is called with the same arguments, and the result can be used in contexts where a constant expression is required, such as array sizes or template arguments.

A constexpr function is declared using the constexpr keyword, like this:
```cpp
constexpr int square(int x) {
    return x * x;
}
```
In C++11, constexpr functions were limited to only containing a single return statement, and could only contain a limited set of operations, such as arithmetic and bitwise operations. In C++14, these restrictions were relaxed, allowing constexpr functions to contain more complex control structures such as loops and conditional statements.

Using constexpr functions can improve program performance by allowing computations to be performed at compile time rather than at runtime, reducing program overhead. However, it is important to note that not all functions are suitable for constexpr evaluation, and the decision of whether to use a constexpr function should be based on the specific requirements of the program.
</details>

<details>
<summary>   What is a bind function?</summary>
In C++, the std::bind function is used to create a new function object that binds arguments to a function. This means that you can take a function that takes n arguments, bind some of them, and create a new function that takes the remaining m arguments, where m <= n.

The general syntax for using std::bind is as follows:
```cpp
auto new_function = std::bind(original_function, arg1, arg2, ...);
```
Here, original_function is the function you want to bind arguments to, and arg1, arg2, etc. are the arguments you want to bind. The resulting new_function can then be called with the remaining arguments, which are passed to original_function.

For example, suppose we have a function add that takes two integers and returns their sum:
```cpp
int add(int x, int y) {
    return x + y;
}
```
We can use std::bind to create a new function add2 that always adds 2 to its argument:
```cpp
auto add2 = std::bind(add, 2, std::placeholders::_1);
```
Here, std::placeholders::_1 is a special placeholder object that represents the first argument to the function. The resulting add2 function can be called like this:
```cpp
int result = add2(3); // result is 5
```
Note that std::bind returns a function object, which can be stored and reused like any other function object. The resulting function object can also be passed to other functions that take a function object as an argument, such as std::for_each.
</details>

<details>
<summary>   What is a forward function?</summary>
std::forward is a utility function provided by the C++ standard library, defined in the '<utility>' header. It is used to perform "perfect forwarding" of arguments to another function, typically a template function or constructor.

Perfect forwarding is a technique used to pass arguments to a function or constructor in a way that preserves their value category (lvalue or rvalue) and constness. This is particularly important when dealing with templates, since the type of the argument is often unknown until the function is instantiated.

std::forward takes a single argument, which is typically named arg and has a template parameter of the form T&&. This allows the argument to be passed as either an lvalue or rvalue reference, depending on the value category of the original argument. The std::forward function then returns the argument cast to the appropriate reference type, preserving its value category.

Here's an example of how std::forward can be used:
```cpp
template <typename T>
void foo(T&& arg) {
    bar(std::forward<T>(arg));
}
```
In this example, foo is a template function that takes a single argument, arg, of type T&&. It then calls another function, bar, passing the argument to std::forward to ensure that its value category is preserved.

By using std::forward in this way, foo can be used with both lvalues and rvalues, and the argument will be passed to bar in the appropriate form.
</details>

<details>
<summary>   What is a functional library?</summary>
In C++, a functional library is a collection of functions and templates that can be used to implement functional programming paradigms. Functional programming is a programming paradigm that emphasizes the use of functions to perform computations and avoids changing state and mutable data. It is based on the mathematical concept of a function, where the output depends only on the input and not on any hidden state. The functional library in C++ provides a set of generic algorithms and function objects that can be used to implement functional programming concepts like higher-order functions, currying, composition, and lazy evaluation. The functional library in C++ is part of the Standard Template Library (STL) and includes classes like std::function, std::bind, and function objects like std::plus, std::minus, and std::greater.
</details>

<details>
<summary>   What is a std::function?</summary>

In C++, std::function is a class template defined in the `<functional>` header that allows storing and invoking callable objects such as functions, function pointers, lambda expressions, and bind expressions. It provides a uniform way to represent different types of callable objects, regardless of their signature, and enables treating them as objects that can be copied, assigned, and stored in containers.

std::function can be used to implement function pointers, callbacks, and other similar functionality in a type-safe way. It is commonly used as a parameter type or return type in interfaces where the exact function to be called is not known at compile time, but determined at runtime.

The class template std::function takes a function signature as a template parameter, which specifies the arguments and return type of the callable object it can hold. For example, `std::function<void(int)>` can hold a callable object that takes an integer argument and returns no value.

std::function is a powerful tool in modern C++ programming that allows implementing generic algorithms and code with higher levels of abstraction and flexibility.
</details>

<details>
<summary>   What is a std::bind?</summary>

std::bind is a function template defined in the <functional> header of the C++ standard library. It allows creating a new function object with some of the original function's parameters "bound" to specific values or objects.

The general syntax for using std::bind is:
```cpp
auto new_function_object = std::bind(original_function, arg1, arg2, ...);
```

Here, original_function is the function to be called, and arg1, arg2, etc. are values or objects that are "bound" to some of the parameters of original_function. The resulting new_function_object can then be called as if it were the original function, with any remaining arguments provided at the time of the call.

For example, suppose we have a function add that adds two integers:

```cpp
int add(int a, int b) {
    return a + b;
}
```

We can use std::bind to create a new function object that adds 5 to any integer passed to it:

```cpp
auto add_five = std::bind(add, 5, std::placeholders::_1);
```

Here, std::placeholders::_1 represents the first argument to the resulting function object, which will be supplied at the time of the call. We can then use add_five like this:

```cpp
int result = add_five(10); // result is 15
```

In this example, add_five is a new function object that "wraps" the add function, with the first argument "bound" to 5.
</details>

<details>
<summary>   What is a function overloading?</summary>

Function overloading is a feature in C++ that allows creating multiple functions with the same name but with different parameters. When a function is overloaded, the compiler determines which version of the function to call based on the number, types, and order of the arguments passed to the function.

For example, consider a simple function named "add" that adds two integers:

```cpp
int add(int x, int y) {
    return x + y;
}
```

We can overload the "add" function to accept and add other types of data, such as doubles or floats:

```cpp
double add(double x, double y) {
    return x + y;
}

float add(float x, float y) {
    return x + y;
}
```

Now, when we call the "add" function, the compiler determines which version of the function to call based on the types of the arguments passed to it:

```cpp
int result1 = add(2, 3);      // calls int add(int x, int y)
double result2 = add(2.5, 3.7); // calls double add(double x, double y)
float result3 = add(2.5f, 3.7f); // calls float add(float x, float y)
```

Function overloading is a powerful feature of C++ that allows creating functions with the same name, but with different functionality based on the types of the arguments passed to them.
</details>

<details>
<summary>   What is a function overriding?</summary>
Function overriding is a concept in object-oriented programming that allows a subclass or derived class to provide its own implementation for a method that is already defined in its superclass or base class.

When a method is called on an object of the subclass, the implementation in the subclass is used instead of the implementation in the superclass. This allows the subclass to modify the behavior of the method without changing the interface or signature of the method.

To override a method in C++, the method must be declared in the base class with the virtual keyword, and the subclass must provide its own implementation of the method using the same function signature.
</details>

<details>
<summary>   What is a lambda expression?</summary>

A lambda expression is a shorthand notation to define and create an anonymous function object in C++. It allows you to create a function object at the same time you need it, without having to explicitly define a named function elsewhere in your code.

The syntax of a lambda expression generally looks like this:

```cpp
[capture-list] (parameter-list) -> return-type { function-body }
```

-   The capture list is used to capture variables from the surrounding scope. It can be empty or contain one or more variables.
-	The parameter list contains the input parameters of the lambda function.
-	The return type is optional and can be inferred by the compiler if not specified.
-	The function body contains the code to be executed when the lambda function is called.

For example, the following lambda expression returns the sum of two integers:

```cpp
auto sum = [](int a, int b) { return a + b; };
```

This creates a lambda function object that takes two integers as input parameters and returns their sum. The auto keyword is used to let the compiler deduce the return type of the lambda function. The lambda function can be called as follows:

```cpp
int result = sum(3, 5); // result is 8
```
</details>