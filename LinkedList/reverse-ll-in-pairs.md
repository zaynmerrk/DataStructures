
``` cpp
// reverse ll in pairs
/*-----------------------------------------------------------------------*/
class Solution {
public:
    ListNode* swapPairs(ListNode* head) {
    	if(!head || !head->next)
    		return head;
    	ListNode *dummy = new ListNode(0);
    	ListNode *pre = dummy;
    	dummy->next = head;

    	while(!head && !head->next){
    		ListNode *temp = pre->next;
    		pre->next = head->next;
    		head->next = head->next->next;
    		pre->next->next = temp;

    		pre = head;
    		head = head->next;
    	}
    	return dummy->next;

    }
};
