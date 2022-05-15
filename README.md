# LeetCode Questions (Data-Structures)
## Arrays
### 1. Sliding Window
#### Q1. Contains Duplicate II
    ->By Brute Force (will show time limit exceeded) 
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
    
    ->Using maps(Correct Solution)
    class Solution {
    public:
        bool containsNearbyDuplicate(vector<int>& nums, int k) {
            unordered_map <int,int> m;
            int n=nums.size();
            for(int i=0;i<n;i++){
                if(m.count(nums[i])>0 && abs(i-(m[nums[i]]))<=k){
                    return true;
                }
                m[nums[i]]=i;
            }
            return false;

        }
    };
     
