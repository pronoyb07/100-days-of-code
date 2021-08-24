#Day14/100


Today I solved two Coding problems on #gfg on  dp + Arrays Topic.




Problem 1:https://practice.geeksforgeeks.org/problems/stock-buy-and-sell-1587115621/1/?problemStatus=solved&page=1&company[]=Media.net%20&query=problemStatussolvedpage1company[]Media.net

```java
class Solution{
    //Function to find the days of buying and selling stock for max profit.
    ArrayList<ArrayList<Integer> > stockBuySell(int A[], int n) {
        // code here
        
        boolean look_min=true;
        ArrayList<ArrayList<Integer> > ans=new ArrayList<>();
        
        
        int last=-1,end=-1;
        
        for(int i=0;i<n-1;i++){
            
            if(look_min && A[i]<A[i+1]){
                last=i;
                look_min=false;
            }else if( !look_min && A[i]>A[i+1]){
                ArrayList<Integer> tem=new ArrayList<>();
                tem.add(last);
                tem.add(i);
                ans.add(tem);
                last=-1;
                look_min=true;
            }
            
        }
        
       if( !look_min && last!=n-1 &&A[n-1]>A[n-2]){
                ArrayList<Integer> tem=new ArrayList<>();
                tem.add(last);
                tem.add(n-1);
                ans.add(tem);
                last=-1;
                look_min=true;
        }
        return ans;
        
    }
}

```

Problem 2:https://practice.geeksforgeeks.org/problems/smallest-window-in-a-string-containing-all-the-characters-of-another-string-1587115621/1/?problemStatus=solved&page=1&company[]=Media.net%20&query=problemStatussolvedpage1company[]Media.net


```java

class Solution
{
    //Function to find the smallest window in the string s consisting
    //of all the characters of string p.
    public static String smallestWindow(String s, String p)
    {
        // Your code 
        
        HashMap<Character,Integer> map=new HashMap<>();
        
        int c=0;
        
        for(int i=0;i<p.length();i++){
            if(map.containsKey(p.charAt(i))){
                map.put(p.charAt(i),map.get(p.charAt(i))+1);
            }else{
                map.put(p.charAt(i),1);
            }
        }
        c=map.size();
        int last=-1,end=-1;
        int i=0,j=0;
        int n=s.length();
        
        while(j<=n){
            
            if(c==0){
                 char c1=s.charAt(i);
                 
                 if(map.containsKey(c1)){
                    
                    map.put(c1,map.get(c1)+1);
                    if(map.get(c1)>0) c++;
                    
                }
                i++;
                
            }else{
                if(j>=n) break;
                
                char c1=s.charAt(j);
                if(map.containsKey(c1)){
                    
                    map.put(c1,map.get(c1)-1);
                    if(map.get(c1)==0) c--;
                    
                }
                j++;
                
            }
            
            if(c==0){
                
                if(last==-1 || end-last>j-i){
                    
                last=i;
                end=j;
                }
            }
        }
        
        if(last==-1) return "-1";
        
        return s.substring(last,end);
        
    }


```

#100DaysOfCode