# LeetCode Questions (Data-Structures)
## Arrays
### 1. Sliding Window
#### Q1. Contains Duplicate II
    By Brute Force (will show tme limit exceeded) 
    class Solution {
    public:
        bool containsNearbyDuplicate(vector<int>& nums, int k) {
           for(int i=0;i<nums.size();i++)
        {
            for(int j=i+1;j<nums.size();j++)
            {
                if(nums[i]==nums[j]&&abs(i-j)<=k)
                    return true;
            }
        }
        return false;
        }
    };
