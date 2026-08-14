# Maximum-Length-Substring-With-Two-Occurrences
This repository has the optimal sliding window solution for the leetcode problem 3090 : Maximum Length Substring With Two Occurrences

class Solution:
    def maximumLengthSubstring(self, s: str) -> int:
        from collections import defaultdict
        
        count = defaultdict(int)
        start = 0
        max_len = 0
        
        for end in range(len(s)):
            count[s[end]] += 1
            
            # Shrink window if any character exceeds 2 occurrences
            while count[s[end]] > 2:
                count[s[start]] -= 1
                start += 1
            
            # Update max length
            max_len = max(max_len, end - start + 1)
        
        return max_len
