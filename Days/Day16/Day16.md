#Day16/100


Today I solved two Coding problems of Graph Topic on #interviewbit.


Problem1:https://www.interviewbit.com/problems/water-flow/

```java
public class Solution {

    int d[][]={{1,0},{0,1},{-1,0},{0,-1}};
    public int solve(ArrayList<ArrayList<Integer>> A) {


        int n=A.size();
        if(n==0) return 0;

        int m=A.get(0).size();

        if(m==0) return 0;


        boolean r[][]=new boolean[n][m];
        boolean l[][]=new boolean[n][m];

        for(int i=0;i<n;i++){

            dfs(i,0,A,r,Integer.MIN_VALUE);
            dfs(i,m-1,A,l,Integer.MIN_VALUE);

        }
        for(int j=0;j<m;j++){
            dfs(0,j,A,r,Integer.MIN_VALUE);
            dfs(n-1,j,A,l,Integer.MIN_VALUE);
        }


        int ans=0;



        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(r[i][j] && l[i][j]){
                    ans++;
                }
            }
        }
        return ans;
    }

    public void dfs(int i,int j,ArrayList<ArrayList<Integer>> g,boolean v[][],int p){

        if(i<0 || i>=g.size() || j<0 || j>=g.get(0).size() ) return;
        if(v[i][j] || g.get(i).get(j) < p) return;
        v[i][j]=true;

        // System.out.println(i+" "+j+v[i][j]);

        for(int f[]:d){
            dfs(i+f[0],j+f[1],g,v,g.get(i).get(j));
        }

    }
}

```

Problem2:https://www.interviewbit.com/problems/stepping-numbers/

```java
public class Solution {
    public ArrayList<Integer> stepnum(int A, int B) {

        ArrayList<Integer> ans=new ArrayList<Integer>();

        for(int i=A;i<=B;i++){
            if(iss(i)){
                ans.add(i);
            }
        }
        return ans;
    }

    public boolean iss(int a){

        int p=a%10;//0
        a=a/10;//10

        while(a!=0){
            int r=a%10;//0,1

            if(Math.abs(p-r)!=1) return false; //0,1
            p=r;//0

            a=a/10;//1
        }

        return true;
    }
}

```
#100DaysOfCode