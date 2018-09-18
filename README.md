## The robot_navigation Stack
### 2.5D Navigation in ROS

#### Available Packages:
 * `nav_core2` - New Planner Interfaces
 * `nav_core_adapter` - Adapters between `nav_core` and `nav_core2`.
 * `nav_2d_msgs` - Core messages defined with x, y and theta.
 * `nav_2d_utils` - Message conversions, etc.
 * `dwb_local_planner` - The core planner logic and plugin interfaces.
 * `dwb_msgs` - ROS Interfaces for interacting with the dwb local planner.
 * `dwb_plugins` - Plugin definitions for velocity iteration and trajectory generation
 * `dwb_critics` - Critic plugin definitions needed for replicating behavior of dwa

And more to come!

Safety Branch:

Added the capability to pause the controller when needed. The planner is now
listens to the "robot/desiredAction" topic and publishes the twist message (calculated
by the planner) ONLY if the it has recieved a "CONTINUE" command during the last
"dt" seconds. The planner immediately pauses the controller if a "PAUSE" command is
recieved on the "robot/desiredAction" topic.

The safety monitor callback is a protected member of the LocalPlannerAdapter; therefore does
not change anything about the nav_core2 interfaces.
