# qa-challenges
## Challenges
### 1. Functional Tests
Assume you work at a plant manufacturing electric cars and that you oversee the production lines for batteries and throttles. While the primary function of a battery is to hold a charge that powers each car, it is also responsible for translating a driver's signals from the throttle into the speed of the car. For the sake of this exercise, let's focus on this interaction between the battery and throttle. Your job is to make sure that batteries and throttles are being manufactured in a way that allows them to function properly and safely and to thoroughly test their interactions before sending them down the line.

Let's first identify our assumptions and the specifications of each component (simplified from real life):
1. Each car has two batteries: 
  a. The first is always ON as long as the car is running which keeps all critical functions engaged.
  b. The second is specifically allocated to translating signals from the throttle into the car's speed.
  c. The second battery is our battery of interest for this exercise -- the first can be more or less ignored.
  d. We can also ignore the concept of reverse for this exercise and only focus on forward movement.
2. The second battery has the following specifications:
  a. OFF = default state when throttle is AT-REST and the car is idling at 0 mph
  b. ON = state when throttle is ENGAGED (i.e. >0) translating into some positive speed
  c. MIN POWER (0 watts) = the lowest amount of power that can be allocated to propelling the car
  d. MAX POWER (1,000 watts) = the highest amount of power that can be allocated to propelling the car
3. The throttle has the following specifications:
  a. AT-REST = default state when the throttle is not ENGAGED and the car is idling at 0 mph
  b. ENGAGED = state when the throttle is signaling the car to move forward at some positive speed
  c. MIN LEVEL (0 mph) = the lowest level on the throttle translating to no forward movement
  d. MAX LEVEL (250 mph) = the highest level on the throttle translating to maximum speed of forward movement

Now, let's consider the interaction between the battery and the throttle:
1. When the throttle is AT-REST at its MIN LEVEL (0 mph), the battery should be receiving no signal, OFF, and generating MIN POWER (0 watts).
2. When the throttle is ENGAGED at its MAX LEVEL (250 mph), the battery should be receiving a signal, ON, and generating MAX POWER (1,000 watts).
3. When the throttle is ENGAGED at any level between its MIN and MAX, the battery should receiving a signal, ON, and generating a corresponding level of power between its MIN and MAX.
4. Example: The throttle is ENGAGED at 50 mph, the battery is receiving a signal, ON, and generating 200 watts of power.

Your challenge is to code up (in your language of choice or even psuedocode) a basic function that replicates the interaction of the battery and the throttle with the level of the throttle as an input and the power level of the battery as an output. Once complete, describe in comments below your function how you would approach testing the interaction between the two components. Consider as many fail states for the two components and their interaction as possible and enumerate them. For those fail states that can be modeled with your function, also provide test cases in the comments as well with any necessary instructions for how to execute them (e.g. The throttle cannot send negative values to the battery; throttle = -20 --> battery = -80 is invalid; to test: `print(battery(-20))`).


### 2. Bug Ticket Filing
Now, assume you are testing the batteries and throttles described above and encounter a bug where every time you set the throttle to a level ending in 3 (e.g. 3, 13, 23, 53, 103, etc.), the amount of power returned by the battery is 30 watts. This is obviously problematic, since moving from a throttle level of, say, 50 mph to 55 mph should translate to a steady increase in power from the battery and smooth acceleration, but instead it results in a temporary drop in power and speed, causing the car to "buck". 

Your challenge is to file a Bug Ticket describing the behavior, your associated testing, and any details you think are sufficient for other testers and engineers to understand the problem and to inform subsequent investigation and, hopefully, resolution of this dangerous defect.


## Submission
When you are ready to submit your solution, please follow these instructions:
* Fork this repo on your own GitHub account.
* Commit all of your work to the fork, including all of your source code and any compiled files.
* Submit a pull request to this repository, and include any necessary instructions.
