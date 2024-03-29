# LeetCode Questions (Data-Structures
  Solved Leetcode question on Data structures and Algorithm

## LeetCode Questions

### Q1. Two Sum
            class Solution {
            public:
                vector<int> twoSum(vector<int>& nums, int target) {
                    for(int i=0;i<nums.size();i++){
                        for(int j=i+1;j<nums.size();j++){
                            if(target- nums[i] == nums[j])
                            return{i,j};   
                        }
                    }
                    return{-1,-1};
                } 
            };
            
### Q2. Palindrome Number
            class Solution {
            public:
                bool isPalindrome(int x) {
                    if(x<0 || (x % 10 == 0 && x != 0) )
                       return false;
                    int y=x;
                    long int n=0;
                    while(x>0){
                        n=n*10;
                        n=n+(x%10);
                        x=x/10;
                    }
                    if(n==y)
                        return true; 
                    else 
                        return false;
                }
            };

### Q3. Roman to Integer
            class Solution {
            public:
                int romanToInt(string s) {
                    int sum=0;
                    unordered_map<char, int>  m = {{'I',1}, {'V', 5}, {'X', 10}, {'L',50}, {'C', 100}, {'D', 500}, {'M', 1000}};

                    for(int i=0;i<s.length();i++){
                        if(m[s[i]]<m[s[i+1]])
                           sum-=m[s[i]];      // eg. -> IV = 4 = 5-1
                        else
                           sum+=m[s[i]];     // eg. -> VI = 6 = 5+1
                    }
                    return sum;
                }
            };
     
### Q4. Longest Common Prefix
            class Solution {
            public:
                string longestCommonPrefix(vector<string>& strs) {
                    int n= strs.size();
                    if(n==0)
                        return "";
                    string ans ="";
                    sort(strs.begin(), strs.end());
                    string a = strs[0];
                    string b = strs[n-1];
                    for(int i=0;i<a.length();i++){
                        if(a[i]==b[i])
                            ans=ans+a[i];
                        else
                            break;
                    }
                    return ans;

                }
            };
        
### Q5. Valid Parentheses            
            class Solution {
            public:
                bool isValid(string s) {
                    stack<char> a;
                    for(auto i : s){
                        if(i=='('|| i=='['|| i=='{' )
                            a.push(i);
                        else {
                            if(a.empty() || (a.top()=='(' && i!=')') || (a.top()=='[' && i!=']')|| (a.top()=='{' && i!='}'))
                                return false;
                            a.pop();
                        }
                    }
                    return a.empty();
                }
           };

### Q6. Merge 2 sorted lists
            class Solution {
            public:
                ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
                    if(list1 == NULL)
                        return list2;
                    if(list2 == NULL)
                        return list1;
                    ListNode* p=NULL;
                    if(list1->val < list2->val)
                    {
                        p=list1;
                        list1=list1->next;
                    }
                    else if(list1->val >= list2->val)
                    {
                        p=list2;
                        list2=list2->next;
                    }

                    ListNode* c=p;
                    while(list1 && list2)
                    {
                        if(list1->val < list2->val)
                        {
                            c->next=list1;
                            list1=list1->next;
                        }
                        else 
                        {
                            c->next=list2;
                            list2=list2->next;
                        }
                        c = c->next;
                    }
                    if(!list1)
                        c->next=list2;
                    else
                        c->next=list1;

                    return p;
                }
            };

### Q7. Remove Duplicates from Sorted Array
            class Solution {
            public:
                int removeDuplicates(vector<int>& nums) {
                    int c=1;
                    for(int i=1;i<nums.size();i++){
                        if(nums[i]==nums[i-1])
                            continue;
                        else
                        {
                            nums[c]=nums[i];
                            c++;   
                        }
                    }
                    return c;
                }
            };
        
### Q8. Remove Element
            class Solution {
            public:
                int removeElement(vector<int>& nums, int val) {
                    int c=0;
                    for(int i=0;i<nums.size();i++){
                        if(nums[i]==val)
                            continue;
                        else{
                            nums[c]=nums[i];
                            c++;
                        }
                    }
                    return c;
                }
            };
       
