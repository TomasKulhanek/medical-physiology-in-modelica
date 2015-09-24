# Cardiovascular System

[Cardiovascular system](http://en.wikipedia.org/Circulatory_system) is an organ system that permits blood to circulate and transport nutrients, gases, hormones, and blood cells to and from the cells in the body to provide nourishment and help in fighting diseases, stabilize temperature and pH, and maintain homeostasis. 

The mathematical formalization of the cardiovascular system, the models, can be divided into two main approaches. The first approach builds 3D models with geometrical, mechanical properties and the time-dependence of the compartments of the CVS. The complexity of such models implicates high demand on computational power to simulate them. These models lead to the solution of partial differential equation (PDE) and e.g. finite element methods. This is not (yet) supported in Modelica.  

The second approach, lumped parameter approach, uses a high degree of simplification and different complex regions are generalized as single compartments characterized by lumped parameter.
## Hemodynamics

This section will cover the hemodynamics (haemodynamics) - it is the study of the blood flow. Using the lumped parameter approach - the hemodynamics is modeled as an analogy of an electrical circuit with a set of resistors, capacitors (elastic vessels), diodes (valves) and inductance (inertial elements) in a closed loop.

The blood vessels are characterized by it's capacity (capacitance), i.e. how much the
