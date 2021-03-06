---
layout: default
math: true
comment: true
date: "9th Oct, 2021"
---

[Home](./) \| [Next Page](./eom1.html) \| [Resources](./conclusion.html)

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/ryhVL7ucbj4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>
## Contents 

*  1.Problem Statement 2. Working Equations 3. Remarks on Function 4. The Final Code 5. Phase Potraits 6.1. Appendix-I(Derivations) 6.2 Appendix-II(RK-4 Method) 

> **If you remember our *[The Final Goal](./#the-final-goal)*, it is the time to start working on that.**

## Problem Statement

The system is due to a problem from the classic Goldstein. The problem follows:
> "The point of suspension of a simple pendulum of length l and the mass m is constrained to move on a parabola \\( z=ax^2 \\) in the verticle plane. Derive the Hamiltonian governing the motion of pendulum and its point of suspension. Obtain the Hamilton's equation of motion." [Ref: Classical Mechanics by Goldstein, Herbert & Poole, Charles & Safko, John. (3rd Ed).(Ch. 8, Prob. 19)]

Here our goal is to find the equation of motions, to solve them within the GNUPlot script, and to simulate the system directly there to produce the above GIF. On the next page we will see how to solve a problem in a programming language and use the saved data to produce such GIF with an example system - *Kapitza's Pendulum*.

## Working Equations

> **DECLARATION:** I cannot claim that all the equations are correct neither that i've correctly written the same equations in the code. There always maybe some calculation or typing mistake. If you see any, please let me know.

After a tedious algebra(see below) one can find the equation of motion from the Lagrangian. One may use Hamilton's equation of motion, but some of the expressions are too long and complicated, so I decided to continue with Lagrangian. Although the computational complexity remains the same because in both cases you have to solve four coupled first-order differential equations.

The lagrangian is

\\[ L = \frac{1}{2}m \left(\dot{x}^2(1+4a^2 x^2) + l^2\dot{\theta}^2 +  2l\dot{x}\dot{\theta}(\cos\theta + 2ax\sin\theta)\right)  - mg(ax^2-l\cos\theta) \\]

The equations of motion are

EOM for \\(x\\) coordinate:
\\[\ddot{x} (1+4a^2 x^2) + 4a\dot{x}^2x+l\ddot{\theta}(\cos\theta + 2ax\sin\theta)+l\dot{\theta}^2(-\sin\theta + 2ax\cos\theta) + 2agx = 0\\]

EOM for \\(\theta\\) coordinate:
\\[l^2\ddot{\theta} + l\ddot{x}(\cos\theta + 2ax\sin\theta) + 2al\dot{x}^2 \sin\theta + gl\sin\theta = 0 \\]

To apply numerical methods (We will be using Runge-Kutta 4-th order method), we need to convert them to the first order.

\\[\dot{x} = X \\]

\\[\dot{\theta} = \Theta \\]

\\[\dot{X} = \frac{\sin\theta(\cos\theta + 2ax\sin\theta)(4aX^2 + g) - 4aX^2x - l\Theta^2(-\sin \theta + 2ax\cos\theta) - 2gax}{(1+4a^2 x^2) - \left(\cos \theta + 2ax\sin\theta\right)^2 } \\]

\\[\dot{\Theta} = -\left(\dot{X}(cos\theta + 2axsin\theta) + 2aX^2\sin\theta+g\sin\theta \right)/l \\]

* First few minutes are recommended of this [lecture](https://youtu.be/nh4TFzg30eQ?list=PLbMVogVj5nJQKk1E7OUQs_TcW_zQoaO4t&t=525){:target="_blank"} (8:46-11:12) by V. Balakrishnan if you're not familiar with such exercise. Here you'll find an illuminating explanation.

# Few Remarks on Function

In the last page, we've seen how to create a function, it's easy! 

`function_name(arguments) = expression/statement`

Here we will use functions not only for the mathematical expressions but also for the printing purpose - like parameters, initial conditions, and title. The functions will look like

```
# a function to print title and time

ptime(tr) = sprintf("{A pendulum is costrained to move}\n\
{on a parabola z=ax^2}\n\
{/Times:Italic t} = %5.2f [s]", tr)

# Print parameters

pparam(q, r, s, t) = sprintf("\
{/Times:Bold Parameters}\n\
{/Times:Italic a} = %.2f (z=ax^2)\n\
{/Times:Italic l} = %3.1f [m]\n\
{/Times:Italic g} = %3.2f [m/s^2]\n\
{/Times:Italic dt} = %.2f [s]\n", q, r, s, t) 

#Print initial conditions

pini(a, b, c, d) = sprintf("\
{/Times:Bold Initial Conditions}\n\
{/Times:Italic x} = %.2f [m]\n\
{/Times:Italic theeta} = %3.2f [rad] \n\
{/Times:Italic x-dot} = %.2f [m/s]\n\
{/Times:Italic theeta-dot} = %.2f [rad/s]\n", a, b, c, d) 
```
The '\' character is understood as the continuation of the same statement. And the working of function `sprintf` is the same as of `printf` in CPP. The braces may be used for fonts, to put greek symbols, etc.

## Wrapping up The Final Code

Now we are ready to put things together. As always, I'll put comments within the code to explain things ~

<script src="https://gist.github.com/arabindo/62260a0aefaab761cd3e51bb7ac037d1.js"></script>

## Phase Potraits

Here I've shown two different phase potrait for two coordinates \\(x\\) and \\( \theta \\). You may try to do so by modifying the above code. Nevertheless, you may find the codes [here](./code.html#cp-phase)

### \\(x\\) Vs. \\( \dot{x} \\) and \\( \theta \\) Vs. \\(\dot{\theta}\\)

<table>
<tr>
<td><iframe width="280" height="157" src="https://www.youtube-nocookie.com/embed/ZVRorFBgrZ4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></td>
<td><iframe width="280" height="157" src="https://www.youtube-nocookie.com/embed/ARniP4R7mo4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</td>

</tr>
</table>

[Home](./) \| [Next Page](./eom1.html) \| [Resources](./conclusion.html)

