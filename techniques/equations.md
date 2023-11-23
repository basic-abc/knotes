### Tips
- Always break down the equation, do not try to understand anything intuitively 
    - i.e. nums[0] <= nums[1] >= nums[2] <= nums[3]
    - nums[i] <= nums[i + 1] >= nums[i + 2] <= nums[i + 3]
    - odd: nums[i] <= nums[i + 1], even: nums[i] >= nums[i + 1]
- Use pen & paper to chart out decision trees to account for all permutations
- When you see an equation, always re-arrange the condition to have the variables on the same side
    - i.e. nums[i] + rev(nums[j]) == nums[j] + rev(nums[i]) should be considered as nums[i] - rev(nums[i]) == nums[j] - rev(nums[j]).
- When you find an equation to hold true to the problem, think of an easier way to apply that new found insight, it may lower complexity or lead to a more straightforward solution
