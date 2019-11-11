Editorial: 💡 Find the greater element
X
Approach
This approach makes use of a stack. This stack stores the indices of the appropriate elements from nums array. The top of the stack refers to the index of the Next Greater Element found so far. We store the indices instead of the elements since there could be duplicates in the nums array. The description of the method will make the above statement clearer.

We start traversing the numsnums array from right towards the left. For an element nums[i] encountered, we pop all the elementsstack[top] from the stack such that nums[stack[top]] ≤ nums[i]. We continue the popping till we encounter a stack[top] satisfying nums[stack[top]]>nums[i]. Now, it is obvious that the current stack[top] only can act as the Next Greater Element for nums[i](right now, considering only the elements lying to the right of nums[i]).

If no element remains on the top of the stack, it means no larger element than nums[i] exists to its right. Along with this, we also push the index of the element just encountered(nums[i]), i.e. ii over the top of the stack, so thatnums[i](or stack[topstack[top) now acts as the Next Greater Element for the elements lying to its left.

We go through two such passes over the complete nums array. This is done so as to complete a circular traversal over the nums array. The first pass could make some wrong entries in the res array since it considers only the elements lying to the right of nums[i], without a circular traversal. But, these entries are corrected in the second pass.

Code

public static int[] nextGreaterElements(int[] nums) {
    int[] res = new int[nums.length];

        Stack stack = new Stack<>();

        for (int i = 2 * nums.length - 1; i >= 0; i--) {

            while (!stack.isEmpty() && nums[stack.peek()] <= nums[i % nums.length]) {
                stack.pop();
            }

            res[i % nums.length] = (stack.isEmpty() ? -1 : nums[stack.peek()]);
            stack.push(i % nums.length);
        }

        return res;

    }