``` cpp
## reverse from any nodes
/*-----------------------------------------------------------------------*/
class Solution {
public:
	ListNode* reverseBetween(ListNode* head, int m, int n) {
		ListNode *dummy = new ListNode(0);
		dummy->next = head;
		ListNode *prev = dummy;
		ListNode *curr = nul;

		if(!head || !head->next)
			return head;

		for (int i = 0; i < m - 1; i++) {
			pre = pre->next;
		}

		curr = pre->next;

		for (int i = 0; i < n - m; i++) {
			ListNode *temp = pre->next;
			pre->next = curr->next;
			curr->next = curr->next->next;
			pre->next->next = temp;
		}

		ListNode *save = dummy->next;
		delete(dummy);

		return save;

	}
};
