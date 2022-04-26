删除链表的倒数第N个节点

给定一个链表，删除链表中倒数第n个节点，并返回链表的头结点

思路：可用双指针pre和cur，现将cur移动n次，然后同时移动pre和cur指针，当cur移动到尾节点NULL时，此时指针pre移动到倒数第n个节点的前一个节点。

```C++
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* vir = new ListNode(-1);
        vir->next = head;
        ListNode* pre = vir;
        ListNode* cur = vir;
        int count = 0;
        while(cur){
            cur = cur->next;
            ++count;
            if(count >= n){
                break;
            }
        }
        cur = cur->next;
        while(cur){
            cur = cur->next;
            pre = pre->next;
        }
      
        pre->next = pre->next->next;

        return vir->next;//return head;时会出错，比如head=[1], n = 1,期望输出是[]，但是实际输出[1]，这是因为删除的节点没有被delete
    }
};
```

