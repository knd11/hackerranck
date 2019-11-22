## 7. Arrays

**Objective**
Today, we're learning about the *Array* data structure. Check out the [Tutorial](https://www.hackerrank.com/challenges/30-arrays/tutorial) tab for learning materials and an instructional video!

**Task**
Given an array, , of  integers, print 's elements in *reverse* order as a single line of space-separated numbers.

**Input Format**

The first line contains an integer,  (the size of our array).
The second line contains  space-separated integers describing array 's elements.

**Constraints**

- 1  $ \leq$ N $\leq$ 1000
- 1  $ \leq$ $A_i$ $\leq$ 10000, where $A_i$  is the  integer in the array.

**Output Format**

Print the elements of array  in reverse order as a single line of space-separated numbers.

**Sample Input**

```
4
1 4 3 2
```

**Sample Output**

```
2 3 4 1
```

```Java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

public class Solution {



    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        int n = scanner.nextInt();
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        int[] arr = new int[n];

        String[] arrItems = scanner.nextLine().split(" ");
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        for (int i = 0; i < n; i++) {
            int arrItem = Integer.parseInt(arrItems[i]);
            arr[n-i-1] = arrItem;
        }

        for(int j=0;j<n;j++){
            System.out.print(arr[j] + " ");
        }
        scanner.close();
    }
}
```



## 8.  Dictionaries and Maps

**Objective**
Today, we're learning about Key-Value pair mappings using a *Map* or *Dictionary* data structure. Check out the [Tutorial](https://www.hackerrank.com/challenges/30-dictionaries-and-maps/tutorial) tab for learning materials and an instructional video!

**Task**
Given  names and phone numbers, assemble a phone book that maps friends' names to their respective phone numbers. You will then be given an unknown number of names to query your phone book for. For each name queried, print the associated entry from your phone book on a new line in the form name =phoneNumber; if an entry for  name is not found, print Not found instead.

**Note:** Your phone book should be a Dictionary/Map/HashMap data structure.

**Input Format**

The first line contains an integer **n** , denoting the number of entries in the phone book.
Each of the  subsequent n lines describes an entry in the form of **2** space-separated values on a single line. The first value is a friend's name, and the second value is an **8**-digit phone number.

After the  n lines of phone book entries, there are *an unknown number of lines of queries*. Each line (query) contains a name to look up, and you must continue reading lines until there is no more input.

**Note:** Names consist of lowercase English alphabetic letters and are *first names* only.

**Constraints**

- 1  $ \leq$ n $\leq$ $10^{-5}$
- 1  $ \leq$ queries $\leq$ $10^{5}$

**Output Format**

On a new line for each query, print `Not found` if the name has no corresponding entry in the phone book; otherwise, print the full  and  in the format `name=phoneNumber`.

**Sample Input**

```
3
sam 99912222
tom 11122222
harry 12299933
sam
edward
harry
```

**Sample Output**

```
sam=99912222
Not found
harry=12299933
```

**Explanation**

We add the following  *(Key,Value)* pairs to our map so it looks like this:



We then process each query and print `key=value` if the queried  is found in the map; otherwise, we print `Not found`.

*Query 0:* `sam`
Sam is one of the keys in our dictionary, so we print `sam=99912222`.

*Query 1:* `edward`
Edward is not one of the keys in our dictionary, so we print `Not found`.

*Query 2:* `harry`
Harry is one of the keys in our dictionary, so we print `harry=12299933`.

```java
//Complete this code or write your own from scratch
import java.util.*;
import java.io.*;

class Solution{
    public static void main(String []argh){
        Scanner in = new Scanner(System.in);
        HashMap<String,Integer> map = new HashMap();
        int n = in.nextInt();
        for(int i = 0; i < n; i++){
            String name = in.next();
            int phone = in.nextInt();
            // Write code here
            map.put(name,phone);
        }
        while(in.hasNext()){
            String s = in.next();
            // Write code here
            if (map.containsKey(s)){
                System.out.println(s + "=" + map.get(s));
            }
            else
                System.out.println("Not found");
        }
        in.close();
    }
}

```

## 9. Recursion 3

**Objective**
Today, we're learning and practicing an algorithmic concept called *Recursion*. Check out the [Tutorial](https://www.hackerrank.com/challenges/30-recursion/tutorial) tab for learning materials and an instructional video!

**Recursive Method for Calculating Factorial**
$$
factorial(N) =\begin{cases}
1& \text{N $\leq$ 1}\\
N*factorial(N-1)& \text{otherwise}
\end{cases}
$$
**Task**
Write a *factorial* function that takes a positive integer N,  as a parameter and prints the result of  N!( N factorial).

