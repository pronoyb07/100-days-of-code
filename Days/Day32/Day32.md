
# Day32/100

Today I solved 5 Coding problems on #interviewbit(4) and #leetcode(1) as part of challenge.


Problem 1:https://www.interviewbit.com/problems/k-reverse-linked-list/
```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     public int val;
 *     public ListNode next;
 *     ListNode(int x) { val = x; next = null; }
 * }
 */
public class Solution {
    public ListNode reverseList(ListNode A, int B) {

        if(A==null) return A;


        ListNode p=null,c=A;

        // System.out.println(c.val);
        int k=B;

        while(c!=null){
            if(B==0) break;
            ListNode tem=c.next;
            c.next=p;
            p=c;
            c=tem;
            B--;
        }

       
        A.next=reverseList(c,k);
        

        return p;
    }
}

```
Problem 2:https://www.interviewbit.com/problems/even-reverse/
```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     public int val;
 *     public ListNode next;
 *     ListNode(int x) { val = x; next = null; }
 * }
 */
public class Solution {
    public ListNode solve(ListNode A) {

        if(A==null) return A;

            ListNode p=null,c=A.next;
            ListNode newH=A;

            while(c!=null){
                if(c.next==null){
                    c.next=p;
                    p=c;
                    break;
                }
                ListNode tem=c.next.next;
                newH.next=c.next;
                newH=c.next;
                c.next=p;
                p=c;
                c=tem;
            }
            newH.next=null;

            // for(  )

            /**


            1->2->3->4->5->6->7->8

            c=2=>4=>6
            newH=1=>3=>5
            p=null=>2=>4

            odd
            1->3->5->7->null

            even
            8->6->4->2->null

            
            
            */

            // ListNode tem1=A,tem2=p;
            // while(tem1!=null){
            //     System.out.print(tem1.val+" ");
            //     tem1=tem1.next;
            // }
            // System.out.println();
            // tem1=p;
            //  while(tem1!=null){
            //     System.out.print(tem1.val+" ");
            //     tem1=tem1.next;
            // }
            // System.out.println();

            ListNode s1=A,s2=p;

            while(s1!=null && s2!=null){
                ListNode t=s1.next,t1=s2.next;
                s1.next=s2;
                s2.next=t;
                s2=t1;
                s1=t;
            }
           

            /*
            p=null
            n  c  n  c
            1->2->3->4->5->6->7
            1->3
            2->null


            2->null
            1->3
            4->2
            */
            return A;
    }
}

```
Problem 3:https://www.interviewbit.com/problems/swap-list-nodes-in-pairs/
```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     public int val;
 *     public ListNode next;
 *     ListNode(int x) { val = x; next = null; }
 * }
 */
public class Solution {
    public ListNode swapPairs(ListNode A) {

        ListNode p=A,c=A.next;
        ListNode last=null;
        if(c==null) return p;

        /*

        1->2->3->4->5
         
        p=1
        c=2
        last=null/1
        A=1/2

        tem=3
        2->1->3->4->5

        

        
        
        
        
        */

        while(c!=null){

            ListNode tem=c.next;
            c.next=p;
            p.next=tem;
            if(last!=null){

            last.next=c;
            last=p;
            }
            else {
                last=p;
                A=c;
            }
            p=p.next;
            if(tem==null) break;
            c=tem.next;
        }

        return A;
    }
}

```

Problem 4:https://www.interviewbit.com/problems/rotate-list/

```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     public int val;
 *     public ListNode next;
 *     ListNode(int x) { val = x; next = null; }
 * }
 */
public class Solution {
    public ListNode rotateRight(ListNode head, int k) {
        int n=0;
        if(k==0) return head;
        ListNode tem=head;
        ListNode last=null;
        // if(head==null ||)
        while(tem!=null){
            last=tem;
            tem=tem.next;
            n++;
        }
        if(n<=1) return head;
        k=k%n;
        if(k==0) return head;
        
        int e=n-k;
        // System.out.println(k+" "+e);

        
        ListNode tem1=head,tem2=null;
        
        ListNode t=head;
        int c=0;
        while(c<e){
            
            c++;

            tem2=tem1;
            tem1=tem1.next;       
        }

        last.next=head;
        tem2.next=null;

        return tem1;
        
    }
}

```

Problem 5:https://leetcode.com/problems/largest-plus-sign/


```java
class Solution {
    
    public int orderOfLargestPlusSign(int n, int[][] mines) {
        
        
        int gr[][]=new int[n][n];
        
        if(mines.length==n*n) return 0;
        
        int ans=1;
        
        for(int i=0;i<mines.length;i++){
            int in[]=mines[i];
            gr[in[0]][in[1]]=1;
        }
        
        
//         for(int i=0;i<n;i++){
//             for(int j=0;j<n;j++){
//                 System.out.print(gr[i][j]+" ");
//             }
//             System.out.println();
//         }
        
        
        for(int i=1;i<n-1;i++){
            
            for(int j=1;j<n-1;j++){
                
                if(gr[i][j]==0){
                    
                    int up=0,dow=0,left=0,right=0;
                    
                    for(int k=i-1;k>=0;k--){
                        if(gr[k][j]!=0)
                        {
                            break;
                            
                        }
                        
                        up++;
                    }
                    for(int k=i+1;k<n;k++){
                        if(gr[k][j]!=0)
                        {
                            break;
                            
                        }
                        
                        dow++;
                    }
                    for(int k=j-1;k>=0;k--){
                        if(gr[i][k]!=0)
                        {
                            break;
                            
                        }
                        
                        left++;
                    }
                    for(int k=j+1;k<n;k++){
                        if(gr[i][k]!=0)
                        {
                            break;
                            
                        }
                        
                        right++;
                    }
                    
                    ans=Math.max(ans,1+Math.min(Math.min(up,dow),Math.min(left,right)));
                }
            }
            
        }
        
        return ans;
        
    }
}


/***/
```


#100DaysOfCode
