**Problem Statement:**  Implement Queue using Singly LinkedList

**Queue Can be Implemented in two ways :** 

1. Static Implementation (Using Arrays)
2. Dynamic implementation (Using LinkedList) .

In this article, we would discuss the implementation of queue using LinkedList.

**Comparison between Implementation of Queue using LinkedList and Array.**

|                                                                                                                                 |                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Array**                                                                                                                       | **LinkedList**                                                                                                                                                     |
| It is Static, Needs to provide space Before implementation.    <br>Overflow occurs when queue size reaches its maximum capacity | Nodes are allocated dynamically, so the queue can grow and shrink as much as needed.  <br>Overflow is not possible until and unless the heap memory got exhausted. |

**Operations Associated with queue are :**

1. Enqueue     (Insert Node at Rare End )
2. Dequeue     (Delete Node from Front ) 
3. Peek            (Return value of Front Node without Dequing)
4. Empty         (Returns True when queue is empty else False)
5. Size             (Returns size of Queue) 

**Let the Initial Queue be 10→20→30→40→Null.**

### **Enqueue:** 

Let’s Enqueue Node with val 50 to Queue. Enqueue is 3 step process 

- Create a node with a value that is to be Enqueued.
- Make the Rare Pointers next, point to the newly created Node.
- As the newly created Node is inserted at the rear end, this is the last value in Queue.

![](https://lh4.googleusercontent.com/N0KDcMiut6Hh3ZUl4aYewhSPFzcB6DER7mnLYT7hEr5vrVBhlDWUz51VGaEuVLJFWvY32KYIU_G1ESOSBanIYPBdhAfLmlKfkMZsyojLEsWaPqEDy5jHel56byM4JUEXijmH4JNa)

### **Dequeue :**

Let’s Dequeue the front value that is, 10 from Queue.

- First create a ListNode pointer temp, and make it point to the Front value of Queue.
- We should delete the Front Value in Queue. So move the Front pointer to the next node after Front Node. That means Front = Front→next 
- Temp is pointing to the previous Front value, temp→next is pointing to the newFront value, as we are interested to delete the temp, Make the temp→next point null.
- We don’t require temp anymore, So delete the temp.

![](https://lh5.googleusercontent.com/HAusTSjp3VCUQwAb1vx1FXqJ9zUMm1dZKAamL3Qkd9cooJsw_OcVL3YGfgxUkfn1kkwo5lSk0jhOK15gUu8e6AsLS9h7HYSo6pSu8jviJ9oIlJf8RWrVyfMjJ2KWjWUpLmfSn61S)

### **Peek:** 

If Queue is not empty return Front value of Queue.

### **Empty:** 

If Front is Null then Queue is empty else not.

### **Size:** 

Maintain a variable size, initially set to zero. Upon Enqueue increment size and on Dequeue decrement size

```cpp
#include<bits/stdc++.h> 
using namespace std;

class QueueNode
{
 public: 
    int val;
    QueueNode *next;
    QueueNode(int data)
    {
       val = data;
       next = nullptr;
    }
};  
QueueNode *Front = nullptr, *Rare = nullptr;

class Queue
{
public:
    int size = 0;
    bool Empty();
    void Enqueue(int value);
    void Dequeue();
    int Peek();
};  
bool Queue ::  Empty()
{
    return Front == nullptr;
}  
int Queue :: Peek()
{
    if(Empty())  
     {  cout<<"Queue is Empty"<<endl;
        return -1;
     } 
    else 
      return Front->val;
}   
void Queue :: Enqueue(int value)
{
    QueueNode *Temp;
    Temp = new QueueNode(value); 
    if (Temp == nullptr)  //When heap exhausted 
        cout << "Queue is Full" << endl;
    else
    {
        if (Front == nullptr)
        {
            Front = Temp;
            Rare = Temp;
        } 
        else
        {
            Rare->next = Temp;
            Rare = Temp;
        }
        cout<<value <<" Inserted into Queue "<<endl;
        size++;
    } 
}      
void Queue :: Dequeue() 
{
    if (Front == nullptr) 
        cout << "Queue is Empty" << endl;
    else
    { 
        cout<<Front->val <<" Removed From Queue"<<endl;
        QueueNode *Temp = Front;
        Front = Front->next;
        delete Temp;
        size--;
    }  
}   
int main()

{
    Queue Q;
    Q.Enqueue(10);
    Q.Enqueue(20);
    Q.Enqueue(30);
    Q.Enqueue(40);
    Q.Enqueue(50);
    Q.Dequeue();
    cout<<"The size of the Queue is "<<Q.size<<endl;
    cout<<"The Peek element of the Queue is "<<Q.Peek()<<endl;
    return 0;
}   
```
