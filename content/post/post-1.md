+++
title = "lvalues references and rvalues references in C++ with Examples"
description = ""
date = 2021-09-01
updated = 2021-09-01
draft = false
slug = "l-value-and-r-value-references"

[taxonomies]
tags = ["C++", "pointers", "references","Github"]
+++

Prerequisites: [lvalue and rvalue in C++](https://www.geeksforgeeks.org/lvalue-and-rvalue-in-c-language/), [References in C++](https://www.geeksforgeeks.org/references-in-c/)

**“l-value”** refers to a memory location that identifies an object. **“r-value”** refers to the data value that is stored at some address in memory. References in C++ are nothing but the alternative to the already existing variable. They are declared using the **‘&’** before the name of the variable.

Example: 

```C++
int a = 10;

// Declaring lvalue reference
int& lref = a;

// Declaring rvalue reference
int&& rref = 20;
```

Below is the implementation for lvalue and rvalue:

```C++
// C++ program to illustrate the
// lvalue and rvalue
 
#include <iostream>
using namespace std;
 
// Driver Code
int main()
{
    // Declaring the variable
    int a{ 10 };
 
    // Declaring reference to
    // already created variable
    int& b = a;
 
    // Provision made to display
    // the boolean output in the
    // form of True and False
    // instead of 1 and
    cout << boolalpha;
 
    // Comparing the address of both the
    // variable and its reference and it
    // will turn out to be same
    cout << (&a == &b) << endl;
    return 0;
}
```

Output:
```
true
```

**Explanation:** The following code will print True as both the variable are pointing to the same memory location. b is just an alternative name to the memory assigned to the variable a. The reference declared in the above code is lvalue reference (i.e., referring to variable in the lvalue) similarly the references for the values can also be declared.

rvalue references have two properties that are useful: 

1. rvalue references extend the lifespan of the [temporary object](https://docs.microsoft.com/en-us/cpp/cpp/temporary-objects?view=vs-2019) to which they are assigned.
2. Non-const rvalue references allow you to modify the rvalue.

**Important:** lvalue references can be assigned with the rvalues but rvalue references cannot be assigned to the lvalue.

```C++
// C++ program to illustrate the
// lvalue and rvalue
#include <iostream>
using namespace std;

// Driver Code
int main()
{
	int a = 10;

	// Declaring lvalue reference
	// (i.e variable a)
	int& lref = a;

	// Declaring rvalue reference
	int&& rref = 20;

	// Print the values
	cout << "lref = " << lref << endl;
	cout << "rref = " << rref << endl;

	// Value of both a
	// and lref is changed
	lref = 30;

	// Value of rref is changed
	rref = 40;
	cout << "lref = " << lref << endl;
	cout << "rref = " << rref << endl;

	// This line will generate an error
	// as l-value cannot be assigned
	// to the r-value references
	// int &&ref = a;
	return 0;
}
```
Output:
```
lref = 10
rref = 20
lref = 30
rref = 40
```

### Uses of the lvalue references:
1. lvalue references can be used to alias an existing object.
2. They can also be used to implement pass-by-reference semantics.

```C++
// C++ program to illustrate lvalue
#include <iostream>
using namespace std;

// Creating the references of the
// parameter passed to the function
void swap(int& x, int& y)
{
	int temp = x;
	x = y;
	y = temp;
}

// Driver Code
int main()
{
	// Given values
	int a{ 10 }, b{ 20 };
	cout << "a = " << a
		<< " b = " << b << endl;

	// Call by Reference
	swap(a, b);

	// Print the value
	cout << "a = " << a
		<< " b = " << b << endl;
	return 0;
}
```

```
a = 10 b = 20
a = 20 b = 10
```

**Note:** When the function return lvalue reference the expression becomes lvalue [expression](https://en.cppreference.com/w/cpp/language/value_category).

### Uses of rvalue references:

1. They are used in working with the move constructor and move assignment.
2. cannot bind non-const lvalue reference of type ‘int&‘ to an rvalue of type ‘int’.
3. cannot bind rvalue references of type ‘int&&‘ to lvalue of type ‘int’.

### Program 1:
```C++
// C++ program to illustrate rvalue
#include <iostream>
using namespace std;

// lvalue reference to the lvalue
// passed as the parameter
void printReferenceValue(int& x)
{
	cout << x << endl;
}

// Driver Code
int main()
{
	// Given value
	int a{ 10 };

	// Function call is made lvalue & can
	// be assigned to lvalue reference
	printReferenceValue(a);
	return 0;
}
```

Output:
```
10
```

### Program 2:
```C++
// C++ program to illustrate rvalue
#include <iostream>
using namespace std;

// Declaring rvalue reference to the
// rvalue passed as the parameter
void printReferenceValue(int&& x)
{
	cout << x << endl;
}

// Driver Code
int main()
{
	// Given value a
	int a{ 10 };

	// Works fine as the function is
	// called with rvalue
	printReferenceValue(100);
	return 0;
}
```

Output:
```
100
```
