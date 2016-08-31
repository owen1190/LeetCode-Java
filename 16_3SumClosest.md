# 16. 3Sum Closest
## 题目
Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target. Return the sum of the three integers. You may assume that each input would have exactly one solution.

 For example, given array S = {-1 2 1 -4}, and target = 1.

 The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).

## 代码


	 public int threeSumClosest(int[] nums, int target) {
	        int result=nums[0]+nums[1]+nums[nums.length-1];//result存入最近的值
	        Arrays.sort(nums);
	        for(int i=0;i<nums.length-1;i++)
	        {
	            int hi=i+1,lo=nums.length-1;
	            while(hi<lo)
	            {
	                int threeSum=nums[i]+nums[hi]+nums[lo];
	                if(threeSum>target)
	                {
	                    lo--;
	                }
	                else 
	                {
	                    hi++;
	                }
	                if(Math.abs(threeSum-target)<Math.abs(result-target))
	                {
	                    result=threeSum;
	                }
	            }
	        }
	        return result;
	    }

