use other data structures whenever possible, not just hash map

Not everything requires a hash map

'current = start', when *'current.next = firstList'* and 'current = current.next', start.next 
still references the 'firstList' because 'current.next = firstList' was called when 
'current = start' referencing

For c++, make sure you save any float related long math exprewssion into a varaible first and then return it

Chances are for 'easy' problems in Leetcode you can do it without utilities and within 30 lines of code


Sometimes 1 pointer is not enought but 2 pointers. Pointing at head and tail of list

sorting sometimes helps

just because you have loop within a loop doesn't necessary mean the run time is terrible. Someimtes
quadratic is unavoidable. It could even be more efficient as the loop can be used to iterate and skip over
certain unnecessary steps (like duplicates)

Consider both the default table PLUS the new possible vlaues
String[] roman = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
        int[] values = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1 };

simplify everything

Don't forget recursion exists as well (learn how to desgin helper function signatures). DFS mode
and go until reach end and then try others

Like BST, 

When given a traversal, think if sorting can help


medium level questions and above require more than just the 'literal' way of solving from the question description.
You gotta be clever and think of intelligent ways to create constraints or keep order or only branch
out for false conditions to reach true at the very end. 

for number comparision, set aside local max and global max

Avoid direct float or double comparision