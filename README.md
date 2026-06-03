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
- [ ] Rewrite for 0.57% 0ms Runtime
<sub>01.06.2026</sub>

* #### [**49. Group Anagrams**](https://leetcode.com/problems/group-anagrams)
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {

        // List<List<String>> answer = new ArrayList<>();

        // for (int i = 0; i < strs.length; i++) {
        //     List<String> current = new ArrayList<>(); 
        //     if(!(strs[i] == null)) {
        //         current.add(strs[i]);
        //         char[] arr1 = strs[i].toCharArray();
        //         Arrays.sort(arr1);
        //         for (int j = i+1; j < strs.length; j++) {
        //             if(!(strs[j] == null)) {
        //                 char[] arr2 = strs[j].toCharArray();
        //                 Arrays.sort(arr2);
        //                 if (Arrays.equals(arr1,arr2)) {
        //                     current.add(strs[j]);
        //                     strs[j] = null;
        //                 }
        //             }
        //         }
        //         answer.add(current);
        //         strs[i] = null;
        //     }
        // }
        // return answer;

        // HashMap version:

        List<List<String>> answer = new ArrayList<>();
        HashMap<String, List<Integer>> map = new HashMap<>();

        for (int i = 0; i < strs.length; i++) {
            char[] arr = strs[i].toCharArray();
            Arrays.sort(arr);
            String text = new String(arr);
            if(map.containsKey(text)){
                List<Integer> arr1 = new ArrayList<>();
                arr1 = map.get(text);
                arr1.add(i);
                map.put(text, arr1);
            } else {
                List<Integer> entry = new ArrayList<>();
                entry.add(i);
                map.put(text, entry);
            }
        }
        
        for(Map.Entry<String, List<Integer>> entry : map.entrySet()) {
            List<String> current = new ArrayList<>(); 
            for (int j : entry.getValue()) {
                current.add(strs[j]);
            }
            answer.add(current);
        }

        return answer;
    }
}
```
<sub>02.06.2026</sub>
