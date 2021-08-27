#include <iostream>
#include <algorithm>

using namespace std;

float arr[1002];

int main()
{
	// variable decleration
	int i,n,itr_max,ans,start,end;

	// required input
	cin>>n;
	for(i=0;i<n;i++)
		cin>>arr[i];

	// sorting the list using build in function
	sort(arr,arr+n);
	// summation max value is 2.00 thus all values above 2.01 will be disposed singally only
	// thus
	itr_max=0;
	while (arr[itr_max]<=2.00 && itr_max<n)
		itr_max++;
	ans=n-itr_max;
	start=0;
	end=itr_max-1;

	// start  counter from  left and keep combining with the farthest value
	// which  end value cannot combine with any has to go single
	while(start<end)
	{
		if(arr[start]+arr[end]<=3.00)
		{
			start++;
			end--;
			ans++;
		}
		else
		{
			end--;
			ans++;
		}
	}
	// add the left overs if any
	if(start<=end)
		ans+=(end-start+1);

	cout<<ans;
	return 0;
}
