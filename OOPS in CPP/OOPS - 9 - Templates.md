### Templates

Take a look at the following class file and main file respectively:

```C++
class temp{
private:
	int x;
	int y;

public:
	void setX(int x){
		this -> x = x;
	}
	void setY(int y){
		this -> y = y;
	}

	int getX(){
		return x;
	}
	int getY(){
		return y;
	}
};
```

Main file:

```C++
#include <iostream>
#include "./temp.cpp"

using namespace std;

int main(){
    temp t1;
    t1.setX(5);
    t1.setY(15);

    cout << t1.getX() << " " << t1.getY();

    return 0;
}
```

Now what if we want to get **double x, y** instead of **int x, y** in the class file? Or maybe **int x and double y**? We would need to create seperate classes for all these datatypes. But we have a solution to this problem in the form of templates. 

What a template does is that it acts as a placeholder for datatype-keywords like **int**, **double**, **char**, etc. Then when we create an object of that class, we specify the datatypes we need in place of those placeholders. We can understand more with the help of this example:

```C++
template <typename T, typename V>

class temp{
private:
	T x;
	V y;
	T z;

public:
	void setX(T x){
		this -> x = x;
	}
	void setY(V y){
		this -> y = y;
	}

	T getX(){
		return x;
	}
	V getY(){
		return y;
	}

	T getZ(){
		return z;
	}
};
```

We have created two placeholders **V** and **T**. Now whatever datatype we provide it while creating its object, that will be used in place of these placeholders. For eg:

```C++
#include <iostream>
#include "./temp.cpp"

using namespace std;

int main(){
    temp<int, double> t1;
    t1.setX(5);
    t1.setY(15.1);

    cout << t1.getX() << " " << t1.getY() << " " << t1.getZ(); // 5 15.1 garbage

    return 0;
}
```

You can observe that we passed **int** and **double** in the parameters in while creating an object. So, this would result in **X and Z** being of type **int** and **Y** being of type **double**. This is how we use.

Templates allow us to create a class without providing a datatype at the type of creation of class so that we can use it however we want when we create its object. This gives us much more flexibility and allows much more reusibility of code. 

*We just need to use a template variable instead of a datatype throughout the program in the desired places and the compiler would compile it without andy problem.*

This is most commonly used in application of trees and graphs.