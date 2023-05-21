 # Two Pointers

 ### Definitions
 * **Two-pointer** is a method where two pointers iterate through the data structure in tandem until one or both of the pointers meet a certain condition.

 * **When to use**
   * Problem involves ```linked list or arrays``` that are sorted or meet specific sorted conditions \
  (like the sum is a target value, find the middle element of a linked list)
   * Maintain a running maximum or minimum elements as you traverse
   * Determine if an array has a cycle
  
* **How it works**
  * **Same direction:** Both pointers start at the beginning (or end) and move in the same direction.
  * **Opposite direction:** One pointer starts at the beginning, the other at the end, and both move towards each other.
    ```Python
    def two_pointer(arr, target):
        left, right = 0, len(arr) - 1
        while left < right:
            current_sum = arr[left] + arr[right]
            if current_sum == target:
                return [left, right]
            elif current_sum < target:
                left += 1
            else:
                right -= 1
        return [-1, -1] # pair not found
    ```
  * **Slow and Fast :** The slow pointer moves one step at a time while the fast pointer moves two steps at a time. If there is a cycle, the fast pointer will eventually meet the slow pointer.
    ```Python
    def hasCycle(head):
        slow = head
        fast = head
        while fast is not None and fast.next is not None:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                return True  # Cycle detected
        return False  # No cycle detected
    ```

### Time and Space Complexity
* **Time Complexity:** O(n). Each element is visited at most once, thus the time complexity is linear.
* **Space Complexity:** O(1). 
  
### Key Points to Note:
* It's important to understand when and how to move the pointers. Generally, this is based on the condition you're trying to satisfy.
* The two pointers method can often help reduce the time complexity from O(n^2) to O(n).
* Always check if your pointers go out of bounds of the array.
* Two pointers method often requires the array or sequence to be sorted or partially sorted to work correctly. It may not work properly on unsorted data.
* It's important to always check for null values especially in data structures like linked lists before moving pointers. A null check can prevent ```NullReferenceExceptions```.

### Problem Sets
[11. Container With Most Water](https://leetcode.com/problems/container-with-most-water/?envType=study-plan-v2&id=leetcode-75) | [Notes](/Two%20Pointers/11.%20Container%20With%20Most%20Water.md) \
[1679. Max Number of K-Sum Pairs | Medium](https://leetcode.com/problems/max-number-of-k-sum-pairs/?envType=study-plan-v2&id=leetcode-75) | [Notes](/Two%20Pointers/1679.%20Max%20Number%20of%20K-Sum%20Pairs.md)
