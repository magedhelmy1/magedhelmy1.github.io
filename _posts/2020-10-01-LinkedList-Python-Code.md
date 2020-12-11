---
title: Practice Linked List with Python Code
date: 2020-10-01 14:00:00 +0100
categories: [Blogging, Computer Science]
tags: [linked_list]
---

Question: An implementation of a singly double list

Explanation: Here we have 6 different methods on the class of the linked list. Where you can get, addAthead, addAtTail, addAtindex and deleteAtIndex. Each of these methods perform an action related to the singly linkedList behaviour.

```Python
class MyLinkedList:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.list= []


    def get(self, index: int) -> int:
        """
        Get the value of the index-th node in the linked list. If the index is invalid, return -1.
        """
        if index >= len(self.list):
            return -1
        return self.list[index]


    def addAtHead(self, val: int) -> None:
        """
        Add a node of value val before the first element of the linked list. After the insertion, the new node will be the first node of the linked list.
        """
        self.list= [val] + self.list


    def addAtTail(self, val: int) -> None:
        """
        Append a node of value val to the last element of the linked list.
        """
        self.list.append(val)


    def addAtIndex(self, index: int, val: int) -> None:
        """
        Add a node of value val before the index-th node in the linked list. If index equals to the length of linked list, the node will be appended to the end of linked list. If index is greater than the length, the node will not be inserted.
        """
        if index > len(self.list):
            return

        self.list.insert(index, val)

    def deleteAtIndex(self, index: int) -> None:
        """
        Delete the index-th node in the linked list, if the index is valid.
        """
        if index >= len(self.list):
            return
        del self.list[index]



# Your MyLinkedList object will be instantiated and called as such:
# obj = MyLinkedList()
# param_1 = obj.get(index)
# obj.addAtHead(val)
# obj.addAtTail(val)
# obj.addAtIndex(index,val)
# obj.deleteAtIndex(index)

```
--------------------------
Question: Given a linked list, determine if it has a cycle in it. To represent a cycle in the given linked list, we use an integer pos which represents the position (0-indexed) in the linked list where tail connects to. If pos is -1, then there is no cycle in the linked list.

Explanation: we check if a linked list has a cycle in by creating 2 pointers. A fast runner and a slow runner. When they both meet each other, that means the linkedList is cyclic.

```Python
class Solution:
    def hasCycle(self, head) -> bool:

        fast, slow = head, head

        while fast and fast.next:
            slow= slow.next
            fast= fast.next.next

            if fast == slow:
                return True

        return False
```
--------------------------
Question:Linked List Cycle II: Given a linked list, return the node where the cycle begins. If there is no cycle, return null. To represent a cycle in the given linked list, we use an integer pos which represents the position (0-indexed) in the linked list where tail connects to. If pos is -1, then there is no cycle in the linked list.

Explanation: Similiar to the previous question, we try to find out at which node does the cycle start. For this, we used Floyd's cycle detection method. Where when the fast and slow runner meets, the fast runner is reset to the head, and when it meets the slow runner again, that is the start of the cycle.

```Python
# use Floyd's cycle detection

class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None

class Solution:
    def detectCycle(self, head: ListNode) -> ListNode:
        fast, slow = head, head

        while fast and fast.next:
            slow= slow.next
            fast= fast.next.next

            # where they meet, take the fast back to head
            # the distance between head and the start of the cycle
            # equals the distance between where they met and the start of the cycle
            if fast == slow:
                fast= head

                while fast != slow:
                    fast= fast.next
                    slow= slow.next
                return slow

        return None
```
--------------------------
Question:Intersection of Two Linked Lists: Write a program to find the node at which the intersection of two singly linked lists begins. Notes:
- If the two linked lists have no intersection at all, return null.
- The linked lists must retain their original structure after the function returns.
- You may assume there are no cycles anywhere in the entire linked structure.
- Your code should preferably run in O(n) time and use only O(1) memory.

Explanation: While both linked linkedList do not equal each other, We iterate through the length of one linkedList, and then jump to the other. If they are linked, both linkedList will eventually cross.

```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:

        #return None directly if headA or headB are null
        if not headA or not headB:
            return None

        #keep the original structure of headA and headB by saving them
        savedA, savedB = headA, headB

        # while both values are not equal iterate. When none is reached
        # to one of the lists, go to the other list and iterate from there.
        # if there is a connection they will both meet at the same node

        while headA != headB:
            headA= savedB if not headA else headA.next
            headB= savedA if not headB else headB.next

        return headA
```
--------------------------
Question:Remove Nth Node From End of List: Given a linked list, remove the n-th node from the end of list and return its head.

Explanation: In linkedList, deleting works by skipping the reference connection. Such as

``` second.next = second.next.next
```
We move the first pointer to where we want to delete the node, and then traverse the second node, the same number of steps as the first node when it reaches None/null. This is the node to be deleted and we can skip is using the line shown earlier.

```Python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        first, second = head, head

        #Take the first.next to the position of the node
        for i in range(n):
            first= first.next

        # if first.next is None, then nothing to delete and return the head as is
        if not first:
            return head.next

        # iterate both till null is reached
        while first.next:
            first= first.next
            second= second.next

        # This connects the second.next to second.next.next, by dropping the node
        second.next = second.next.next

        return head

```
--------------------------
Question:Reverse a singly linked list.

Input: 1->2->3->4->5->NULL
Output: 5->4->3->2->1->NULL

A linked list can be reversed either iteratively or recursively. Could you implement both?

Explanation: The first thing we do is create a temprorily variable to store the pointer of the next value using `next= head.next`, we later point this next to the head `head= next`. We then point the the head.next to the previous value `head.next= prev` so we can reverse the arrows. We then point the prev to the current head.

```Python
class Solution:
    def reverseList(self, head: ListNode) -> ListNode:

        prev= None

        # we flip the orientation of the arrow to reverse the list
        while head:
            next= head.next # temp variable to keep track of what is suppose to be next
            head.next= prev # We point the head.next to the prev value
            prev= head # We update the prev value to be the current head
            head= next # We update the head to point next, which was the temp value we created

        reversed = prev
        return reversed


```
--------------------------
Question:   Remove Linked List Elements

Explanation:

```Python
class Solution:
    def removeElements(self, head: ListNode, val: int) -> ListNode:

        dummy = ListNode(None)
        dummy.next = head

        prev = dummy
        curr = head

        while curr:

            if curr.val == val:
                prev.next = curr.next

            else:
                prev = curr

            curr = curr.next

        return dummy.next

```
--------------------------
Question:   Odd Even Linked List

Explanation:

```Python
class Solution:
    def oddEvenList(self, head: ListNode) -> ListNode:

        even_head= ListNode(None)
        even= even_head

        odd_head= ListNode(None)
        odd= odd_head

        while head:
            odd.next= head
            odd= odd.next
            even.next= head.next
            even= even.next

            head= head.next.next if even else None

        odd.next= even_head.next
        return odd_head.next

```
--------------------------
Question:   Palindrome Linked List

Explanation:

```Python
class Solution:
    def isPalindrome(self, head: ListNode) -> bool:
        fast= head
        slow= head
        rev= None
        tmp_slow= None

        while fast and fast.next:
            fast= fast.next.next
            tmp_slow= slow.next
            slow.next= rev
            rev= slow
            slow= tmp_slow

        if fast:
            slow= slow.next

        while slow:
            if slow.val != rev.val:
                return False
            slow= slow.next
            rev= rev.next

        return True

```
--------------------------
Question:
Explanation:

```Python


```
--------------------------
Question:
Explanation:

```Python


```
--------------------------
