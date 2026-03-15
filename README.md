# StacksQueuesLab
CISC 187 Week 6 Lab
## Task 1 illustrate the result of each operation in the sequence 
### using figure 17 as a model, on an empty stack S stored in an array S[1..6]
Stacks are LIFO Last In First Out
PUSH Inserts element at the end
POP Deletes elements from the end
(S is the stack we are affecting, # is the Value inserting)

Rough ASCII Diagramming for now
#### PUSH(S, 4)
| 4 |  |  |  |  |  |
#### PUSH(S, 1)
| 4 | 1 |  |  |  |  |
#### PUSH(S, 3)
| 4 | 1 | 3 |  |  |  |
#### POP(S) (3 would get removed LIFO)
| 4 | 1 |  |  |  |  |
#### PUSH(S, 8)
| 4 | 1 | 8 |  |  |  |
#### POP(S) (8 Would get removed LIFO)
| 4 | 1 |  |  |  |  |

## Task 2 illustrate the result of each operation in the sequence 
### using figure 18 as a model, on an initially empty queue Q stored in an array Q[1..6]
From Book: FIFO
Same Concept (Q is queue, # is inserted element)
Enqueue takes place at tail, dequeue is element at head
We start with Q.head = Q.tail (ie)empty
Order is Q.head, Q.head+1, ....., Q.tail -1
#### ENQUEUE(Q, 4)
Head = 1
Tail = 1
| 4 |  |  |  |  |  |
#### ENQUEUE(Q, 1)
Head = 1
Tail = 2
| 4 | 1 |  |  |  |  |
#### ENQUEUE(Q, 3)
Head = 1
Tail = 3
| 4 | 1 | 3 |  |  |  |
#### DEQUEUE(Q)
Head = 2
Tail = 3
|  | 1 | 3 |  |  |  |
#### ENQUEUE(Q, 8)
Head = 2
Tail = 4
|  | 1 | 3 | 8 |  |  |
#### DEQUEUE(Q)
Head = 3
Tail = 4
|  |  | 3 | 8 |  |  |

## Task 3 Rewrite ENQUEUE and DEQUEUE to detect underflow and overflow of a queue.

Use pseudocode in book as a baseline to build on top of for these

### ENQUEUE Rewrite

Q[Q.tail] = x
if Q.tail == Q.length
    Q.tail = 1
else Q.tail = Q.tail + 1


Overflow occurs when? If S.top exceeds n
How to detect Overflow. We could have a running counter by passing in an additional parameter to both Push and Pop. If we push we increment the counter by 1, decrement if pop. By doing so we can implement a while statement that says if counter <= n we can continue with our Push operations, if not we notify that the action would cause overflow, and either prompt user to continue with action or stop.

Underflow occus when? If we attempt to pop an empty stack.
Same process with the counter, but we add an if statement to POP that say if n > 0  we can POP. If not we then cout that this would cause underflow.

### DEQUEUE Rewrite

x = Q[Q.head]
if Q.head == Q.length
    Q.head = 1
else Q.head = Q.head + 1
return x

Overflow occurs when?
Q.head = Q.tail + 1 or Q.head = 1 && Q.tail = Q.length. We can set 2 values that track our tail and head, both starting as null values. When we Enqueue we increment our tail by 1, and for the first element added increment the head by 1. If we Dequeue the head increments. We set conditionals that track whether the overflow conditions are met.

Underflow occus when?

If we attempt to dequeue and empty queue. We can use a counter, similar to the Stack option. Just now realizing the questions is asking for queue specific operations. Well... we brainstormed it all so include logic in pseudocode or actual code later. Showing it in C++ might not be to hard either, or take pseudocode Queue logic and just add our extra vars.

## Task 4: Write 4 O(1)-time procedures to insert elements into and delete elements from both ends of a deque implemented array


O(1) time would be iterating through elements once, minimize to one for loop for each operation 
Insertion at beginning

Most likely would have logic from both stack and queue that can be utilized in four operations we could call PUSH POP QUEUE AND ENQUEUE.  We dont have to write flags for under/overflow, so my assumption would be its essentially a hybrid of the two and implementation would be rather simple. If we use a hybrid as the base it would be simply indexing at 0 and -1. But we might want dynamic sorting, so for every element to shift over 1, verify this, or look at existing deque logic. My guess would be a vector could do this, or we can use hashtable logic from last week, although that seems like overkill here. I feel overriding at each index seems a bit trivial of a solution though so dynamic behavior seems the best. Honestly, including code and a termninal screen shot for md that shows print statemetns like: "Inserting at the front" and prints array shifted and new element present seems great for clarity, leaning this direction. Map this out and write later. 
Insertion at end

Deletion at beginning

Deletion at end
