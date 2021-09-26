
# Day48/100

Today I solved 2  Coding problems on hackerEarth while take part in long coding content.

Jeel and Range Queries

Problem:
There is a bulb, which can have two states, ON or OFF. You are given the initial state of the bulb s and a binary string d which has either 0's or 1's. A single flip is defined as changing one single bit from 0 to 1 or 1 to 0. You are given q queries, each having two integers l and r. They denote two positions in the binary string. The sequence of bits from l to r, denotes a decimal integer p. Find the state of the bulb after performing p flips.

Note that the state of the bulb is reverted back to its initial state after each query.

Jeel being a friend of yours and respected member of international coding community asks you to solve this problem for him.

```java

import java.util.*;
import java.io.*;


class TestClass {
    public static void main(String args[] ) throws Exception {

         BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
 int t=Integer.parseInt(br.readLine());

        while(t-->0){
           
            String s=br.readLine();
            String d=br.readLine();
            int q=Integer.parseInt(br.readLine());

            StringBuffer ans=new StringBuffer();

                String d1[]=br.readLine().split(" ");
                int l=Integer.parseInt(d1[0])-1;
                int r=Integer.parseInt(d1[1])-1;
               
                if(d.charAt(r)=='1'){
                   ans.append(s.equals("OFF")?"ON":"OFF");
                }else{
                   ans.append(s);
                }
                q--;
            while(q-->0){
                d1=br.readLine().split(" ");
                l=Integer.parseInt(d1[0])-1;
                r=Integer.parseInt(d1[1])-1;
                
                if(d.charAt(r)=='1'){
                   ans.append("\n"+(s.equals("OFF")?"ON":"OFF"));
                }else{
                   ans.append("\n"+s);
                }
            }
            System.out.println(ans);
        }

    }
}



```

[Problem 2](https://www.hackerearth.com/problem/algorithm/do-you-hate-geometry-37c5631c/)

```java

import java.util.*;
import java.io.*;


class TestClass {
    public static void main(String args[] ) throws Exception {
        Scanner sc = new Scanner(System.in);
        double r = sc.nextInt();
        r *= 2;
        double a = sc.nextInt();
        double c = sc.nextInt();

        double b = Math.sqrt(Math.pow(r,2) - Math.pow(a,2));
        double d = Math.sqrt(Math.pow(r,2) - Math.pow(c,2));
        double s = (a+b+c+d)/2;
        double ans = Math.sqrt((s-a)*(s-b)*(s-c)*(s-d));
        System.out.printf("%.2f",ans);

    }
}



```


#100DaysOfCode
