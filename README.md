Tansa: Dancing Robotics Platform
================================
[![Build Status](https://travis-ci.org/dennisss/tansa.svg?branch=master)](https://travis-ci.org/dennisss/tansa)

An open platform for making drones dance! This project includes the following:

1. The reference quadcopter electrical/mechanical design used for developing the system
	- Around $500 BOM cost. Requires a drill, saw, 3d printer, off the shelf parts, and time to replicate.
	- Features 2 controllable spotlights for theatrical purposes

2. Drone control algorithms and drivers
	- Written in C++ with no dependency on ROS
	- Interface to networked MAVLink vehicles
	- Trajectory generation and control
		- Control based on the paper: `Minimum Snap Trajectory Generation and Control for Quadrotors` by Daniel Mellinger and Vijay Kumar
	- Motion capture support
		- Driver for using with OptiTrack Motive 1.9.0

3. Operator User Interface
	- TODO

License
-------

Unless otherwise specified, all current files and future contributions in this repository are distributed under the MIT License (see `LICENSE` file).


Requirements
------------

This platform was primary developed for UNIX based OSes (Linux / Mac OS X), but should be mostly compatible with Windows as well.

For running/compiling the core code, the following libraries must be installed:

- CMake
- Eigen3
- CGAL

For running the simulations, all dependencies on the PX4 toolchain/gazebo SITL environment must be met:
- See http://dev.px4.io/starting-installing.html
- See http://dev.px4.io/simulation-gazebo.html
	- We test with Gazebo 7

Recommended/Optional Dependencies:
- The IBM CPLEX library is a recommended addition if you are using advanced trajectory generation. It is required for making collision free trajectories. If not included, it will fallback to the less stable CGAL solvers when possible.


Building
--------

Alternatively, run `make sim` to start up a multidrone simulator

Run `make run` to build the core stuff and start up the controller. Make sure that config.json has the right filepaths, and the right ip addresses if not using simulator.


UI
--

Before doing `make run`, do `make server`. Then see the UI at `http://127.0.0.1:3000`

- The root url will take you to the web-based 3d viewer

- Go to `http://127.0.0.1:3000/flightControl` for full the flight controls.

Documentation
-------------

See the `doc` folder
