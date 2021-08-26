#Day17/100



Today I took Part in Codeforces Round #741 (Div. 2). I was able to two Finished A, B problems. I tried to solve  Problem C but I was not able to solve it after problem C. I will Try to Up-solve those problems.

ProblemA:
```java
import java.util.*;
import java.lang.*;
import java.io.*;
/**
* @author zeel prajapati
 */
// public class Main{
final public class Solution{
static int max=Integer.MAX_VALUE;
static int min=Integer.MIN_VALUE;
public static void main(String[] args)throws IOException{
 BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
 int t=Integer.parseInt(br.readLine());
 while(t-->0){
 
    int arr[]=Inputarr(br);
    int di=arr[1]/2;
 
    if(di>=arr[0]){
 
        System.out.println(di- (arr[1]%2==0?1:0));
    }else{
        System.out.println(arr[1]-arr[0]);
    }
 
 }
}
 
/**
 * 13 14 15 16 17 18 19 20 21 22 23 24 25 26
 * 23 -11 =12
 * 
 * largest prime number - smallest prime number
 * 23%11 = 1
 *26-8=18 
 25-13
8+26= 34/2=>17
26/2==13-1
 */
 
 
public static int[] Inputarr(BufferedReader br){
    try{
    String s=br.readLine();
    String d[]=s.split(Character.toString(' '));
    int n=d.length;
    
    int arr[]=new int[n];
    for(int i=0;i<n;i++){
        arr[i]=Integer.parseInt(d[i]);
    }
        return arr;
    }catch(IOException e){
     System.out.println(1); 
    }
    return new int[1];
}
 
public static void printarr(int arr[]){
    StringBuffer br=new StringBuffer();
    for(int i=0;i<arr.length;i++){
        br.append(arr[i]+Character.toString(' '));
    }
    System.out.println(br);
}
}
class Node{
int i,j,value;
Node(int i,int j,int v){
this.i=i;
this.j=j;
this.value=v;
}
}
class com implements Comparator<Integer>{
@Override
public int compare(Integer arg0, Integer arg1) {
return arg1-arg0;
}
}
```

ProblemB:
```java

import java.util.*;
import java.lang.*;
import java.io.*;
/**
* @author zeel prajapati
 */
// public class Main{
final public class Solution{
static int max=Integer.MAX_VALUE;
static int min=Integer.MIN_VALUE;
public static void main(String[] args)throws IOException{
 BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
 int t=Integer.parseInt(br.readLine());
 while(t-->0){
 
    int k=Integer.parseInt(br.readLine());
    String s=br.readLine();
 
    if(s.contains("1")){
        System.out.println("1\n1");
    }else if(s.contains("4")){
        System.out.println("1\n4");
    }else if(s.contains("6")){
        System.out.println("1\n6");
    }else if(s.contains("8")){
        System.out.println("1\n8");
        
    }else if(s.contains("9")){
        System.out.println("1\n9");
 
    }else{
 
        //2357
        int arr[]=new int[10];
        boolean f=false;
 
        for(int i=0;i<s.length();i++){
            int in=s.charAt(i)-'0';
            arr[in]++;
 
            if(arr[in]>=2){
                f=true;
                System.out.println("2\n"+s.charAt(i)+""+s.charAt(i));
                break;
            }
            
        }
 
        if(!f){
 
            for(int i=0;i<s.length();i++){
                boolean g=false;
                for(int j=i+1;j<s.length();j++){
 
                    int ans=Integer.parseInt(s.charAt(i)+""+s.charAt(j));
 
                    // System.out.println(ans);
 
                    if(isnot(ans)){
                        g=true;
                        System.out.println("2\n"+ans);
                        break;
                    }
 
                    
                }
                if(g) break;
            }
 
            
 
        }
 
 
 
    }
 
    // int arr[]=Inputarr(br);
    // int di=arr[1]/2;
 
    // if(di>=arr[0]){
 
    //     System.out.println(di- (arr[1]%2==0?1:0));
    // }else{
    //     System.out.println(arr[1]-arr[0]);
    // }
 
 }
}
 
private static boolean isnot(int ans) {
 
    for(int i=2;i*i<=ans;i++){
        if(ans%i==0) return true;
    }
    return false;
}
 
/**
 * 13 14 15 16 17 18 19 20 21 22 23 24 25 26
 * 23 -11 =12
 * 
 * 2 4 6 8 
 * 
 * 1 2 3 5 7 
 * 2 -> even
 * 1 3 5 7 -> 
 * 27
 * 1 2 3 5 7 11 13 17 19 23 29 31 37 .......
 * 
 * none prime number 
 * 1 4 6 8 9
 * 
 * 2 3 5 7 
 * 
 * 32
 * 52
 * 72
   35
 * 25
 * 75
 * 
 * 
 * 
 * 
 * 27
 * 53
 * 
 * 
 * 25
 * 75
 * 35
 * 
 * 32
 * 52
 * 72
 * 
 * 
 * 
 * 
 * 
 * 
 * none prime
 * 
 * 1 2 3 4 5 6 7 8 9
 * largest prime number - smallest prime number
 * 23%11 = 1
 *26-8=18 
 *25-13
 *8+26= 34/2=>17
 *26/2==13-1
 *-> 1 2 3 5 7 11 13 29
 
*->2 digit 1 digit 
*=>
 
1 2 3 4 5 6 7 8 9
1 n a n a n a n n
 */
 
 
public static int[] Inputarr(BufferedReader br){
    try{
    String s=br.readLine();
    String d[]=s.split(Character.toString(' '));
    int n=d.length;
    
    int arr[]=new int[n];
    for(int i=0;i<n;i++){
        arr[i]=Integer.parseInt(d[i]);
    }
        return arr;
    }catch(IOException e){
     System.out.println(1); 
    }
    return new int[1];
}
 
public static void printarr(int arr[]){
    StringBuffer br=new StringBuffer();
    for(int i=0;i<arr.length;i++){
        br.append(arr[i]+Character.toString(' '));
    }
    System.out.println(br);
}
}
class Node{
int i,j,value;
Node(int i,int j,int v){
this.i=i;
this.j=j;
this.value=v;
}
}
class com implements Comparator<Integer>{
@Override
public int compare(Integer arg0, Integer arg1) {
return arg1-arg0;
}
}

```
#100DaysOfCode