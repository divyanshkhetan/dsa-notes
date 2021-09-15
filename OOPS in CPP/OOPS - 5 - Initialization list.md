### Initialization List

Sometimes we use a variable throughout a function but we only read its value throughout the function and do not modify it. So, in a scenario like this it is best that we use such a copy of the original value of such list which is non-mutable. We can do this by using a constant variable type.

```C++
const int age = 50;

// OR

int const age = 50;
```

Both the syntax formats are correct. But a major constraint that arises with const-type variables is that it needs to be initialized at the time of its declarations. This means that the following will result in an error:

```C++
const int age;

// OR 

int const age;
```

You might be asking why is this a problem? Consider the following class:


```C++
class Student{
	private:
		int rollno;
		const int age;
	public:
		void display(){
			cout << rollno << " " << age << "\n";
		}
};
```

This would result in an error because we did not initialize **age** at the time of its declaration and we are using it without initialization.

To solve this problem we use a concept of initialization list. This is how we use it:

```C++
class Student{
private:
	int rollno;
	const int age;
	int &x;
public:
	Student(int rollno, int age) : rollno(rollno), age(age), x(age){
		// some code or maybe empty
	}

	void display() {
		cout << rollno << " " << age << " " << x << "\n";
	}
};
```

This will not throw any error. It is worthwhile to note that initialization lists can only be used in constructors.

---

### Reference Variable

Suppose we have a variable **int i = 10;** and we need a variable through which we can access i **by-reference**. You might think that we can do it by using pointers. But the problem with pointers is that we need to deferenece it everytime we need to use it. There is an alternative to this. It's called reference variable and it is used like this:

```C++
int &ref_variable = i;

// Now ref_variable points to the location of i and any changes made to ref_variable is reflected in i and vice-versa.

// We can use ref_variable without dereferencing it.

cout << ref_variable;
```

**NOTE:** Just like const variables, we need to intialize it at the time of declaration.

**NOTE 2:** We can surpass the constraint mentioned in NOTE 1 by the use of initialization list.