### Q9. Search Insert Position 
            class Solution {
            public:
                int searchInsert(vector<int>& nums, int target) {
                    int l=0, h=nums.size()-1;
                    while(l<=h){
                        int mid = (l+h)/2;
                        if(target==nums[mid])
                            return mid;
                        else if(target>nums[mid])
                            l=mid+1;
                        else 
                            h=mid-1;
                    }
                    return l;
                }
            };

### Q10. Length of last word
            class Solution {
            public:
                int lengthOfLastWord(string s) {
                    int c=0,f=0;
                    for(int i=s.length()-1;i>=0;i--){
                        if(s[i]!=' '){
                            c++;
                            f=1;
                        }
                        else{
                            if(f==1)
                                break;
                        }
                    }
                    return c;

                }
            };
            
### Q11. Plus One
            class Solution {
            public:
                vector<int> plusOne(vector<int>& digits) {
                    for(int i=digits.size()-1;i>=0;i--){
                        if(digits[i]==9)
                            digits[i]=0;
                        else {
                            digits[i]=digits[i]+1;
                            return digits;
                        }
                    }
                    digits.push_back(0);
                    digits[0] = 1;
                    return digits;
                }
            };
            
### Q12. Climbing stairs
            class Solution {
            public:
                int climbStairs(int n) {
                    if(n<=2)
                        return n;
                    int s1=2,s2=1, r=0;
                    for(int i=3;i<=n;i++){
                        r=s1+s2;
                        s2=s1;
                        s1=r;
                    }
                    return r;
                }
            };
            
### Q13. Remove Duplicates from Sorted List
            class Solution {
            public:
                ListNode* deleteDuplicates(ListNode* head) {
                    if(!head) return head;
                    ListNode* cur = head;
                    while(cur->next != NULL){
                        if(cur->val == cur->next->val )
                            cur->next=cur->next->next;
                        else
                            cur=cur->next;
                    }
                    return head;
                }
            };

### Q14. Merge Sorted Array
            class Solution {
            public:
                void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
                    int i=m-1, j=n-1, k=(m+n)-1;
                    while(i>=0 && j>=0){
                        if(nums1[i]>nums2[j])
                            nums1[k--] = nums1[i--];
                        else
                            nums1[k--] = nums2[j--];
                    }
                    while(i>=0)
                        nums1[k--]=nums1[i--];
                    while(j>=0)
                        nums1[k--]=nums2[j--];
                }
            };

### Q15. Container With Most Water
            class Solution {
            public:
                int maxArea(vector<int>& height) {
                    int water = 0;
                    int i = 0, j = height.size() - 1;
                    while (i < j) {
                        int h = min(height[i], height[j]);
                        water = max(water, (j - i) * h);
                        while (height[i] <= h && i < j) i++;
                        while (height[j] <= h && i < j) j--;
                }
                return water;  
                }
            };

### Q16. Single Number
         
            class Solution {
            public:
                int singleNumber(vector<int>& nums) { 
                   sort(nums.begin(),nums.end());
                    for(int i=1;i<nums.size();i+=2)
                    {
                        if(nums[i]!=nums[i-1])
                            return nums[i-1];
                    }
                    return nums[nums.size()-1];
                }
            }; 
            
### Q17. Linked List Cycle

            class Solution {
            public:
                bool hasCycle(ListNode *head) {
                    ListNode* p1 = head;
                    ListNode* p2 = head;
                    if(head==NULL)
                        return false;
                    while(p2!=NULL && p2->next!=NULL){
                        p2=p2->next->next;
                        p1=p1->next;

                        if(p1==p2)
                            return true;
                    }
                    return false;

                }
            };
          
### Q.18 Valid Palindrome  
            class Solution {
            public:
                bool isPalindrome(string s) {
                    if(s.length() <= 1)
                        return true;
                    int l=0, h=s.length()-1;
                    while(l<h){
                         while(l<h && !isalnum(s[l])) // isalnum - function to check whether given charater is alphanumeric (i.e either alphabet or numeric) or not
                            l++;
                        while(l<h && !isalnum(s[h]))
                            h--;
                        if(l<h && tolower(s[l]) != tolower(s[h]))
                            return false;   
                        l++;
                        h--;     
                    }
                    return true;
                }
            };
            
