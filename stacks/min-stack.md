https://leetcode.com/problems/min-stack/
/*++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*/

best solution here- https://leetcode.com/problems/min-stack/discuss/904680/Without-stack-In-O(1)-both-timespace-complexity-cpp

``` cpp

class MinStack {
public:
    /** initialize your data structure here. */
    stack<int> s;
    stack<int> ss;
//     MinStack() {

//     }
    
    void push(int x) {
        s.push(x);
        
        if(ss.empty() || x<=ss.top())
            ss.push(x);
        
    }
    
    void pop() {
        if(s.empty()){
            return;
        }
        if(s.top()==ss.top()){
            ss.pop();
        }
        s.pop();    
    }
    
    int top() {
       if(s.empty()){
          return INT_MAX;
      }  
        return s.top();
    }
    
    int getMin() {
       if(s.empty() || ss.empty()){
          return INT_MAX;
      } 
        return ss.top();
    }
};

/*^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^*/
#define ll     long long int
class MinStack {
public:
	/** initialize your data structure here. */
	stack<ll> s;

	//global variable
	ll min_element = 0;

	void push(ll x) {
		if (s.empty()) {
			min_element = x;
			s.push(x);
		}
		else if (min_element <= x) {
			s.push(x);
		}
		else {
			ll temp = (1LL*(2 * x - min_element));
			min_element = x;
			s.push(temp);
		}
	}

	void pop() {
		if (s.empty()) {
			return;
		}
		else if (min_element <= s.top()) {
			s.pop();
		}
		else {
			// that flag
			ll temp = (1LL*(2 * min_element - s.top()));
			min_element = temp;
			s.pop();
		}
	}

	int top() {
		if (s.empty()) {
			return INT_MAX;
		}
		else if (min_element > s.top()) {
			return int(min_element);
		}

		return int(s.top());
	}

	int getMin() {
		if (s.empty()) {
			return INT_MAX;
		}

		return int(min_element);
	}
};
