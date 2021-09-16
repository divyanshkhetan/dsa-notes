### Operator Overloading

Suppose we have a structure for complex numbers and we want to add two complex numbers and store it in a third complex number. You would say that we can define an add() function and use it to return an object. You are right. It would look something like this:

```C++
Complex n3 = add(n1, n2);
```

What if I tell you that we can do something like this:

```C++
Complex n3 = n1 + n2;
```

The native '+' operator does not support using it in such a fashion. We need to define a new method for this operation in our class file so that we can use it like this. This is called operator overloading.

```C++
class Complex{
public:
	int real;
	int imaginary;

	Complex(int r, int i){
		real = r;
		imaginary = i;
	}

	void display() const{
		cout << real << " + " << imaginary << "i\n";
	}

	Complex operator+(Complex &n2) const{
		int real = this -> real + n2.real;
		int imaginary = this -> imaginary + n2.imaginary;

		Complex n3(real, imaginary);
		return n3;
	}
};
```

This is the main file:

```C++
#include <iostream>
using namespace std;

#include "./Complex.cpp"
int main(){
    Complex n1(1, 1);
    Complex n2(2, 2);
    Complex n3 = n1 + n2;
    n3.diplay();
}
```

The first operand, i.e., **n1** is passed as **this** and the second operand, i.e., **n2** is passed as argument.

I hope you understood how to use operator overloading. You can do the same for ==, multiplication, power, etc. 
