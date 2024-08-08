Here's a code implementation of a [[Linked List]] in Java.

```java
package com.github.kauajuno.ds;  
  
public class LinkedList {  
    Node head;  
  
    public static class Node{  
        int val;  
        Node next;  
  
        Node(int val){  
            this.val = val;  
            this.next = null;  
        }  
    }  
  
    public void insertAtBegin(int value){  
        Node new_node = new Node(value);  
  
        if(this.head == null){  
            this.head = new_node;  
            return;  
        }  
  
        new_node.next = head;  
        head = new_node;  
    }  
  
    public void insertAtEnd(int value){  
        Node new_node = new Node(value);  
  
        if(this.head == null){  
            this.head = new_node;  
            return;  
        }  
  
        Node aux = this.head;  
  
        while(aux.next != null){  
            aux = aux.next;  
        }  
  
        aux.next = new_node;  
    }  
  
    public Node getNode(int value){  
        Node aux = this.head;  
        while(aux != null){  
            if(aux.val == value){  
                return aux;  
            }  
            aux = aux.next;  
        }  
        System.out.println("ALERT: NODE NOT FOUND");  
        return null;  
    }  
  
    public void insertAfter(Node prev, int val){  
        if(prev == null){  
            System.out.println("ALERT: PREV NODE CANNOT BE NULL");  
            return;  
        }  
  
        Node aux = new Node(val);  
        aux.next = prev.next;  
        prev.next = aux;  
    }  
  
    public void traversal(){  
        Node aux = this.head;  
  
        while(aux != null){  
            System.out.print(aux.val + " -> ");  
            aux = aux.next;  
        }  
  
        System.out.println("NULL");  
    }  
   
}
```

