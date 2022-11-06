- use other data structures whenever possible, not just hash map. Stack, queue, linked list, etc, although most leet code puzzle will aim for least heavy data structure as possible

- Not everything requires a hash map

- 'current = start', when *'current.next = firstList'* and 'current = current.next', start.next 
still references the 'firstList' because 'current.next = firstList' was called when 
'current = start' referencing

- Chances are for 'easy' problems in Leetcode you can do it without utilities and within 10 lines of code

- Sometimes 1 pointer is not enought but 2 pointers. Pointing at head and tail of list

- sorting sometimes helps when given a data structure. When given a traversal, think if sorting can help

- Someimtes quadratic is unavoidable.

- just because you have loop within a loop doesn't necessary mean the run time is terrible. It could even be more efficient as the loop can be used to iterate and skip over certain unnecessary steps (like duplicates)

- sometimes it is easier to map out all possible cases and not just the given case in description:

Consider both the default table PLUS the new possible vlaues
String[] roman = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
        int[] values = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1 };

- Don't forget recursion exists as well (learn how to desgin helper function signatures). DFS mode and go until reach end and then try others. Back tracking problems are good examples of DFS. Remembe


- medium level questions and above require more than just the 'literal' way of solving from the question description.
You gotta be clever and think of intelligent ways to create constraints or keep order or only branch

- Sometimes in a true or false question, out for false conditions to reach true at the very end. 

- for number comparision, set aside local max and global max

- Avoid direct float or double comparision

- sometimes greedy doesn't work; instead of focusing too much on deriving patterns from the process, focus more on the property of the answers they want.

Ex) max abs sum: instead of figuring how to get max abs sum in one go by looking at the example process,
think what max abs sum means: max absolute sum will be either the abs(max sum) or the abs(min sum)

ex) max product: this requires a product so any element with 0 needs to be reset. In addition, any number will only increase the absolute product, thus think about the most hard case when there are odd number of negative elements

- sometimes combine two practices
ex) max product of conituig array: combine idea of two pointers AND global,local max comparision

- Sometimes it helps you to traverse more than once; first to get the max or latest values of sth
from the traversable and then a second traverse to really  calculate what you need
Ex) partitionLabel. Instead of once traversing and then updating as you go along, it is much
faster when you already traverse once to get the max index of a character, so that you know
until how long the partition should be

- Trying to come up with several branches to cover all possible cases can be distracting. Sometimes there is one 
or two simple conditions checks that covers all t he cases
ex) unique paths with obstacles

- Memoization: recursively calls but keeping track so that you don't repeat already computed results.
Ex) fibonnacci 