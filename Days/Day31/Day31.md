
# Day31/100

Today I solved three Coding problems on #interviewbit(1) and #leetcode(2) as part of challenge.


Problem 1:https://www.interviewbit.com/problems/min-xor-value/
```java
public class Solution {
    public int findMinXor(int[] A) {
        Arrays.sort(A);

        int min=Integer.MAX_VALUE;

        for(int i=0;i<A.length-1;i++){

            int xor=A[i]^A[i+1];
            if(min>xor){
                min=xor;
            }

        }
        return min;
    }
}

```
Problem 2:https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/submissions/
```java
class Solution {
    public int removeDuplicates(int[] a) {
        
        int n=a.length;
        if(n<=1) return n;
        int i=0;
        
        if(a[i]==a[i+1]) i++;
        
        for(int j=i+1;j<n;j++){
            
            if(a[i]!=a[j]){
                
                if(a[i]!=a[j] && j!=n-1 && a[j]==a[j+1]){
                    i++;
                    a[i]=a[j];
                    i++;
                    a[i]=a[j+1];
                }else if(a[i]!=a[j]){
                    i++;
                    a[i]=a[j];
                }
                
            }
            
        }
        return i+1;
        
    }
}
```
Problem 3:https://leetcode.com/problems/remove-duplicates-from-sorted-array/

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        
        int n=nums.length;
        
        if(n<=1) return n;
        
        for(int i=0;i<n-1;i++){
            if(nums[i]==nums[i+1]){
                nums[i]=-1000;
            }
        }
        
        int i=0,j=1;
        // System.out.println(Arrays.toString(nums));
        
        while(j<n){
            
            if(nums[i]==-1000 && nums[j]!=-1000){
                int tem=nums[j];
                nums[j]=nums[i];
                nums[i]=tem;
                i++;
                j++;
            }else if(nums[i]==-1000){
                j++;
               
            }else{
                
                i++;
                j++;
            }
        }
        if(nums[n-1]!=-1000) i++;
        
        return i;
        
    }
}
```

#100DaysOfCode
