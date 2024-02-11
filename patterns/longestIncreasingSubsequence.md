### ELI5
- Sort the array
- Initiate a strictly increasing list
- For each new element
  - If larger than last element, append to list 
  - Else binary search to find insertion point & replace the next largest element
- Return list size

### Pitfalls
- This algorithm focuses on find the "length" of the longest subsequence in O(nlogn); it cannot provide the valid subsequence
- A more general DP approach would have been O(n^2)

### Template
- [300. Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/description/)
```
public int lengthOfLIS(int[] nums) {
        ArrayList<Integer> sub = new ArrayList<>();
        sub.add(nums[0]);
        
        for (int i = 1; i < nums.length; i++) {
            int num = nums[i];
            if (num > sub.get(sub.size() - 1)) {
                sub.add(num);
            } else {
                int j = binarySearch(sub, num);
                sub.set(j, num);
            }
        }
        
        return sub.size();
    }
    
    private int binarySearch(ArrayList<Integer> sub, int num) {
        int left = 0;
        int right = sub.size() - 1;
        int mid = (left + right) / 2;
        
        while (left < right) {
            mid = (left + right) / 2;
            if (sub.get(mid) == num) {
                return mid;
            }
            
            if (sub.get(mid) < num) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        
        return left;
    }
```
