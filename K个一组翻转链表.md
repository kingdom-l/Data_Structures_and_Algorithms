K个一组翻转链表

规则：每k个链表节点为一组，进行翻转，返回修改后的链表。如果最后剩余的节点数不足k个时，保持最后剩余节点的顺序。

思路：统计链表节点的个数，然后每k个节点为一组翻转

```C++
class Solution {
public:
    ListNode* reverseKGroup(ListNode* head, int k) {
        //首先统计元素的个数
        int num = 0;
        ListNode* temp = head;
        while(temp){
            num++;
            temp = temp->next;
        }
        int n = num / k;
        ListNode* vir = new ListNode(-1);
        vir->next = head;
        ListNode* pre = vir; //记录上一组的尾节点
        ListNode* cur = head;//记录本次待翻转的头节点
        ListNode* next;
        for(int i = 0; i < n; ++i){
            //第i组的翻转，两个两个的交换，每次交换都将节点放到上一组尾节点的后面
            for(int j = 0; j < k - 1; ++j){
                next = cur->next;
                cur->next = next->next;
                next->next = pre->next;
                pre->next = next;
            }
            pre = cur;
            cur = pre->next;
        }
        return vir->next;
    }
};
```

