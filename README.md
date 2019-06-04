 This metapackage allows starting the stack of tasks for TIAGO.

## Introduction

Two methods to use the SoT with TIAGO are possible:

 1.  One based on roscontrol_sot which is using the roscontrol interface. The SoT is then acting as a Controller object interacting with the hardware interface. This is was is used with Gazebo and on the real robot.
 2. One based on geometric-simu. This software is simply a taking the control provided by the SoT and integrates it using a Euler scheme. The order of integration is chosen automatically according to the control law.

## Using roscontrol_sot 

### On Gazebo
 
To start the SoT in position mode control:
    roslaunch roscontrol_sot_tiago sot_tiago_controller_gazebo.launch
    
To start the SoT in effort mode control:
	roslaunch roscontrol_sot_tiago sot_tiago_controller_gazebo_effort.launch

### On the real robot

To start the SoT in position mode control:
``
roslaunch roscontrol_sot_tiago sot_tiago_controller.launch
`` 
To start the SoT in effort mode control:
``
roslaunch roscontrol_sot_tiago sot_tiago_controller_effort.launch
``

## Using geometric_simu

``
roslaunch sot_tiago_bringup geometric_simu.launch
``

## Parameters

The following parameters are read by Geometric Simu and / or Roscontrol Sot:

```yaml
sot_controller:
  # Read by        RS
  verbosity_level: integer
  log:
    size: integer

  # Read by GS and RS
  # Ordered list of joints. Should be the same as in SoT
  # All elements of this list must be in /robot_description
  joint_names: [ list_of_joint_names ]
  # Period between iterations of SoT
  dt: double

  # Read by        RS
  jitter: double
  simulation_mode: boolean
  libname: string
  # Map of data communication between ROS and SoT.
  map_rc_to_sot_device:
    # ROS -> SoT
    - motor-angles: motor-angles 
    - joint-angles: joint-angles
    - velocities: velocities
    - forces: forces
    - currents: currents
    - torques: torques
    - accelerometer_0: accelerometer_0
    - gyrometer_0: gyrometer_0
    # SoT -> ROS
    - control: control
  # Define the type of control for each joint.
  # CONTROL_MODE is one of POSITION, VELOCITY, EFFORT
  control_mode:
    joint_name_1:
      ros_control_mode: CONTROL_MODE
    joint_name_2:
      ros_control_mode: CONTROL_MODE
  # Control prior to execution of SoT.
  # Whatever the control mode, the position of each joint is controlled
  # to the position read when initializing roscontrol_sot.
  effort_control_pd_motor_init:
    gains:
      joint_name:  {p: 1, d: 0.0, i: 0, i_clamp: 1.5 }
  velocity_control_pd_motor_init:
    gains:
      joint_name:  {p: 1, d: 0.0, i: 0, i_clamp: 1.5 }

  # Read by GS
  joint_state_parallel:
    # Eventually, add a minus sign before active_joint_name to invert the sign.
    - passive_joint_name: active_joint_name

# Read by GS
geometric_simu:
  paused: boolean
```
