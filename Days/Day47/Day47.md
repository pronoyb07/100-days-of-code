
# Day47/100

Today I solved 3 medium level Coding problems of Graph topic in #interviewbit.

[Problem 1](https://www.interviewbit.com/problems/possibility-of-finishing-all-courses-given-prerequisites/)
```java
public class Solution {
    int v;
    List<Integer> adj[];
    boolean visited [];
    boolean samePath[];
    boolean flag =  true;
    public void addEdge(int u, int w) {
        adj[u].add(w);
    } 
    
    public int solve(int A, ArrayList<Integer> B, ArrayList<Integer> C) {
        flag = true;
        v = A;
        adj = new LinkedList[v];
        visited = new boolean[v];
        samePath = new boolean[v];
        for(int i = 0; i< v; i++) {
            adj[i] = new LinkedList<Integer>();
        }
        for(int i = 0; i< B.size(); i++) {
            int u = B.get(i)-1;
            int w = C.get(i)-1;
            addEdge(u, w);
        }
        return dfs();
    }
    
    public int dfs() {
        for(int i =0 ; i < v; i++) {
            if(!visited[i]) {
                dfs(i);
            }
        }
        return 
        flag ? 1 : 0;
    }
    
    public void dfs(int u) {
        visited[u] = true; 
        samePath[u] = true;
        for(int w : adj[u]) {
            if(samePath[w]) flag = false;
            if(!visited[w])
            dfs(w);
        }
        samePath[u] = false;
    }
    
    
}


```

[Problem 2](https://www.interviewbit.com/problems/cycle-in-undirected-graph/)

```java

public class Solution {
    public int solve(int A, int[][] B) {

        ArrayList<ArrayList<Integer>> ans=new ArrayList<>();

        for(int i=0;i<A;i++){
            ans.add(new ArrayList<Integer>());
        }
        // int s=-1;

        for(int a[]:B){
            ans.get(a[0]-1).add(a[1]-1);
            ans.get(a[1]-1).add(a[0]-1);

        }

        boolean v[]=new boolean[A];
        for(int s=0;s<A;s++){

        if(v[s]) continue;


        Queue<Node> q=new LinkedList<>();
        

        q.add(new Node(s,-1));
        v[s]=true;

        while(!q.isEmpty()){

            Node t=q.poll();

            ArrayList<Integer> te=ans.get(t.v);

            for(int i:te){
                if(v[i]){
                    if(t.p!=-1 && t.p!=i) return 1;
                }else{
                    v[i]=true;
                    q.add(new Node(i,t.v));
                }
            }

            

        }
        }

        return 0;




    }
    class Node{
        int v,p;
        Node(int v,int p){
            this.v=v;
            this.p=p;
        }
    }
}

```
[Problem 3](https://www.interviewbit.com/problems/black-shapes/)

```java
public class Solution {

    int ans=0;
    public int black(ArrayList<String> A) {

        ans=0;

        int n=A.size();
        int m=A.get(0).length();

        boolean v[][]=new boolean[n][m];

        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                char c=A.get(i).charAt(j);

                if(c=='X' && !v[i][j]){
                    // System.out.println(i+" "+j);
                    ans++;
                    dfs(A,v,i,j);
                }
            }
        }

       

        return ans;

    }

    public void dfs(ArrayList<String> arr, boolean v[][],int i,int j){

        if(i<0 || j<0 || i>=arr.size() || j>=arr.get(0).length() || arr.get(i).charAt(j)=='O' || v[i][j]) return;

        v[i][j]=true;

        int di[][]={{1,0},{0,1},{-1,0},{0,-1}};

        dfs(arr,v,i+1,j);

        dfs(arr,v,i,j+1);

        dfs(arr,v,i-1,j);

        dfs(arr,v,i,j-1);


    }
}


```

#100DaysOfCode
