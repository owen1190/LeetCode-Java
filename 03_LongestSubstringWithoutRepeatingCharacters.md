# 3. Longest Substring Without Repeating Characters
## 题目
Given a string, find the length of the longest substring without repeating characters.

Examples:

Given "abcabcbb", the answer is "abc", which the length is 3.

Given "bbbbb", the answer is "b", with the length of 1.

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
## 代码
建立一个hashmap，key为字符串中字符，value为所对应的位置。
设置两个指针，i负责扫描整个字符串，当遇到重复字符时，j负责移动到最后发现重复字符的处。


	public int lengthOfLongestSubstring(String s) {
        if(s.length()==0) return 0;
        HashMap<Character,Integer> hashMap=new HashMap<>();
        int max=0;
        for(int i=0,j=0;i<s.length();i++)
        {
           if(hashMap.containsKey(s.charAt(i)))
            {
                //将j指针移动到最后发现重复的地方，而且确保只能向前移动
				j=Math.max(j,hashMap.get(s.charAt(i))+1);
            }
            hashMap.put(s.charAt(i),i);
            max=Math.max(max,i-j+1);
        }
        return max;
    }
