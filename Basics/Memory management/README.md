
<details>
<summary>   What is a pointer?</summary>

In C++, a pointer is a variable that stores the memory address of another variable. Pointers allow you to work directly with memory locations, which can be useful in a variety of programming scenarios.

To declare a pointer variable in C++, you use the * symbol before the variable name. For example:
```cpp
int num = 5;
int *ptr = &num;
cout << *ptr; // Output: 5
cout << ptr;  // Output: adress of num variable
```
</details>


<details>
<summary>   What is a reference variable?</summary>
In C++, a reference variable is an alias for an existing variable. It allows you to access the same memory location as the original variable, but using a different name.

To declare a reference variable in C++, you use the & symbol after the variable type. For example:
```cpp
int num = 5;
int &ref = num;
cout << num;    //Output: 5
cout << ref;    //Output: 5
ref = 10;
cout << num;    //Output: 10
cout << ref;    //Output: 10
num = 20;
cout << num;    //Output: 10
cout << ref;    //Output: 10
```
Hint:

Reference variables are particularly useful in situations where you want to pass values by reference to a function, rather than by value. This allows you to modify the original value directly, rather than creating a copy of the value. Additionally, references can be used to create more readable and concise code, as they allow you to work with aliases for variables rather than the original variables themselves.
</details>

<details>
<summary>   What is a constant pointer?</summary>
In C++, a constant pointer is a pointer whose value (i.e., the memory address it points to) cannot be changed. However, the value of the object being pointed to can still be modified through the constant pointer.

To declare a constant pointer in C++, you use the const keyword before or after the * symbol in the pointer declaration. For example:
```cpp
int num = 5;
const int *ptr = &num;

cout << *ptr; // Output: 5
num = 10;
cout << *ptr; // Output: 10

*ptr = 15; // Error: Assignment of read-only location
ptr = nullptr; // This is allowed, as it changes the pointer value, not the pointed-to value
```
Hint:

Constant pointers can be useful when you want to ensure that the memory address stored in a pointer does not change, while still allowing the value of the pointed-to object to be modified. They are particularly useful in situations where you want to pass pointers to functions as arguments, but don't want the function to accidentally modify the memory address of the pointer itself.
</details>


<details>
<summary>   What is a constant reference?</summary>
In C++, a constant reference is a reference to a constant object. It allows you to refer to an object by a different name, but does not allow you to modify the object through the reference.

Once you have declared a constant reference, you can use it in the same way as a regular reference. However, any attempts to modify the object being referred to through the constant reference will result in a compiler error.

To declare a constant reference in C++, you use the const keyword before the reference variable type. For example:
```cpp
int num = 5;
const int &ref = num;

cout << ref; // Output: 5
num = 10;
cout << ref; // Output: 10

ref = 15; // Error: Assignment of read-only reference
```
Hint:

Constant references can be useful when you want to pass values to functions without creating copies of the values. They are particularly useful in situations where you want to ensure that the value being referred to is not modified accidentally, either through the reference variable itself or through another means.
</details>


<details>
<summary>   What is a smart pointer?</summary>
In C++, a smart pointer is a class that wraps a raw pointer and provides additional features such as automatic memory management, reference counting, and type checking. Smart pointers are designed to help prevent memory leaks and other memory-related errors by providing a safe and easy-to-use way to manage dynamically allocated memory.

There are two types of smart pointers in C++: std::unique_ptr and std::shared_ptr.

std::unique_ptr is a smart pointer that owns the object it points to and ensures that the object is deleted when the std::unique_ptr goes out of scope. It is designed to be used when you need a single object to have exclusive ownership of a resource.

Here's an example of using std::unique_ptr to manage a dynamically allocated integer:
```cpp
#include <memory>
#include <iostream>

int main() {
    std::unique_ptr<int> p(new int(42));
    std::cout << *p << std::endl;
    return 0;
}
```
In this example, std::unique_ptr<int> p declares a smart pointer that manages a dynamically allocated integer with an initial value of 42. The *p dereferences the pointer to get the value of the integer, which is then printed to the console.

std::shared_ptr is a smart pointer that allows multiple std::shared_ptr objects to share ownership of the same object. It uses reference counting to keep track of how many std::shared_ptr objects are pointing to the same object, and deletes the object when the last std::shared_ptr goes out of scope.

Here's an example of using std::shared_ptr to manage a dynamically allocated integer:
```cpp
#include <memory>
#include <iostream>

int main() {
    std::shared_ptr<int> p1(new int(42));
    std::shared_ptr<int> p2 = p1;

    std::cout << *p1 << " " << *p2 << std::endl;

    return 0;
}
```
In this example, std::shared_ptr<int> p1 declares a smart pointer that manages a dynamically allocated integer with an initial value of 42. The second line, std::shared_ptr<int> p2 = p1, creates a second std::shared_ptr object that points to the same integer. The *p1 and *p2 dereferences the pointers to get the value of the integer, which is then printed to the console.

Smart pointers are an important feature in modern C++ programming, as they help ensure the correctness and safety of dynamically allocated memory.
</details>


<details>
<summary>   What is a unique pointer?</summary>
In C++, a unique pointer is a smart pointer that owns the object it points to and ensures that the object is deleted when the unique pointer goes out of scope. It is designed to manage the lifetime of a single object and guarantee that the object is only deleted once.

