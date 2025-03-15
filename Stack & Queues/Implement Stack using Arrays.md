Stack following LIFO - Last In First Out
push() - Insert the element in the stack
pop() - Remove and return the topmost element in stack
top() - Return the topmost element in the stack 
size() - Return the number of remaining elements in the stack 
### Approach 
###### Declare an array of particular size 
###### Define a variable "Top" and initialize it as -1 
###### push(x) - insert element in array by increasing top by one
###### pop() - check whether top!= -1 , return top and decrease its value by one 
###### size() - return top+1

### Code 

```cpp
#include<bits/stdc++.h>

using namespace std;
class Stack {
  int size;
  int * arr;
  int top;
  public:
    Stack() {
      top = -1; // Initialize top as -1 
      size = 1000; 
      arr = new int[size]; // Define array 
    }
  void push(int x) {
    top++; // Increment top --> -1 to 0 => top[0] = x
    arr[top] = x;
  }
  int pop() {
    int x = arr[top]; // First check if top!= -1 ==> return top 
    top--; // decrease top by 1 
    return x;
  }
  int Top() {
    return arr[top];
  }
  int Size() {
    return top + 1;
  }
};
int main() {

  Stack s;
  s.push(6);
  s.push(3);
  s.push(7);
  cout << "Top of stack is before deleting any element " << s.Top() << endl;
  cout << "Size of stack before deleting any element " << s.Size() << endl;
  cout << "The element deleted is " << s.pop() << endl;
  cout << "Size of stack after deleting an element " << s.Size() << endl;
  cout << "Top of stack after deleting an element " << s.Top() << endl;
  return 0;
}
```


Time Complexity = O(N)
Space Complexity = O(N)