**Note:** If you fail to use recursion or fail to name your recursive function *factorial* or *Factorial*, you will get a score of  0.

**Input Format**

A single integer N,  (the argument to pass to *factorial*).

**Constraints**

- 2  $ \leq$ N $\leq$ 12
- Your submission must contain a recursive function named *factorial*.

**Output Format**

Print a single integer denoting N .

**Sample Input**

```
3
```

**Sample Output**

```
6
```

**Explanation**

Consider the following steps:

1. $factorial(3)  =  3 \times factorial(2);$
2. $factorial(2)  =  2 \times factorial(1);$
3. $factorial(1)  =  1;$

From steps  2 and 3 , we can say $factorial(2)  =  2 \times 1;$; then when we apply the value from $factorial(2);$ to step 1, we get $factorial(3)  =  3 \times 2;$ . Thus, we print  6 as our answer.

```java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

public class Solution {

    // Complete the factorial function below.
    static int factorial(int n) {
        int result = 1;
        if(n>1)
        {
            result = n*factorial(n-1);
        }

        return result;
    }

    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) throws IOException {
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        int n = scanner.nextInt();
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        int result = factorial(n);

        bufferedWriter.write(String.valueOf(result));
        bufferedWriter.newLine();

        bufferedWriter.close();

        scanner.close();
    }
}

```

## 10. Binary Numbers

**Objective**
Today, we're working with binary numbers. Check out the [Tutorial](https://www.hackerrank.com/challenges/30-binary-numbers/tutorial) tab for learning materials and an instructional video!

**Task**
Given a base-**10** integer, **n**, convert it to binary (base-**2**). Then find and print the base- integer denoting the maximum number of consecutive **1**'s in **n**'s binary representation.

**Input Format**

A single integer,**n** .

**Constraints**

- 1 $\leq$ n $\leq 10^6$

**Output Format**

Print a single base-10 integer denoting the maximum number of consecutive 1's in the binary representation of  n.

**Sample Input 1**

```
5
```

**Sample Output 1**

```
1
```

**Sample Input 2**

```
13
```

**Sample Output 2**

```
2
```

**Explanation**

*Sample Case 1:*
The binary representation of 5 is 101, so the maximum number of consecutive 1's is 1.

*Sample Case 2:*
The binary representation of 13 is 1101, so the maximum number of consecutive 1's is 2.

```java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

public class Solution {



    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        int n = scanner.nextInt();
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        int temp = n;
        int count = 1;
        int count_max = 1;
        String res = "";
        

        while(temp!=0)
        {
            res = res + temp%2;
            temp = temp/2;  
        }
        

        for(int i=1;i<res.length();i++)
        {
            if(res.charAt(i)=='1' && res.charAt(i)==res.charAt(i-1))
                ++count;         
            else
                count = 1;
            
            if(count>count_max)
                count_max = count;
        }
            
        System.out.print(count_max);
        scanner.close();
    }
}

```



## 11. 2D Arrays

**Objective**
Today, we're building on our knowledge of *Arrays* by adding another dimension. Check out the [Tutorial](https://www.hackerrank.com/challenges/30-2d-arrays/tutorial) tab for learning materials and an instructional video!

**Context**
Given a  $6 \times 6$ *2D Array*, **A**:

```
1 1 1 0 0 0
0 1 0 0 0 0
1 1 1 0 0 0
0 0 0 0 0 0
0 0 0 0 0 0
0 0 0 0 0 0
```

We define an hourglass in A to be a subset of values with indices falling in this pattern in A's graphical representation:

```
a b c
  d
e f g
```

There are 16 hourglasses in **A**, and an *hourglass sum* is the sum of an hourglass' values.

**Task**
Calculate the hourglass sum for every hourglass in A, then print the *maximum* hourglass sum.

**Input Format**

There are  6 lines of input, where each line contains 6 space-separated integers describing *2D Array* A; every value in A  will be in the inclusive range of  -9 to 9.

**Constraints**

- $-9 \leq A[i][j] \leq 9$
- $0 \leq i,j  \leq 9$

**Output Format**

Print the largest (maximum) hourglass sum found in  A.

**Sample Input**

```
1 1 1 0 0 0
0 1 0 0 0 0
1 1 1 0 0 0
0 0 2 4 4 0
0 0 0 2 0 0
0 0 1 2 4 0
```

**Sample Output**

```
19
```

**Explanation**

A contains the following hourglasses:

