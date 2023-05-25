 # Sliding Window

 ### Definitions
 * **Sliding Window** is a technique for reducing the complexity of algorithms. It is used such that the need for reusing the loops gets reduced and hence the program gets optimized. In this technique, we reuse the result of the previous step to compute the result of the next step.

 * **When to use**
   * When the problem involves continuous sequences or contiguous subsequences, or is about finding a subset of elements that satisfy certain constraints. 
   * Problems that ask for maximum/minimum sum or length (substring, subarray, or sublist) under certain constraints (positive numbers, values within a range, etc.)
   * Problems that involve string manipulations, such as substrings or palindrome problems.
  
* **How it works**
  *  Fixed Length Window 
    ```Python
    left = 0
    right = 0

    while right < len(nums):
        window.append(nums[right])
        
        # 超过窗口大小时，缩小窗口，维护窗口中始终为 window_size 的长度
        if right - left + 1 >= window_size:
            # 维护答案
            window.popleft()
            left += 1
        
        # 向右侧增大窗口
        right += 1
    ```
    * Non Fixed Length Window
    ```Python
    left = 0
    right = 0

    while right < len(nums):
        window.append(nums[right])
        
        while 窗口需要缩小:
            # ... 可维护答案
            window.popleft()
            left += 1
        
        # 向右侧增大窗口
    right += 1

    left = 0
    right = 0

    while right < len(nums):
        window.append(nums[right])
        
        # 超过窗口大小时，缩小窗口，维护窗口中始终为 window_size 的长度
        if right - left + 1 >= window_size:
            # ... 维护答案
            window.popleft()
            left += 1
        
        # 向右侧增大窗口
        right += 1



    ```

    ```Python
    def max_sub_array_of_size_k(k, arr):
        max_sum , window_sum = 0, 0
        window_start = 0

        for window_end in range(len(arr)):
            window_sum += arr[window_end]  # add the next element
            # slide the window, we don't need to slide if we've not hit the required window size of 'k'
            if window_end >= k-1:
                max_sum = max(max_sum, window_sum)
                window_sum -= arr[window_start]  # subtract the element going out
                window_start += 1  # slide the window ahead
        return max_sum
    ```

### Time and Space Complexity
* **Time Complexity:** O(n).
* **Space Complexity:** O(1). 

### Links
[Window Sliding Technique - geeksforgeeks ](https://www.geeksforgeeks.org/window-sliding-technique/)


### Problem Sets
[643. Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/?envType=study-plan-v2&id=leetcode-75) | [Notes](/643.%20Maximum%20Average%20Subarray%20I.md) 
