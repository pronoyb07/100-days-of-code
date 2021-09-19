
# Day41/100

Today I solved three Coding problems on #leetcode as part of challenge.


Problem 1:https://leetcode.com/contest/weekly-contest-258/problems/reverse-prefix-of-word/
```java
class Solution {
    public String reversePrefix(String word, char ch) {
        
        StringBuffer s=new StringBuffer(word);
        
        int index=-1;
        
        for(int i=0;i<word.length();i++){
            if(ch==word.charAt(i)){
                index=i;
                break;
            }
        }
        
        if(index==-1) return word;
        
        int i=0,j=index;
        while(i<j){
            char c=s.charAt(i);
            s.setCharAt(i,s.charAt(j));
            s.setCharAt(j,c);
            i++;
            j--;
        }
        
        return s.toString();
        
    }
}

```
Problem 2:https://leetcode.com/contest/weekly-contest-258/problems/number-of-pairs-of-interchangeable-rectangles/
```java
class Solution {
    public long interchangeableRectangles(int[][] arr) {
        
        HashMap<Double,Long> m=new HashMap<>();
        
        
        for(int i=0;i<arr.length;i++){
            
            Double ans=((double)arr[i][0])/arr[i][1];
            
            if(m.containsKey(ans)){
                m.put(ans,m.get(ans)+1);
            }else{
                m.put(ans,(long)1);
            }
        }
        
        long ans=0;
        
        for(Double i:m.keySet()){
            if(m.get(i)>1){
                ans=ans+(m.get(i)*(m.get(i)-1))/2;
            }
        }
        
        // 1,2,3
            
            // n*n(n-1)
        
        return ans;
        
        
    }
}
```
Problem 3:https://leetcode.com/contest/weekly-contest-258/problems/maximum-product-of-the-length-of-two-palindromic-subsequences/

```java
class Solution {
    
    StringBuffer s,tem,tem1;
    int ans=-1;


    public int maxProduct(String s1) {
        
        
        s=new StringBuffer(s1);
        
        tem=new StringBuffer();
        tem1=new StringBuffer();
        
        find(0,s1.length());
    
        
        return ans;
    
    }
    
    public void find(int i,int n){
        
        if(i>=n){
            if(isP(tem) && isP(tem1)){   
                
               ans=Math.max(ans,tem.length()*tem1.length());
            }
            return;
        }
        
     
        
        tem.append(s.charAt(i));
        find(i+1,n);
        tem.deleteCharAt(tem.length()-1);
        tem1.append(s.charAt(i));
        find(i+1,n);
        tem1.deleteCharAt(tem1.length()-1);
        find(i+1,n);    
    }
    
    public boolean isP(StringBuffer br){
        
        int i=0,j=br.length()-1;
        
        while(i<j){
            if(br.charAt(i)!=br.charAt(j)){
                return false;
            }
            i++;
            j--;
        }
        return true;
    }
    
}


```

#100DaysOfCode
