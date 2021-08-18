
# Day9/100

Today I solved three Coding problems on #interviewbit on Tree Topic. I  learned How we can travels in trees, What BST is, and many more things about trees in DAS.

[Problem 1](https://www.interviewbit.com/problems/valid-bst-from-preorder/)

```java
public class Solution {
    public int solve(ArrayList<Integer> A) {

        Stack<Integer> ans=new Stack<>();

        int r=-1;

        for(int i=0;i<A.size();i++){
            
            while(!ans.isEmpty() && A.get(i)>ans.peek()){
                r=ans.pop();
            }

            if(A.get(i)<r){
                return 0;
            }

            ans.push(A.get(i));
        }
        return 1;
    }
}

```


[Problem 2](https://www.interviewbit.com/problems/2sum-binary-tree/)

```java
/**
 * Definition for binary tree
 * class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) {
 *      val = x;
 *      left=null;
 *      right=null;
 *     }
 * }
 */
public class Solution {
    public int t2Sum(TreeNode A, int B) {

        Stack<TreeNode> left=new Stack<>();
        Stack<TreeNode> right=new Stack<>();

        TreeNode tem=A;
        while(tem!=null){
            left.push(tem);
            tem=tem.left;
        }

        tem=A;


        while(tem!=null){
            right.push(tem);
            tem=tem.right;
        }

        int i=0;

        while(!left.isEmpty() && !right.isEmpty()){


            TreeNode l=left.peek();
            TreeNode r=right.peek();

            if(l.val+r.val==B && l!=r) return 1;
            else if(l.val+r.val > B){
                TreeNode c=right.pop();
                c=c.left;

                while(c!=null){
                    right.push(c);
                    c=c.right;
                }
            }else{
                 TreeNode c=left.pop();
                c=c.right;

                while(c!=null){
                    left.push(c);
                    c=c.left;
                }

            }


        }


        return i;




        //my
        // HashSet<Integer> ans=new HashSet<>();
        // // left->root->right
        // TreeNode tem=A;
        // while(!s.isEmpty() || tem!=null){
        //     if(tem!=null){
        //         s.push(tem);
        //         tem=tem.left;
        //     }else{
        //         TreeNode t=s.pop();
        //         if(ans.contains(B-t.val)){
        //             return 1;
        //         }else{
        //             ans.add(t.val);
        //         }



              

        //         tem=t.right;
        //     }

        
        // }
        // return 0;



    }
}

```

[Problem 3](https://www.interviewbit.com/problems/kth-smallest-element-in-tree/)

```java

/**
 * Definition for binary tree
 * class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) {
 *      val = x;
 *      left=null;
 *      right=null;
 *     }
 * }
 */
public class Solution {
    int c=1;
    public int kthsmallest(TreeNode A, int B) {

        // if(A!=null){
        //     int ans=kthsmallest(A.left,B);
        //     if(ans!=-1){
        //         return ans;
        //     }
        //     if(c==B){
        //         return A.val;
        //     }
        //     c++;
        //     return kthsmallest(A.right,B);
        // }
        // return -1;

        Stack<TreeNode> s=new Stack<>();


        // left->root->right

        TreeNode tem=A;


        while(!s.isEmpty() || tem!=null){

            if(tem!=null){
                s.push(tem);
                tem=tem.left;
            }else{

                TreeNode t=s.pop();

                if(c==B){

                    return t.val;

                }
                c++;

                tem=t.right;
            }

        
        }
        return -1;

       
    }
    
}


```


   
#100DaysOfCode
@ZeelCodder