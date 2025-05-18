1. look at the first item
2. compare to the item next to it
3. if next < current, then swap
4. go to the next item and do 1 to 3
5. then do the same to the previous items

- you should always have a sorted array from the start to the current position
- best case: O(n) when sorted
- worst case: O(n^2) when nothing is sorted
- usage: mostly sorted lists - small lists