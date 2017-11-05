# Overview
This repository contains all the code needed to complete the final project for the Localization course in Udacity's Self-Driving Car Nanodegree.

## Project Introduction
Your robot has been kidnapped and transported to a new location! Luckily it has a map of this location, a (noisy) GPS estimate of its initial location, and lots of (noisy) sensor and control data.

In this project I implement a 2 dimensional particle filter in C++. This particle filter will be given a map and some initial localization information (analogous to what a GPS would provide). At each time step your filter will also get observation and control data.

[image1]: ./imgs/screenshot.png "screenshot"

## Running the Code

Once the install for uWebSocketIO is complete, the main program can be built and ran by doing the following from the project top directory.

1. mkdir build
2. cd build
3. cmake ..
4. make
5. ./particle_filter

During my develop, I use XCode on MacOS, build output from XCode is under ./debug or ./release.

Can run command like bellow to start the particle_filter

5. ./debug/particle_filter


Alternatively some scripts have been included to streamline this process, these can be leveraged by executing the following in the top directory of the project:

1. ./clean.sh
2. ./build.sh
3. ./run.sh

Tips for setting up the environment can be found [here](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/0949fca6-b379-42af-a919-ee50aa304e6a/lessons/f758c44c-5e40-4e01-93b5-1a82aa4e044f/concepts/23d376c7-0195-4276-bdf0-e02f1f3c665d)

The meat of this project is in file  src/particle_filter.cpp, and particle_filter.h


## Inputs to the Particle Filter
The particle filter data are in in the `data` directory.

#### The Map*
`map_data.txt` includes the position of landmarks (in meters) on an arbitrary Cartesian coordinate system. Each row has three columns
1. x position
2. y position
3. landmark id

### All other data the simulator provides, such as observations and controls.

> * Map data provided by 3D Mapping Solutions GmbH.

## Pass Criteria

Based on the rubic, if the we run the application and simulator, and can see following screen means meets the rubic.  Please see following screenshot which show the "Success" pass.

![Pass Criteria][image1]


## Sample Data between Simulator and Application

Input from simulator

  Incoming data from simulator telemetry

  highest w 0.0119507
  average w 0.00528024

Output from application, send back to simulator

  Message send back to simulator:
  42["best_particle",{"best_particle_associations":"","best_particle_sense_x":"","best_particle_sense_y":"","best_particle_theta":0.144708547691593,"best_particle_x":46.3871959955385,"best_particle_y":12.7109229708847}]


# P.S.

## Data Protocol between Simulator and Application

Here is the main protocol that main.cpp uses for uWebSocketIO in communicating with the simulator.

  INPUT: values provided by the simulator to the c++ program

      // sense noisy position data from the simulator

      ["sense_x"]

      ["sense_y"]

      ["sense_theta"]

      // get the previous velocity and yaw rate to predict the particle's transitioned state

      ["previous_velocity"]

      ["previous_yawrate"]

      // receive noisy observation data from the simulator, in a respective list of x/y values

      ["sense_observations_x"]

      ["sense_observations_y"]


  OUTPUT: values provided by the c++ program to the simulator

      // best particle values used for calculating the error evaluation

      ["best_particle_x"]

      ["best_particle_y"]

      ["best_particle_theta"]

      //Optional message data used for debugging particle's sensing and associations

      // for respective (x,y) sensed positions ID label

      ["best_particle_associations"]

      // for respective (x,y) sensed positions

      ["best_particle_sense_x"] <= list of sensed x positions

      ["best_particle_sense_y"] <= list of sensed y positions


## Directory Structure
The directory structure of this repository is as follows:

```
root
|   build.sh
|   clean.sh
|   CMakeLists.txt
|   README.md
|   run.sh
|
|___data
|   |   
|   |   map_data.txt
|   
|   
|___src
    |   helper_functions.h
    |   main.cpp
    |   map.h
    |   particle_filter.cpp
    |   particle_filter.h
```
