## ur5e.xml

MJCF model of UR5e.

License of files in this directory follows [ros-industrial/universal_robot](https://github.com/ros-industrial/universal_robot) and [deepmind/mujoco_menagerie](https://github.com/deepmind/mujoco_menagerie).

The following changes are made to [the MJCF model in deepmind/mujoco_menagerie](https://github.com/deepmind/mujoco_menagerie/tree/main/universal_robots_ur5e).

- Since the joints are controlled by mc_mujoco, the gain settings of the motors are removed.
- The names of the meshes are explicitly specified so that the robot-name prefix is attached to them correctly.
- `general` elements of actuator are replaced with `motor` elements so that mc_mujoco can find the control joints.
