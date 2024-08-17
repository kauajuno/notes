Being honest, pointers are the single most headache-causing concepts in programming specially if you are a beginner. However, once you understand the concept, everything surrounding it sound much easier, eventually it becomes somehow natural.

Not every language offer you the possibility to manipulate pointers, as they offer a lot of control over the memory management that can let to unsafe situations, such as memory access, memory leaks, etc. Some of the programming languages that let the programmer use pointers are C, C++, Go, C# and Rust.

**A pointer is a variable that stores the memory address as its value.** At first it sounds pointless, but there's a lot of use to it once you start to deal with complex [[Data structures|data structures]] and its operations.

```cpp
#include<iostream>

using namespace std;

int main(){
	int age = 23;
	int *address = &age;
	cout << age << '\n'; // always 23
	cout << address << '\n'; // might change
	cout << *address << '\n'; // always 23
	return 0;
}
```

You might notice that every time you run this code, the output for the address is different, because each time a random location is selected for the variable to be stored in.

# Pointers as references to [[Array|arrays]]

Pointers become much easier to understand once you've dominated the concept of [[Array|arrays]]. Arrays are stored contiguously in the memory. So, if the first element is in a slot in the memory, the second element is the one right after it, the third the one right after the second, and so on.

The main point here is that they are stored contiguously, so if we create a pointer containing the address to the first element of the array, it's really easy to navigate through all the elements of that array.

```cpp
#include<iostream>

using namespace std;

int main(){
    int arr[5] = {1, 2, 3, 4, 5};
    int *ptr = arr;

    for(int i = 0; i < 5; i++){
        cout << *ptr << '\n'; // prints the value to which the address points
        ptr++; // goes to the next slot in memory
    }
}
```

# Pointers as a way to change variables passed as a parameter

When passing a variable as a parameter, it's created a copy of that variable as a parameter, so it's impossible to change its value if the variable itself is passed.

```cpp
#include <iostream>

using namespace std;

void swap(int x, int y)
{
    int aux = x;
    x = y;
    y = aux;
}

int main()
{

    int x = 2, y = 4;

    swap(x, y);

    cout << x << '-' << y << '\n'; // 2-4

    return 0;
}
```

However, when the address to that value we want to change it's passed, it doesn't matter if the address is a copy or not, because the access to the value that is in fact intended to change is now obtained.

```cpp
#include <iostream>

using namespace std;

void swap(int *x, int *y)
{
    int aux = *x;
    *x = *y;
    *y = aux;
}

int main()
{

    int x = 2, y = 4;

    swap(&x, &y);

    cout << x << '-' << y << '\n'; //4-2

    return 0;
}
```

These parameters might get rather confusing when dealing with [[Linked List]] operations, as the complexity of the operations are much bigger.

# Pointers as a way to increase performance when passing memory-heavy entities as a parameter

It's much faster to pass a 8-byte pointer to something (let's suppose, a array of size 9999) than to create a copy of that same thing every time the function is called.

```cpp
#include <iostream>
#include <time.h>

using namespace std;

void iterate(int arr[], int size)
{
    for (int i = 0; i < size; i++)
    {
        cout << arr[i] << ' ';
    }
}

void iteratePointer(int *arr, int size)
{
    for (int i = 0; i < size; i++)
    {
        cout << arr[i] << ' ';
    }
}

int main()
{

    clock_t start, end;

    int arr[9999];

    for (int i = 0; i < 9999; i++){
        arr[i] = rand();
    }

    start = clock();
    iterate(arr, 9999);
    end = clock();

    cout << "\n\n\n\n"
         << ((double)(end - start)) / CLOCKS_PER_SEC << "\n\n\n\n";

    start = clock();
    iteratePointer(arr, 9999);
    end = clock();

    cout << "\n\n\n\n"
         << ((double)(end - start)) / CLOCKS_PER_SEC << "\n\n\n\n";

    return 0;
}
```

For the example above, that uses a relatively small array, the function using reference parameter passage works usually 2x faster, that difference tends to get much bigger as the function receives larger parameters and is used more often.
