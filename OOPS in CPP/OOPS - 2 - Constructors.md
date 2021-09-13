# Contructors

A constructor is the first function that is called when we declare an Object of a class. According to GFG, A constructor is a special type of member function of a class which initializes objects of a class. In C++, Constructor is automatically called when object(instance of class) create. It is special member function of the class because it does not have any return type.

What a constructor does is that it initialises all the data members with garbage value. If some variable is seen initialised with 0, it is a mere coincidence.

### Custom Constuctor.

C++ provides us with a default constructor which is called everytime we create an object. We can also make a custom constructor. As soon as we provide a custom constructor, the default one will be disabled for us. 

- This is how we can define a custom constructor.

```C++
class Student{
public:
    int age;
    int rollno;

Student() {
	cout << "Constructor Called!\n"; //prints this, everytime we make an object
    age = 2;
    rollno = 10;
}
};

```

- Now if we try to use it in main, it will look something like this:

```C++
#include <iostream>
using namespace std;

#include "./Student.cpp"

int main(){
    Student s1;
    cout << s1.age << " " << s1.rollno << "\n"; // 2 10

    Student s2;
    cout << s2.age << " " << s2.rollno << "\n"; // 2 10
}
```

### Custom constructors with parameters

In the above example we saw how to define a custom constructor and use it to print a statement and perform initialisation. We can also use these constructors with parameters to allow us to assign values that we choose to give. An example is:

- Student File: 

```C++
class Student{
public:
    int age;
    int rollno;

Student(int a, int b) {
    cout << "Constructor Called!\n";
    age = a;
    rollno = b;
}
};

```

- Main file:

```C++
#include <iostream>
using namespace std;

#include "./Student.cpp"

int main(){
    Student s1(11, 40);
    cout << s1.age << " " << s1.rollno << "\n"; // 11 40

    Student s2 (6006, 40);
    cout << s2.age << " " << s2.rollno << "\n"; // 6006 40
}
```

We can use the above format to perform any operation we want.

**NOTE:** If we try to do **Student s1;** without any parameters in the above main function then the program will fail. This is because the default constructor has been disabled as soon as we declare this new one. To solve this problem, we can use 2 constructors. One with parameters and the other without parameters in the same Student Class. The one without the parameters would initialise it with garbage value. Example would be:

- Student File:

```C++
class Student{
public:
    int age;
    int rollno;

Student(int a, int b) {
    cout << "Constructor Called!\n";
    age = a;
    rollno = b;
}
Student(){}
};
```

- Main File: 
```C++
#include <iostream>
using namespace std;

#include "./Student.cpp"

int main(){
    Student s1(11, 40);
    cout << s1.age << " " << s1.rollno << "\n"; // 11 40

    Student s2;
    cout << s2.age << " " << s2.rollno << "\n"; // 13965008 0
}
```