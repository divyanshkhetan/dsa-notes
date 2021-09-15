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