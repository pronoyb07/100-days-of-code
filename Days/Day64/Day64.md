
# Day64/100

Today I solved 3 Hard  Coding problems on Bit Manipulation


Link1:https://www.interviewbit.com/problems/count-total-set-bits/
```java
public class Solution {
    public int solve(int A) {
        long c=0,m=(long)1e9+7;
        // System.out.println(m);
        while(A!=0){
            
            long pow=find(A);
            // System.out.println(pow+" "+A);
            long x=(long)Math.pow(2,pow);
            long x2=x/2;

            c=(c+(x2*(pow))%m+A-x+1)%m;
            A=A-(int)x;
        }
        /*314447109*/

        return (int)c;
    }

    public int find(int a){

        int c=0;

        for(int i=1;i<=a;i=i*2){
            c++;
        }
        return c-1;
    }
}



```


Link2:https://www.interviewbit.com/problems/palindromic-binary-representation/
```java
public class Solution 
{static int INT_SIZE = 32; 
    int constructNthNumber(int group_no, int aux_num, 
                                        int op) 
{ 
    int a[] = new int[INT_SIZE]; 
  
    int num = 0, len_f; 
    int i = 0; 
  
    if (op == 2) 
    { 
        len_f = 2 * group_no; 
  
        a[len_f - 1] = a[0] = 1; 
  
        while (aux_num > 0) 
        { 
            a[group_no + i] = a[group_no - 1 - i] 
                            = aux_num & 1; 
            aux_num = aux_num >> 1; 
            i++; 
        } 
    } 
  
    else if (op == 0) 
    { 
        len_f = 2 * group_no + 1; 
  
        a[len_f - 1] = a[0] = 1; 
        a[group_no] = 0; 
  
        while (aux_num > 0) 
        { 
            a[group_no + 1 + i] = a[group_no - 1 - i] 
                                = aux_num & 1; 
            aux_num = aux_num >> 1; 
            i++; 
        } 
    } 
    else    
    { 

        len_f = 2 * group_no + 1; 
  
       
        a[len_f - 1] = a[0] = 1; 
        a[group_no] = 1; 
  
        while (aux_num>0) 
        { 
          
            a[group_no + 1 + i] = a[group_no - 1 - i] 
                                = aux_num & 1; 
            aux_num = aux_num >> 1; 
            i++; 
        } 
    } 
  
    for (i = 0; i < len_f; i++) 
        num += (1 << i) * a[i]; 
    return num; 
} 
    public int solve(int n) 
    {
         int group_no = 0, group_offset; 
    int count_upto_group = 0, count_temp = 1; 
    int op, aux_num; 
  
    while (count_temp < n) 
    { 
        group_no++; 
  
        count_upto_group = count_temp; 
        count_temp += 3 * (1 << (group_no - 1)); 
    } 
  
   
    group_offset = n - count_upto_group - 1; 
  
    if ((group_offset + 1) <= (1 << (group_no - 1))) 
    { 
        op = 2; 
        aux_num = group_offset; 
    } 
    else
    { 
        if (((group_offset + 1) - (1 << (group_no - 1))) % 2==1) 
            op = 0; 
        else
            op = 1;
        aux_num = ((group_offset) - (1 << (group_no - 1))) / 2; 
    } 
  
    return constructNthNumber(group_no, aux_num, op);
    }
}



```


Link3:https://www.interviewbit.com/problems/xor-ing-the-subarrays/
```java
public class Solution {
    public int solve(ArrayList<Integer> A) {

        int n=A.size();

        int ans=0;

        for(int i=0;i<n;i++){

            int c=(i)*(n-i)+ n-i-1;

            // System.out.println(c+" "+A.get(i));
            if(i==0 || i==n-1){
                if(n%2!=0){
                    
                    ans=ans^A.get(i);
                }
                continue;
            }

            if(c%2==0){
                ans=ans^A.get(i);
            }

        }

        return ans;
    }
}


```


#100DaysOfCode
