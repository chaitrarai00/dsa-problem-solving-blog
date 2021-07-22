---
title: Reverse a Linked List
date: "2021-07-22T22:40:32.169Z"
description: find the reverse of a given linked list
---

##Reversing a Linked List

> First using the iterative approach

> Create a class Linkedlist with a static head: a common start point

> Create a common class Node a static one with a data for holding list value and a next node to point to the value next to it

> Now the way to reverse the list is to make the pointers pointing to the next values point to the previous value

> we take 3 node placeholders a current, a previous and the next

> for every current the previous and next is changed,i.e, the pointer to the next node is changed to point to the previous

> Remember to store the next values of current in the next placeholder so that is not lost

```java
class LinkedList {
    static Node head;
    static class Node{
        int data;
        Node next;
        Node(int value){
            data=value;
            next=null;
        }
    }

    Node reverseLinkedlist(Node head){
        Node prev=null;
        Node curr=head;
        Node next=null;
        while(curr!=null){
            next=curr.next;
            curr.next=prev;
            prev=curr;
            curr=next;
        }
        head=prev;
        return head;
    }

    void printLinkedlist(Node node){
        while(node!=null){
            System.out.print(node.data+"->");
            node=node.next;
        }
    }

	public static void main (String[] args) {
	    LinkedList list=new LinkedList();
	    list.head=new Node(1);
	    list.head.next=new Node(2);
	    list.head.next.next=new Node(3);
	    list.head.next.next.next=new Node(4);
	    list.head.next.next.next.next=new Node(5);
	    System.out.println("Given List: ");
	    list.printLinkedlist(head);
	    System.out.println("");
	    head=list.reverseLinkedlist(head);
	    System.out.println("List Reversed: ");
	    list.printLinkedlist(head);
	}
}
```

###Time complexity of the problem is O(n), to traverse is node for n elements
