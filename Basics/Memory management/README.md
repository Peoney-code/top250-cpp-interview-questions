
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
A memory leak is a situation in computer programming where a program or process fails to release the memory it has allocated and no longer needed. As a result, the available memory in the system is reduced, and the program's performance may suffer or even crash.

Memory leaks occur when memory is allocated dynamically, usually using the new operator in C++ or the malloc() function in C, and is not freed properly using the corresponding delete operator or free() function.

For example, consider the following code snippet:
```cpp
int main() {
    int* p = new int[100];
    // some code here
    return 0;
}
```
In this example, we allocate an array of 100 integers using the new operator, but we do not release the memory using the delete operator. This creates a memory leak that will persist until the program exits.

Memory leaks can be difficult to diagnose, especially in large and complex programs. They can cause the program to consume excessive amounts of memory, leading to poor performance or even crashes. In some cases, they can also pose security risks by allowing attackers to exploit the system's memory resources.

To avoid memory leaks, it's important to always free the memory that has been allocated dynamically using the corresponding delete operator or free() function, and to make sure that all objects and resources are properly cleaned up when they are no longer needed. In addition, there are various tools and techniques that can help detect and prevent memory leaks, such as memory profilers and smart pointers in C++.
</details>

<details>
<summary>   How do you prevent memory leaks in C++?</summary>
Here are some techniques to prevent memory leaks in C++:
-   Always use RAII (Resource Acquisition Is Initialization) technique: This technique involves acquiring resources (such as memory) during object creation and releasing them during object destruction. In C++, this can be done using smart pointers and containers such as std::vector and std::unique_ptr.
-   Always delete dynamically allocated memory: Whenever you allocate memory dynamically using the new operator, make sure you delete it using the delete operator. In cases where exceptions may be thrown, use std::unique_ptr or std::shared_ptr instead of raw pointers to ensure that the memory is deleted properly.
-   Avoid using new and delete directly: Instead of using new and delete directly, use container classes such as std::vector, std::map, and std::set, which handle memory management automatically.
-   Use a memory profiler: Memory profilers are tools that help detect memory leaks by tracking memory usage and identifying memory blocks that are not released properly.
-   Avoid circular references: Circular references occur when two or more objects reference each other, causing memory leaks when they are deleted. To avoid this, use std::weak_ptr or std::unique_ptr instead of raw pointers to break the circular reference.
-   Test your code: Regularly test your code for memory leaks using tools such as Valgrind or Visual Leak Detector.

By following these techniques, you can prevent memory leaks in your C++ code and improve the overall stability and performance of your application.
</details>

<details>
<summary>   What is dynamic memory allocation in C++?</summary>
Dynamic memory allocation in C++ refers to the process of allocating memory for a program at runtime. Unlike static memory allocation, where the memory is allocated at compile-time, dynamic memory allocation allows the program to request memory from the operating system as needed.

C++ provides two operators for dynamic memory allocation: new and delete. The new operator is used to allocate memory for an object or an array of objects, while the delete operator is used to free the memory that was allocated with new.

Here is an example of dynamic memory allocation in C++:
```cpp
int* ptr = new int;   // Allocate memory for an integer
*ptr = 10;            // Assign a value to the integer
delete ptr;           // Free the memory
```
In this example, the new operator is used to allocate memory for an integer, and the pointer ptr is assigned the address of the allocated memory. The value of 10 is then assigned to the integer, and finally, the delete operator is used to free the memory that was allocated with new.

Dynamic memory allocation can be useful in situations where the size of the memory required is not known at compile-time, or when memory needs to be allocated and deallocated at runtime. However, it also carries the risk of memory leaks and fragmentation if not managed properly.
</details>

<details>
<summary>   What is the difference between new and malloc?</summary>
new and malloc are both used for dynamic memory allocation, but they are different in several ways.

-   Type safety: new is type-safe, while malloc is not. new ensures that the memory allocated is of the correct type and handles object initialization, while malloc simply returns a void* pointer to raw memory without any type information.
-   Operator vs. function: new is an operator, while malloc is a function. This means that new is integrated into the C++ language and can be overloaded, while malloc is a C library function.
-   Constructor and destructor calls: new automatically calls the constructor of an object, and delete calls the destructor. malloc does not handle object initialization or destruction, so the constructor and destructor must be called explicitly.
-   Size calculation: new automatically calculates the size of the memory to be allocated based on the data type, while malloc requires the size to be specified manually.
-   Exception handling: new throws a bad_alloc exception if memory allocation fails, while malloc returns a null pointer.

Here is an example that shows the difference between new and malloc:
```cpp
int* p1 = new int;       // allocate memory and initialize with 0
int* p2 = (int*) malloc(sizeof(int));   // allocate memory (no initialization)
```
In this example, p1 is allocated memory using new and is initialized with the value 0. p2 is allocated memory using malloc and is not initialized.

