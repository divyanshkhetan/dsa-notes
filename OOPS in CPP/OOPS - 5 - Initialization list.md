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

