### Classes 

A class in C++ is the building block, that leads to Object-Oriented programming. It is a user-defined data type, which holds its own data members and member functions, which can be accessed and used by creating an instance of that class. A C++ class is like a blueprint for an object.

### Objects 

An Object is an instance of a Class. When a class is defined, no memory is allocated but when it is instantiated (i.e. an object is created) memory is allocated.


### Syntax of a class

```C++

class ClassName {
	Access Specifier: // public, private or protected
	Data Members; // int a; double b;
	Member Functions(){} // void displayAge(int age) { cout << age };
}
```
### Declaration of an Object

At first, we need to import the class file into our main file. An example would look something like this:

- Suppose this is the class named "Student.cpp" that we want to import:

```C++
class Student{
public:
	int rollNumber;
private:
	int age;
public:
	setAge(int newAge){
		age = newAge;
	}

	returnAge(){
		return age;
	}
}
```

- And this is the main file where we import the class file:

```C++
#include <iostream>
using namespace std;

#include "Student.cpp"

int main()
{
	Student s1;
	Student *s2 = new Student;

	s1.rollNumber = 23;

	(*s2).rollNumber = 23;
	s2 -> rollNumber = 25;
}

```


There can be multiple access specifiers, namely:
1. **Public** - The data members and member functions are accessible outside of the program too.

2. **Private** - The data members and member functions are accessible only within the file. **This is the default mode.**

3. **Protected** - More on this soon.

##### On declaration of the object, objects can be declared in two ways:
 
1. **Static allocation:**

```C++
Student s1; // it is stored on stack memory

// We can access the data members through:

cout << s1.rollNumber;
```

2. **Dynamic Allocation:**

```C++
Student *s2 = new Student; // Stored on Heap memory

// Notice that s2 is a pointer that points to the location of Student Object in the heap memory. This implies that we need to access the data through pointer approach, i.e.,

cout << (*s2).rollNumber;


// There is another way to access the data members using arrow symbol.

cout << s2 -> rollNumber;
```

**In both the cases the data members are initialised with garbage value. If any variable is seen to be initialised with 0, it is mere coincidence.**

---

We have already established that Private members are not accessible to any other file outside of the source. This means that in the above example, **age** is not accessible to the main method. So, in order to access the **age** variable, we can use a public method in the source while which returns the private members in the same file. This method can also be used to modify the values on private variable through some other file. For eg, we can do the following for the above **Student** Class:


```C++
#include <iostream>
using namespace std;

#include "Student.cpp"

int main()
{
	Student s1;

	s1.rollNumber = 23;

	s1.setAge(25);

	// now, rollnumber = 23 and age = 25
	// we can also print the variable age like this:

	cout << s1.returnAge();
}
```