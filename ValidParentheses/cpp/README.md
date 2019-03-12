**思路**:

堆栈记录左括号，下标逐个访问字符串，字符串为左括号'([{'即入栈，当前为右括号时，栈顶与当前字符不匹配立即返回false，直到所有字符处理完毕。
最后堆栈不为空，则返回false，否则返回true。
时间复杂度：所有元素均需要访问，因此为O(n)
空间复杂度: 字符串全为左括号时，需要n个内存空间，因此为O(n)

**解法**:
```
class Solution {
public:
    vector<char> stack;
    bool isValid(string s) {
        if(s.size() < 1) return true;
        for(int i = 0; i < s.size(); ++i)
        {
            if(s[i] == '(' || s[i] == '[' || s[i] == '{')
                stack.push_back(s[i]);
            else{
                if(stack.size() == 0 || s[i] != get_match_parenthese(stack.back()))
                {
                    return false;
                }
                stack.pop_back();
            }
        }
        if(stack.size() > 0) return false;
        else return true;
    }
    char get_match_parenthese(char c)
    {
        if('[' == c)
            return ']';
        if('(' == c)
            return ')';
        return '}';
    }
    
};
```

**Runtime Result**:
Runtime: 4 ms, faster than 100.00% of C++ online submissions for Valid Parentheses.
Memory Usage: 8.7 MB, less than 96.24% of C++ online submissions for Valid Parentheses.