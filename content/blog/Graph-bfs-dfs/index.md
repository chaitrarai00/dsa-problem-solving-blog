---
title: Graphs BFS and DFS
date: "2021-07-23T22:40:32.169Z"
description: Find if a Path exists and a Shortest Path in a Graph
---

##Problem Statement is to Find if a Path exists and a SHortest Path in a Graph using BFS and DFS

> BFS is used to find the shortest path and goes spreading breadth wise

> It takes extra memory to keep track of how each node is reachable

> BFS can be traversed using queue

```java
class Graph {
	private LinkedList<Integer> adjacent[];
	Graph(int vertices){
	    adjacent= new LinkedList[vertices];
	    for(int i=0;i<vertices;i++){
	        adjacent[i]=new LinkedList<Integer>();
	    }
	}

	void addEdges(int source, int destination){
	    adjacent[source].add(destination);
	    adjacent[destination].add(source);
	}

	int bfs(int source, int destination){
	 boolean[] visited_nodes= new boolean[adjacent.length];
	 int[] parent_toreach=new int[adjacent.length];
	 Queue<Integer> q=new LinkedList();
	 visited_nodes[source]=true;
	 parent_toreach[source]=-1;
	 //mark the source node as not reached by any but a starting point
	 q.add(source);
	 while(!q.isEmpty()){
	     int curr=q.poll();
	     if(curr==destination) break;
	     for(int neighbour: adjacent[curr]){
	         if(!visited_nodes[neighbour]){
	            visited_nodes[neighbour]=true;
	            parent_toreach[neighbour]=curr;
	            q.add(neighbour);
	         }
	     }
	 }
	 int curr=destination; //to iterate and get the shortest path and distance
	 int distance=0;
	 System.out.println("Shortest Path from "+source+" and "+destination);
	 while(parent_toreach[curr]!=-1){
	     System.out.print(curr+"->");
	     curr=parent_toreach[curr];
	     distance++;
	 }
	 return distance;
	}
	public static void main (String[] args) {
	    Graph g=new Graph(6);
	    g.addEdges(0,1);
	    g.addEdges(0,3);
	    g.addEdges(1,2);
	    g.addEdges(3,2);
	    g.addEdges(2,4);
	    g.addEdges(2,5);
	    System.out.println("Shortest Path distance "+g.bfs(0,2));
	}
}
```

> DFS is more memory efficient and is used just to find it there is a path existing

> Its used to just find the path existance and goes through nodes and backtracks if needed

> DFS can be implemnted using stack

```java
class Graph {
	private LinkedList<Integer> adjacent[];
	Graph(int vertices){
	    adjacent= new LinkedList[vertices];
	    for(int i=0;i<vertices;i++){
	        adjacent[i]=new LinkedList<Integer>();
	    }
	}

	void addEdges(int source, int destination){
	    adjacent[source].add(destination);
	    adjacent[destination].add(source);
	}

	boolean dfs(int source, int destination){
	 boolean[] visited_nodes= new boolean[adjacent.length];
	 Stack<Integer> stack=new Stack<Integer>();
	 visited_nodes[source]=true;
	 stack.push(source);
	 while(!stack.isEmpty()){
	     int curr=stack.pop();
	     if(curr==destination) return true;
	     for(int neighbour:adjacent[curr]){
	         if(!visited_nodes[neighbour]){
	             visited_nodes[neighbour]=true;
	             stack.push(neighbour);
	         }
	     }
	 }
	 return false;
	}

	public static void main (String[] args) {
	    Graph g=new Graph(6);
	    g.addEdges(0,1);
	    g.addEdges(0,3);
	    g.addEdges(1,2);
	    g.addEdges(3,2);
	    g.addEdges(2,4);
	    //g.addEdges(2,5);
	    System.out.println("Path exists? "+g.dfs(0,4));
	     System.out.println("Path exists? "+g.dfs(0,5));
	}
}
```
