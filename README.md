##  Arrays, Searching & Sorting, Collection, Stack, Queue, Linklist, Hashmap, Tree, Graph, Recursion, DP
- Jagged Array - in which array where number of column is not fix.


| **Leetcode No.**             | **Use Case**                      |
|-------------------------|----------------------------------|
| **268**      |  Missing Number  |
| **2161**      | Partition Array According to Given Pivot | 
| **1337**  | Get to know store data in increasing order based on index number from array |
| **3280** | Convert Number into Binary |
| **345** |  swapping using two pointer |  
| **2679** | Sum in Matrix | 
| **2906** | Multiplication of Matrix | 
| **867** | Transpose Matrix | 
| **643 / 1343** | Sliding window | 




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
#### 2. Remove consecutive subsequence 
(where element length > 1 we have remove)
```
import java.util.*;

public class Main {
  public static int[]  removeConsecutive(int[] arr, int n){
    Stack<Integer> st = new Stack<>();
    for(int i=0; i<n; i++){
      if(st.size()== 0|| st.peek() != arr[i]){
        st.push(arr[i]);
      }
       else if(i == n-1 || arr[i] != arr[i+1]){
            st.pop();
       }
    }
    int[] res = new int[st.size()];
    int m = res.length;
    for(int i=m-1; i>=0; i--){
      res[i] = st.pop();
    }
    return res;
  }
    public static void main(String[] args) {
      int[] arr = {1,2,2,3,4,4,4,5,6,6,7,7,10,10,10,2};
      int[] res = removeConsecutive(arr, arr.length);
      System.out.println(Arrays.toString(res));
  }
}
```

### 3. Next Grater Element
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
## find unique element with the help of xor operator
```
function findUnique(arr) {
    let result = 0;
    for (let num of arr) result ^= num; // XOR cancels out duplicates
    return result;
}
console.log(findUnique([1, 2, 3, 2, 1])); // Output: 3
```
# Masai Webinar

- Binary search occurance of any number first and last indix
- https://www.spoj.com/problems/EKO/ eko-eko
- Predicate Function in DSA (Data Structures and Algorithms)
A predicate function is a function that returns a boolean value (true or false) based on a given condition. It is commonly used in searching, filtering, and conditional operations in DSA.

## Collection and Framework:
- Framework; A set of classses and interface.
- https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html

### Set Interface: (Hashset)
- it is implemented of set Interface function.
- Unique
- unordered
- hashing Internally

### Map Interface: (Hashmap)
- Store data in key value pair mapping
- Method: put(), get(), containsKey(), containsValue(), putIfAbsent(), keySet, entrySet(), values()
- unordered

# Matrix 2D Array:

## Why multidimensional?
- Graph represent - 2D architecture
- Grid
- Google Sheet format Data

## Addition Matrix
Note: r1 == r2 , c1 == c2

## Multiplication in matrix
Note: r2 == c1 and resultant matrix is [r1 * c2]

```
import java.util.*;

public class Main {
    public static void main(String[] args) {
     int[][] arr1 = {
                       {1,2,3,4},
                       {5,6,7,8},
                    };
      int r1 = 2;
      int c1 = 4;
     
      int[][] arr2 = {
                       {1,2,3},
                       {4,5,6},
                       {7,8,9},
                       {2,3,5}
                     };
      int r2 = 4;
      int c2 = 3;
                     
    // Here multiple will be of this arr only when c1 == r2
    //  result array is length: int[][] res = new int[r1][c2]
    
    int[][] res = new int[r1][c2];
    
    for(int i=0; i<r1; i++){
      for(int j=0; j<c2 ;j++){
        for(int k=0; k< c1; k++){
          
          res[i][j] += (arr1[i][k] + arr2[k][j]);
          
        }
      }
    }
     
     System.out.println(Arrays.deepToString(res));
     
  }
}
```

## Transpose of Matrix
```
import java.util.*;

public class Main {
    public static void main(String[] args) {
      int r1 = 4;
      int c1 = 3;
       int[][] arr1 = {
                         {1,2,3},
                         {4,5,6},
                         {7,8,9},
                         {10,11,12}
                      };
      
      int[][] res = new int[c1][r1];
      
      for(int i=0; i<c1; i++){
        for(int j=0; j<r1; j++){
            res[i][j] = arr1[j][i];
            
        }
      }
     System.out.println(Arrays.deepToString(res));
  }
}
```

# TransposeInPlace Matrix only work in square matrix 
```
import java.util.*;

public class Main {
    public static void main(String[] args) {
      int r1 = 3;
      int c1 = 3;
       int[][] arr1 = {
                         {1,2,3},
                         {4,5,6},
                         {7,8,9},
                       
                      };
      
      for(int i=0; i<c1; i++){
        for(int j=i; j<r1; j++){
           int temp =   arr1[i][j];
            arr1[i][j] = arr1[j][i];
             arr1[j][i] = temp;
        }
      }
     System.out.println(Arrays.deepToString(arr1));
  }
}
```
## Given a square Matrix turn into 90Degree in a clock wise direction
- Solution1 : Transpose Matrix
- Solution2 : Reverse String
```
import java.util.*;

public class Main {
  public static void reverseArray(int[] arr ){
    int i = 0;
    int j = arr.length-1;
    
    while(i<j){
      int temp = arr[i];
      arr[i]= arr[j];
      arr[j] = temp;
      i++;
      j--;
      
    }
  }
  
    public static void main(String[] args) {
      int r1 = 3;
      int c1 = 3;
       int[][] arr1 = {
                         {1,2,3},
                         {4,5,6},
                         {7,8,9}
                      };
      
      // Transpose Matrix
      for(int i=0; i<c1; i++){
        for(int j=i; j<r1; j++){
           int temp =   arr1[i][j];
            arr1[i][j] = arr1[j][i];
             arr1[j][i] = temp;
        }
      }
       for(int i=0; i<c1; i++){
            reverseArray(arr1[i]);
        } 
     System.out.println(Arrays.deepToString(arr1));
  }
}
```

## Pascal element (Jagged Array)
```
| 1 |          
| 1 | 1 |
| 1 | 2| | 1 |
| 1 | 3 | 3 | 1 |
| 1 | 4 | 6 | 4 | 1 |
```
- property:
- p[i][j] = p[i-1][j] + p[i-1][j-1] (means mid element should me some of above row left and right element some)
- In every row first and last element should be one 1.
- Jagged Array: ith row have ith column
```
import java.util.*;
public class Main {
    public static void main(String[] args) {
     int n = 5;
        int[][] ans = new int[n][];
        for(int i=0; i<n; i++){
          ans[i] = new int[i+1];      // number of column in ith row
          ans[i][0] = ans[i][i] = 1;
          for(int j= 1; j<i; j++){
             ans[i][j] = ans[i-1][j] + ans[i-1][j-1]; // calculating mid element of pascal array
          }
        }
     System.out.println(Arrays.deepToString(ans));
  }
}
```

## Binary Trees
- A binary tree is a hierarchical data structure in which each node has at most two children:
1. Left child
2. Right child

### Each node in a binary tree contains:
- A value (data)
- A pointer/reference to its left child
- A pointer/reference to its right child













