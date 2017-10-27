### Lindenmayer Systems

[Lindemayer Systems](https://en.wikipedia.org/wiki/L-system), or more commonly *L-Systems*, are a formalized language for modeling agent-based growth — especially for simulating cellular or floral growth and goal-seeking behaviors. They are used heavily by the cinematic and effects industries for quickly modeling plant-like objects, and by scientists studying self-similar and recursive systems like fractals, contagion and epidemic spread, and human consumption and population growth patterns.

An agent, often called for unknown reasons a *turtle*, is stationed at an origin point and is allowed to move in any direction defined in a [Euler Angle-based](https://en.wikipedia.org/wiki/Euler_angles) coordinate system (like an airplane -- pitch, yaw, roll).

The turtle follows an encoded set of directions...

```
F move forward at distance L(Step Length) and draw a line
f move forward at distance L(Step Length) without drawing a line
+ turn left A(Default Angle) degrees
– turn right A(Default Angle) degrees
roll left A(Default Angle) degrees
/ roll right A(Default Angle) degrees
^ pitch up A(Default Angle) degrees
& pitch down A(Default Angle) degrees
| turn around 180 degrees
J insert point at this position
“ multiply current length by dL(Length Scale)
! multiply current thickness by dT(Thickness Scale)
[ start a branch(push turtle state)
] end a branch(pop turtle state)
A/B/C/D.. placeholders, used to nest other symbols
```

The turtle is given a starting pattern (its *axiom*), a set of rules to follow, and a number of iterations to complete.

```
Axiom: FA
Rule 1: A = +F-FA 
Iterations: 3
```

The turtle will, for each iteration, follow the rules. At the end, all replacement symbols are dropped.

```
Iteration 0 : FA
Iteration 1 : F+F-FA
Iteration 2 : F+F-F+F-FA
Iteration 3 : F+F-F+F-F+F-FA
Final Pattern : F+F-F+F-F+F-F
```

We can set `F` equal to `move one unit forward`, `+` to `turn right 90 degrees`, and `-` to `turn left 90 degrees`.

The turtle now is walking in a stair step pattern toward the upper right. More complex patterns, especially those invoking scale change and randomness, can create beautiful, organic, recursively complex results. Complexity builds quickly.

---

An Example from Wikipedia for modeling Sierpinski Fractals

```
Axiom  : A
Rule 1 : A = B−A−B
Rule 2 : B = A+B+A

+ : Turn Clockwise 60 degrees
- : Turn Counter-Clockwise 60 Degrees
F : Move Forward One Unit
```

Here is the results at different iteration counts (2,4,6,8)

![sierpinski triangle](tri.png)
