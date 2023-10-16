These notes serve as a very brief and incomplete overview of the Lagrangian, the Hamiltonian, and Maxwell's equations.

I chose these topics because they're prominent elements of an introductory college physics sequence that aren't covered in AP physics. They're written for the curious adult who remembers physics from high school but never got further in the subject and wants to opportunistically sample these topics.

We will define everything mathematically (but not rigorously), starting with a review of multivariable calculus, such that a motivated reader could *in theory* solve some textbook exercises from just these notes. But for the sake of brevity, we will solve almost no problems, despite edifying examples being an important staple of all textbooks. We also will not include pictures, despite them being a crucial learning aid for these topics. As such, these notes are not recommended for serious students who want to build on this material.

## Multivariable calculus

Three concepts in multivariable calculus are the **divergence**, **curl**, and **gradient**. They are connected to each other in several ways, one of which is the notation used to define them.

$\vec{\nabla}$ is called the **del** or **nabla** operator. It is a notational convenience, not useful for anything on its own, and is defined as follows:

$$
\vec{\nabla} = 
\hat{i}\frac{\partial}{\partial x} + \hat{j}\frac{\partial}{\partial y} + \hat{k}\frac{\partial}{\partial z} = 
\left(\frac{\partial}{\partial x}, \frac{\partial}{\partial y}, \frac{\partial}{\partial z}\right)
$$

