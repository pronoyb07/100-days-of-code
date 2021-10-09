
# Day58/100





Today I solved 3 medium-level Coding problems on  #interviewbit of topic Binary Search and Strings.

[Problem 1](https://www.interviewbit.com/problems/median-of-array/)

```java

public class Solution {
    // DO NOT MODIFY BOTH THE LISTS
    public double findMedianSortedArrays(final List<Integer> a, final List<Integer> b) {
        if(a.size()>b.size()) return findMedianSortedArrays(b, a);
        
        int x = a.size();
        int y = b.size();
        
        int low = 0; int high = x;
        
        while(low<=high){
            int partitionX = (low+high)/2;
            int partitionY = (x+y+1)/2-partitionX;
            
            int leftMaxX = (partitionX==0)? Integer.MIN_VALUE: a.get(partitionX-1);
            int leftMaxY = (partitionY==0)? Integer.MIN_VALUE:b.get(partitionY-1);
            
            int rightMinX = (partitionX==x)? Integer.MAX_VALUE:a.get(partitionX);
            int rightMinY = (partitionY==y)? Integer.MAX_VALUE:b.get(partitionY);
            
            if((leftMaxX<=rightMinY)&& (leftMaxY<=rightMinX)){
                if((x+y)%2==0){
                    return ((double)Math.max(leftMaxX,leftMaxY)+Math.min(rightMinX, rightMinY))/2;
                }else{
                    return ((double)Math.max(leftMaxX, leftMaxY));
                }
           }else if(leftMaxX>rightMinY) {
               high = partitionX-1;
               
           }
           else low = partitionX+1;
    }
    return -1;
}}



```

[Problem 2](https://www.interviewbit.com/problems/multiply-strings/)

```java
public class Solution {
    public String multiply(String A, String B) {
        if(A.length()<B.length()) return multiply(B,A);

        int zero=B.length()-1;

        // if(B.equals("0")) return "0";

        String last="";


        for(int i=zero;i>=0;i--){
            String back="";
            for(int j=0;j<i;j++){
                back+="0";
            }

            int c=B.charAt(B.length()-i-1)-'0';
            int carray=0;

            String p="";

            // boolean isStart=false;

            for(int j=A.length()-1;j>=0;j--){
                int s=A.charAt(j)-'0';

                int mul=s*c+carray;

                int add=mul/10;
                int r=mul%10;

                
                p=r+p;
                
                carray=add;
            }



            p=p+back;

            if(carray!=0){
                p=carray+p;
            }

            // System.out.println(p+" }");

            if(last=="") last=p;
            else {
                last=sum(p,last);
            }
        }


        int i=-1;
        for(int j=0;j<last.length();j++){
            if(last.charAt(j)!='0'){

i=j;
                break;

            }
        }

        if(i!=-1){
            last=last.substring(i);
        }else{
            last="";
        }

        return last.length()==0?"0":last;
        
    }

    public String sum(String s1,String s2){

        String ans="";
        int c=0;

        int i=s1.length()-1,j=s2.length()-1;

        while(i>=0 && j>=0){

            int s=s1.charAt(i)-'0' + s2.charAt(j)-'0'+c;
            int add=s/10;
            int r=s%10;

            ans=r+ans;
            c=add;
            i--;
            j--;
        }
        while(i>=0){

            int s=s1.charAt(i)-'0' + c;
            int add=s/10;
            int r=s%10;

            ans=r+ans;
            c=add;
            i--;
        }

        while(j>=0){

            int s=s2.charAt(j)-'0'+c;
            int add=s/10;
            int r=s%10;

            ans=r+ans;
            c=add;
            j--;
        }

        if(c!=0){
            ans=c+ans;
        }

        return ans;

    }
}


/**

12
10
--
120
 00
---
120
1
19
12
---
120
138


2
12
---
  20
   4
-----
24
---





*/




```

[Problem 3](https://www.interviewbit.com/problems/power-of-2/)

```java


public class Solution {
   public static int power(String A) {

    if(A.equals("1")) return 0;

    int co=0;


    while(!A.equals("")){
        String p="";
        int c=0;
        boolean isStart=false;
        for(int i=0;i<A.length();i++){
            int c1=A.charAt(i)-'0';
            int s=c1;
            if(c==1){
                s=10+s;
            }
            int ans=s/2;
            int r=s%2;
            c=r;
            if(!isStart && ans!=0){
                isStart=true;
            }
            if(isStart){
                p=p+ans;
            }
        }
        // int i=-1;
        // for(int j=0;j<p.length();j++){
        //     if(p.charAt(j)!='0'){
        //         i=j;
        //         break;
        //     }
        // }
        // if(i!=-1){
        //     p=p.substring(i);
        // }else{
        //     p="0";
        // }
        if(c==1 && !A.equals("1")){
                // System.out.println(A);
                return 0;
        }
        // System.out.println(A+" "+p);
        A=p;

    }
    return 1;
 }
}

/*
1 2 3 4 5 6 7   8  9   10
2 4 8 16 32 64 128 256 512

2|512 
 |1280
 |64 0
 |32 0 
 |16 0
 |8  0 
 |4  0
 |2  0
 |1  0
 |0  1

 2 | 20
   | 10 0
   | 5  0
   | 2  1
**/


```


#100DaysOfCode
