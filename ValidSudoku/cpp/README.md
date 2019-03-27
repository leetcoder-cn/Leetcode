**思路**

行和列同时判断，需要三层循环，每逢3*3的左上角位置，检查所在的3x3格子是否合规，直到所有的格子被检查。

**Runtime Result**

Runtime: 16 ms, faster than 98.63% of C++ online submissions for Valid Sudoku.
Memory Usage: 9.7 MB, less than 98.24% of C++ online submissions for Valid Sudoku.

**代码**

```cpp
class Solution {
public:
    bool isValidSudoku(vector<vector<char>>& board) {
        for(int i = 0; i < 9; ++i)
        {
            for(int j = 0; j < 8; ++j)
            {
                if(i % 3 == 0 && j % 3 == 0)
                {
                    set<int> nums;
                    for(int k = 0; k < 3; ++k)
                    {
                        for(int t = 0; t < 3; ++t)
                        {
                            int x = i + k,  y = j + t;
                            if(board[x][y] == '.') continue;
                            if(nums.find(board[x][y]) != nums.end())
                            {
                                return  false;
                            }else{
                                nums.insert(board[x][y]);
                            }
                        }
                    }
                }
                if(board[i][j] != '.') 
                {
                    for(int k = j + 1; k < 9; ++k)
                    {
                        if(board[i][j] == board[i][k])
                        {
                            return false;
                        }
                    }                    
                }
                if(board[j][i] != '.') 
                {
                    for(int k = j + 1; k < 9; ++k)
                    {
                        if(board[j][i] == board[k][i])
                        {
                            return false;
                        }
                    }
                }                
            }
        }
        return true;
    }
};
```