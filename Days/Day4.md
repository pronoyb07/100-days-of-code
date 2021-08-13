
# Day4/100

Today I solved two Coding problems in #interviewbit as part of challenge..

[Problem 1](https://www.interviewbit.com/problems/combination-sum/)
```java
public class Solution {

    Set<ArrayList<Integer>> s=new HashSet<>();
      ArrayList<ArrayList<Integer>> ans=new ArrayList<>();

	public ArrayList<ArrayList<Integer>> combinationSum(ArrayList<Integer> a, int b) {

      Collections.sort(a);
      

      fills(a,b,new ArrayList<Integer>(),0);

      
      return ans;



	}

    public void fills(ArrayList<Integer> a,int b,ArrayList<Integer> arr,int in){

        if(b<0 ||  (in>=a.size() && b!=0)){
            return;
        }

        if(b==0){
            if(!s.contains(arr)){

                ArrayList<Integer> tem=new ArrayList<>();
                
                for(int i=0;i<arr.size();i++){
                    tem.add(arr.get(i));
                }
                s.add(tem);
                ans.add(tem);

            }
            return;
        }

        arr.add(a.get(in));
        fills(a,b-a.get(in),arr,in);
        arr.remove(arr.size()-1);
        for(int i=in+1;i<a.size();i++){
            if(a.get(i)==a.get(i-1)) continue;
            arr.add(a.get(i));
            fills(a,b-a.get(i),arr,i+1);
            arr.remove(arr.size()-1);
            fills(a,b,arr,i+1);
        }
    }
}

```

[Problem 2](https://www.interviewbit.com/problems/subset/)

```java
public class Solution {
    // Set<ArrayList<Integer>> s1=new TreeSet<>();
    ArrayList<ArrayList<Integer>> ans=new ArrayList<>();
    public ArrayList<ArrayList<Integer>> subsets(ArrayList<Integer> A) {
   
        Collections.sort(A);

        ans.add(new ArrayList());
        find(A,new ArrayList(),0);
        // for(ArrayList<Integer> a:s1){
            // ans.add(a);
        // }

            Collections.sort(ans,new Comparator<ArrayList<Integer>>() {
            @Override
            public int compare(ArrayList<Integer> a1, ArrayList<Integer> a2) {
                boolean f=true;
                int min=Math.min(a1.size(),a2.size());
                for(int i=0;i<min;i++){
                    if(a1.get(i)>a2.get(i)){
                        return 1;
                    }else if(a1.get(i)<a2.get(i)){
                        return -1;
                    }
                }
                return (a1.size()>a2.size())?1:-1;
            }
            });
        return ans;
    }

    public void find(ArrayList<Integer> a,ArrayList<Integer> s,int i){
        if(i>=a.size()){
            if(s.size()>=1){

            ans.add(new ArrayList(s));
            }
            return;
        }

        s.add(a.get(i));
        find(a,s,i+1);
        s.remove(s.size()-1);
        find(a,s,i+1);
    }
}
```

#100DaysOfCode
#100daysofcodechallenge 
@ZeelCodder