# [Letter Combinations of a Phone Number][title]

## Description

Given a digit string, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below.

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png)

**Example:**

```
Input: "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```

**Note:**

Although the above answer is in lexicographical order, your answer could be in any order you want.

**Tags:** String, Backtracking


## 思路

用map存储.

```java
class Solution {
    public List<String> letterCombinations(String digits) {
        if(digits.length()==0){
            return Collections.emptyList();
        }
        LinkedList<String> list = new LinkedList<String>();
        list.add("");
        Map<String,String[]> map = new HashMap<>();
        map.put("2",new String[]{"a","b","c"});
        map.put("3",new String[]{"d","e","f"});
        map.put("4",new String[]{"g","h","i"});
        map.put("5",new String[]{"j","k","l"});
        map.put("6",new String[]{"m","n","o"});
        map.put("7",new String[]{"p","q","r","s"});
        map.put("8",new String[]{"t","u","v"});
        map.put("9",new String[]{"w","x","y","z"});
        String[] str = digits.split("");

        for(int i = 0 ; i< str.length ; i++){
            while(list.getFirst().length()==i){
                String s=list.removeFirst();
                for(String a:map.get(str[i])){
                    list.addLast(s+a);
                }
            }     
        }
        return list;  
    }
```



## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我：[leetcode_java][ajl]



[title]: https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/
[ajl]: https://github.com/Bellazx/leetcode_java