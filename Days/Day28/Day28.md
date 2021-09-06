#Day28/100


Today I solved two Medium Level problems of Binary Search on #interviewbit. 


Problem1:https://www.interviewbit.com/problems/woodcutting-made-easy/
```java
public class Solution {
    public int solve(int[] A, int B) {
 
 
        int i=0,j=A.length-1;
        if(j==-1) return 0;
 
        int max=A[0];
 
        for(i=1;i<A.length;i++){
 
            if(max<A[i]){
                max=A[i];
            }
        }
 
        int ans=-1;
        j=max;i=0;
 
        while(i<=j){
 
            int m=i+(j-i)/2;
            long cu=find(A,m);
 
            if(cu>=(long)B){
                ans=m;
                i=m+1;
            }else{
                j=m-1;
            }
        }
        return ans;
 
 
    }
 
    public long find(int arr[],int v)
    {
 
        long ans=0;
        for(int i=0;i<arr.length;i++){
            if(v<arr[i]){
                ans=ans+arr[i]-v;
            }
        }
 
        return ans;
    }
}
```

Problem2:https://www.interviewbit.com/problems/search-for-a-range/
```java
public class Solution {
    // DO NOT MODIFY THE ARGUMENTS WITH "final" PREFIX. IT IS READ ONLY
    public int[] searchRange(final int[] A, int B) {

        int i=0,j=A.length-1;

        int s=-1,e=-1;

        while(i<=j){
            int m=i+(j-i)/2;

            if(A[m]<B){
                i=m+1;
            }else if(A[m]>B){
                j=m-1;
            }else{
                s=m;
                j=m-1;
            }
        }

        i=0;j=A.length-1;

        while(i<=j){
            int m=i+(j-i)/2;

            if(A[m]<B){
                i=m+1;
            }else if(A[m]>B){
                j=m-1;
            }else{
                e=m;
                i=m+1;
            }
        }

        int ans[]=new int[2];
        ans[0]=s;
        ans[1]=e==-1 ? s:e;

        return ans;


    }
}

```
#100DaysOfCode