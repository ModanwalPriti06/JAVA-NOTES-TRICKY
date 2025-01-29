
##  Arrays, Searching & Sorting, Collection, Stack, Queue, Linklist, Hashmap, Tree, Graph, Recursion, DP

### Rotate Array Trick
k = k%n
here k = how many times have to rotate and n = length of array

### Find first digit of number - 	divide the given number by 10 till num is greater than 0.
     while (num >= 10) {
            num = num / 10;
        }
        firstDigit = num;
### Find last digit of a given number-  we modulo divide the given number by 10. Which is last_digit = num % 10.
        lastDigit = num % 10;

### Product of digits: 1234
      while (num != 0) {
            product *= num % 10;
            num /= 10;
        }
```
For big letters (A to Z): ASCII values are between 65 and 90.
For small letters (a to z): ASCII values are between 97 and 122.
For numbers (0 to 9): ASCII values are between 48 and 57.
```
## Stack
#### Push in bottom using recursion
```
public class Main {
    public static void pushBotom(Stack<Integer> st, int num){
    if(st.size()==0) {
      st.push(num);
      return;
    }
    int top = st.pop();
    pushBotom(st, num);
    st.push(top);

  }
  
  public static void displayRev(Stack<Integer> st){
    if(st.size()==0) {
      return;
    }
    int top = st.pop();
    displayRev(st);
    System.out.print(top+" ");
    st.push(top); 
  }
    public static void main(String[] args) {
      Stack<Integer> st = new Stack<>();
      st.push(1);
      st.push(2);
      st.push(3);
      st.push(4);
      pushBotom(st,5);
      displayRev(st); 
  }
}
```
### Remove from Bottom
```
import java.util.*;

public class Main {
    public static void main(String[] args) {
      Stack<Integer> st = new Stack<>();
       Stack<Integer> res = new Stack<>();
      st.push(1);
      st.push(2);
      st.push(3);
      st.push(4);
      
      while(st.size()>1){
        res.push(st.pop());
      }
      st.pop();
      
      while(res.size()>0){
        st.push(res.pop());
      }
  System.out.print("Stack "+st);
  }
}
```
## Stack implementation with array
```
import java.util.*;
public class Main {
  public static class Stack{
    int[] arr = new int[5];
    int idx = 0;
    
   void push(int n){
     if(isFull()){
       System.out.println("Stack is Full ");
       return;
     }
    arr[idx]= n;
    idx++;
  }
  int peek(){
    if(idx==0){
      System.out.println("Stack is empty");
      return -1;
    }
    return arr[idx-1];
    
  }
   int pull(){
     if(idx==0){
      System.out.println("Stack is empty");
      return -1;
    }
    int top = arr[idx-1];
      arr[idx-1] = 0;
      idx--;
      return arr[idx];
     
   }
   
   void display(){
     for(int i=0; i<idx; i++){
       System.out.println(arr[i]+ " ");
     }
     System.out.println();
   }
   
   int size(){
     return idx;
   }
   
   Boolean isEmpty(){
     if(idx == 0) return true;
     else return false;
   }
   
   Boolean isFull(){
     if(idx == arr.length) return true;
     else return false;
   }
    
  }
  
    public static void main(String[] args) {
      Stack st = new Stack();
      st.push(1);
      st.push(2);
      st.push(3);
      st.push(4);      
      st.push(4);
      st.push(4);
      st.display();
  }
}
```
## Stack implementation with Linkedlist
```
import java.util.*;

public class Main {
  public static class Node{  //user define data type
    int val;
    Node next;
    Node(int val){
      this.val = val;
      this.next = null;
    }
  }
  public static class Stack{ // user define data structure
    int size = 0;
    Node head = null;
    
    void push(int x){
      Node newNode = new Node(x);
      newNode.next = head;
      head = newNode;
      size++;
      
    }
    
    void display(){
      Node temp = head;
      while(temp!= null){
        System.out.print(temp.val+" ");
        temp = temp.next;
      }
      System.out.println();
    }
    
    int pull(){
      if(head == null){
        System.out.println("LL is empty");
        return -1;
      }
      int x = head.val;
      head = head.next;
      size--;
      return x;
    }
    
    int peek(){
       if(head == null){
          System.out.println("LL is empty");
          return -1;
        }
        return head.val;
    }
    
    int size(){
      return size;
    }
    
    boolean isEmpty(){
      if(size == 0) return true;
      else retun flase;
    }
    
  }

  
    public static void main(String[] args) {
      Stack st = new Stack();
      st.push(1);
      st.push(2);
      st.push(3);
      st.push(4);      
      st.display();
      System.out.println("peek element is: "+st.peek());
      st.pull();
      st.display();
  }
}
```
---
## Stack Interview Question:

#### 1. Balance Paranthesis
   RULES:
   1. opening push in stack
   2. Closing : top = ')' pop, if stack is empty, return false
```
import java.util.*;

public class Main {
  public static Boolean balancePara(String str)
  {
    Stack<Character> st = new Stack<>();
    int n= str.length();
    for(int i=0; i<n; i++){
      char ch = str.charAt(i);
      if(ch == '('){
        st.push(ch);
      } else{
        if(st.size() == 0) return false;
        if(st.peek() == '(') st.pop();
      }
    }
    if(st.size() > 0) return false;
    else return true;
  }
    public static void main(String[] args) {
        String str = "(())";
        // balancePara(str);
        System.out.println(balancePara(str));
    }
}
```
#### 2. 
--- 
## Monotonic Stack
In Data Structures and Algorithms (DSA), a sequence or array is called monotonic if it is either entirely non-increasing or non-decreasing. This means that the elements of the sequence either never increase or never decrease as you traverse the sequence.

### Types of Monotonic Arrays
#### 1. Monotonic Increasing:
The elements either strictly increase or stay the same.
Example: [1, 2, 2, 3, 4] (non-decreasing).
Strictly increasing example: [1, 2, 3, 4].

#### 2. Monotonic Decreasing:
The elements either strictly decrease or stay the same.
Example: [5, 4, 4, 2, 1] (non-increasing).
Strictly decreasing example: [5, 4, 3, 2].

## Missing number

- find array length n
- m = n * (n+1) /2;
- get all sum of array element and - m;
```
var missingNumber = function (nums) {
    let n = nums.length;
    let sum = (n * (n + 1)) / 2
    let res = nums.reduce((acc, curr) => {
        return acc + curr;
    }, 0)
    return sum-res;
};
```
## Fibonacci series: The Fibonacci series is a sequence of numbers where each number is the sum of the two preceding ones, starting from 0 and 1. The sequence goes:
0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...
```
function fibonacci(n){
  let a= 0, b = 1;
 for (let i = 0; i < n; i++) {
        console.log(a);
        [a, b] = [b, a + b];
    }
}
fibonacci(10);
```








