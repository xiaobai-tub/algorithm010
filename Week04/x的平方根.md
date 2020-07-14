class Solution {
    public int mySqrt(int x) {
        if ( x == 0 ) return 0;
        long left = 0;
        long right = x;
        long result = -1;
        while(left <= right){
            long mid = (left + right)/2;
            
            if (mid * mid <= x){
                result = mid;
                left = mid + 1;
            }else{
                right  = mid - 1;
            }
        }
        return (int)result;
        

    }
}