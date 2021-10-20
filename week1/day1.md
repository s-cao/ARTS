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

## Review

## Tips

## Share
https://en.wikipedia.org/wiki/Cycle_detection#Floyd's_tortoise_and_hare
