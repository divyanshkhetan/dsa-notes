# this Keyword

Suppose in the student class we have the following code:

```C++
class Student{
public:
	int rollno;
	int age;

	Student(int age){
		age = age;
	}
}
```

Now suppose if we declare an object with the following code:

```C++
Student s1(21);
cout << s1.age;
```

#### What will be printed?

This will give an error. Why?

Because we try to assign age to age in the parameterized-constructor of the student class.

```C++ 
age = age;
```

The compiler doesn't know that we are trying to do **s1.age = age;**. This is where the **this** keyword comes in handy.

### this keyword

**this** keyword holds the address of the object to which the constructor is called. So, basically **this** is a pointer that points to the address of **s1**. If we try to do **cout << this;** in the constructor, it will print the address of s1. So, we can use it to solve the above problem as:

```C++
this -> age = age;
```

**Notice that we used arrow operator since *'this'* is a pointer to s1.**