# leetCode 709

## 题目描述：

请编写一个函数，使其可以删除某个链表中给定的（非末尾）节点，你将只被给定要求被删除的节点。

示例 1:
```
输入: head = [4,5,1,9], node = 5
输出: [4,1,9]
解释: 给定你链表中值为 5 的第二个节点，那么在调用了你的函数之后，该链表应变为 4 -> 1 -> 9.
示例 2:
```
```
输入: head = [4,5,1,9], node = 1
输出: [4,5,9]
解释: 给定你链表中值为 1 的第三个节点，那么在调用了你的函数之后，该链表应变为 4 -> 5 -> 9.
```

说明:
+ 链表至少包含两个节点。
+ 链表中所有节点的值都是唯一的。
+ 给定的节点为非末尾节点并且一定是链表中的一个有效节点。
+ 不要从你的函数中返回任何结果。

## solution@dunmin:
C++:
```
class Solution {
public:
    void deleteNode(ListNode* node) {
        node->val = node->next->val;
        node->next = node->next->next;
    }
};
```
```
point:
(1)题目的意思就是只给一个链表上要删除的节点，问你如何删除它，出题方式十分巧妙
(2)解法很有意思，直接删除当前结点但是不知道该节点之前的是谁，那么就把后面一个的值给要去掉的节点，那么要去掉的就是下一个节点了，并且也知道了该节点的前一个后一个是谁，那么就变成了普通的链表删除节点问题
```

## 说明@dunmin:
```
巧妙的题目
```