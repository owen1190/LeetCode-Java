# 4. Median of Two Sorted Arrays
## 题目
There are two sorted arrays nums1 and nums2 of size m and n respectively. Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).
## 代码
```
public class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int m=nums1.length,n=nums2.length;
        int[] num=new int[m+n];
        int i=0,j=0,k=0;
        while(i<m||j<n)
        {
            //nums1数组已经查找完，直接将nums2数组存入nums
            if(i>=m&j<n) {num[k++]=nums2[j++];continue;}
            //nums2数组已经查找完，直接将nums2数组存入nums
            if(j>=n&i<m) {num[k++]=nums1[i++];continue;}
            if(nums1[i]>nums2[j]) {num[k++]=nums2[j++];}
            else num[k++]=nums1[i++];
        }
        int mid=(m+n)/2;
        //求中位数区分个数为偶数和奇数情况
        if((m+n)%2==0)
        {
            return (num[mid]+num[mid-1])/2.0;
        }
        else
        {return (double)num[mid];}
    }
}
```