(we'll assume unless otherwise specified that we are working in $\mathbb{R}^3$).

### Divergence

$\vec{\nabla} \cdot$ is the **divergence** operator and $\vec{\nabla} \cdot \vec{A}$ is the divergence of a vector field $\vec{A} = A_x\hat{i} + A_y\hat{j} + A_z\hat{k}$. Using the definition of **del** above, this expands to

$$
\begin{align*}
\vec{\nabla} \cdot \vec{A} 
&= 
\left(\frac{\partial}{\partial x}, \frac{\partial}{\partial y}, \frac{\partial}{\partial z}\right)
\cdot
\left(A_x, A_y, A_z\right) \\ 
&= 
\frac{\partial A_x}{\partial x} + \frac{\partial A_y}{\partial y} + \frac{\partial A_z}{\partial z}
.\end{align*}
$$

Applying the divergence operator to a vector field produces a scalar field. If a vector field represents fluid flow, then the divergence at a given point is a scaled measure of how much net fluid flows outward from that point.

The divergence of a vector field at a point is positive if it acts as a "source" and negative if it acts as a "sink". A physical analogy is to imagine sawdust floating on water. Divergence is positive in spots where sawdust disperses and negative where sawdust collects.

Divergence is zero if there is no net flow at that point. A vector field is called **solenoidal** if its divergence is zero everywhere.

An equivalent, coordinate-free definition of divergence at a point is

$$
\vec{\nabla} \cdot \vec{A}  = 
\lim_{V \rightarrow 0} \frac{1}{V}
\oint_{S} \vec{A} \cdot \hat{n} \, da.
$$

Here the surface integral represents the **flux** of $\vec{A}$ through a closed surface $S$ surrounding the point of interest, where $\hat{n}$ is the outward unit normal to that surface. It is a scalar quantity that can be thought of as the "net outflow" through $S$. In physics, we will see flux denoted by $\Phi$.

The divergence at a point is thus the net efflux through a closed surface $S$ around that point per unit volume $V$ enclosed by $S$ as $V$ shrinks to zero.

Another way to look at divergence is through what is known as the **divergence theorem** (also known as **Gauss's theorem**). This theorem states that the divergence of a vector field within an enclosed volume is equal to the outflux of that field through a closed surface representing that volume.

$$
\int_{V} (\vec{\nabla} \cdot \vec{A}) \, dV = \oint_{S} \vec{A} \cdot \hat{n} \, da.
$$

Notice the similarity between this expression and the coordinate-free definition of divergence. If we shrink the volume in the divergence theorem down to a point, we get the coordinate-free divergence definition.

### Curl

$\vec{\nabla} \times$ is the **curl** operator and $\vec{\nabla} \times \vec{A}$ is the curl of $\vec{A}$. Referring again to our definition of del, this expands to

$$
\begin{align*}
\vec{\nabla} \times \vec{A} 
&= 
\left(\frac{\partial}{\partial x}, \frac{\partial}{\partial y}, \frac{\partial}{\partial z}\right)
\times
\left(A_x, A_y, A_z\right) \\ 
&= 
\begin{vmatrix}
\hat{i} & \hat{j} & \hat{k} \\
\frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\
A_x & A_y & A_z
\end{vmatrix} \\
&= 
\left(\frac{\partial A_z}{\partial y} - \frac{\partial A_y}{\partial z}\right)\hat{i} +
\left(\frac{\partial A_x}{\partial z} - \frac{\partial A_z}{\partial x}\right)\hat{j} +
\left(\frac{\partial A_y}{\partial x} - \frac{\partial A_x}{\partial y}\right)\hat{k}
.\end{align*}
$$

The curl of a vector field at a point is a vector representing the tendency for flow to "circulate" around it. To use a physical analogy, a paddlewheel held in a vector field representing water flow would rotate faster in regions with high curl.

Similar to divergence, we have an equivalent, coordinate-free definition of curl:

$$
(\vec{\nabla} \times \vec{A}) \cdot \hat{n} = 
\lim_{S \rightarrow 0} \frac{1}{S}
\oint_{C} \vec{A} \cdot d\hat{l}.
$$

The line (not surface) integral here represents the net **circulation** of a $\vec{A}$ along a *closed* curve $C$. The curl at a point is thus the circulation along a closed curve $C$ surrounding that point per unit area $S$ enclosed by $C$ when the path $C$ shrinks to a point.

Analogous to the divergence theorem, **Stokes' theorem** states that the flux of the curl of a vector field through a surface is equal to the circulation of that field over the closed path bounding that surface.

$$
\int_{S} (\vec{\nabla} \cdot \vec{A}) \, dS = \oint_{C} \vec{A} \cdot \hat{n} \, dl.
$$

We can again see the equivalence by taking the surface in Stokes' theorem and shrinking it to a point.

The divergence of the curl of a vector field is zero, which we can verify by expanding $\vec{\nabla} \cdot (\vec{\nabla} \times f) = 0$.

### Gradient

$\vec{\nabla} f$ is the **gradient** of a scalar field $f$.

$$
\begin{align*}
\vec{\nabla} f
&= 
\left(\frac{\partial}{\partial x}, \frac{\partial}{\partial y}, \frac{\partial}{\partial z}\right)
f \\
&= 
\left(\frac{\partial f}{\partial x}, \frac{\partial f}{\partial y}, \frac{\partial f}{\partial z}\right)
.\end{align*}
$$

It is a vector representing the "direction of steepest" ascent for the function $f$.

A **conservative** vector field is one that is the gradient of some function. The circulation of a conservative field around any closed curve is zero, meaning that line integrals in conservative fields are independent of the path taken. Thus the curl of a conservative field is zero, which we can verify by expanding $\vec{\nabla} \times \vec{\nabla}f = 0.$

The **Helmholtz decomposition theorem** states that any (sufficiently nice) vector field can be resolved into the sum of a solenoidal (div-free) and conservative (curl-free) vector field.

### Other

$\vec{\nabla} \cdot \vec{\nabla} = \vec{\nabla}^2 = \Delta = \frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial y^2} + \frac{\partial^2}{\partial z^2}$ is the **Laplacian**.

It appears often in physics. For instance, the **heat equation** $\dot{u} = \alpha^2\vec{\nabla}^2u$ describes the evolution of temperature $u$ over time for some constant $\alpha$.

The **wave equation** $\ddot{u} = c^2\vec{\nabla}^2u$ describes the evolution of displacement $u$ over time for some constant $c$.

### Summary

$\vec{\nabla} = \left(\frac{\partial}{\partial x}, \frac{\partial}{\partial y}, \frac{\partial}{\partial z}\right)$

$\text{div} \, \vec{A} = \vec{\nabla} \cdot \vec{A}$
* where the sources and sinks of $\vec{A}$ are
* input: vector field
* output: scalar field

$\text{curl} \, \vec{A} = \vec{\nabla} \times \vec{A}$
* where $\vec{A}$ rotates the most
* input: vector field
* output: vector field

$\text{grad} \, f = \vec{\nabla} f$
* the direction of steepest ascent for $f$
* input: scalar field
* output: vector field

## Classical electrodynamics

**Maxwell's equations** are a set of 4 coupled PDEs that form the foundations of classical electrodynamics.

They describe the interrelated behaviors of an electric field $\vec{E}$ and a magnetic field $\vec{B}$ by relating them to a constant $\varepsilon_{0}$ (permittivity of free space).

### Review

Recall that the force experienced by one charged particle due to another is governed by **Coulomb's law**, $\vec{F} = kq_1q_2/r^2$.

Charged particles create an **electric field** in the sense that a test particle with charge $q$ will experience a force due to the net influence of every other other charged particle in the vicinity.

We define the electric field $\vec{E}$ such that $\vec{F_e} = q\vec{E}$ is the force experienced by a test particle with charge $q$.

Just as charged particles "create" an electric field, magnets "create" a **magnetic field**. The magnetic field $\vec{B}$ applies a force on *moving* charged particles such that $\vec{F_b} = q\vec{v} \times \vec{B}$.

Together, the force $\vec{F_e} + \vec{F_b}$ experienced by a point charge due the combination of electric and magnetic effects is called the **Lorentz force**.

We take as axioms that charged particles (protons/electrons) and magnets (which always manifest as N-S dipoles) simply "exist". Furthermore, electric currents create magnetic fields (electromagnets) and a changing magnetic field *induces* an electric current.

The "why" behind these phenomena is usually explored further in special relativity, but we will just accept for our purposes that these are the laws of nature.

### Gauss's law for electric fields

$\vec{\nabla} \cdot \vec{E} = \rho/\varepsilon_{0}$ (differential form)

$\oint_{S} \vec{E} \cdot \hat{n} \, da = q_{enc}/\varepsilon_{0}$ (integral form)

Maxwell's equations can all be expressed in equivalent differential and integral froms. This relates the net electric efflux through a *closed* surface $S$ to the charge enclosed within (in differential form, $\rho$ represents charge density).

This implies that excess charge on a solid conductive object rests entirely on the surface. Why? The electric field within the object must be zero at equilibrium, or charges at that point would move. If we apply Gauss's law for electric fields to any imaginary closed surface (called a **Gaussian surface**) within the object, we see that $q_{enc}$ must thus be zero within that surface. Therefore charge must be *on* the object's surface where it is mechanically constrained from further movement by its host.

This law is often referred to as simply **Gauss's law**, but is not to be confused with Gauss's theorem for divergence.

### Gauss's law for magnetic fields

$\vec{\nabla} \cdot \vec{B} = 0$ (differential form)

$\oint_{S} \vec{B} \cdot \hat{n} \, da = 0$ (integral form)

The second of Maxwell's equations states that the net magnetic flux through any closed surface $S$ is zero.

This is evident when we consider that magnetic monopoles do not exist in nature. Thus, any magnetic field line that goes into a surface must also come out of it.

It is exactly Gauss's theorem for divergence (the "divergence theorem") that equates the differential and integral forms of Gauss's laws for electric and magnetic fields.

### Faraday's law

$\vec{\nabla} \times \vec{E} = -\frac{\partial\vec{B}}{\partial t}$ (differential form)

$\oint_{S} \vec{E} \cdot d\vec{l} = -\frac{d}{dt} \oint_{S} \vec{B} \cdot \hat{n}  \, da$ (integral form)

Faraday's law of induction describes how a changing magnetic field induces an electromotive force (voltage) and hence current. Specifically, the electromotive force around a closed path is equal to the negative time derivative of the magnetic flux through that path.

As the negative sign shows, the induced emf opposes the change in flux. This qualitative effect is known as **Lenz's law**.

### Ampère-Maxwell law

$\vec{\nabla} \times \vec{B} = \mu_{0}\left(\vec{J} + \varepsilon_{0}\frac{\partial\vec{E}}{\partial t}\right)$ (differential form)

$\oint_{C} \vec{B} \cdot d\vec{l} = \mu_{0}\left(I_{enc} + \varepsilon_{0} \frac{d}{dt} \oint_{S} \vec{E} \cdot \hat{n}  \, da\right)$ (integral form)

The Ampère-Maxwell law relates the circulation of a magnetic field around a closed path $C$ to two factors: a steady current $I_{enc}$ and the time derivative of the electric flux through a surface $S$ bounded by $C$ (in differential form, $\vec{J}$ represents current density).

In other words, currents produce magnetic fields and changing electric flux also produce magnetic fields.

Stokes' theorem equates the differential and integral forms of both Faraday's law and the Ampère-Maxwell law.

### Summary

**Gauss's law for electric fields**: electric charges produce electric fields

**Gauss's law for magnetic fields**: magnetic dipoles produce magnetic fields

**Faraday's law**: changing magnetic fields induce electric fields

**Ampère-Maxwell law**: currents and changing electric fields induce magnetic fields

## Classical mechanics

Newtonian mechanics gives us a framework for calculating the behavior of classical mechanical systems, such as that of a sliding block on an incline plane. It starts with Newton's laws of motion (e.g. $\vec{F} = m\vec{a}$) as axioms and defines a process for drawing free-body diagrams to solve for a quantity of interest.

Lagrangian mechanics was developed later and lays out an equivalent, but equally valid framework for describing classical mechanical systems. Its advantage was that certain problems were easier to solve using the Lagrangian approach compared to the Newtonian.

Hamiltonian mechanics was a later reformulation of Lagrangian mechanics that similarly found advantages over prior approaches for certain types of problems.

### Lagrangian mechanics

The **Lagrangian** $\mathcal{L}$ is defined as $T-U$, the difference between the kinetic and potential energies of a system. It is not related to the total energy of a system, $T+U$, except by coincidence.

The main assertion in Lagrangian mechanics is that a mechanical system evolving from $t_1$ to $t_2$ is described by stationary points (where derivative is zero) of the **action integral**

$$\int_{t_1}^{t_2} \mathcal{L}(q_1, \dot{q_1}, \dots, q_n, \dot{q_n}, t) \, dt.$$

Here, the $q$'s are **generalized coordinates** — they can be Cartesian, polar, or anything else — and $t$ is a parameter of the coordinates $q_i = q_i(t)$, typically thought of as time.

The justification for this approach is called **Hamilton's principle**. Why this principle is true is often not obvious to students first encountering the topic; Newton's laws are somehow easier to accept as being consistent with our physical intuition. We won't further address the "why" for our purposes.

Nevertheless, we can show that Hamilton's principle ends up being equivalent to Newton's laws of motion. We can also show using calculus that solutions to the **Euler-Lagrange equations**

$$
\frac{\partial \mathcal{L}}{\partial q_i}(t, \mathbf{q}(t), \mathbf{\dot{q}}(t)) =
\frac{d}{dt}\frac{\partial \mathcal{L}}{\partial \dot{q}_i}(t, \mathbf{q}(t), \mathbf{\dot{q}}(t))
$$

are exactly those that describe these stationary points.

So the Lagrangian approach is to compute the Lagrangian $\mathcal{L}$, choose a set of generalized coordinates $\{q_i\}$, and apply the Euler-Lagrange equations to solve for each $q_i$.

### Example: block sliding on a wedge

Consider a block of mass $m$ sliding down the top of a frictionless wedge of mass $M$. The wedge itself is free to frictionlessly slide on the table it's on. What is the behavior of the system if the wedge has angle $\alpha$ and the length of its sloping face is $l$?

To solve this problem using Newtonian methods takes a bit of insight when writing out all the forces and constraints. With the Lagrangian method, the required insight shifts to just choosing a good set of generalized coordinates.

Let $q_1(t)$ be the distance from the top of the wedge to the block's current position (in the wedge's frame of reference). Let $q_2(t)$ be the horizontal distance between the wedge and its starting position on the table.