A unique pointer is represented by the std::unique_ptr class, which is defined in the <memory> header. It is called "unique" because there can only be one std::unique_ptr object that owns a given resource at any given time.

Here's an example of using std::unique_ptr to manage a dynamically allocated integer:
```cpp
#include <memory>
#include <iostream>

int main() {
    std::unique_ptr<int> p(new int(42));
    std::cout << *p << std::endl;
    return 0;
}
```
In this example, std::unique_ptr<int> p declares a unique pointer that manages a dynamically allocated integer with an initial value of 42. The *p dereferences the pointer to get the value of the integer, which is then printed to the console.

When the std::unique_ptr object goes out of scope, the delete operator is automatically called to delete the integer it owns. This ensures that the dynamically allocated memory is properly deallocated and there are no memory leaks.

Unique pointers are a powerful tool for managing dynamic memory in C++, as they help prevent common errors such as dangling pointers and memory leaks. They also make it easier to write exception-safe code by ensuring that resources are properly cleaned up even in the face of exceptions.
</details>

<details>
<summary>   What is a shared pointer?</summary>
In C++, a shared pointer is a smart pointer that allows multiple shared pointer objects to share ownership of the same object. It uses reference counting to keep track of how many shared pointer objects are pointing to the same object and automatically deletes the object when the last shared pointer object goes out of scope.

A shared pointer is represented by the std::shared_ptr class, which is defined in the <memory> header. It is called "shared" because it allows multiple objects to share ownership of the resource it points to.

Here's an example of using std::shared_ptr to manage a dynamically allocated integer:
```cpp
#include <memory>
#include <iostream>

int main() {
    std::shared_ptr<int> p1(new int(42));
    std::shared_ptr<int> p2 = p1;

    std::cout << *p1 << " " << *p2 << std::endl;

    return 0;
}
```
In this example, std::shared_ptr<int> p1 declares a shared pointer that manages a dynamically allocated integer with an initial value of 42. The second line, std::shared_ptr<int> p2 = p1, creates a second shared pointer object that points to the same integer. The *p1 and *p2 dereference the pointers to get the value of the integer, which is then printed to the console.

When the last shared pointer object goes out of scope, the delete operator is called to delete the integer it owns. This ensures that the dynamically allocated memory is properly deallocated and there are no memory leaks.

Shared pointers are useful when you need to pass a resource between multiple objects or when you need to manage a resource that may have multiple owners. They help prevent memory leaks and other memory-related errors by automatically managing the lifetime of the resource.
</details>

<details>
<summary>   What is a weak pointer?</summary>
In C++, a weak pointer is a smart pointer that behaves similarly to a shared pointer, but it does not participate in ownership of the pointed-to object. A weak pointer can be used to observe an object that is owned by one or more shared pointers, but without actually taking ownership of the object.

A weak pointer is represented by the std::weak_ptr class, which is defined in the <memory> header. It is called "weak" because it does not participate in the reference counting of the shared pointer and does not affect the lifetime of the object it points to.

Here's an example of using std::weak_ptr to observe an object managed by a std::shared_ptr:
```cpp
#include <memory>
#include <iostream>

int main() {
    std::shared_ptr<int> p1(new int(42));
    std::weak_ptr<int> p2 = p1;

    std::cout << *p1 << std::endl;

    if (auto sp = p2.lock()) {
        std::cout << *sp << std::endl;
    } else {
        std::cout << "The object has been deleted" << std::endl;
    }

    p1.reset();

    if (auto sp = p2.lock()) {
        std::cout << *sp << std::endl;
    } else {
        std::cout << "The object has been deleted" << std::endl;
    }

    return 0;
}
```
In this example, std::shared_ptr<int> p1 declares a shared pointer that manages a dynamically allocated integer with an initial value of 42. The second line, std::weak_ptr<int> p2 = p1, creates a weak pointer that points to the same integer. The *p1 dereferences the shared pointer to get the value of the integer, which is then printed to the console.

The p2.lock() method tries to obtain a shared pointer that points to the same object as p2. If the object still exists, it returns a std::shared_ptr object, which can be used to access the object's value. If the object has been deleted, it returns an empty std::shared_ptr object, which evaluates to false in a boolean context.

When the p1.reset() is called, it destroys the shared pointer object and deletes the integer it owns. However, the weak pointer object p2 still exists and can be used to check if the object has been deleted or not.

Weak pointers are useful when you need to observe an object that is owned by one or more shared pointers, without actually taking ownership of the object. They help prevent memory-related errors and make it easier to write safe and correct code that manages dynamic memory.
</details>


<details>
<summary>   What is a memory leak?</summary>
</details>

<details>
<summary>   How do you prevent memory leaks in C++?</summary>
</details>

<details>
<summary>   What is dynamic memory allocation in C++?</summary>
</details>

<details>
<summary>   What is the difference between new and malloc?</summary>
</details>

<details>
<summary>   What is the difference between delete and free?</summary>
</details>

<details>
<summary>   What is a std::unique_ptr?</summary>
</details>

<details>
<summary>   What is a std::shared_ptr?</summary>
</details>

<details>
<summary>   What is a std::weak_ptr?</summary>
</details>

<details>
<summary>   What is a std::make_shared?</summary>
</details>

<details>
<summary>   What is a std::make_unique?</summary>
</details>

<details>
<summary>   What is a std::move?</summary>
</details>

<details>
<summary>   What is a std::copy?</summary>
</details>