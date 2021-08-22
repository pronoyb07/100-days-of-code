#Day13/100


Today I solved three Coding problems on #interviewbit on Greedy Algorithm Topic. I learned How we can think Greedy to solve problems so that time complexity reduce.

Problem 1:https://www.interviewbit.com/problems/highest-product/

```java

public class Solution {
    public int maxp3(ArrayList<Integer> A) {
 
        Collections.sort(A);

        return Math.max(A.get(0)*A.get(1)*A.get(A.size()-1),A.get(A.size()-1)*A.get(A.size()-2)*A.get(A.size()-3));
    }
}


```
Problem 2:https://www.interviewbit.com/problems/interview-questions/
```java

public class Solution {
    public int bulbs(ArrayList<Integer> A) {

        int ans=0;
        int look=0;

        for(int i=0;i<A.size();i++){
            if(A.get(i)==look){
                ans++;
                look=(look==0)?1:0;
            }
        }
        return ans;
    }
}

```
Problem 3:https://www.interviewbit.com/problems/disjoint-intervals/
```java
public class Solution {
    public int solve(ArrayList<ArrayList<Integer>> A) {

        Collections.sort(A,(x,y)->
        
                          {
                             return x.get(0)-y.get(0);
                          });

        ArrayList<Integer> last=A.get(0);
        int c=1;

        for(int i=1;i<A.size();i++){

            ArrayList<Integer> cu=A.get(i);

            if(cu.get(0)<=last.get(1)){

                last=(last.get(1)<cu.get(1))?last:cu;

            }else{
                c++;
                last=cu;
            }
        }
        return c;
    }
}


/* 
1-2- 3?4 5 6 7 9 
       4-5-6-7-9
1-2-3-4-5-6-7-9
-----e<s----------------
                -----
                Which end is less
                if bot end is same the take any 
                defult takei secound
                ->last
                ->this
                if(last is in this) than make last=this -> do not do i++
                else not in -> take last and makei currte=last ->ans++

         -----------



-------
   1    2
  ---      3
      -----
              ---
1 2 3 4 5 6 7 8 9

*/

```

#100DaysOfCode

