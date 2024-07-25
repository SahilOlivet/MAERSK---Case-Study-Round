# MAERSK---Case-Study-Round
# Container Terminal Simulation

This repository contains three versions of a simulation for a container terminal using SimPy. The simulation involves vessels arriving at a terminal, berthing, unloading containers using quay cranes, and transporting containers to yard blocks using trucks.

## Table of Contents

- [Overview](#overview)
- [Environment](#environment)
- [Processes](#processes)
- [Resources](#resources)
- [Events Logged](#events-logged)
- [Code Versions](#code-versions)
  - [1. Simulation with with statement](#1-simulation-with-with-statement)
  - [2. Simulation with Manual Resource Management](#2-simulation-with-manual-resource-management)
  - [3. Priority-Based Vessel Operation](#3-priority-based-vessel-operation)
- [How to Run](#how-to-run)

## Overview

The simulation models the operations of a container terminal where vessels arrive, berth at the terminal, unload containers using quay cranes, and transport containers to yard blocks using trucks. The key components of the simulation include the environment, processes, and resources.

## Environment

The environment is simulated using the SimPy library, which provides a framework for discrete-event simulation. The main environment in this simulation is represented by simpy.Environment().

## Processes

- *Vessel Arrival Generator*: Generates vessels arriving at the terminal based on an exponential distribution.
- *Vessel Process*: Manages the vessel's arrival, berthing, unloading of containers, and departure.
- *Crane and Truck Operations*: Handle the movement of containers from the vessel to the terminal trucks and then to the yard blocks.

## Resources

- *Berths*: Limited to 2, representing the slots available for vessels to berth.
- *Cranes*: Limited to 2, used for unloading containers from vessels.
- *Trucks*: Limited to 3, used for transporting containers to yard blocks.

## Events Logged

The following events are logged with timestamps to show the sequence and timing of activities in the terminal:

- *Vessel Arrival*: Logs the arrival time of each vessel.
- *Vessel Berthing*: Logs when a vessel berths and its waiting time if it had to wait for a berth to become available.
- *Crane Operations*: Logs when a crane starts unloading a container from a vessel.
- *Truck Operations*: Logs when a container is placed on a truck, when the truck starts transporting the container to the yard block, and when the truck returns to the quay crane.
- *Vessel Departure*: Logs when a vessel departs after unloading all containers.

## Code Versions

### 1. Simulation with 'with' statement

This version uses the with statement for resource requests and releases. It simplifies resource management by automatically handling resource release at the end of the with block. This is a straightforward approach that ensures resources are properly managed without needing explicit release calls.

### 2. Simulation with Manual Resource Management

This version manually controls resource requests and releases, providing more explicit control over the resource lifecycle. This approach allows for finer control over when and how resources are released, which can be useful in complex scenarios or when specific resource management strategies are needed. 

In this version, the constants provided in the task description remain the same, only the code structure is modified to avoid using the with statement.

### 3.Priority-Based Vessel Operations: Preparing for Future Enhancements

This version introduces a priority system for vessels. Certain vessels have higher priority (e.g., carrying perishable goods) and can preempt resources from lower-priority vessels. The manual control over resource management is used here to implement this priority system, ensuring that higher-priority vessels are serviced first while still ensuring fair service to lower-priority vessels.

## How to Run

1. *Install Dependencies*: Make sure you have Python and SimPy installed. You can install SimPy using pip:
   ```bash
   pip install simpy
