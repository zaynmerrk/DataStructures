https://practice.geeksforgeeks.org/problems/maximum-index3307/1

``` cpp
#include<stack>
class Solution{
public:
    int maxIndexDiff(int a[], int n) {
	stack<int> st;
	int ans=0;
	for(int i=0;i<n;i++)
	{
  		 if(st.empty()||a[st.top()]>a[i]) 
       		st.push(i);
 	}
	for(int i=n-1;i>=0;i--)
	{

       while(!st.empty()&&a[st.top()]<=a[i])
       {
           if(ans<i-st.top())
            ans=i-st.top();
            
           st.pop();
       }
   
	}
	return ans;
    }
};

