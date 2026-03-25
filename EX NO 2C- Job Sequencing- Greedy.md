
# EX 1C Job Sequencing using Greedy Approach
## DATE:03-02-2026

## AIM:

To write a Java program to for given constraints.
Given an integer array nums and an integer k, return the number of pairs (i, j) where i < j such that |nums[i] - nums[j]| == k.

The value of |x| is defined as:

x if x >= 0.
-x if x < 0.You're given N jobs, each with:

A unique jobId

A deadline (by which it must be completed)

A profit (earned only if completed on or before the deadline)

Each job:

Takes exactly 1 unit of time

Only one job can be done at a time

Your goal is to maximize total profit while completing the maximum number of jobs possible within their deadlines.

## Algorithm:

1. Sort all jobs in decreasing order of profit.
2. Find the maximum deadline among all jobs to determine the number of time slots needed.
3. Create a boolean array slot[] of size maxDeadline + 1 to track free time slots.
4. Initialize count = 0 (jobs done) and totalProfit = 0.
5. For each job in sorted order, try to assign it to the latest free slot before its deadline. if a free slot is found, mark it, increase count, and add the job’s
   profit.
6. After processing all jobs, return {count, totalProfit}.   

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

public class JobScheduling {

    static class Job {
        int id, deadline, profit;

        Job(int id, int deadline, int profit) {
            this.id = id;
            this.deadline = deadline;
            this.profit = profit;
        }
    }

    public static int[] jobScheduling(Job[] jobs, int n) {
        // Type Your Code Here.
        Arrays.sort(jobs,(a,b)->b.profit - a.profit);
        int maxdl=0;
        for(Job job:jobs)
        {
            maxdl=Math.max(maxdl,job.deadline);
        }
        boolean[] slot=new boolean[maxdl+1];
        int jobdone=0;
        int totalprofit=0;
        for(Job job:jobs)
        {
            for(int j=job.deadline;j>0;j--)
            {
                if(!slot[j])
                {
                    slot[j]=true;
                    jobdone++;
                    totalprofit+=job.profit;
                    break;
                }
            }
        }
        return new int[]{jobdone,totalprofit};
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        Job[] jobs = new Job[n];

        for (int i = 0; i < n; i++) {
            int id = sc.nextInt();
            int deadline = sc.nextInt();
            int profit = sc.nextInt();
            jobs[i] = new Job(id, deadline, profit);
        }

        int[] result = jobScheduling(jobs, n);
        System.out.println(result[0] + " " + result[1]);
    }
}

```
## Output:

<img width="352" height="420" alt="image" src="https://github.com/user-attachments/assets/a140503b-4e1c-4ab8-9b77-00ce5f96ff8b" />


## Result:
The program successfully implemented and the expected output is verified.
