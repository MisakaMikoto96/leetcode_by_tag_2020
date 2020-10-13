# ��̬�滮�����Ŀ

### [120. Triangle](https://leetcode.com/problems/triangle/)

> Given a triangle, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.
> 
> For example, given the following triangle

```
[
     [2],
    [3,4],
   [6,5,7],
  [4,1,8,3]
]
```
> The minimum path sum from top to bottom is 11 (i.e., 2 + 3 + 5 + 1 = 11).
- ����/�������ı任
- ��ʼ�����/�յ㣬���յ�/���
```
class Solution {
public:
    int minimumTotal(vector<vector<int>>& triangle) {
        if ( triangle.empty() || triangle[0].empty()){
            return 0;
        }
        vector<vector<int>> dp(triangle);
        for ( int i=dp.size()-2; i >= 0; i--){
            // ���һ�п�ʼ
            for ( int j=0; j < dp[i].size(); j++){
                dp[i][j] += min(dp[i+1][j], dp[i+1][j+1]);
            }
        }
        return dp[0][0];
    }
};
```
---