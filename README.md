# leetcode---2130
Maximum Twin Sum Of  a Linked List
Code in Java
class Solution {
    public int pairSum(ListNode head) {
        ListNode slowPtr = head;
        ListNode fastPtr = head;
        ListNode prevPtr = null;

        // Reverse the first half of the linked list
        while (fastPtr != null && fastPtr.next != null) {
            fastPtr = fastPtr.next.next;
            ListNode nextNode = slowPtr.next;
            slowPtr.next = prevPtr;
            prevPtr = slowPtr;
            slowPtr = nextNode;
        }

        // Adjust pointers if the length of the linked list is odd
        if (fastPtr != null) {
            slowPtr = slowPtr.next;
        }

        int maxSum = Integer.MIN_VALUE;
        while (slowPtr != null) {
            maxSum = Math.max(maxSum, slowPtr.val + prevPtr.val);
            slowPtr = slowPtr.next;
            prevPtr = prevPtr.next;
        }
        return maxSum;
    }
}