### Q19. Intersection of Two Linked Lists        
      
          class Solution {
          public:
              ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
                  ListNode* a=headA;
                  ListNode* b=headB;

                  if(a==NULL || b== NULL)
                      return NULL;

                  while(a != NULL && b != NULL ){
                      if(a!=b){
                          a=a->next;
                          b=b->next;
                      }
                      if(a==b)
                          return a;
                      if (a == NULL) a = headB;
                      if (b == NULL) b = headA;
                  }
                  return a;
              }

          };
          
### Q20. Majority Element
          class Solution {
          public:
              int majorityElement(vector<int>& nums) {
                  sort(nums.begin(),nums.end());
                  int n=nums.size();
                  return nums[n/2];
              }
          };
      
### Q21. Add Binary
          class Solution {
            public:
                string addBinary(string a, string b) {
                    string val;
                    int sum=0,carry=0;
                    int i=a.length()-1, j=b.length()-1;
                    while(i>=0 || j>=0){
                        sum=carry;
                        if(i>=0)
                            sum+=a[i]-'0';
                        if(j>=0)
                            sum+=b[j]-'0';
                        val+=to_string(sum%2);
                        carry = sum/2;
                        i--,j--;
                    }
                    if(carry!=0)
                        val+='1';
                    reverse(val.begin(),val.end());
                    return val;
                }
            };
            
### Q22. Add Two Numbers
            class Solution {
            public:
                ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
                    ListNode* dummy = new ListNode();
                    ListNode* temp = dummy;
                    int carry=0;
                    while(l1!=NULL || l2!=NULL || carry == 1){
                        int sum=0;
                        if(l1!=NULL){
                            sum+=l1->val;
                            l1=l1->next;
                        }
                        if(l2!=NULL){
                            sum+=l2->val;
                            l2=l2->next;
                        }
                        sum+=carry;
                        carry=(sum/10);
                        ListNode* node = new ListNode(sum%10);
                        temp->next = node;
                        temp = temp->next;
                    }
                    return dummy -> next;
                }
            };
            
### Q23. Excel Sheet Column Number
            class Solution {
            public:
                int titleToNumber(string columnTitle) {
                    int res=0;
                    for(int i=0; i<columnTitle.size(); i++){
                        res = res*26 + (columnTitle[i]-'A'+1);
                    }
                    return res;
                }
            }; 
            
### Q24. Excel Sheet Column Title

            class Solution {
            public:
                string convertToTitle(int columnNumber) {
                  string res="";
                  while(columnNumber!=0){
                      columnNumber--;
                      res=(char)(columnNumber%26 + 'A' ) + res;
                      columnNumber/=26;
                  }
                  return res;
                }
            };
       
### Q25. Number Of 1 Bits 
    
            class Solution {
            public:
                int hammingWeight(uint32_t n) {
                    int c=0;
                    while(n>0){
                        if(n&1==1)
                            c++;
                        n=n>>1;
                    }
                    return c;
                }
            };
            
 ### Q26. Happy Number
 
            class Solution {
            public:
                bool isHappy(int n) {
                    unordered_set<int> a;
                    int sum=0;
                    while(n != 1){
                        if(a.find(n) == a.end())
                            a.insert(n);
                        else
                            return false;
                        sum=0;
                        while(n!=0){
                            sum+= pow(n%10,2);
                            n=n/10;
                        }
                        n=sum;
                    }
                    return true;
                }
            };

 ### Q27. Remove Linked List Elements
            class Solution {
            public:
                ListNode* removeElements(ListNode* head, int val) {
                    if(head==nullptr)
                        return head;
                    while(head!=nullptr && head->val==val){
                        head=head->next;
                    }
                    ListNode *cur=head;
                    while(cur!=nullptr && cur->next!=nullptr){
                        if(cur->next->val==val)
                            cur->next=cur->next->next;
                        else
                            cur=cur->next;
                    }
                    return head;
                }
            };
### Q28. Reverse Linked List
            
            class Solution {
            public:
                ListNode* reverseList(ListNode* head) {
                    ListNode *temp=NULL;
                    ListNode *prev=head;
                    ListNode *cur=head;
                    if(head=nullptr)
                        return head;
                    while(cur!=NULL){
                        cur=cur->next;
                        prev->next=temp;
                        temp=prev;
                        prev=cur;
                    }
                    return temp;
                }
            };

