# LeetCode Questions (Data-Structures
  Solved Leetcode question on Data structures and Algorithm
## Arrays
### Q1.Two Sum

            class Solution {
            public:
                vector<int> twoSum(vector<int>& nums, int target) {
                    int n=nums.size();
                    for(int i=0;i<n;i++)
                    {
                        for(int j=i+1;j<n;j++)
                        {
                            if(target-nums[i]==nums[j]){
                                return {i,j};
                            }
                        }
                    }
                    return {-1,-1};

                }
            };

### Q2. Best Time to buy and sell stock
            
            class Solution {
            public:
                int maxProfit(vector<int>& prices) {
                    int min_prices = prices[0];
                    int profit=0;
                    for(int i=0; i < prices.size(); i++){

                        min_prices = min(min_prices,prices[i]);
                        profit = max(profit, prices[i]-min_prices);

                    }
                    return profit;

                }
            };
           
### Q3. Merge Sorted Arrays
            //when extra space is not allowed
            
            class Solution {
            public:
                void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
                    int i=m-1,j=n-1,k=(m+n)-1;
                    while(i>=0 && j>=0){
                        if(nums1[i]>=nums2[j]){
                            nums1[k--]=nums1[i--];
                        }
                        else{
                            nums1[k--]=nums2[j--];
                        }
                    }
                    while(i>=0){
                        nums1[k--]=nums1[i--];
                    }
                    while(j>=0){
                        nums1[k--]=nums2[j--];
                    }

                }
            };

### Q4. Move Zeroes
            //using 2 pointer approach
            
            class Solution {
            public:
                void moveZeroes(vector<int>& nums) {
                    int j=0;
                    for(int i=0;i<nums.size();i++){
                        if(nums[i]!= 0){
                            nums[j++]=nums[i];
                        }
                    }
                    while(j<nums.size())
                        nums[j++]=0;


                }
            };
            
### Q5. Best Time to buy aand sell stocks II

            class Solution {
            public:
                        int maxProfit(vector<int>& prices) {
                        int net=0;
                        for(int i=1;i<prices.size();i++){
                                    if(prices[i]>prices[i-1]){
                                                net+=(prices[i]-prices[i-1]);
                                    }
                        }
                        return net;
        
        
                        }
            };
        
### Q6. Running Sum of 1D Array 
            class Solution {
            public:
                vector<int> runningSum(vector<int>& nums) {
                    for(int i=1;i<nums.size();i++){
                        nums[i]+=nums[i-1];
                    }
                    return nums;
                }
            };
            
### Q7. Find Pivot Index
            class Solution {
            public:
                int pivotIndex(vector<int>& nums) {
                    int sum=0;
                    for(int i=0;i<nums.size();i++){
                        sum+=nums[i];
                    }
                    int rsum=sum;
                    int lsum=0;
                    for(int i=0;i<nums.size();i++){
                        lsum+=nums[i];
                        if(lsum==rsum)
                            return i;
                        rsum-=nums[i];
                    }
                    return -1;
                }
            };
            
### Q8. Majority Elements
            class Solution {
            public:
                int majorityElement(vector<int>& nums) {
                    int n=nums.size();
                    for(int i=0;i<n;i++){
                        int c=0;
                        for(int j=i;j<n;j++){
                            if(nums[i] == nums[j]){
                                c++;
                            }
                        }
                        if(c>n/2)
                            return nums[i];
                    }
                    return -1;

                }
            };

### Q9. Fibonacci Series
            class Solution {
            public:
                int fib(int n) {
                    if(n==1)
                        return 1;
                    if(n==0)
                        return 0;
                    else
                        return (fib(n-1) + fib(n-2));
                }
            };


### Q10. Squares of a Sorted Array
            class Solution {
            public:
                vector<int> sortedSquares(vector<int>& nums) {
                    vector<int> a;
                    for(int i=0;i<nums.size();i++){
                        int n=nums[i]*nums[i];
                        a.push_back(n);
                    }
                    sort(a.begin(),a.end());
                    return a;

                }
            };
             Remove Duplicates from Sorted Array
### Q11.  Remove Duplicates from Sorted Array
            class Solution {
            public:
                int removeDuplicates(vector<int>& nums) {
                    int x=1;
                    for(int i=1;i<nums.size();i++){
                        if(nums[i]==nums[i-1])
                            continue;
                        else{
                            nums[x]=nums[i];
                            x++;
                        }
                    }
                    return x;
                }
            };
         
