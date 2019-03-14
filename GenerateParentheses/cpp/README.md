**思路**

回溯法，两个变量记录当前左右括号的剩余数量，有左括号就放左括号，左括号放完、或者回溯时，查看右括号的余量，在右括号有余量并且右括号余量大于左括号时，放右括号。当左右括号全部放完时，记录一次结果。

**Runtime Result**

Runtime: 8 ms, faster than 98.89% of C++ online submissions for Generate Parentheses.
Memory Usage: 17.8 MB, less than 15.18% of C++ online submissions for Generate Parentheses.

**解法**
```
class Solution {
public:
    vector<string> result;
    vector<string> generateParenthesis(int n) {
        tbk(n, n, "");
        return result;
    }
    void tbk(int left, int right, string s)
    {
        if(left == 0 && right == 0){
            result.push_back(s);
        }else{
            if(left > 0){
                tbk(left - 1, right, s + '(');
            }
            if(right > 0 && right > left)
            {
                tbk(left, right - 1, s + ')');
            }
        }
    }
};
```