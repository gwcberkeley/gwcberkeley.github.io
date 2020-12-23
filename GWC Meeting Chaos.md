---
title: GWC Meeting Chaos
parent: Probability Problems
grand_parent: Fun Interview Problems
has_children: false
nav_order: 1
---

# GWC Meeting Chaos

In a GWC meeting in another parallel universe where we can meet in person, there are 100 attendees and everyone is assigned a seat,
numbered from 1 to 100. The person who is assigned seat 1 decides to pick a seat uniform randomly from the 100 seats🤯 For the rest of attendees,
if their seats are taken, they pick a random available seat; if their assigned seats are available, they choose the assigned seats.

What is the probability that the last attendee gets its assigned seat?


<details>
  <summary>Click to expand!</summary>
  
  
    **Answer:** `1/2`

    This is a classical probability question. First let's think intuitively.
    **Notice that the last member will either get the first seat or the last seat.** There are two possibilities for GWC member 2–99:
    1. The member’s assigned seat is empty. They sit in that seat.
    2. The member’s assigned seat is occupied. They sit in some other seat at random.

    After each of these members takes a seat, it is necessarily true that their assigned seat is occupied. Either it was previously unoccupied (option 1 above) and they sit in it, or it was already occupied (option 2).
    Before the last member enters the room, we know that the assigned seats of members 2–99 are occupied. At this point, the last member can only take either the first seat or the last seat. Since at each choice step, the first or last is equally probable to be taken, the last person will get either the first or last with equal probability: `1/2`


    Now let's prove rigorously. Here we provide a prove offered by math.stonybrook.edu since it is very clear and straightforward.

    Let’s consider the problem for n members attending the meeting, and let’s number them 1 through n according to the order at which they enter the 
    room. Consider the first member. 

    If she takes her seat (which happens with probability `1/n`), every other member(including the last one) gets her seat with probability 1, since they will not be forced to take seats other than their own. 

    If the first person takes the seat of last member, then, obviously, the last member has no chance to get her seat. 

    Now let’s look at the case where the first member occupies the place of the k’th member, where `1 < k < n`. Members 2...(k − 1) take their
    own seats, since they are vacant. Now member k starts to act exactly like the first person:
    1. She takes a seat randomly;
    2. If she takes the seat of the first person, which we can think of as being her seat now, then
    members `k + 1`, `k + 2`, ..., `n` get to their seats with probability 1;
    3. If she takes the last member’s seat, last member gets her seat with probability 0.

    Therefore, if we let f(x) be the probability that the last member takes her seat in the room with x seats (according to the conditions stated at the problem), then the probability that the last person takes her seat given that the first person took the seat of k’th member is f(k).

    Since the seat of k’th member is taken with probability `1/n` (both the first person and a person whose seat was occupied select new seat with with uniform randomness), we have `f(n) = 1/n + (1/n)(∑n−1,i=2 f(i))`.

    We observe that in case n = 2, the first person takes her seat with probability `1/2`, in which case the last member always gets her sit, and that she gets the seat of last passenger with probability `1/2` as well; hence f(2) = `1/2`. Our claim is that f(n) = `1/2` for all n, and we prove it using full induction on n. 

    We have shown the base case above. Now let f(n) = `1/2` for n ≤ k. Then `f(k + 1) = 1/k+1 + (1/k+1)(∑k,i=2 f(i)) = 1/k+1 + k−1/2k+2 = k+1/2k+2 = 1/2`, as desired. The claim follows by the principle of full mathematical induction.

</details>
