Queue follows FIFO - First In First Out and Stack follows LIFO - Last In First Out
push() - Insert the element in the stack.
pop() - Remove and return the topmost element of stack.
top() - Return the topmost element of the stack. 
size() - Return the size of the stack.

#### Solution 1: Using two Stacks where push operation is O(N)

![[Pasted image 20250315124935.png]] 
###### push(x) :
![[Pasted image 20250315130522.png]]
###### pop() -
![[Pasted image 20250315130606.png]]
###### top() -
###### ![[Pasted image 20250315130613.png]]size() - size() operation is for returning the size of a queue which can be done by using the function Stack1. size(). It will actually return the total number of elements in the queue.

### Code 

```cpp
#include <bits/stdc++.h>

using namespace std;

struct Queue {
  stack < int > input, output;
  
  // Push elements in queue
  void Push(int data) {
    // Pop out all elements from the stack input
    while (!input.empty()) {
      output.push(input.top());
      input.pop();
    }
    // Insert the desired element in the stack input
    cout << "The element pushed is " << data << endl;
    input.push(data);
    // Pop out elements from the stack output and push them into the stack input
    while (!output.empty()) {
      input.push(output.top());
      output.pop();
    }
  }
  // Pop the element from the Queue
  int Pop() {
    if (input.empty()) {
      cout << "Stack is empty";
      exit(0);
    }
    int val = input.top();
    input.pop();
    return val;
  }
  // Return the Topmost element from the Queue
  int Top() {
    if (input.empty()) {
      cout << "Stack is empty";
      exit(0);
    }
    return input.top();
  }
  // Return the size of the Queue
  int size() {
    return input.size();
  }
};
int main() {
  Queue q;
  q.Push(3);
  q.Push(4);
  cout << "The element poped is " << q.Pop() << endl;
  q.Push(5);
  cout << "The top of the queue is " << q.Top() << endl;
  cout << "The size of the queue is " << q.size() << endl;
}
```

Time Complexity = O(N)
Space Complexity = O(2N)

#### Solution 2: Using two Stacks where push operation is O(1)

**Push()->**

**![](https://lh5.googleusercontent.com/cyrQpSoer5LXYHsWlE7EexruYcBcHOOYR6dFWVhwG8ZhIV0N6ZQ5BqGYaVQnxCfe86bL999w7DRTK0xNLGzapCvDUnc-IdwN24arTdyFTpuO5Wx4Mx5V4K2b86s7d1ZApLvfRz8n)**

**Pop()->**

![](https://lh6.googleusercontent.com/SCtOoeI2c7RfhqiTJ04h6S6ypvD8D56X0xADIHJp4kkLqjjpA_9Hh0cSSWVS1ud-NPhaRNjt91tGE_vkYHU5oh7dW7-96M3xW44RcafiX-EcsJAoF3ux45ntrB7bi4Xadx-Px1eY)

![](https://lh3.googleusercontent.com/AlCUaPu7QOThJqIXiiUvOaxxft_GrbLZZf4WmSEOqjJmPUJjLzjzrCxQdi18kyQc_Q97lkazuL-H07ciVUrvZ_KCXY8nnH6YjyEw9I4KhYXuzT8wmoW1IGmUmnu8gOaTb3yfy94k)

**top()**->

![](https://lh4.googleusercontent.com/hHNIa47YcwkZ0h9M94cxYBIuLl89TP8TJkbPOJcXcC5TWFNxlTtFWR8wq454ab4ShPK44w9LRUAZBsH3CN8kiF96LlxxqqyBlMnsYhVzj09zjbS6jAOF-oaoyjVPGLLQZJGSISfN)

![](https://lh3.googleusercontent.com/45nuKRNKUuc90kPtPB-iF9rna58jlPvHuceM1c5vo2IVsFB1E5JeWsaFRUboa7BNrVdzpAvGjvqxIw8gm3_Ssb7XncavzVU_iVLvVtuAvO084cFcIHZt91YlPYAxHdu1AwT6uyee)

**Size():**

**![](https://lh5.googleusercontent.com/wZaLy37CL0kx0VtN73DmjmiSuvHjSdPlzS3BNIfnbZz8i5QtLao1Mjb6QoVJCy53OCczCVHs3f5GCeHkYUqimJI_aT_oXp_HKZ1HThaqjcskYfQCINjq1qsjxQlTJIgwCR3W4J8X)

**Code** -
```cpp
#include <bits/stdc++.h>

using namespace std;

class MyQueue {
  public:
    stack < int > input, output;
  /** Initialize your data structure here. */
  MyQueue() {

  }

  /** Push element x to the back of queue. */
  void push(int x) {
    cout << "The element pushed is " << x << endl;
    input.push(x);
  }

  /** Removes the element from in front of queue and returns that element. */
  int pop() {
    // shift input to output 
    if (output.empty())
      while (input.size())
        output.push(input.top()), input.pop();

    int x = output.top();
    output.pop();
    return x;
  }

  /** Get the front element. */
  int top() {
    // shift input to output 
    if (output.empty())
      while (input.size())
        output.push(input.top()), input.pop();
    return output.top();
  }

  int size() {
    return (output.size() + input.size()); 
  }

};
int main() {
  MyQueue q;
  q.push(3);
  q.push(4);
  cout << "The element poped is " << q.pop() << endl;
  q.push(5);
  cout << "The top of the queue is " << q.top() << endl;
  cout << "The size of the queue is " << q.size() << endl;

}
```

Time Complexity - O(1)
Space Complexity - 0(2N)
