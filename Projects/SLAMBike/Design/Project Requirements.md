## Problem
Bicycles off the shelf are not capable of piloting themselves. This is an inconvenience especially when the user has to transport the bike by pushing it. Having to push a bike by hand distracts from conversations with others. Additionally, it requires both your hands to push a bike and prevents you from carrying bulky objects. 

There exists a need for bicycle ridesharing services that meet users where they are rather than where the location of a bike rack. This need also extends to electric scooters and requires similar implementation to that of the bike. 

## Mission statement:
Retrofit a road bicycle with the necessary components so that:
1. Steering is automatic with full range of motion with feedback
2. The bike can propel itself forward if there is no additional weight at 5-8 mph. 
3. The bike will break and slow down to maintain a speed along a decline.
4. The bike can stand on its own and compensate for minor perturbations from side to side.
5. The bike will be controllable via a remote control with a range of 100 feet
6. The bike can drive itself for at least 1.5 hours before a recharge is necessary.
7. The cost of retrofitting a bike should remain under $250 dollars
8. The bike will still function as a normal bike and be driveable by a person
9. The system must be capable of surviving snow and showers or must be easily attachable/removeable to store indoors
10. The components must be capable of surviving falls
11. Bike itself prior to upgrades is at most 27 pounds

## Safety:
- All electrical connections are insulated
- The bike does not power on if there is a person on it
- The bike does not exceed a pre-set speed limit

## User story:
The user takes their charged system and latches it onto the bike. The user flicks a switch to turn on the system and begin calibration of the bike on a flat surface. The user powers on their remote control and drives the bike up and down the street. They drive it up and down the hill of Werth Tower with no issues. Performance stats are visible on the remote control. If the user tries to sit on the bike it will detect it and not drive. The bike saves 360 camera footage onto a sim card for future use.

## Subsystems and criteria:
### Steering
1. Cost
2. Max turn acceleration
3. (T/F) Feedback
4. (T/F) Disengageable

### Stabilization
1. Recovery degree angle
2. Power usage
3. Footprint
4. Weight
5. Cost 

### Power
1. Weight
2. Size
3. Cost

### Propulsion
1. Top speed
2. Power usage
3. Cost
4. (T/F) Disengageable

### Breaking
1. Max breaking force
2. Cost
3. Power usage
4. (T/F) Disengageable

### Communication
1. Range
2. Communication speed
3. Cost

### Compute
1. Power usage

**Ideas**
- Assistive steering? Don’t try to fully stabilize a person, but help them complete turns
- Add retractable training wheels just for testing purposes to catch a fall?