```
1 1 1   1 1 0   1 0 0   0 0 0
  1       0       0       0
1 1 1   1 1 0   1 0 0   0 0 0

0 1 0   1 0 0   0 0 0   0 0 0
  1       1       0       0
0 0 2   0 2 4   2 4 4   4 4 0

1 1 1   1 1 0   1 0 0   0 0 0
  0       2       4       4
0 0 0   0 0 2   0 2 0   2 0 0

0 0 2   0 2 4   2 4 4   4 4 0
  0       0       2       0
0 0 1   0 1 2   1 2 4   2 4 0
```

The hourglass with the maximum sum (19) is:

```
2 4 4
  2
1 2 4
```

```java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

public class Solution {



    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        int[][] arr = new int[6][6];
        // int[][] hG = new int[(6-2)*3][(6-2)*3];
        int SUM = 0;
        int SUM_MAX = -9*7;//注意不能初始化为0，因为和可能为负数

        for (int i = 0; i < 6; i++) {
            String[] arrRowItems = scanner.nextLine().split(" ");
            scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

            for (int j = 0; j < 6; j++) {
                int arrItem = Integer.parseInt(arrRowItems[j]);
                arr[i][j] = arrItem;
            }
        }

        for(int m = 1; m < 5; m++)
        {
            for(int n =1; n<5; n++){
                // hG[3*(m-1)][3*(n-1)] = arr[m-1][n-1];
                // hG[3*(m-1)][3*(n-1)] = arr[m-1][n];
                // hG[3*(m-1)][3*(n-1)] = arr[m-1][n+1];
                // hG[3*(m-1)][3*(n-1)] = arr[m][n];
                // hG[3*(m-1)][3*(n-1)] = arr[m+1][n-1];
                // hG[3*(m-1)][3*(n-1)] = arr[m+1][n];
                // hG[3*(m-1)][3*(n-1)] = arr[m+1][n+1];
                SUM = arr[m-1][n-1] + arr[m-1][n] + arr[m-1][n+1] + arr[m][n] + arr[m+1][n-1] + arr[m+1][n] + arr[m+1][n+1];
                if(SUM >= SUM_MAX)
                    SUM_MAX = SUM; 
            }
        }

        System.out.print(SUM_MAX);

        scanner.close();
    }
}
```

## 12. Inheritance

**Objective**
Today, we're delving into Inheritance. Check out the attached tutorial for learning materials and an instructional video!

**Task**
You are given two classes, *Person* and *Student*, where *Person* is the base class and *Student* is the derived class. Completed code for *Person* and a declaration for *Student* are provided for you in the editor. Observe that *Student* inherits all the properties of *Person*.

Complete the *Student* class by writing the following:

- A Student  class constructor, which has 4 parameters: 
  1. A string, `firstName`.
  2. A string,`lastName` .
  3. An integer, `id`.
  4. An integer array (or vector) of test scores, `scores`.
- A *char calculate()* method that calculates a Student object's average and returns the grade character representative of their calculated average:

