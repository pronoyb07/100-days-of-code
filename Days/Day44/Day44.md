
# Day44/100

Today I solved two medium level Coding problems of Graph topic in #interviewbit and learn the prims and Kruskal’s Algorithma.

[Problem 1](https://www.interviewbit.com/problems/commutable-islands/)
```java
public class Solution {

    int sum=0;


    public int solve(int A, int[][] B) {

        ArrayList<ArrayList<Node>> graph=new ArrayList<>();

        for(int i=0;i<A;i++){
            graph.add(new ArrayList<Node>());
        }

        int min=-1,v1=-1,v2=-1;

        for(int a[]:B){

            graph.get(a[0]-1).add(new Node(a[1]-1,a[2]));
            graph.get(a[1]-1).add(new Node(a[0]-1,a[2]));

            if(min==-1 || min>a[2]){
                min=a[2];
                v1=a[0]-1;
                v2=a[1]-1;
            }
        }

        sum=min;

        int v[]=new int[A];
        v[v1]=1;
        v[v2]=1;
        sum=min;

        findMin(graph,v);

        return sum;
    }

    public void findMin(ArrayList<ArrayList<Node>> g,int v[]){


        int min=-1,v1=-1,v2=-1;

        for(int i=0;i<g.size();i++){

            if(v[i]==1){

            ArrayList<Node> tem=g.get(i);
            for(Node t:tem){
            if(v[t.v]==1) continue;
            if(min==-1 || min>t.w){
                min=t.w;
                v1=i;
                v2=t.v;
            }
            }
            }
        
        }

        if(min!=-1){

            // System.out.println((v1+1)+" ->"+(v2+1)+" :"+min);

            sum+=min;
            v[v1]=1;
            v[v2]=1;
            findMin(g,v);

        }
            
            
        
    }

    class Node{
        int v,w;

        Node(int v,int w){
            this.v=v;
            this.w=w;
        }
    }
}

```

[Problem 2](https://www.interviewbit.com/problems/delete-edge/)

```java
public class Solution {
    public int deleteEdge(int[] A, int[][] B) {

        int n=A.length,m=B.length;

        HashMap<Integer,ArrayList<Integer>> g=new HashMap<>();

        long sum=0;

        for(int i=0;i<n;i++){
            sum=sum+A[i];

            g.put(i,new ArrayList<>());
        }

        for(int i=0;i<m;i++){

            g.get(B[i][0]-1).add(B[i][1]-1);

            g.get(B[i][1]-1).add(B[i][0]-1);
        }

        long sum2=0,ans=-1,m1=1000000007;

        int visited[]=new int[n];
        long sumq[]=new long[n];

        find(0,g,visited,sumq,A);

        // for(long i:sumq){
        //     System.out.print(i+" ");
        // }

        for(int i=0;i<m;i++){

            int se=B[i][1]-1;

            ans=Math.max(ans,((sum-sumq[se])*sumq[se])%m1);

        }

        return (int)ans;


    }

    public long find(int i,HashMap<Integer,ArrayList<Integer>> g,int visited[],long sum[],int w[]){

        visited[i]=1;

        ArrayList<Integer> tem=g.get(i);
        long sum1=w[i];

        for(int v:tem){
            if(visited[v]==0){
                sum1+=find(v,g,visited,sum,w);
            }
        }

        sum[i]=sum1;
        return sum1;
    }
}

```

#100DaysOfCode