### Q.29 Rotate Array
            class Solution {
            public:
                void rotate(vector<int>& nums, int k) {
                  k%=nums.size();
                  reverse(nums.begin(), nums.end());  //reverse the array
                  reverse(nums.begin(), nums.begin()+k); //reverse from start till start+k elements
                  reverse(nums.begin()+k, nums.end()); // reverse from start+k till end 
                }
            };

### Q30. Check if Array Is Sorted and Rotated
            class Solution {
            public:
                bool check(vector<int>& nums) {
                    int count =0;
                    int n =nums.size();
                    for(int i=1;i<n;i++){
                        if(nums[i-1]>nums[i])
                            count++;
                    }
                    if(nums[n-1]>nums[0])
                        count++;
                    if(count<=1)
                        return true;
                    else
                        return false;
                }
            };
            
### Q31. Remove All Occurrences of a Substring
            class Solution {
            public:
                string removeOccurrences(string s, string part) {
                    while(s.length()!=0 && s.find(part) < s.length()){
                        s.erase(s.find(part), part.length());
                    }
                    return s;
                }
            };

### Q32. Remove All Adjacent Duplicates In String
            class Solution {
            public:
                string removeDuplicates(string s) {
                    stack<char> t;
                    for(char x:s){
                        if(!t.empty() && t.top()==x) 
                            t.pop();
                        else
                            t.push(x);
                    }
                    s="";
                    while(!t.empty()){
                        s=t.top() + s;
                        t.pop();
                    }
                    return s;
                }
            };

### Q33. String Compression
            class Solution {
            public:
                int compress(vector<char>& chars) {
                    int i=0;
                    int ansIndex=0;
                    while(i<chars.size()){
                        int j=i+1;
                        while(j<chars.size() && chars[i]==chars[j]){
                            j++;
                        }
                        chars[ansIndex++]=chars[i];
                        int count = j-i;    //j will be at another elements position

                        if(count > 1){
                            //converting count into single digit & saving in ansIndex 
                            string cnt = to_string(count);
                            for(char ch: cnt){
                                chars[ansIndex++]=ch;
                            }
                        }
                        i=j;
                    }
                    return ansIndex;
                }
            };
### Q34. Spiral Matrix
            class Solution {
            public:
                vector<int> spiralOrder(vector<vector<int>>& matrix) {

                    vector<int> ans;
                    int row = matrix.size();
                    int col = matrix[0].size();

                    int count=0;
                    int total_elements = row*col;
                    int s_row = 0;
                    int s_col = 0;
                    int e_row = row-1;
                    int e_col = col-1;

                    while(count < total_elements){
                        //printing starting row
                        for(int i = s_row ; count < total_elements && i <= e_col; i++){
                            ans.push_back(matrix[s_row][i]);
                            count++;
                        }
                        s_row++;

                        //for printing ending column
                        for(int i=s_row ; count < total_elements && i <= e_row; i++){
                            ans.push_back(matrix[i][e_col]);
                            count++;
                        }
                        e_col--;

                        //printing ending row;
                        for(int i=e_col ; count < total_elements && i>=s_col; i--){
                            ans.push_back(matrix[e_row][i]);
                            count++;
                        }
                        e_row--;

                        //printing starting col
                        for(int i=e_row; count < total_elements && i>=s_row; i--){
                            ans.push_back(matrix[i][s_col]);
                            count++;
                        }
                        s_col++;
                    }
                    return ans;
                }
            };

### Q35. Rotate Image
            class Solution {
            public:
                void rotate(vector<vector<int>>& matrix) {
                    reverse(matrix.begin(), matrix.end());
                    for(int i=0; i<matrix.size();i++){
                        for(int j=i+1; j<matrix[0].size();j++){
                            swap(matrix[i][j], matrix[j][i]);
                        }
                    }
                }
            };

### Q36. Search a 2D matrix 
            //using binary search in 2D
            class Solution {
            public:
                bool searchMatrix(vector<vector<int>>& matrix, int target) {
                    int row = matrix.size();
                    int col =  matrix[0].size();

                    int s = 0;
                    int e = row*col-1;

                    int mid = s + (e-s)/2;

                    while(s<=e){

                        int element = matrix[mid/col][mid%col];

                        if(element==target){
                            return 1;
                        }
                        else if(element < target){
                            s=mid+1;
                        }
                        else{
                            e=mid-1;
                        }
                        mid = s + (e-s)/2;
                    }
                    return 0;
                }
            };
            
