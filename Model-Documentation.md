## CarND - Path planning project

This project implements a planner to navigate a given path in the simulator with acceleration and jerk constraints.

### Frenet Coordinates

Frenet coordinates are used to ease the calculations in car's local coordinates. Using CarND's helper functions, global coordinates are converted into car's local coordinates to plan the future actions and are converted back to global coordinates to adhere with simulator's coordinates system.


### Acceleration and Jerk Constraints

One main criteria of the project is to ensure the car meets the maximum acceleration and jerk requirements. Every waypoint inputs given to the simulators are calculated with 0.02 seconds time interval and velocity increments and decrements are carefully chosen to meet this criteria.

Further, spline library is used to fit a spline for calculated waypoints and create smooth path.


### Lane Management

Path planning makes sure that car stays in it's lane for as long as it is not blocked by another car in front of it. While in such a situation, it uses a simple state transition mechanism to switch the lanes.

When the car spots another car in front of it, it starts decelerating initially. While the velocity reaches below a set threshold, it looks for other cars around, including the blind spots, to figure out the safe lane to switch to. When the adjacent has enough room to squeeze in, the algorithm creates waypoints to switch to next lane and continue in that lane.
