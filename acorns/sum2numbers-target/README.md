/*
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.
 

Example 1:

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].


Example 2:

Input: nums = [2,3,4], target = 6
Output: [0,2]


Example 3:

Input: nums = [3,3], target = 6
Output: [0,1]


Constraints:

2 <= nums.length <= 105
-109 <= nums[i] <= 109
-109 <= target <= 109

Only one valid answer exists.
 */

import java.io.*;
import java.util.*;

/*
 * To execute Java, please define "static void main" on a class
 * named Solution.
 *
 * If you need more classes, simply define them inline.
 */

class Solution {



  public List<Integer> findTargetIndexes(List<Integer> nums, int target) {
    List<Integer> result = new ArrayList<Integer>();

    /*
     * Define a variable to store the sum of two numbers
     * Interate in the array
     *   - For each position get the number and the sum it with the next number
     *
     * [2,7,11,15]
     *
     *   i = 1
     *   j = i + 1 = 2
     *
     */

    HashMap<Integer, Integer> backtrack = new HashMap<>();

    for (int i = 0; i < nums.size(); i++) {
      if (backtrack.containsKey(target - nums.get(i))) {
        return Arrays.asList(backtrack.get(target - nums.get(i)), i);
      }
      backtrack.put(nums.get(i), i);
    }
    return result;

  }

  public static void main(String[] args) {
    List<Integer> testArray = new ArrayList<Integer>();

    //  [1,2,3,4,5,6]
    testArray.add(2);
    testArray.add(2);
    testArray.add(3);
    testArray.add(4);
    testArray.add(5);
    testArray.add(6);
    int target = 5;

    Solution s = new Solution();
    System.out.println(s.findTargetIndexes(testArray, target));


  }

}
