# Airport Security Simulator

In this problem, I can simulate a simplified airport security system at a busy airport. Passengers arrive
according to a Poisson distribution with λ1 = 5 per minute (i.e., mean interarrival rate µ1 = 0.2 minutes) to
the ID/boarding-pass check queue, where there are several servers who each have exponential service
time with mean rate µ2 = 0.75 minutes. I will be modeling them as one block that has more than one
resource. After that, the passengers are assigned to the shortest of the several personal-check queues,
where they go through the personal scanner (time is uniformly distributed between 0.5 minutes and 1
minute).


I will use Python with SimPy to build a simulation of the
system, and then vary the number of ID/boarding-pass checkers and personal-check queues to determine
how many are needed to keep average wait times below 15 minutes. [I can use λ1 = 50 to simulate a busier airport.]


The simulation resulted in an average wait time of 23.45 minutes, so I will need to adjust either or both the number of ID/boarding-pass checkers (NUM_CHECKERS) and the number of personal-check queues/scanners (NUM_SCANNERS) to reduce the average wait time below 15 minutes.
The strategies I can employ to achieve this are to increase the number of checkers, increase the number of scanners, or adjust both. Increasing the number of checkers reduces the time passengers spend in the ID/boarding-pass check queue. If this queue is a significant contributor to the overall wait time, increasing the number of checkers will have a substanCal impact.
More scanners can reduce wait time, especially if the bokleneck is occurring at the personal-check stage. Given that the current setup did not meet the target, and assuming the number of checkers and scanners are the same (as I mentioned 35 each), I will start by incrementally increasing the number of resources until the desired wait time is achieved. My approach:
1.Increase NUM_CHECKERS by 5 and run the simulation. If the wait time drops below 15 minutes, you’ve found a solution. If not, proceed to step 2.
2.Reset NUM_CHECKERS to 35, increase NUM_SCANNERS by 5, and run the simulation. If the wait time drops below 15 minutes, I’ve found a solution. If not, proceed to step 3.
3.Increase both NUM_CHECKERS and NUM_SCANNERS by small increments (5 each time), and run the simulation until I find the combination that brings the average wait time below 15 minutes.
combinations I will try till I get 15:
• NUM_CHECKERS = 40, NUM_SCANNERS = 35
• NUM_CHECKERS = 35, NUM_SCANNERS = 40
• NUM_CHECKERS = 40, NUM_SCANNERS = 40
I will continue incrementing unti I reach the goal to find the most cost-effective solution without over- provisioning resources.
After running this, I got the desired result at NUM_CHECKERS = 40, NUM_SCANNERS = 35 and can make the observaCon that these many can satisfy the condition. However, I can also follow an approach of reducing by 1⁄2 each time to find the exact amount. For example, I will start at 37 for one, and so on till I come across an exact number for each which falls within these criteria.
