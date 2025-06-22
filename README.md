# LA-MJ-EPFL-PDS

> This repository contains the tests performed during an EPFL semester project in the **Automatic Control Laboratory (LA)**.

## 🎯 Investigation into Distributed Wireless Communication Latency

This project explores **latency sources** in a distributed wireless system consisting of a collection of drones performing **Model Predictive Control (MPC)** for coordinated movements.

The focus is on measuring latency introduced by the **ROS 2 network stack overhead**, and evaluating alternatives including:

* 🔵 TCP sockets
* 🟢 UDP sockets
* 🔴 Raw sockets

---

## 🧪 Main Tests

There are **three main tests** performed, each located in a separate Git branch:

### 1) ROS\_IMPLEMENTATIONS

Investigates the latency of the default **ROS 2 netstack**, the current implementation used in the distributed system. Various ROS 2 parameters are varied to observe their influence on latency. To retrieve data: Use `get_logs.sh` if the talker runs on the **main computer**. Use `holo_get_logs.sh` if the talker runs on a **drone**.

### 2) SOCKET\_IMPLEMENTATIONS

Deploys **TCP**, **UDP**, and **Raw sockets** and tests their communication latency.

> ⚠️ **Important Note:** This code is currently configured for specific drone IP addresses.

**Talker** must be launched on the `.131 drone`. **Listener** IP address does **not** matter.

**Launch scripts:** Talker on drone: `holo_talker_docker_launch.sh` Talker on main computer: `main_docker_launch.sh` Listener on drone: `holo_launch_docker.sh`

> ⚠️ **Critical:** Start the **talker node first** before the listener node to prevent socket connection issues.

> ⚠️ **Critical:** For the ROS2 and socket implementations, to change modes, it is important to uncomment the desired implementation macro at the top of the talker.cpp and listener.cpp, the modes must match.

### 3) DISTRIBUTED\_UDP

Implements **UDP socket communication** across the entire distributed system, replacing the default ROS 2 stack.

**Launch scripts:** On drones: `holo_talker_docker_launch.sh` On main computer: `main_launch_exp.sh`

🔗 Repository Link

You can find the full repository here: https://github.com/MatasJones/LA-MJ-EPFL-PDS.git
