---
layout: post
title: "Tello Drone Real Time Trajectory Tracking"
date: 2022-02-02 15:14:00 +0400
categories: tello drone trajectory
---

{% include lib/mathjax.html %}

To work with the [tello](https://www.ryzerobotics.com/tello) drone, we will use the [DJITelloPy](https://github.com/damiafuentes/DJITelloPy) library.

```python
from djitellopy import tello

drone = tello.Tello()
drone.connect()
```

With the telemetry of the Tello drone, we can get information about the speed of the drone along three axes.

```python
speed_x = drone.get_speed_x()
speed_y = drone.get_speed_y()
speed_z = drone.get_speed_z()
```

Acceleration is the derivative of velocity with respect to time ($$a = \dot{v}$$), and velocity is the derivative of position with respect to time ($$v = \dot{x}$$). Therefore, to get the position coordinates, we need to integrate the speed over time.

$$
\begin{equation}
    x = \int_{t_0}^{t_1} v_x \mathrm{d} t,
\end{equation}
$$

where $$t_0$$ and $$t_1$$ are the start and end times, respectively, at which the drone's speed along the $$x$$-axis direction is $$v_x$$.

Computing this integral, we get the following:

$$
\begin{equation}
    x = (t_1 - t_0) \cdot v_x.
\end{equation}
$$

In our case with a drone, $$(t_1 - t_0)$$ will be the time period for receiving telemetry from the drone.

Having made the same analogous calculations for the $$y$$ and $$z$$ coordinates, we obtain the position of the drone in three-dimensional space relative to the flight start point

```python
import time

last_timestamp = time.time()
pos_x, pos_y, pos_z = (0, 0, 0)

while True:
    speed_x = drone.get_speed_x()
    speed_y = drone.get_speed_y()
    speed_z = drone.get_speed_z()

    dt = (time.time() - last_timestamp)

    # Multiply the value by 10 to get the coordinates in centimeters.
    pos_x += (10 * speed_x * dt)
    pos_y += (10 * speed_y * dt)
    pos_z += (10 * speed_z * dt)

    last_timestamp = time.time()

    print(dt, pos_x, pos_y, pos_z)

    time.sleep(0.01)
```

Tello drone has a built-in TOF sensor, the data of which can be used as a height coordinate, that is, $$z$$:

```python
pos_z = drone.get_distance_tof()
```

Thus, we received the coordinates of the drone in real time. Then we can run our code in a thread and visualize this data during the flight.


<p align="center">
    <iframe width="560" height="315"
    src="https://www.youtube.com/embed/luXw3lQC7wI" 
    frameborder="0" 
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" 
    allowfullscreen></iframe>
</p>

### Project:

[tivole/drone-trajectory-plotter](https://github.com/tivole/drone-trajectory-plotter)

### Authors:

- [Kamran Asgarov](https://github.com/tivole)
- [Anar Mammadov](https://github.com/anarmammad)