
# Day5/100

Today I solved One Coding problems on #interviewbit as part of challenge..

[Problem](https://www.interviewbit.com/problems/largest-continuous-sequence-zero-sum/)
```java
public class Solution {
    public ArrayList<Integer> lszero(ArrayList<Integer> A) {

        ArrayList<Integer> ans=new ArrayList<>();
        HashMap<Integer,Integer> map=new HashMap<>();
        ArrayList<Integer> sum=new ArrayList<>();

        if(A.size()==0){
            return ans;
        }

        int n=A.size();
        sum.add(A.get(0));

        for(int i=1;i<n;i++){

            sum.add(A.get(i)+sum.get(i-1));
            
        }
        int last=-3,end=-1;



        for(int i=0;i<n;i++){


            if(sum.get(i)==0){
              if((last==-3) || (end-last < i+1)){
                    last=-1;
                    end=i;
            // System.out.println(last+" "+end);
              }
                continue;
            }




            if(map.containsKey(sum.get(i))){
                int index=map.get(sum.get(i));
                if(last==-3 || end-last < i-index){
                    last=index;
                    end=i;
                }
            }else{
                map.put(sum.get(i),i);
            }
        }

        if(last==-3){
            return ans;
        }

        

        for(int i=last+1;i<=end;i++){
            ans.add(A.get(i));
        }
        return ans;

    }
}

// 1 2 -2 5 2 4 -4 3 -3

//1:[0]
//5 :[3]
//2:[4]
//0:[5,6,7,8]

//O(n),O(n);
// ans:[1,2]








```

#100DaysOfCode
#100daysofcodechallenge 
@ZeelCodder