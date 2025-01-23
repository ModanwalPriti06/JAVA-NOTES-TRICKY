
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