We first wish to compute the Lagrangian $\mathcal{L} = T-U$.

Going through the motions, we get

$$T = T_M + T_m = \frac{1}{2}(M+m)\dot{q_2}^2 + \frac{1}{2}m(\dot{q_1}^2 + \dot{q_2}^2 + 2\dot{q_1}\dot{q_2}\cos\alpha)$$

$$U = -mgq_1\sin\alpha$$

and

$$\mathcal{L} = T-U = \frac{1}{2}(M+m)\dot{q_2}^2 + \frac{1}{2}m(\dot{q_1}^2 + \dot{q_2}^2 + 2\dot{q_1}\dot{q_2}\cos\alpha) + mgq_1\sin\alpha.$$

Now we apply the Euler-Lagrange equations

$$\frac{\partial \mathcal{L}}{\partial q_1} = \frac{d}{dt}\frac{\partial \mathcal{L}}{\partial \dot{q_1}}
\qquad \text{and} \qquad
\frac{\partial \mathcal{L}}{\partial q_2} = \frac{d}{dt}\frac{\partial \mathcal{L}}{\partial \dot{q_2}}.$$

Solving the equation for $q_2$ first, we get $M\dot{q_2} + m(\dot{q_2} + \dot{q_1}\cos\alpha) = \text{const.}$

