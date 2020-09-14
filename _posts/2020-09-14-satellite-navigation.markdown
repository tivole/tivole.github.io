---
layout: post
title: "Satellite Navigation"
date: 2020-09-14 14:33:00 +0400
categories: math satellite navigation
---

{% include lib/mathjax.html %}

The idea that your GPS receiver gets your coordinates from satellites in orbit is a mistake. Firstly, the satellites simply do not know them, and secondly, the satellites do not personify their messages and send them into space, to everyone at once, and not just to your receiver. How, then, does the navigator determine your coordinates?

There are two main segments in satellite navigation system: space and management. Space segment is a constellation of satellites, evenly located around the Earth. Management segment, located on the Earth, provides, in particular, synchronization on all satellites of system-wide time and use of a single coordinate system.

Each satellite constantly sends navigation messages containing, in particular, the coordinates of the satellite at the time of sending the message and the time of sending.

Receiver that reads this message can calculate the distance to the satellite: $$ d = (t_{rc} - t_{send}) c $$.

In this formula, the transit time of the signal (from sending time $$t_{send}$$ to receiving time $$t_{rc}$$) is multiplied by the speed of radio signal propagation, ie the speed of light $$c$$.

On the other hand, if in a rectangular Cartesian system the coordinates are equal $$(x, y, z)$$ and the coordinates of the satellite at the moment of sending the message were equal $$(x_1, y_1, z_1)$$, then the distance $$d$$ is equal to $$\sqrt{(x-x_1)^2 + (y-y_1)^2 + (z-z_1)^2}$$.

If the receiver simultaneously receives navigation messages from two more satellites, it will be able to find your coordinates $$(x, y, z)$$ by solving a system of three equations.

$$
\begin{equation}\left\{\begin{array}{l}
    (x-x_1)^2 + (y-y_1)^2 + (z-z_1)^2 = d_1^2\\
    (x-x_2)^2 + (y-y_2)^2 + (z-z_2)^2 = d_2^2\\
    (x-x_3)^2 + (y-y_3)^2 + (z-z_3)^2 = d_3^2
\end{array}\right.\end{equation}
$$

where $$(x_i, y_i, z_i)$$ is the coordinates of i-th satellite, and $$d_i$$ is the distance to it.

The geometric interpretation of this system is as follows. Message from one satellite allocates a part of which you are a sphere defined by its center-satellite and radius.

Infomation from the second satellite is another sphere. Crossing of these two spheres, in general is a circle. A message from the third satellite adds another restriction is another sphere, and already defines your coordinates unambiguously. The fact that all three spheres have a common point, follows from the very compilation of the system. Of the two formal solutions (the intersection of the circle and the third sphere), one is improbable, and the other is your coordinates.

Described scheme of satellite navigation system is simplified. The reality forces the use of a more complex model. For example, the scheme considered is very sensitive to errors, one of the main problems is the influence of the accuracy of the navigator's watch, which has no opportunity to contact the ground stations of the navigation system to correct the time. Imagine that the clock is 0.001 s behind the system time. The speed of light is equal to $$c = 300000$$ km/s, so you will get a 300 km error in determining the distances to satellites (sphere radii)! In the system, if it will have a solution, then not related to your location...

Fortunately, such a problem can be overcome, even when the accuracy of the watch is unknown to us. Let's assume that the premiere clock lags behind the system time by an unknown value $$\delta$$, and its reading at the moment of receiving the message $$t_{rc}$$. The navigator will assume that the distance to the satellite $$d = (t_{rc} - t_{send}) c$$, which is less than the true distance $$d+\delta c$$.

To find the coordinates $$(x, y, z)$$ and a new unknown $$r = \delta c$$, you need another equation, it will appear if you have data from four satellites:

$$
\begin{equation}\left\{\begin{array}{l}
    (x-x_1)^2 + (y-y_1)^2 + (z-z_1)^2 = (d_1 + r)^2\\
    (x-x_2)^2 + (y-y_2)^2 + (z-z_2)^2 = (d_2 + r)^2\\
    (x-x_3)^2 + (y-y_3)^2 + (z-z_3)^2 = (d_3 + r)^2\\
    (x-x_4)^2 + (y-y_4)^2 + (z-z_4)^2 = (d_4 + r)^2
\end{array}\right.\end{equation}
$$

The geometrical interpretation of the problem solution is as follows. The receiver is the center of a sphere of radius $$r$$, which is externally (because the clock was lagging behind) touched by four spheres of radius $$d_i$$, whose centers are satellites.

After calculating the coordinates of this system, the navigator as an additional bonus gets the value of system-wide time, corrects its clock and tells you the exact time!
