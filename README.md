# find-the-smallest-divisor-given-a-threshold
class Solution {
public:
bool can(vector<int>& nums,int mid,int threshold){
        int val=0;
        for(int x:nums){
            val +=(x+mid-1)/mid;
        }
        return val<=threshold;
}
    int smallestDivisor(vector<int>& nums, int threshold) {
        int l=1;
        int r=*max_element(nums.begin(),nums.end());
        int ans=r;
        while(l<=r){
            int mid=l+(r-l)/2;
            if(can(nums,mid,threshold)){
                ans=mid;
                r=mid-1;
            }
            else{
                l=mid+1;
            }
        }
        return ans;
    }
};
