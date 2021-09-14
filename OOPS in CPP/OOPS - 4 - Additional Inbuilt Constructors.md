We have already learnt about default constructors. Apart from that we have a few more constructors and its functions which can be quite useful in real life. Let's start with it.

### 1. Copy Constructors

Suppose we have to objects **Student s1** and **Student s2**, and we want the data members of **s2** to have the same values as that of **s1**, then we can use the copy constructor to copy the values of an already existing object into a new object. This can be done as follows:

```C++
Student s2(s1);
```
This is an inbuilt operation so we do not need to define anything regarding this in the class file.

It is worthwhile noting that in case of pointers/dynamically allocated objects we need to do the following:

```C++
Student *s3 = new Student(s1);

// and to copy a dynamically allocated object to another dynamically object we can do the following:

Student *s4 = new Student(*s3);	
```

### 2. Copy Assignmnet Operator

In case of the **Copy Constructor**, we need to copy the previous object to the new object at the time of declaration itself. But whatif we want to copy an object to another object that already exist? This is where copy assignment operator comes in handy and it is very simple to use.

```C++
Student s1, s2;
s1 = s2;

Student *s3 = new Student;
Student *s4 = new Student;
*s3 = s1;
*s4 = *s3;
```

### 4. Destructors

Destructors are the functions that are used to delete an object (by default, at the end of the program) to free the system memory. Few of the properties are:

- Same name as Class name
- No return type
- No input arguments

In C++, we are allowed to invoke a destructor anytime we want. By default, it is invoked at the end of the program.

```C++
Student s1;

// some code

delete s1;

// some code
```


We can also define our own destructor, i.e., a user defined constructor. We use tilde symbol to define a destructor (**~**). An example of the syntax is given below:

```C++
~Student() {
 cout << "Destructor called!";
}
```
