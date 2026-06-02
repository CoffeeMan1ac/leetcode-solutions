# LeetCode Solutions
> AI free repo <br>AI free reasoning/solutions<br>No hints<br>Syntax checks OK

### Arrays & Hashing
* #### [**217. Contains Duplicate**](https://leetcode.com/problems/contains-duplicate)
```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        // I can either create an array and record every number and check against it
        // (some storage, some memory load)
        // or check every number against every number in array (no storage, memory load)

        // I can sort first, and then just check every number to the number next to it

        Arrays.sort(nums);

        for (int i= 0; i < nums.length-1; i++) {
            if(nums[i] == nums[i+1]) {
                return true;
            }
        }

        return false;
    }
}
```
<sub>31.05.2026</sub>

* #### [**242. Valid Anagram**](https://leetcode.com/problems/valid-anagram)
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        // I need to:
        // - collect all letters from s
        // - collect all letters from t
        // - check that those arrays are identical

        if (s.length() != t.length()) return false;

        char[] arr1;
        char[] arr2;
        arr1 = s.toCharArray();
        Arrays.sort(arr1);
        arr2 = t.toCharArray();
        Arrays.sort(arr2);

        //if (arr1.equals(arr2)) System.out.println("PASSED");
        if(Arrays.equals(arr1,arr2)) return true;

        return false;
    }
}
```
<sub>31.05.2026</sub>

* #### [**1. Two Sum**](https://leetcode.com/problems/two-sum)
```java
// Refamiliarized with HashMap's. Took a long time until hit 2ms runtime.
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> copy = new HashMap<>();
        int[] answer = new int[2];
        for (int i = 0; i < nums.length; i++) {
            if (copy.containsKey(target-nums[i])) {
                answer[0] = copy.get(target-nums[i]);
                answer[1] = i;
                return answer;
            }
            copy.put(nums[i], i);
        }
        return answer;
    }
}
```
<sub>01.06.2026</sub>
