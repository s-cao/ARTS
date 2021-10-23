# Day 1 - Oct 20, 2021
## Algorithm
https://leetcode.com/problems/linked-list-cycle-ii/

    class Solution:
        def detectCycle(self, head: ListNode) -> ListNode:
            address_and_index = {}
            while(True):
                if head is None:
                    break
                elif head.next in address_and_index:
                    return head.next
                else:
                    address_and_index[head] = 1
                    head = head.next
        return None
# Day 2 - Oct 21, 2021
## Algorithm
https://leetcode.com/problems/reverse-linked-list-ii/

    class Solution:
    def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
        swaps = right - left
        cur_node = head
        if swaps == 0:
            return head
        if left == 1:
            return self.swapSegment(cur_node, swaps)
        # loop until we get to the start of the index we want to swap
        cur = 1
        prev = head
        while(cur < left):
            prev, cur_node = cur_node, cur_node.next
            cur += 1
        prev.next = self.swapSegment(cur_node, swaps)
        return head
    
    def swapSegment(self, head, swaps):
        cur, prev = head, None
        while(swaps):
            cur.next, prev, cur = prev, cur, cur.next
            swaps -= 1
        head.next = cur.next
        cur.next = prev
        return cur
# Day 3 - Oct 22, 2021
## Algorithm
https://leetcode.com/problems/remove-nth-node-from-end-of-list/

    class Solution:
        def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
            pt1, pt2 = head, head
            while(n):
                pt1 = pt1.next
                n = n-1
            while(pt1 and pt1.next):
                pt1 = pt1.next
                pt2 = pt2.next
            if (pt1 is None):
                return pt2.next
            elif (pt2.next):
                pt2.next = pt2.next.next
            return head

## Review

## Tips

## Share
https://en.wikipedia.org/wiki/Cycle_detection#Floyd's_tortoise_and_hare
