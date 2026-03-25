
# EX 2E Pattern Matching using KMP Algorithm.
## DATE:25-02-2026

## AIM:

To write a Java program for the following constraints.
Longest Palindromic Substring
Given a string s, return the longest palindromic substring in s.
using Manacher's Algorithm

## Algorithm:

1. Transform the string by inserting # between characters (e.g., "babad" → #b#a#b#a#d#) to handle odd/even palindromes uniformly.
2. Create an array palindromeRadii[] to store the palindrome radius at each index and initialize center = 0, radius = 0.
3. Scan each position i in the transformed string and compute its mirror index using mirror = 2 * center - i.
4. If i is within the current right boundary radius, initialize palindromeRadii[i] = min(radius - i, palindromeRadii[mirror]).
5. Expand around index i while characters match on both sides and update the radius length for that center. If the palindrome expands beyond the current boundary,
   update center and radius.
6. After scanning all positions, find the index with the maximum radius, convert it back to the corresponding start index in the original string, and return the
   substring. 

## Program:
```
/*
Program to implement Reverse a String
Developed by: Naveenkumar M
Register Number:  212224230182
*/
```
```
import java.util.Scanner;

public class Solution {
    public String longestPalindrome(String s) {
        //Type code here...
        StringBuilder sprime=new StringBuilder("#");
        
        for(char c:s.toCharArray()){
            sprime.append(c).append("#");
        }
        
        int n=sprime.length();
        int[] p=new int[n];
        int c=0;
        int r=0;
        for(int i=0;i<n;i++)
        {
            int mirror=2*c-i;
            if(i<r){
                p[i]=Math.min(r-i,p[mirror]);
            }
            while(i+1+p[i]<n && i - 1 - p[i] >= 0 && sprime.charAt(i + 1 + p[i]) == sprime.charAt(i - 1 - p[i])){
                p[i]++;
            }
            if(i+p[i]>r)
            {
                c=i;
                r=i+p[i];
            }
        }
        
        int maxlength=0;
        int centerindex=0;
        for(int i=0;i<n;i++){
            if(p[i]>maxlength){
                maxlength=p[i];
                centerindex=i;
            }
        }
        int startindex=(centerindex-maxlength)/2;
        return s.substring(startindex,startindex+maxlength);
    }

    // Main method for user input
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String input = scanner.nextLine();

        Solution sol = new Solution();
        String result = sol.longestPalindrome(input);

        System.out.println("Longest Palindromic Substring: " + result);
        scanner.close();
    }
}

```
## Output:

<img width="830" height="200" alt="image" src="https://github.com/user-attachments/assets/21e81d23-e198-4132-935b-3952a09cfa2b" />


## Result:
The program successfully implemented and the expected output is verified.