### Q12. Merge Intervals
            class Solution {
            public:
                    vector<vector<int>> merge(vector<vector<int>>& intervals) {
                    vector<vector<int>> a;
                    if(intervals.size()==0)
                        return a;
                    sort(intervals.begin(), intervals.end());
                    vector<int> temp=intervals[0];
                    for(auto it:intervals){
                        if(it[0]<=temp[1]){
                            temp[1]=max(it[1], temp[1]);
                        }
                        else{
                            a.push_back(temp);
                            temp=it;
                        }
                    }
                    a.push_back(temp);
                    return a;
                    }
            };

### Q13. 3Sum 
            class Solution {
            public:
                vector<vector<int>> threeSum(vector<int>& nums) {
                    vector<vector<int>> a;

                    sort(nums.begin(), nums.end());

                    // 2 pointer approach
                    for(int i=0;i<nums.size()-2; i++){
                        if(i==0 || (i>0 && nums[i]!=nums[i-1])){
                            int l=i+1, h=nums.size()-1, sum= -nums[i];
                            while(l<h){
                                if(nums[l]+nums[h]==sum){
                                    vector<int> t;
                                    t.push_back(nums[i]);
                                    t.push_back(nums[l]);
                                    t.push_back(nums[h]);
                                    a.push_back(t);

                                    while(l<h && nums[l]==nums[l+1]) l++;
                                    while(l<h && nums[h]==nums[h-1]) h--;

                                    l++;h--;
                                }
                                else if(nums[l]+nums[h]<sum) l++;
                                else h--;
                            }
                        }

                    }
                    return a;
                }
            };
      
### Q14. Product of Array except self
            class Solution {
            public:
                vector<int> productExceptSelf(vector<int>& nums) {
                    vector<int> a;
                    if(nums.size()==0)
                        return a;
                    int p=1;
                    for(int i=0;i<nums.size(); i++){
                        p*=nums[i];
                        a.push_back(p);
                    }

                    p=1;
                    for(int j=nums.size()-1; j>0;j--){
                        a[j]=a[j-1]*p;
                        p*=nums[j];
                    }
                    a[0]=p;
                    return a;

                }
            };
            
### Q15. Subarray sum equals K
          class Solution {
          public:
              int subarraySum(vector<int>& nums, int k) {
                  unordered_map<int,int> m;
                  int sum=0;
                  int c=0;
                  for(int i=0;i<nums.size();i++){
                      sum+=nums[i];
                      if(sum==k)
                          c++;
                      if(m.find(sum-k)!=m.end())
                          c=m[sum-k]+c;
                      if(m.find(sum)!=m.end())
                          m[sum]++;
                      else
                          m[sum]=1;
                  }
                  return c;

              }
          };

### Q16. Next Permutation
        class Solution {
        public:
            void nextPermutation(vector<int>& nums) {
                if(nums.size()==0)
                    return;
                int id1;
                for(int i=nums.size()-2;i>=0;i--){
                    if(nums[i]<nums[i+1]){
                        id1=i;
                        break;
                    }
                }
                if(id1<0){
                    reverse(nums.begin(), nums.end());
                }
                else{
                    int id2=0;
                    for(int i=nums.size()-1;i>=0;i--){
                        if(nums[id1]<nums[i]){
                            id2=i;
                            break;
                        }
                    }
                    swap(nums[id1], nums[id2]);
                    reverse(nums.begin()+id1+1, nums.end());
                }

            }
        };

### Q17. Spiral Matrix
        class Solution {
        public:
            vector<int> spiralOrder(vector<vector<int>>& matrix) {
                int n = matrix.size();
                int m = matrix[0].size();
                vector<int>a;
                int count = 0;
                int total = n*m;

                int left= 0;
                int top = 0;
                int right = n-1;
                int down = m-1;

                while(count<total){
                    //starting row
                    for(int i=top;count<total && i<=down;i++){
                        a.push_back(matrix[left][i]);
                        count++;
                    }
                    left++;

                    //ending column
                    for(int i=left;count<total && i<=right;i++){
                        a.push_back(matrix[i][down]);
                        count++;
                    }
                    down--;

                    //ending row
                    for(int i = down;count<total && i>=top;i--){
                        a.push_back(matrix[right][i]);
                        count++;
                    }
                    right--;

                    //starting column
                    for(int i = right;count<total && i>=left;i--){
                        a.push_back(matrix[i][top]);
                        count++;
                    }
                    top++;
                }
                return a;
            }
        };
