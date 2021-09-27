
# Day49/100


Today I solved 3 medium level Coding problems on #leetcode(2) and #interviewbit(1).

[Problem 1](https://leetcode.com/explore/challenge/card/september-leetcoding-challenge-2021/639/week-4-september-22nd-september-28th/3987/)

```java

class Solution {
    
    int min=-1;
    int di[][]={{1,0},{0,1},{-1,0},{0,-1}};
    public int shortestPath(int[][] grid, int k) {
        // dfs(grid,0,0,k,0);
        
        int n=grid.length,m=grid[0].length;
        
        if(n==0 && m==0) return 0;
        
        boolean v[][]=new boolean[n][m];
        int diff[][]=new int[n][m];
        
        int l=1;
        
        Queue<int[]> q=new LinkedList<>();
        
        q.add(new int[]{0,0,grid[0][0]});
        
        diff[0][0]=grid[0][0];
        
    
        
        while(!q.isEmpty()){
            
            int s1=q.size();
            
            
            for(int i=0;i<s1;i++){
                int []c=q.poll();
                
                if(c[0]==n-1 && c[1]==m-1) return l-1;
                
                for(int d[]:di){
                    int  x=c[0]+d[0];
                    int y=c[1]+d[1];
                    
                    if(x<0 || y<0 || x>=n || y>=m) continue;
                    
                    int odl=diff[x][y];
                    int newq=c[2]+grid[x][y];
                    
                    if((!v[x][y])  && (newq<=k)){
                        q.add(new int[]{x,y,newq});
                        v[x][y]=true;
                        diff[x][y]=newq;
                    }
                    
                     if((odl>newq)&&(newq<=k)){
                        q.add(new int[]{x,y,newq});
                        v[x][y]=true;
                        diff[x][y]=newq;
                    }
                }
            }
            
            l++;
            
            
        }
        
        
        return -1;
    }
    
    
    public void dfs(int [][]grid,int i,int j,int k,int ans){
        
        
        if(i==grid.length-1 && j==grid[0].length-1){
           if(min==-1){
               min=ans;
           }else{
               min=Math.min(min,ans);
           }
            return;
        }
        
        int t=grid[i][j];
        
        grid[i][j]=-1;
        
        
        for(int l[]:di){
            
            int x=i+l[0];
            int y=j+l[1];
            
            if(x<0 || y<0 || x>=grid.length || y>=grid[0].length || grid[x][y]==-1) continue;
            
            if(grid[x][y]==1){
                
                if(k>0){
                dfs(grid,x,y,k-1,ans+1);
                }
                
            }else{
                dfs(grid,x,y,k,ans+1);
            }
        }
        
        
        grid[i][j]=t;
    }
}


```

[Problem 2](https://leetcode.com/explore/challenge/card/september-leetcoding-challenge-2021/639/week-4-september-22nd-september-28th/3989/)

```java
class Solution {
    public int numUniqueEmails(String[] e) {
        
        Set<String> list=new HashSet<String>();
        
        for(String i:e){
            
            boolean hashp=false;
            
            String s="";
            
            for(int j=0;j<i.length();j++){
                
                
                if(i.charAt(j)=='+'){
                    hashp=true;
                }
                
                if(i.charAt(j)=='@'){
                    s=s+i.substring(j);
                    break;
                }
                
                if(hashp){
                    continue;
                }
                
                if(i.charAt(j)!='.'){
                    s=s+i.charAt(j);
                }
            }
            
            list.add(s);
            
            
            
        }
        
        return list.size();
        
        
        
    }
    
    
}



```

[Problem 3](https://www.interviewbit.com/problems/maximum-absolute-difference/)

```java


public class Solution {
    public int maxArr(ArrayList<Integer> A) {

        int n=A.size();


        int max1=Integer.MIN_VALUE,min1=Integer.MAX_VALUE;
        int max2=Integer.MIN_VALUE,min2=Integer.MAX_VALUE;
      


        for(int i=0;i<n;i++){
            max1=Math.max(A.get(i)+i,max1);
            min1=Math.min(A.get(i)+i,min1);

            max2=Math.max(A.get(i)-i,max2);
            min2=Math.min(A.get(i)-i,min2);

            // System.out.println(max1+" "+min1+" "+max2+" "+min2);
        }


        return Math.max(max1-min1,max2-min2);


        

        // int min=0,max=0;

        // for(int i=1;i<n;i++){

        //     if(A.get(i)<A.get(min)){

        //         min=i;

        //     }

        //     if(A.get(i)>A.get(max)){
        //         max=i;
        //     }

        // }

        // return A.get(max)-A.get(min)+ Math.abs(max-min);
    }
}


```


#100DaysOfCode
