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

