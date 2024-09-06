# Largest-number-leetcode

class Solution {
    private class LargerNumberComparator implements Comparator<String> {
        @Override // custom comparator
        public int compare(String a, String b) { // suppose 30 and 3. compares.
            String order1 = a + b;  // 303 < 330. sort b+a
            String order2 = b + a;
            return order2.compareTo(order1);
            // each new string gets compared to all sorted strings except i thinnk if its a lesser value then no sense
            // comoparing to even higher ones
        }
    }

    public String largestNumber(int[] nums) {

        String[] asStrs = new String[nums.length];
        for (int i = 0; i < nums.length; i++) {
            asStrs[i] = String.valueOf(nums[i]);
        }

        Arrays.sort(asStrs, new LargerNumberComparator());

        if (asStrs[0].equals("0")) { //written here and not as if length == 0,etc. because if we have [0,0,0]
            return "0"; // length != 0 and still largest int is 0
        }

        String largestNumberStr = new String();
        for (String numAsStr : asStrs) {
            largestNumberStr += numAsStr;
        }

        return largestNumberStr;
    }
}


//class Solution {
//    public String largestNumber(int[] nums) {
//        Arrays.sort(nums);
//        StringBuilder sb = new StringBuilder();
//        for(int i = nums.length-1; i>=0; i--){
//            sb.append(nums[i]);
//        }
//        return sb.toString();
//    }// not single digit ints. fails under condition (10,2) returns 102 not 210
//    // would need to find each 9 but nonconseutive 9's likee 990 would come after '9' etc. complicated
//}
// sort low-high
// decrementing loop
// can't do (sum *= 10) + digit since number may be too long. Integer.toString
// won't work

// stringbuilder -> string.
