# Array-4

## Problem1 Array partition (https://leetcode.com/problems/array-partition/)

class Solution {
public:
    int arrayPairSum(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int i=0;
        int j=nums.size()/2;
        int sum=0;
        for(int i=0;i+1<nums.size();i+=2){
            sum+=min(nums[i],nums[i+1]);

        }

        return sum;
    }
};

## Problem2 Maximum Subarray (https://leetcode.com/problems/maximum-subarray/)

class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int i, max_sum_so_far = 0, curr_sum=0;
        for(i=0;i<nums.size();i++){
            curr_sum += nums[i];
            if(curr_sum >  max_sum_so_far){
                max_sum_so_far = curr_sum;
            }
            if(curr_sum<0){
                curr_sum = 0;
            }
        }
        if (max_sum_so_far == 0){
            max_sum_so_far = INT_MIN;
            for(i=0;i<nums.size();i++){
                if(max_sum_so_far < nums[i])
                    max_sum_so_far = nums[i];
            }
        }
        return max_sum_so_far;
    }
};

## Problem3  Next permutation(https://leetcode.com/problems/next-permutation/)

class Solution {
public:
    void swap(int *a,int *b)
    {
        int temp;
        temp=*a;
        *a=*b;
        *b=temp;
    }
    void nextPermutation(vector<int>& nums) {
        int n=nums.size();
        int i;
        if(n==1)
            cout<<nums[0];
        else
        {
        for(i=n-1;i>0;i--)
        {
            if(nums[i-1]<nums[i] )
                break;
        }
        if(i==0)
        {
            sort(nums.begin(),nums.end());
            
        }
        else
        {   
            int j,x=nums[i-1],smallest=i;
            for(j=i+1;j<n;j++)
            {
                if(nums[j]>x && nums[j]<nums[smallest])
                        smallest=j;
            }
            swap(&nums[i-1],&nums[smallest]);
            sort(nums.begin()+i,nums.end());
        }
        for(i=0;i<n;i++)
            cout<<nums[i];
        }
    }
        
};