Overall, new is preferred in C++ for dynamic memory allocation because it provides type safety and handles object initialization and destruction automatically. However, malloc can still be useful in certain situations, such as when interfacing with C libraries.
</details>

<details>
<summary>   What is the difference between delete and free?</summary>
delete and free are used to deallocate memory in C++ and C, respectively. While they serve a similar purpose, there are some key differences between them.

-   Operator vs. function: delete is an operator in C++, while free is a C library function.
-   Type safety: delete is type-safe and calls the destructor of an object before deallocating its memory, while free simply releases the memory block without any type information or destructor calls.
-   Size information: delete knows the exact size of the memory block being deallocated, while free requires the size of the memory block to be explicitly specified.
-   Null pointer handling: delete can handle null pointers and does nothing when called with a null pointer, while free can cause undefined behavior if called with a null pointer.

Here's an example that demonstrates the difference between delete and free:
```cpp
int* p1 = new int;        // allocate memory
int* p2 = (int*) malloc(sizeof(int));    // allocate memory

delete p1;               // deallocate memory and call destructor
free(p2);                // deallocate memory
```

In this example, p1 is deallocated using delete, which calls the destructor of the object before deallocating the memory. p2 is deallocated using free, which simply releases the memory block without any destructor calls.

Overall, it is recommended to use delete in C++ and free in C to deallocate dynamically allocated memory. Mixing them can cause undefined behavior and memory leaks.
</details>

<details>
<summary>   What is a std::unique_ptr?</summary>
std::unique_ptr is a smart pointer class template in C++ that provides automatic memory management for dynamically allocated objects. It ensures that the object it points to is deleted when the unique_ptr object goes out of scope or is reset.

The key feature of std::unique_ptr is that it is the sole owner of the object it points to, meaning that it cannot be copied. However, it can be moved to transfer ownership to another unique_ptr. This makes it a good choice for managing dynamically allocated resources that should not be shared between different parts of the code.

Here's an example of using std::unique_ptr:
```cpp
#include <memory>

int main() {
    std::unique_ptr<int> p(new int(42));  // allocate an int and initialize it with 42

    // use the value pointed to by p
    int x = *p;

    // reset p to point to a different object
    p.reset(new int(123));

    // use the new value pointed to by p
    int y = *p;

    // the object pointed to by p is automatically deleted when p goes out of scope
    return 0;
}
```
In this example, p is a unique_ptr that points to an int with value 42. We can access the value using the dereference operator *. We can also reset p to point to a different int with value 123. When p goes out of scope at the end of the main() function, the object it points to is automatically deleted, preventing memory leaks.
</details>

<details>
<summary>   What is a std::shared_ptr?</summary>
std::shared_ptr is a smart pointer class template in C++ that provides shared ownership of dynamically allocated objects. It ensures that the object it points to is deleted when the last shared_ptr pointing to it goes out of scope or is reset.

The key feature of std::shared_ptr is that it allows multiple shared_ptr objects to share ownership of the same object. Each shared_ptr contains a reference count that tracks how many shared_ptr objects are currently pointing to the same object. When the last shared_ptr pointing to the object is destroyed, the object is automatically deleted.

Here's an example of using std::shared_ptr:
```cpp
#include <memory>

int main() {
    std::shared_ptr<int> p1(new int(42));
    std::shared_ptr<int> p2 = p1;

    // use the value pointed to by p1 or p2
    int x = *p1;
    int y = *p2;

    // reset p1 and p2 to point to a different object
    p1.reset(new int(123));
    p2.reset(new int(456));

    // use the new values pointed to by p1 and p2
    int z = *p1;
    int w = *p2;

    // the object originally pointed to by p1 and p2 is deleted automatically
    return 0;
}
```
In this example, p1 and p2 are shared_ptr objects that share ownership of an int with value 42. We can access the value using the dereference operator *. We can also reset p1 and p2 to point to different ints with values 123 and 456, respectively. When both p1 and p2 go out of scope at the end of the main() function, the object they originally pointed to is automatically deleted, preventing memory leaks.
</details>

<details>
<summary>   What is a std::weak_ptr?</summary>


std::weak_ptr is another smart pointer class template in C++ that provides a non-owning ("weak") reference to an object managed by std::shared_ptr. It allows you to access the object pointed to by a shared_ptr without extending its lifetime.

Unlike std::shared_ptr, std::weak_ptr does not increment the reference count of the object it points to. Instead, it points to the same control block that the shared_ptr points to, which contains a reference count and a weak reference count. The reference count is incremented when a new shared_ptr is created that points to the same object, while the weak reference count is incremented when a new weak_ptr is created that points to the same control block.