Combining this result with the equation for $q_1$, we find

$$\ddot{q_2} = -\frac{m}{M+m}\ddot{q_1}\cos\alpha$$

$$\ddot{q_1} = \frac{g\sin\alpha}{1-\frac{m\cos^{2}\alpha}{M+m}}$$

which we can convert back to Cartesian coordinates if we'd like.

The Lagrangian approach's advantage is that it is highly general and often doesn't require as much problem-specific insight, especially when Cartesian coordinates are less suited to the problem. However, there is no guarantee that the resultant system of Euler-Lagrange equations will be easily solvable. The Newtonian approach is often preferred if we need to account for non-conservative forces like friction.

### Hamiltonian mechanics

As we previously mentioned, the Euler-Lagrange equations imply Newton's second law. For a particle in 2-d,

$$\mathcal{L} = T - U = \frac{1}{2}m(\dot{x}^2+\dot{y}^2) - U(x, y)$$

with the corresponding Euler-Lagrange equations

$$\frac{\partial \mathcal{L}}{\partial x} = \frac{d}{dt}\frac{\partial \mathcal{L}}{\partial \dot{x}}
\qquad \text{and} \qquad
\frac{\partial \mathcal{L}}{\partial y} = \frac{d}{dt}\frac{\partial \mathcal{L}}{\partial \dot{y}}.$$

