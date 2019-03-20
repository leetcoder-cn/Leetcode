**思路**

将字符串锯齿状排列，再将所有字符顺序输出，每行应该输出的字符的迭代步长与当前所在行有关，拿图画一下就可以了。公式难点在代码中j的迭代策略上，可以参考代码。

**Runtime Result**
Runtime: 20 ms, faster than 97.81% of C++ online submissions for ZigZag Conversion.
Memory Usage: 16.4 MB, less than 97.86% of C++ online submissions for ZigZag Conversion.


**代码**
```
class Solution {
public:
    string convert(string s, int n) {
        int slen = s.size();
        if(slen < n || slen < 2 || n < 2)
        {
            return s;
        }
        int iter_length = 2 * n - 2;
        string res(slen, ' ');
        int i = 0, j;
        int row = 0, cur = 0;
        while(row < n)
        {
            i = row;
            if(i == 0 || i == n - 1)
            {
                while(i < slen)
                {
                    res[cur] = s[i];
                    cur ++;
                    i += iter_length;
                }
            }else
            {
                while(i < slen)
                {
                    res[cur] = s[i];
                    cur++;
                    j = i + iter_length - 2 * row;
                    if(j < slen)
                    {
                        res[cur] = s[j];
                        cur ++;
                    }
                    i += iter_length;
                }
            }
            
            row++;
        }
        return res;
    }
};
```

