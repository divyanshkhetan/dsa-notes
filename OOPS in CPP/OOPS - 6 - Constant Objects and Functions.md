### Constant Objects and Functions

Just like we define constant variables, we can also define constant Objects. For eg,

```C++
const Student s1(12, 22);  // parameters are (rollno, age)
```

A constant object is an object in which we can only call constant funtions, i.e., the functions which can only read the values from a variable and not modify them. C++ is not smart enough to identify which functions is a constant function and which is not. (I tired this on my compiler). You need to explicitly tell C++ whether a function is constant or not. Take a look at below example: 

```C++
class Student{
private:
    int rollno;
    int age;
public:
    Student(int rollno, int age){
        this -> rollno = rollno;
        this -> age = age;
    }

    void display() const{
        cout << rollno << " " << age << "\n";
    }

    int getAge() const{
        return age;
    }
};
```

I have defined the functions as constant with the **const** keyword. You will need to do the same. If you try to omit the **const**, it will throw an error. And if you try to add **const** to a function which changes the state (value) of a variable, then also it will throw an error. For eg,

```C++
void sum() const {
	age = age + rollno;
}
```

If you try to do something like this, it will throw an error.

**NOTE:** It is worthwhile noting that merely the presence of this function in the class will give you an error. It does not matter whether you call it or not. (I tried this too on my compiler. Infact almost everything in these notes has been checked.)

---

I found an example online. It will give you more clarity on the topic.

```C++
#include <iostream>

using namespace std;

class Student {
    private:
    	int rollNo;
	public:
    	int age;

    public :

	    Student(int roll) {
	        rollNo = roll;
	    }

	    int getRollNumber() {
	        return rollNo;
	    }
};

int main() {
    Student s1(101);
    s1.age = 20;

    Student const s2 = s1;
    cout << s2.getRollNumber();
}
```

What should be the output for this? It should return an error because we have try to access a non-constant function (**getRollNumber()**) in a constant object (**s2**). This proves that C++ is not intelligent enough to distinct between const and non-const functions. But if the print statement was just **cout << s2.age();** then it would not return any error since we did not invoke the non-constant function so it would work fine.

But if we declare **getRollNumber()** as a **const** then it would work just fine.

```C++
#include <iostream>

using namespace std;

class Student {
    private:
    	int rollNo;
	public:
    	int age;

    public :

	    Student(int roll) {
	        rollNo = roll;
	    }

	    int getRollNumber() {
	        return rollNo;
	    }
};

int main() {
    Student s1(101);
    s1.age = 20;

    Student const s2 = s1;
    cout << s2.getRollNumber();
}
```

Hope you understand this now.