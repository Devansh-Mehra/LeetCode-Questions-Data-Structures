# LeetCode Questions (Data-Structures)
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

