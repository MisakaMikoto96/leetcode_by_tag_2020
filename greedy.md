# ̰���㷨
## [55. Jump Game ???](https://leetcode.com/problems/jump-game/)
> Given an array of non-negative integers, you are initially positioned at the first index of the array.
> 
> Each element in the array represents your maximum jump length at that position.
> 
> Determine if you are able to reach the last index.
```
Example 1:

Input: nums = [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
Example 2:

Input: nums = [3,2,1,0,4]
Output: false
Explanation: You will always arrive at index 3 no matter what. Its maximum jump length is 0, which makes it impossible to reach the last index.
```
- ֻ�����ܲ��ܵ����ұߣ�����̰��
- �߽�����
```
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int reach = 0; // ��ǰ����������Զ����
        for ( int i=0; i < nums.size(); i++){
            if ( i > reach || reach >= nums.size()-1){
                // i > reach �󣬺��治��Ҫ�����ˣ��϶������ˣ�
                // �߽���������
                break;
            }
            reach = max( reach, i + nums[i]);
        }
        return reach >= nums.size()-1;
    }
};
```
---
## [45. Jump Game II](https://leetcode.com/problems/jump-game-ii/)

```
Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Your goal is to reach the last index in the minimum number of jumps.

Example:

Input: [2,3,1,1,4]
Output: 2
Explanation: The minimum number of jumps to reach the last index is 2.
    Jump 1 step from index 0 to 1, then 3 steps to the last index.
```
- ����̰��ѭ����ʵ���ڰ���̰��ǰλ�õ���һ������������������Զ���롣����cur_begin��cur_end������䲻���Ե���˳��
```
class Solution {
public:
    int jump(vector<int>& nums) {
        int res=0;
        int cur_begin=0, cur_end=0, reach=0;
        while ( cur_end < nums.size()-1){
            for ( int i = cur_begin; i <= cur_end; i++){
                reach = max(reach, i + nums[i]);
            }
            res += 1;
            cur_begin = cur_end+1;
            cur_end = reach;
            
        }
        return res;
        
    }
};
```
