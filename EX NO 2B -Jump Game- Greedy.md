
# EX 2B Jump Game using Greedy Algorithm.
## DATE:09-02-2026

## AIM:

To write a Java program to for given constraints.
You are given an array of integers. Each number represents the maximum number of steps you can jump forward from that position.

You start from the first element (index 0). 
Write a program to find the minimum number of jumps required to reach the last index of the array.

If it is not possible to reach the end, return -1.

## Algorithm:

1. If the array length is ≤ 1 or the first element is 0, return -1 (cannot move).
2. Initialize three variables: far = 0 → farthest index reachable, end = 0 → end of current jump range, jump = 0 → number of jumps made
3. Loop from i = 0 to n - 2 and update far = max(far, i + nums[i]).
4. When i reaches end, increment jump and update end = far.
5. After updating, if end >= n - 1, break the loop (last index reachable).
6. Return jump if end reaches last index, otherwise return -1.    

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

public class MinJumpToEnd {

    // Function to return minimum jumps to reach end
    public static int minimumJumps(int[] nums) {
        // Type Your Code Here.
        int jumps=0;
        int currentend=0;
        int farthest=0;
        if(nums.length<=1) return 0;
        if(nums[0]==0) return -1;
        for(int i=0;i<nums.length-1;i++)
        {
            farthest=Math.max(farthest,i+nums[i]);
            if(i==currentend)
            {
                jumps++;
                currentend=farthest;
            }
            
        }
        if(currentend<nums.length-1) return -1;
        return jumps;
    }

    // Main method to handle input and output
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(); // Number of elements
        int[] nums = new int[n];

        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        System.out.println("Minimum jumps to reach last index: " + minimumJumps(nums));
    }
}

```
## Output:

<img width="918" height="307" alt="image" src="https://github.com/user-attachments/assets/7a246e2c-ace2-4dfa-86c9-acf292d2489c" />


## Result:
The program successfully implemented and the expected output is verified.