### Q37. Search a 2D Matrix II
            class Solution {
            public:
                bool searchMatrix(vector<vector<int>>& matrix, int target) {
                    int row = matrix.size();
                    int col = matrix[0].size();

                    int rowIndex=0;
                    int colIndex = col-1;

                    while(rowIndex < row && colIndex >= 0){
                        int element = matrix[rowIndex][colIndex];
                        if(element == target)
                            return 1;
                        else if(element < target)
                            rowIndex++;
                        else 
                            colIndex--;
                    }
                    return 0;
                }
            };

### Q38. Count Primes
            //brute foce approach and will give TLE
            class Solution {
            bool isPrime(int n){
                if(n<=1)
                    return false;
                for(int i=2;i<n;i++){
                    if(n%i==0)
                        return true;
                }
                return false;
            }
            public:
                int countPrimes(int n) {
                 int count=0;
                 for(int i=2;i<n;i++){
                     if(isPrime(i))
                        count++;
                 }
                 return count;   
                }
            };
            
            //using sieve of Eratosthenes.
            class Solution {
            public:
                int countPrimes(int n) {
                    int count =0;
                    vector<bool> prime(n+1,true); //vector elements from 0 to n
                    prime[0]=prime[1]=false;
                    for(int i=2;i<n;i++){
                        if(prime[i]!=0){
                            count++;

                            for(int j=2*i;j<n;j+=i){  // make multiples of i == 0
                                prime[j]=0;
                            }
                        }
                    }
                    return count;

                }
            };
            
### Q39. Fibonacci Number
            class Solution {
            public:
                int fib(int n) {
                    if(n==0)
                        return 0;
                    if(n==1)
                        return 1;

                    return fib(n-1)+fib(n-2);
                }
            };
            
### Q40. Subsets 
            class Solution {
            private:
                void solve(vector<int> nums, vector<int> output, int index, vector<vector<int>>& ans){
                    //base case
                    if(index >= nums.size()){
                        ans.push_back(output);
                        return;
                    }

                    //exclude
                    solve(nums,output,index+1,ans);

                    //include
                    int element = nums[index];
                    output.push_back(element);
                    solve(nums,output,index+1,ans);
                }
            public:
                vector<vector<int>> subsets(vector<int>& nums) {
                    vector<vector<int>> ans; //to store all ans 
                    vector<int> output;
                    int index=0;
                    solve(nums,output,index,ans); 
                    return ans ;
                }
            };

### Q41. Letter Combinations of a Phone Number
            class Solution {
            private:
                void solve(string digit, string output, int index, vector<string>& ans, string mapping[]){
                    //base case
                    if(index >= digit.length()){ 
                        ans.push_back(output);
                        return;
                    }

                    int number = digit[index] - '0';
                    string value = mapping[number];

                    for(int i=0 ; i<value.length() ; i++){
                        output.push_back(value[i]);
                        solve(digit, output, index+1, ans, mapping);
                        output.pop_back();  //to backtrack or empty the output 
                    }
                }

            public:
                vector<string> letterCombinations(string digits) {
                    vector<string> ans;

                    if(digits.length()==0) //empty string
                        return ans;
                    string output;
                    int index=0;

                    // to map no. with corresponding alphabet
                    string mapping[10] = {"", "", "abc", "def","ghi","jkl","mno","pqrs","tuv","wxyz"}; 
                    solve(digits, output, index, ans, mapping);
                    return ans;


                }
            };
            
### Q42. Permutations
            class Solution {
            void solve(vector<int> nums, vector<vector<int>>& ans,  int index){
                //base case
                if(index >= nums.size()){
                    ans.push_back(nums);
                    return;
                }

                for(int j=index ; j<nums.size() ; j++){
                    swap(nums[index], nums[j]); //step 1 - swap 1 with 1,2,3
                    solve(nums,ans,index+1); //recursive call

                    //backtrack
                    swap(nums[index], nums[j]);
                }
            }

            public:
                vector<vector<int>> permute(vector<int>& nums) {
                    vector<vector<int>> ans;
                    int index=0;
                    solve(nums, ans, index);
                    return ans;
                }
            };

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
                int right = n-1;
                int top = 0;
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

