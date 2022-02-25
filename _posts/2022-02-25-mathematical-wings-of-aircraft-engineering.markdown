---
layout: post
title: "Mathematical Wings of Aircraft Engineering"
date: 2022-02-25 21:55:00 +0400
categories: math aircraft engineering
---

<p align="center">
    <img src="/assets/images/aircraft-wings/fighter.png" />
</p>

Aircraft building is the most important branch of the modern industry. There is a competition between aircraft manufacturing companies (including research institutes associated with them), the purpose of which is to create products that are superior to competitors: for passenger and cargo aircraft - in safety, efficiency, environmental friendliness; for military aircraft - by combat qualities. For research in modern aviation science, it is common to use adequate mathematical models, the basis of which is a clear understanding of the physics of the phenomena under study. The development and construction of new aircraft is impossible without the use of "highly mathematical" sciences, such as aerodynamics, control theory, strength.

Aerodynamics is a science that studies the interaction of an air flow and a body streamlined by it. The speed of the aircraft is so great that the flow around it becomes turbulent. A turbulent flow differs from a "calm" laminar flow by a chaotic change in its characteristics over time (velocity, pressure, etc.), leading to intensive mixing of the gas, to the appearance of vortices. The main mathematical problem of turbulence - the creation of a system of partial differential equations that would describe arbitrary turbulent flows and which could be solved on modern computers - has not yet been solved. Therefore, semi-empirical models of turbulence are currently being created on the basis of the equations of mathematical physics, suitable for describing only a narrow class of flows.

How are the aerodynamic characteristics of an aircraft determined? Basically two methods: experimental and calculated. To conduct experimental research in wind tunnels, aircraft models are created - several times reduced copies of the originals. This is due to the fact that the dimensions of the wind tunnels do not allow testing with real aircraft. But the data obtained during model testing in a wind tunnel cannot be recalculated into aircraft characteristics by simple scaling, taking into account the similarity coefficient of the model and the real aircraft.

The fact is that the equations that govern the characteristics of the flow are quite complex. If we bring them to a basic-dimensional form, i.e., express all dimensional quantities in parameters characteristic of a given flow, then the equations will include dimensionless quantities that bear the names of prominent scientists: Mach number, Reynolds number, Strouhal number, etc. For strict similarity, it is necessary so that all these values coincide during the actual flight of the aircraft and when testing the model in the tube. But the specific properties of the air flow used in the pipe do not allow fulfilling all the similarity criteria. In addition, in both closed and open pipe cases, the fact that the flow is not unlimited affects the aerodynamic performance.
  
The problem arises of recalculating integral characteristics (total forces and moments) and distributed characteristics (values at specific points of pressure, temperature, etc.) from the model to a full-scale aircraft. This problem is solved by carrying out a numerical calculation of the equations of mathematical physics for two semi-empirical models: an aircraft in an infinite flow and an aircraft model in a wind tunnel. The aerodynamic characteristics of the aircraft are obtained by adding to the data obtained from tests of a reduced copy of the aircraft in a wind tunnel, the difference of the same type of data obtained for the two described semi-empirical models.

It would seem, why not make a calculation immediately, without resorting to an experiment? The issue here is accuracy. The accuracy of experimental data obtained in good wind tunnels is several times higher than the calculation accuracy.

The wing of the aircraft must be optimal. One of the most important parameters of a wing is its quality: this is the name given to the ratio of lift to drag. To create an optimal (“high-quality”) wing, problems of the calculus of variations are solved.

**Control theory.**

The flight of an aircraft consists of several phases: takeoff, climb, cruising, turns, descent, and landing. At each stage, the aircraft must be controlled. A flap on a wing or an elevator on the tail are examples of controls. The control system must be designed so that the simple movements of the pilot in the cockpit are transmitted and reach the controls, causing appropriate reactions. On the other hand, the system must be sufficiently "smart", the elements of its design must not go beyond the boundaries of the safe mode.

Another task is to create an autopilot capable of controlling the movement of an aircraft without the intervention of a pilot.

The mathematical theory of automatic aircraft control, based mainly on the theory of differential equations, is responsible for all these problems. With the help of the same theory, a mathematical model of the spatial motion of an aircraft is created, and questions of flight stability are studied.

**Strength.**

It is not enough to create an aircraft with good aerodynamic data, it is necessary that it does not collapse in flight, so that its resource (longevity) is high enough. A science called strength is responsible for solving this problem.

Strength methods are used to study elastic and plastic deformations of aircraft structural elements, the growth of cracks in the aircraft skin (microcracks are initially present in the skin material, which can grow with time), and the destruction of the structure.

The mathematical arsenal for solving strength problems includes classical and modern methods of equations of mathematical physics, differential equations, calculus of variations, complex analysis, computational sections of linear algebra.

Everyone who has seen through the window how an aircraft wing behaves in flight has noticed a fairly large amplitude of its oscillations. The fact is that in order to reduce the amplitude of oscillations of the roof, it is necessary to increase its weight, and in an aircraft, they try to minimize the weight of structures. Therefore, it is not possible to get rid of wing vibrations. The branch of mechanics that studies the problems of the mathematical theory of oscillations and resonance is aeroelasticity.
