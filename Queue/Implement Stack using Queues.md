
``` cpp
https://leetcode.com/problems/implement-stack-using-queues/


/*^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^*/
class MyStack {
public:
    /** Initialize your data structure here. */
    // MyStack() {

    // }
    queue<int> q1, q2;

    /** Returns whether the stack is empty. */
    bool empty() {
        return q1.empty() == 1;
    }
   
   /** Push element x onto stack. */
    int top_ele = -1;
    void push(int x) {
        q1.push(x);
        top_ele = x;
    }

    /** Removes the element on top of the stack and returns that element. */
    int pop() {
        // if (empty())
        //     return hell;

        while (q1.size() > 1) {
            top_ele = q1.front();

            q2.push(top_ele);
            q1.pop();
        }

        int save_return = q1.front();
        q1.pop();

       swap(q1,q2);

        return save_return;
    }

    /** Get the top element. */
    int top() {
        // if (empty())
        //     return hell;

        return top_ele;
    }
};
