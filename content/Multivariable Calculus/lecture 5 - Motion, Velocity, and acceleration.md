# Curves: 
$$\lim_{t\rightarrow a}r(t) = \begin{bmatrix} \lim_{t\rightarrow a}x(t) \\ \lim_{t\rightarrow a}y(t) \\ \lim_{t\rightarrow a}z(t) \\ \end{bmatrix} \land r'(t) = \begin{bmatrix} x'(t) \\ y'(t) \\ z'(t) \end{bmatrix}$$

# Propertiies of functions
- you can pull constants out and do indvidual derivatives
$$ 
\begin{align}
\frac d {dt} (cr(t)) = c r'(t)\\
\frac d {dt} (r(t) + q(t)) = r'(t) + q'(t)
\end{align}
$$
### Differentiation Rules
| Rule           | Formula                                                                                                    |
| -------------- | ---------------------------------------------------------------------------------------------------------- |
| Constant       | $\frac{d}{dt}\big(c\,\vec r(t)\big) = c\,\vec r\,'(t)$                                                     |
| Sum            | $\frac{d}{dt}\big(\vec r + \vec q\big) = \vec r\,' + \vec q\,'$                                            |
| Scalar product | $\frac{d}{dt}\big(f\,\vec r\big) = f'\,\vec r + f\,\vec r\,'$                                              |
| Dot product    | $\frac{d}{dt}\big(\vec q\cdot\vec r\big) = \vec q\,'\cdot\vec r + \vec q\cdot\vec r\,'$                    |
| Cross product  | $\frac{d}{dt}\big(\vec q\times\vec r\big) = \vec q\,'\times\vec r + \vec q\times\vec r\,'$ (order matters) |
| Chain rule     | $\frac{d}{dt}\,\vec r\big(f(t)\big) = f'(t)\,\vec r\,'\big(f(t)\big)$                                      |
## Integration
Also componentwise:
$$\int_a^b \vec r(t)\,dt = \left\langle \int_a^b x(t)\,dt,\ \int_a^b y(t)\,dt,\ \int_a^b z(t)\,dt \right\rangle$$
> The result is a **vector**, not an area.
 
### Fundamental Theorem
$$\vec r(t) = \vec r(t_0) + \int_{t_0}^{t} \vec r\,'(u)\,du$$
(value at $t$ = starting value + accumulated change)
 
## Motion
- Position: $\vec r(t)$
- Velocity: $\vec v(t) = \vec r\,'(t)$
- Acceleration: $\vec a(t) = \vec v\,'(t) = \vec r\,''(t)$
- Speed: $v = |\vec v(t)|$ (scalar)
- Newton: $\vec F = m\,\vec a$ (vector = scalar · vector)

### Circular Motion
$$\vec r(t) = \langle R\cos\omega t,\ R\sin\omega t\rangle$$
$$\vec a(t) = -\omega^2\,\vec r(t) \quad\text{(points toward center)}$$
$$|\vec a| = R\omega^2 = \frac{v^2}{R}, \qquad v = R\omega$$
 
### Direction Change ⇒ Nonzero Acceleration
If $\vec a = \vec 0$, then $\vec v(t) = \vec v(t_0)$ is constant, so direction is constant. Contrapositive: changing direction requires $\vec a \neq \vec 0$.
> [!note] Converse is false: $\vec r(t) = \langle 3t^2, 0\rangle$ has $|\vec a| \neq 0$ but constant direction.

### Method: Position from Acceleration
Integrate twice using the FTC, applying initial conditions each time. For pexiecewise $\vec a$, use the end state of one piece as the initial condition of the next.
 
**Example:** Find $\vec r(t)$ given
$$\vec a(t) = \begin{cases} \hat i - t\,\hat j, & t \le 6 \\ \vec 0, & t > 6 \end{cases} \qquad \vec r(0) = \vec 0,\quad \vec v(0) = \vec 0$$

**Part 1: $t \le 6$**

1. Velocity from acceleration:
$$\vec v(t) = \vec v(0) + \int_0^t \vec a(u)\,du = \vec 0 + \int_0^t (\hat i - u\,\hat j)\,du$$
$$\vec v(t) = t\,\hat i - \frac{t^2}{2}\,\hat j$$

2. Position from velocity:
$$\vec r(t) = \vec r(0) + \int_0^t \vec v(u)\,du = \vec 0 + \int_0^t \left(u\,\hat i - \frac{u^2}{2}\,\hat j\right)du$$
$$\boxed{\vec r(t) = \frac{t^2}{2}\,\hat i - \frac{t^3}{6}\,\hat j}$$

3. State at $t = 6$ (the initial conditions for Part 2):
$$\vec r(6) = \frac{36}{2}\,\hat i - \frac{216}{6}\,\hat j = 18\,\hat i - 36\,\hat j$$
$$\vec v(6) = 6\,\hat i - \frac{36}{2}\,\hat j = 6\,\hat i - 18\,\hat j$$

**Part 2: $t > 6$**

4. Velocity. Since $\vec a = \vec 0$, velocity stays constant:
$$\vec v(t) = \vec v(6) + \int_6^t \vec 0\,du = 6\,\hat i - 18\,\hat j$$

5. Position. Integrating a constant gives a linear function:
$$\vec r(t) = \vec r(6) + \int_6^t (6\,\hat i - 18\,\hat j)\,du$$
$$\boxed{\vec r(t) = 18\,\hat i - 36\,\hat j + (6\,\hat i - 18\,\hat j)(t - 6)}$$

**Evaluate at $t = 10$:**
$$\vec r(10) = 18\,\hat i - 36\,\hat j + (6\,\hat i - 18\,\hat j)(4) = \boxed{42\,\hat i - 108\,\hat j}$$

