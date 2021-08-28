#Day19/100


Today I solved two Coding problems of Graph Topic on #interviewbit. And Also Learn About Shortest Path Finding Dijkstra Algorithm.


Problem1:https://www.interviewbit.com/problems/useful-extra-edges/
```java
public class Solution {
    public int solve(int A, ArrayList<ArrayList<Integer>> B, int C, int D, ArrayList<ArrayList<Integer>> E) {
    
    

    ArrayList<LinkedList<Node>> g=new ArrayList<>();
   

    for(int i=0;i<=A;i++){
        g.add(new LinkedList<Node>());
    }

    for(int i=0;i<B.size();i++){
        g.get(B.get(i).get(0)).add(new Node(B.get(i).get(1),B.get(i).get(2)));
        g.get(B.get(i).get(1)).add(new Node(B.get(i).get(0),B.get(i).get(2)));
    }
    int ans=dfs(g,C,D);
    // int ans=0;

    for(int j=0;j<E.size();j++){

        g.get(E.get(j).get(0)).add(new Node(E.get(j).get(1),E.get(j).get(2)));
        if(E.get(j).get(1)<g.size()){
        g.get(E.get(j).get(1)).add(new Node(E.get(j).get(0),E.get(j).get(2)));
        }

        int tem=dfs(g,C,D);

        ans=Math.min(ans,tem);
        g.get(E.get(j).get(0)).remove(g.get(E.get(j).get(0)).size()-1);
        if(E.get(j).get(1)<g.size()){
        g.get(E.get(j).get(1)).remove(g.get(E.get(j).get(1)).size()-1);
        }

    }



    return ans==Integer.MAX_VALUE?-1:ans;
    
    
    
    }

    public int dfs(ArrayList<LinkedList<Node>> g,int s,int e){

        int ans[]=new int[g.size()+1];
        // boolean visited[]=new boolean[g.size()+1];
        for(int i=0;i<=g.size();i++) ans[i]=Integer.MAX_VALUE;
        ans[s]=0;
        PriorityQueue<Node> q=new PriorityQueue<>((x,y)->x.w-y.w);

        q.add(new Node(s,0));
        // visited[s]=true;
      

        while(!q.isEmpty()){

            Node tem=q.poll();

            LinkedList<Node> arr=g.get(tem.v);

            for(Node n:arr){

                int in=n.v;
         
                if(ans[in]>ans[tem.v]+n.w){
                    ans[in]=ans[tem.v]+n.w;
                    q.add(new Node(n.v,ans[in]));
                }

            }
        }
        return ans[e];
    }
}


class Node{

    int v,w;

    Node(int v,int w){

        this.v=v;
        this.w=w;

    }

}
```

Problem2:https://www.interviewbit.com/problems/largest-distance-between-nodes-of-a-tree/
```java
public class Solution {
    int max=-1,maxn=-1;
    public int solve(ArrayList<Integer> A) {

        ArrayList<ArrayList<Integer>> ans=new ArrayList<>();

        for(int i=0;i<A.size();i++){
            ans.add(new ArrayList<>());
        }

        int root=0;

        for(int i=0;i<A.size();i++){
            if(A.get(i)!=-1){
                ans.get(A.get(i)).add(i);
                ans.get(i).add(A.get(i));
            }else{
                root=i;
            }
        }
        // System.out.println(ans);
        int ans1=-1,n=A.size();
       
        dsf(root,ans,new boolean[n],0);

        max=-1;

        dsf(maxn,ans,new boolean[n],0);
          
        return max;

    }

    public void dsf(int s,ArrayList<ArrayList<Integer>> g,boolean visited[],int d){

      
        if(d>max) 
        {
            max=d;maxn=s;
        }
        visited[s]=true;

        for(int i:g.get(s)){
            if(!visited[i]){
                
                dsf(i,g,visited,d+1);
            }
        }



       
    }
}

```
#100DaysOfCode