If we evaluate the equations, we'd get

$$
\begin{align*}
\frac{\partial \mathcal{L}}{\partial x} &=
\frac{d}{dt}\frac{\partial \mathcal{L}}{\partial \dot{x}} \implies \\
-\frac{\partial U}{\partial x} &= \frac{d}{dt}\frac{\partial T}{\partial \dot{x}} \implies \\
F_x &= \frac{d}{dt}m\dot{x} = m\ddot{x}
\end{align*}
$$

and correspondingly, $F_y = m\ddot{y}$.

When we use generalized coordinates $q_i$, we call

$$\frac{\partial \mathcal{L}}{\partial q_i} = m\ddot{q_i}$$ 

the **generalized force**
and

$$\frac{\partial \mathcal{L}}{\partial \dot{q_i}} = m\dot{q_i} = p_i$$

the **generalized momentum**.

The Hamiltonian approach is heavily related to the Lagrangian; we first define the **Hamiltonian** function as $\mathcal{H} = {\sum}_{i=1}^n p_i\dot{q_i} - \mathcal{L}.$

Just as the Euler-Lagrange equations can be used to solve systems if we have the Lagrangian, **Hamilton's equations**

$$\dot{q_i} = \frac{\partial\mathcal{H}}{\partial p_i}\qquad \text{and} \qquad \dot{p_i} = -\frac{\partial\mathcal{H}}{\partial q_i}$$

can be used to solve systems if we have the Hamiltonian.

In the Lagrangian approach, we have a second-order ODE involving $q_i(t), \dot{q_i}(t)$ for each generalized coordinate $q_i$.

In the Hamiltonian approach, we have two first-order ODEs involving $q_i(t), p_i(t)$ for each generalized coordinate.

The overall transformation from $(q, \dot{q}) \to (q, p)$ is a particular case of the **Legendre transformation**.

The particular advantages of the Hamiltonian over the Lagrangian lie in the functional form of Hamilton's equations compared to that of the Euler-Lagrange equations. These advantages are more clear in quantum or statistical mechanics, and we unfortunately won't shed any light on them here.

### Liouville's theorem

Consider the evolution of $(\mathbf{q}, \mathbf{p})$ for a particular system under Hamilton's equations. This evolution defines a **phase space orbit**. Now imagine we have many identical systems (with different initial conditions) occupying different points in the phase space. If we look at the aggregate evolution of all of these systems as a fluid, we would find that the fluid moves faster in some regions than in others. **Liouville's theorem** states that the density of the fluid remains constant — namely, that the divergence of the velocity field $(\mathbf{\dot{q}}, \mathbf{\dot{p}})$ representing the fluid is zero everywhere.

## Postscript

The content above is unlikely to be useful for anyone actually trying to "learn" physics, for to learn a subject is to appreciate it through many angles by repeatedly doing problems and connecting concepts together. It is similarly likely insufficient in providing the tooling for solving any practical exercise involving physics. And it is likely too incomplete for students who already know this material and are looking for a review.

I wrote these notes because I'm an adult with none of the above aims. As someone who will likely never use physics in my life, I just wanted a flavor of what students learn when they learn physics. I find most YouTube videos too "pop sci" for this purpose, trying to provide viewers with an intuition that I believe is impossible to grasp without going through the mathematical formalism.

I'm clearly not a "physics person" and it's very possible I've made mistakes. Please feel free to let me know and I'll correct them.