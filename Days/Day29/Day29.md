#Day29/100


Today I solved two Medium Level problems on #interviewbit. 


Problem1:https://www.interviewbit.com/problems/integer-to-roman/
```python

class Solution:
    # @param A : integer
    # @return a strings
    def intToRoman(self, A):
        intToRoman = {1:'I', 4:'IV', 5:'V', 9:'IX', 10:'X', 40:'XL', 50:'L', 90:'XC', 100:'C', 400:'CD', 500:'D', 900:'CM', 1000:'M'}
        ans = ""
        if A >= 1000:
            ans += intToRoman[1000]*(A//1000)
            A = A % 1000
        if A >= 900:
            ans += intToRoman[900]
            A = A % 900
        if A >= 500:
            ans += intToRoman[500]
            A = A % 500
        if A >= 400:
            ans += intToRoman[400]
            A = A % 400
        if A >= 100:
            ans += intToRoman[100]*(A//100)
            A = A % 100
        if A >= 90:
            ans += intToRoman[90]
            A = A % 90
        if A >= 50:
            ans += intToRoman[50]
            A = A % 50
        if A >= 40:
            ans += intToRoman[40]
            A %= 40
        if A >= 10:
            ans += intToRoman[10]*(A//10)
            A %= 10
        if A == 9:
            ans += intToRoman[9]
            return ans
        elif A > 5:
            ans += intToRoman[5] + intToRoman[1]*(A - 5)
            return ans
        elif A == 5:
            ans += intToRoman[5]
            return ans
        elif A == 4:
            ans += intToRoman[4]
            return ans
        else:
            ans += intToRoman[1]*A
            return ans



```

Problem2:https://www.interviewbit.com/problems/roman-to-integer/
```python
public class Solution {
  class Solution:
    # @param A : string
    # @return an integer
    def romanToInt(self, A):
        dic ={ "I" : 1,"V":5,"X":10,"C":100,"D":500,"L":50,"M":1000}

        i=len(A)-1;
        ans=dic[A[i]]
        i-=1
        while(i>=0):
            if dic[A[i]]<dic[A[i+1]]:
                ans=ans-dic[A[i]]
            else:
                ans=ans+dic[A[i]]
            i-=1
        return ans;

        


```
#100DaysOfCode