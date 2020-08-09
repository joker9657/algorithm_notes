# 题目描述
输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

 

示例 1：
```java
输入：head = [1,3,2]
输出：[2,3,1]
```

限制：

- 0 <= 链表长度 <= 10000

> 来源：力扣（LeetCode）  
链接：https://leetcode-cn.com/problems/cong-wei-dao-tou-da-yin-lian-biao-lcof  
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解题思路1：FILO(first in last out) 
```java
/**
 * 时间复杂度：O(n)
 * 空间复杂度：O(n)
 */
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public int[] reversePrint(ListNode head) {
        LinkedList<Integer> stack = new LinkedList<>();
        while (head != null) {
            stack.addLast(head.val);
            head = head.next;
        } 
        int[] ans = new int[stack.size()];
        for (int i = 0; i < ans.length; i++) {
            ans[i] = stack.removeLast();
        }
        return ans;
    }
}
```

## 解题思路2：递归
```java
/**
 * 时间复杂度：O(n)
 * 空间复杂度：O(n)
 */
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    ArrayList<Integer> tmp = new ArrayList<>();
    public int[] reversePrint(ListNode head) {
        recur(head);
        int[] res = new int[tmp.size()];
        for (int i = 0; i < res.length; i++) {
            res[i] = tmp.get(i);
        }
        return res;
    }
    public void recur(ListNode head) {
        if (head == null) {
            return;
        }
        recur(head.next);
        tmp.add(head.val);
    }
}
```