![Grading.png](https://s3.amazonaws.com/hr-challenge-images/17165/1458142706-3073bc9143-Grading.png)

**Input Format**

The locked stub code in your editor calls your *Student* class constructor and passes it the necessary arguments. It also calls the *calculate* method (which takes no arguments).

*You are not responsible for reading the following input from stdin:*
The first line contains , `firstName,lastname`, and `id`, respectively. The second line contains the number of test scores. The third line of space-separated integers describes `scores` .

**Constraints**

- $1 \leq |firstName|,|lastName| \leq 10$
- $|id| \equiv 7$
- $0 \leq score,average \leq 100$

**Output Format**

*This is handled by the locked stub code in your editor.* Your output will be correct if your *Student* class constructor and *calculate()* method are properly implemented.

**Sample Input**

```
Heraldo Memelli 8135627
2
100 80
```

**Sample Output**

```
 Name: Memelli, Heraldo
 ID: 8135627
 Grade: O
```

**Explanation**

This student had  2 scores to average 100 and 80 . The student's average grade is $\frac{100+80}{2} = 90$. An average grade of  90 corresponds to the letter grade O , so our *calculate()* method should return the character`'O'`.

```java
import java.util.*;

class Person {
	protected String firstName;
	protected String lastName;
	protected int idNumber;
	
	// Constructor
	Person(String firstName, String lastName, int identification){
		this.firstName = firstName;
		this.lastName = lastName;
		this.idNumber = identification;
	}
	
	// Print person data
	public void printPerson(){
		 System.out.println(
				"Name: " + lastName + ", " + firstName 
			+ 	"\nID: " + idNumber); 
	}
	 
}

class Student extends Person{
	private int[] testScores;
    private int id;
    /*	
    *   Class Constructor
    *   
    *   @param firstName - A string denoting the Person's first name.
    *   @param lastName - A string denoting the Person's last name.
    *   @param id - An integer denoting the Person's ID number.
    *   @param scores - An array of integers denoting the Person's test scores.
    */
    // Write your constructor here

    public Student(String firstName,String lastName,int id,int[] scores){
        super(firstName,lastName,id);
        testScores = scores;
    } 

    /*	
    *   Method Name: calculate
    *   @return A character denoting the grade.
    */
    // Write your method here
    

    public char calculate(){
        int total = 0;
        for(int i = 0; i < testScores.length; i++)
            total = total + testScores[i];

        total = total/testScores.length;
        return ( total > 89 ? 'O' : 
                total > 79 ? 'E' : 
                total > 69 ? 'A' : 
                total > 54 ? 'P' :
                total > 39 ? 'D' : 'T' );
    }
}

class Solution {
	public static void main(String[] args) {
		Scanner scan = new Scanner(System.in);
		String firstName = scan.next();
		String lastName = scan.next();
		int id = scan.nextInt();
		int numScores = scan.nextInt();
		int[] testScores = new int[numScores];
		for(int i = 0; i < numScores; i++){
			testScores[i] = scan.nextInt();
		}
		scan.close();
		
		Student s = new Student(firstName, lastName, id, testScores);
		s.printPerson();
		System.out.println("Grade: " + s.calculate() );
	}
}
```



## 13.Abstract Classes

**Objective**
Today, we're taking what we learned yesterday about [*Inheritance*](https://docs.oracle.com/javase/tutorial/java/IandI/subclasses.html) and extending it to [*Abstract Classes*](https://docs.oracle.com/javase/tutorial/java/IandI/abstract.html). Because this is a very specific Object-Oriented concept, submissions are limited to the few languages that use this construct. Check out the [Tutorial](https://www.hackerrank.com/challenges/30-abstract-classes/tutorial) tab for learning materials and an instructional video!

**Task**
Given a *Book* class and a *Solution* class, write a *MyBook* class that does the following:

- Inherits from *Book*

- Has a parameterized constructor taking these 3 parameters:

  1. string title
  2. string name
  3. int price  
- Implements the Book class' abstrac display() method so it prints these

   

  

   

  lines:

  1. , a space, and then the current instance's .
2. , a space, and then the current instance's .
  3. , a space, and then the current instance's .

**Note:** Because these classes are being written in the same file, you must not use an access modifier (e.g.: ) when declaring *MyBook* or your code will not execute.

**Input Format**

You are not responsible for reading any input from stdin. The *Solution* class creates a *Book* object and calls the *MyBook* class constructor (passing it the necessary arguments). It then calls the *display* method on the *Book* object.

**Output Format**

The  method should print and label the respective , , and  of the *MyBook* object's instance (with each value on its own line) like so:

```
Title: $title
Author: $author
Price: $price
```

**Note:** The  is prepended to variable names to indicate they are placeholders for variables.

**Sample Input**

The following input from stdin is handled by the locked stub code in your editor:

```
The Alchemist
Paulo Coelho
248
```

**Sample Output**

The following output is printed by your *display()* method:

```
Title: The Alchemist
Author: Paulo Coelho
Price: 248
```

```java
import java.util.*;

abstract class Book {
    String title;
    String author;
    
    Book(String title, String author) {
        this.title = title;
        this.author = author;
    }
    
    abstract void display();
}

class MyBook extends Book{

    private int Price;

    MyBook(String title, String author, int price){
        super(title,author);
        Price = price;
    }

    public void display(){
        System.out.print("Title: " + title + "\nAuthor: " + author + "\nPrice: " + Price);
    } 
}
// Declare your class here. Do not use the 'public' access modifier.
    // Declare the price instance variable
    
    /**   
    *   Class Constructor
    *   
    *   @param title The book's title.
    *   @param author The book's author.
    *   @param price The book's price.
    **/
    // Write your constructor here
    
    /**   
    *   Method Name: display
    *   
    *   Print the title, author, and price in the specified format.
    **/
    // Write your method here
    
// End class

public class Solution {
   
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String title = scanner.nextLine();
        String author = scanner.nextLine();
        int price = scanner.nextInt();
        scanner.close();

        Book book = new MyBook(title, author, price);
        book.display();
    }
}
```



