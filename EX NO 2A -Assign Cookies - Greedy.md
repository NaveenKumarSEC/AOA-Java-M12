
# EX 2A Assign Cookies using Greedy Algorithm. 
## DATE:08-02-2026

## AIM:

To Write a Java program for the following Constraints.
Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie.

Each child i has a greed factor g[i], which is the minimum size of a cookie that the child will be content with; and each cookie j has a size s[j]. If s[j] >= g[i], we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximise the number of your content children and output the maximum number.

## Algorithm:

1. Sort the greed array g and cookie array s in ascending order.
2. Set two pointers: i = 0 for children and j = 0 for cookies.
3. While both pointers are within their array limits (i < g.length and j < s.length), repeat steps 4–5.
4. If the current cookie s[j] can satisfy the current child g[i], increment i (child is satisfied).
5. Always increment j to check the next cookie.
6. Return i, which represents the total number of satisfied children. 

## Program:
```
/*
Program to implement Reverse a String
Developed by: Naveenkumar M
Register Number:  212224230182
*/
```
```
import java.util.*;

public class AssignCookies {
    
    public static int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);
        int i=0,j=0;
        while(i<g.length && j<s.length)
        {
            if(s[j]>=g[i]) i++;
            j++;
        }
        return i;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] g = new int[n];
        for (int i = 0; i < n; i++) g[i] = sc.nextInt();
        int m = sc.nextInt();
        int[] s = new int[m];
        for (int i = 0; i < m; i++) s[i] = sc.nextInt();
        System.out.println(findContentChildren(g, s));
    }
}

```
## Output:

<img width="348" height="338" alt="image" src="https://github.com/user-attachments/assets/152f4a07-0d77-47bf-a8bf-438586d94db8" />


## Result:
The program successfully print all the numbers from 1 to N. 