Here's an example of using std::weak_ptr:
```cpp
#include <memory>
#include <iostream>

int main() {
    std::shared_ptr<int> p1(new int(42));
    std::weak_ptr<int> p2 = p1;

    std::cout << "p1: " << *p1 << std::endl;
    std::cout << "p2.lock(): " << *p2.lock() << std::endl;

    p1.reset(new int(123));

    std::cout << "p1: " << *p1 << std::endl;

    if (p2.lock()) {
        std::cout << "p2.lock(): " << *p2.lock() << std::endl;
    } else {
        std::cout << "p2 is expired." << std::endl;
    }

    return 0;
}
```
In this example, p1 is a shared_ptr that points to an int with value 42. We create a weak_ptr p2 that points to the same object. We can use the lock() method of p2 to get a shared_ptr that shares ownership of the same object as p1. We can also check if p2 is still valid by calling the expired() method. When we reset p1 to point to a different int with value 123, p2 becomes invalid because the object it pointed to has been deleted. We can check if p2 is still valid by calling the lock() method and checking if the returned shared_ptr is not null.

std::weak_ptr is useful when you need to store a reference to an object managed by std::shared_ptr, but you don't want to keep the object alive longer than necessary. It's commonly used to break cyclic references between shared_ptr objects, where two or more objects hold shared_ptr references to each other, causing a memory leak. By using weak_ptr instead of shared_ptr in one or more of the objects, you can break the cycle and ensure that the objects are eventually deleted when they're no longer needed.
</details>

<details>
<summary>   What is a std::make_shared?</summary>
std::make_shared is a function template in C++ that constructs and returns a std::shared_ptr object. It is used to create a shared pointer from a dynamically allocated object, with better performance and exception safety than the alternative of using new and constructing a shared pointer object with it.

The std::make_shared function takes arguments for constructing the object being pointed to, and returns a std::shared_ptr object that points to that object. The object is dynamically allocated using a single allocation, which may improve performance in some cases. The std::make_shared function also ensures that the shared pointer and the managed object are constructed atomically, reducing the risk of resource leaks in case an exception is thrown during construction.

Here is an example of using std::make_shared:
```cpp
std::shared_ptr<int> p = std::make_shared<int>(42);
```
This creates a std::shared_ptr object named p that points to a dynamically allocated integer with value 42. The std::make_shared function allocates memory for the integer and constructs it in place using the argument 42. The resulting std::shared_ptr object p owns the dynamically allocated integer, and the memory will be automatically deallocated when all std::shared_ptr objects that point to it are destroyed.
</details>

<details>
<summary>   What is a std::make_unique?</summary>
std::make_unique is a function template introduced in C++14 that constructs and returns a std::unique_ptr object. It is used to create a unique pointer from a dynamically allocated object, with better performance and exception safety than the alternative of using new and constructing a unique pointer object with it.

The std::make_unique function takes arguments for constructing the object being pointed to, and returns a std::unique_ptr object that points to that object. The object is dynamically allocated using a single allocation, which may improve performance in some cases. The std::make_unique function also ensures that the unique pointer and the managed object are constructed atomically, reducing the risk of resource leaks in case an exception is thrown during construction.

Here is an example of using std::make_unique:
```cpp
std::unique_ptr<int> p = std::make_unique<int>(42);
```
This creates a std::unique_ptr object named p that points to a dynamically allocated integer with value 42. The std::make_unique function allocates memory for the integer and constructs it in place using the argument 42. The resulting std::unique_ptr object p owns the dynamically allocated integer, and the memory will be automatically deallocated when the std::unique_ptr object is destroyed. Note that std::make_unique is only available in C++14 or later, and cannot be used in older versions of C++.
</details>

<details>
<summary>   What is a std::move?</summary>
std::move is a C++11 standard library function that allows you to move the ownership of an object from one variable to another. It is typically used to transfer ownership of a resource such as dynamically allocated memory, or to enable more efficient copying of large objects.

When an object is moved, its contents are transferred from its current location to a new location, and the original location is left in an unspecified state. The object being moved should be considered invalid after the move operation, and should not be used again until it is assigned a new value.

The std::move function is defined in the `<utility>` header and takes a single argument, which is the object to be moved. The function returns an rvalue reference to the object, indicating that it can be safely moved from.

Here is an example of using std::move:
```cpp
std::vector<int> source{1, 2, 3};
std::vector<int> destination = std::move(source);
```
In this example, we create a std::vector object named source containing three integers, and then move it to a new std::vector object named destination. After the move operation, the contents of source are unspecified, but destination contains the original elements of source. The std::move function is used to transfer ownership of the elements from source to destination, which can be more efficient than copying the entire vector.

Note that std::move does not actually move the object itself, but rather allows you to move the object by enabling the use of move constructors or move assignment operators. It is typically used with types that implement move semantics, such as std::unique_ptr, std::vector, or std::string.
</details>
