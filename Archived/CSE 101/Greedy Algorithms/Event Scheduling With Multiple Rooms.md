conference to plan with n events, unlimited supply of rooms, how can you assign in a way to minimize the rooms

### Specification
- Instance: $[(s_1,f_1),...,(s_n,f_n)]$
- Solution Format: Array indexed by 1,2,3,...,n using positive integers, each assigned to an event
- Constraints: no two events in the same room overlap
- Objective: total number of different values in array (number of rooms used)
- Goal: Minimize array

### Pick a method
- Run Event Scheduling to find max number of non-overlapping events, and assign those to room 1, repeat until none left.
- Wacky Idea: merge the event that ends the earliest with the next event that ends the earliest, keep going until you can't merge anymore
- Sort Events: Keep track of the max number of events happening at the same time

### Solution
1. number each room from 1 to n
2. Sort the events by earliest start time
3. assign first event to room 1
4. for each following event, assign each event to the lowest numbered room available