### Q18. Container with most water
        class Solution {
        public:
            int maxArea(vector<int>& height) {
                int c=0;
                int l=0;
                int r=height.size()-1;
                while(l<=r){
                    c=max(min(height[l],height[r])*(r-l), c);
                    if(height[l]<height[r])
                        l++;
                    else
                        r--;
                }
                return c;

            }
        };
        
### Q19. Rotate Image
      class Solution {
      public:
          void rotate(vector<vector<int>>& matrix) {
              for(int i=0;i<matrix.size(); i++){
                  for(int j=0;j<i;j++){
                      swap(matrix[i][j], matrix[j][i]);
                  }
              }
              for(int i=0;i<matrix.size();i++){
                  reverse(matrix[i].begin(), matrix[i].end());
              }

          }
      };

### Q20. Word Search
      class Solution {
      public:
          bool help(vector<vector<char>>& board, string word,int i,int j,int n,int m,int k){
              if(k>=word.size()) return true;
              if(i<0 || j<0 || i>=n || j>=m || board[i][j]=='.' || word[k]!=board[i][j]) return false;
              if(word.size()==1 && word[k]==board[i][j]) return true;
              board[i][j]='.';
              bool temp = false;
              int x[4]={0, 0, -1, 1};
              int y[4]={-1,1,0,0};
              for(int index=0;index<4;index++){
                  temp = temp || help(board, word, i+x[index], j+y[index], n,m,k+1);
              }
              board[i][j]=word[k];
              return temp;
          }

          bool exist(vector<vector<char>>& board, string word) {
              int n=board.size();
              if(n==0) return false;
              int m = board[0].size();
              if(word.size()==0) return false;
              for(int i=0;i<n;i++){
                  for(int j=0;j<m;j++){
                      if(word[0]==board[i][j]){
                          if(help(board, word, i, j, n, m, 0)) return true;
                      }
                  }
              }
              return false;
          }
      };
      
### Q21. 3Sum Closest
      class Solution {
      public:
          int threeSumClosest(vector<int>& nums, int target) {
              int min = INT_MAX, a, sum;
              sort(nums.begin(), nums.end());

              for(int i=0; i<nums.size()-2; i++){
                  if(i==0 || nums[i]!=nums[i-1]){
                      int l=i+1;
                      int h=nums.size()-1;
                      while(l<h){
                          sum = nums[i]+nums[l]+nums[h];
                          if(sum==target)
                              return sum;
                          else if(sum<target)
                              l++;
                          else
                              h--;
                      }
                      if(abs(sum-target)<min){
                          a = sum;
                          min = abs(sum-target);
                      }
                  }
              }

              return a;
          }
      };
### Q22. Game Of Life 
      class Solution {
      public:
          bool isValidNeighbour(int x, int y, vector<vector<int>>& board){
              return(x >= 0 && x < board.size() && y>=0 && y<board[0].size());
          }
          void gameOfLife(vector<vector<int>>& board) {
              //8 coordinates of neighbour(dx,dy)
              vector<int> dx = {0,0,1,1,1,-1,-1,-1};
              vector<int> dy = {1,-1,1,-1,0,0,1,-1};

              for(int row=0; row<board.size(); row++){
                  for(int col=0; col<board[0].size(); col++){
                      int count_live=0;

                      for(int i=0;i<8;i++){
                          int curr_x = row+dx[i], curr_y = col+dy[i];
                          if(isValidNeighbour(curr_x,curr_y, board)&&abs(board[curr_x][curr_y])==1)
                              count_live++;
                      }
                      if(board[row][col]==1 && (count_live<2 || count_live>3))
                          board[row][col]=-1;
                      if(board[row][col]==0 && (count_live==3))
                          board[row][col]=2;
                  }
              }
              for(int row=0;row<board.size();row++){
                  for(int col=0;col<board[0].size();col++){
                      if(board[row][col] >= 1)
                          board[row][col] = 1;
                      else
                          board[row][col]=0;
                  }
              }

          }
      };
