# C++ Primer


## Header Files (.hpp/.h) vs Soure Files (.cpp)

A common source of confusion for new C++ users is the distinction between header and source files. 

#### Header Files

- Header files usually have a `.hpp` or `.h` extension, or no extension at all (as is the case with all STL headers)
- Header files typically contain what is called the **declaration** of either classes or functions. A declaration simply lays out the skeleton of a class or the signature of functions, omitting their actual implementation:
  ```cpp
  // MyClass.hpp
  #pragma once
  class MyClass {
  public:
    MyClass();
    double a_member_function(double x);
  };
  ```
  ```cpp
  // Math.hpp
  #pragma once
  double add(double a, double b);
  double subtract(double a, double b);
  ```
- Header files conventionally define one class per header file, or a group of related functions per header file, as shown above. However, it's up to the developer how to organize header files -- the compiler generally does not care.
- Header files are **incuded** in all the places you wish to use the declared class or functions by using a `#include "MyClass.hpp` statement, etc. 
- Header files typically beging with an include gaurd, e.g `#pragma once`, so that they are not included more than once in a single `.cpp` file.

#### Source Files

- Source files will almost always use `.cpp` for C++ code, and `.c` for plain C code
- Source files generally contain the **definition** or **implementation** of code declared by header files. *If the header file is the table of contents, then the source file is the actual book.*
  ```cpp
  // MyClass.cpp
  #include "MyClass.hpp"
  
  MyClass::MyClass() { std::cout << "Hello, World" << std::endl; }
  double MyClass::a_member_function(double x) { return 2 * x };
  ```
  ```cpp
  // Math.cpp
  #include "Math.hpp"
  
  double add(double a, double b) { return a + b; }
  double subtract(double a, double b} { return a - b; }
  ```

#### But You Should Know ...

- Functions and classes defined in source files don't necessiarly have to be first declared in header files. You can add utility classes and free functions to source files without declaring them in header files.
- Sometimes header files will contain the definitions, and omit the source file. This generally the case of **template** and **inline** classes/functions. 
 
