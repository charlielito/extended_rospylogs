# Extended ROS logs for python (rospy)

`extended_rospylogs` implements for `rospy` some of the extra functionalities found in `roscpp` for logging.


## Installation

You can install `extended_rospylogs` from pip using

```
pip install extended_rospylogs
```

or using

```
pip install git+https://github.com/charlielito/extended_rospylogs
```

## ROS log messages extension
In `rospy` there are only 5 functions for logging: `rospy.logdebug`, `rospy.loginfo`, `rospy.logwarn`, `rospy.logerr` and `rospy.logfatal`. In `roscpp` you can find other options like `ROS_DEBUG_COND`, `ROS_DEBUG_NAMED`, `ROS_DEBUG_COND_NAMED`, etc (for more info go to [ros logging](http://wiki.ros.org/roscpp/Overview/Logging)).

The conditional option for logging is very useful when you want to have different logging messages in your nodes, and you want to change it in runtime (because you only can specify the `log_level` when initializing the node).

### Extended Functions
For the moment here are implemented all the `rospy` logging functions with the `cond` option:

* `logdebug_cond(bool, message)`
* `loginfo_cond(bool, message)`
* `logwarn_cond(bool, message)`
* `logerr_cond(bool, message)`
* `logfatal_cond(bool, message)`


## Usage

```python
import rospy
from extended_rospylogs import logdebug_cond, loginfo_cond


rospy.init_node('some_node')
rate = 30
debug = True
r = rospy.Rate(rate)

while not rospy.is_shutdown():

  #### DO STUFF
  logdebug_cond(debug, "Some debug message")
  loginfo_cond(debug, "Some info message for debugging")

  r.sleep()
```

Note that the `debug` variable could be a **node parameter** so it could be changed on runtime.
