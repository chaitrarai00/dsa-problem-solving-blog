---
title: Check if a given Binary Tree is a Binary Search Tree
date: "2021-07-23T22:40:32.169Z"
description: Check if a given Binary Tree is a Binary Search Tree
---

##Problem Statement is to Check if a given Binary Tree is a Binary Search Tree

> We will try to solve this problem recursively

> We will have a maximum value and a minimum value for each node we traverse in

> For any node we take all the values to the left is less than it which means that the maximum value would be the value at the node

> For any node we take all the values to the right is more than it which means that the minimum value would be the value at the node

```java
class BinaryTree {
    static Node root;
    static class Node{
        int data;
        Node left;
        Node right;
        Node(int value){
            data=value;
            left=null;
            right=null;
        }
    }

    boolean isValid(Node root){
        return isvalidate(root,null,null);
    }

    private boolean isvalidate(Node node, Integer max, Integer min){
        if(node==null){
            return true;
        }
        else if((max!=null && node.data>=max)||(min!=null && node.data<=min)){
            return false;
        }
        else{
            return isvalidate(node.left,node.data,min)
            && isvalidate(node.right,max,node.data);
        }
    }

	public static void main (String[] args) {
	    BinaryTree tree= new BinaryTree();
	    tree.root=new Node(3);
	    tree.root.left=new Node(2);
	    tree.root.left.left=new Node(1);
	    tree.root.right=new Node(4);
	    tree.root.right.right=new Node(5);
	    System.out.println(tree.isValid(root));
	}
}
```

##The Time Complexity would be O(n) as each node is traversed and checked for once.
