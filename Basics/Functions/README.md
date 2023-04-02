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
<summary>   What is a function parameter?</summary>
</details>

<details>
<summary>   What is a default parameter?</summary>
</details>

<details>
<summary>   What is an inline function?</summary>
</details>

<details>
<summary>   What is a constexpr function?</summary>
</details>

<details>
<summary>   What is a bind function?</summary>
</details>

<details>
<summary>   What is a forward function?</summary>
</details>

<details>
<summary>   What is a functional library?</summary>
</details>

<details>
<summary>   What is a std::function?</summary>
</details>

<details>
<summary>   What is a std::bind?</summary>
</details>
<details>
<summary>   What is a function overloading?</summary>
</details>

<details>
<summary>   What is a function overriding?</summary>
</details>

<details>
<summary>   What is a lambda expression?</summary>
</details>