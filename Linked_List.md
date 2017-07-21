## Linked List

### advantage

- Linked lists are a dynamic data structure, which can grow and be pruned, allocating and deallocating memory while the program is running.
- Insertion and deletion node operations are easily implemented in a linked list.
- Dynamic data structures such as stacks and queues can be implemented using a linked list.
- There is no need to define an initial size for a Linked list.
Items can be added or removed from the middle of list.

### Disadvantages
- They use more memory than arrays because of the storage used by their pointers.
- Nodes in a linked list must be read in order from the beginning as linked lists are inherently sequential access.
- Nodes are stored incontiguously, greatly increasing the time required to access individual elements within the list, especially with a CPU cache.
- Difficulties arise in linked lists when it comes to reverse traversing. For instance, singly linked lists are cumbersome to navigate backwards[1] and while doubly linked lists are somewhat easier to read, memory is consumed in allocating space for a back-pointer.

### strategy 
1. Use **dummy node** if involving operations about head node
2. Use of **two pointers**:
    - find the middle node fast:
        - set **fast** and **slow** node pointing to the head
        - **fast** moves twice the step as **slow**
        - when **fast** gets the end, **slow** points to the middle
    - check if there is a circle in the linked list
        - set **fast** and **slow** node pointing to the head
        - **fast** moves twice the step as **slow**
        - if **fast** == null, it doesn't have circle
        - if **fast** == **slow**, it has
        - [linked list circle](https://leetcode.com/problems/linked-list-cycle/?tab=Description)
    - Use **two pointers** to traverse the linked list in different speed when finding particular position in linked list
3. Take care of **next** pointer when traversing the linked list in order to reverse the list

### Example
1. Swap two adjacent node:

Record the next node of second node first, then change the pointer in this order: former node->second node->first node:

```
while head and head.next:
    # record the next node
    nextnode = head.next.next
    # swap nodes, start from former
    former.next = head.next
    head.next.next = head
    head.next = nextnode
    
    former = former.next.next
    head = nextnode
```

https://leetcode.com/problems/swap-nodes-in-pairs/?tab=Description

2. Reverse a linked list:
- recursive solution:
    
```py
class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head or not head.next:
            return head
        p = self.reverseList(head.next)
        head.next.next = head
        head.next = None
        return p
```


- iterative solution:
    
```js
var reverseList = function(head) {
    var newHead = null;
    var next;
    while(head !== null){
        next = head.next;
        head.next = newHead;
        newHead = head;
        head = next;
    }
    return newHead;
};
```
