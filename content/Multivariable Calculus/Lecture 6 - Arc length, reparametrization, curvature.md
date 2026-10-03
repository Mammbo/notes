## 1. Warm-up: Piecewise Acceleration → Position
 
Suppose
 
$$
\vec a(t) =
\begin{cases}
\hat i - t\,\hat j, & t \le 6 \\
\vec 0, & t > 6
\end{cases}
$$
 
**Integrate to get velocity:**
 
$$
\vec v(t) =
\begin{cases}
t\,\hat i - \dfrac{t^2}{2}\,\hat j + \vec C, & t \le 6 \\[4pt]
6\,\hat i - 18\,\hat j, & t > 6
\end{cases}
$$
 
- Initial condition: $\vec v(0) = \vec 0 = \vec C$
- For $t > 6$, velocity is constant, fixed by continuity:
$$
\lim_{t \to 6^-} \vec v(t) = \lim_{t \to 6^+} \vec v(t) \implies \vec v = 6\,\hat i - 18\,\hat j
$$
**Integrate again to get position:**
 
$$
\vec r(t) =
\begin{cases}
\dfrac{t^2}{2}\,\hat i - \dfrac{t^3}{6}\,\hat j + \vec C, \quad \vec C = \vec 0, & t \le 6 \\[4pt]
6t\,\hat i - 18t\,\hat j + \vec D, & t > 6
\end{cases}
$$
 
**Match at $t = 6$:**
 
$$
\vec r(6) = 18\,\hat i - 36\,\hat j = 36\,\hat i - 108\,\hat j + \vec D
$$
$$\boxed{\vec D = -18\,\hat i + 72\,\hat j}$$

## 2. Smooth Curves & the Unit Tangent
 
> [!definition] Smooth curve
> A parameterized curve $\vec r(t)$ is called **smooth** provided
> $$\vec r\,'(t) \neq \vec 0 \quad \text{for all } t.$$
 
A smooth curve has a well-defined **unit tangent vector**:
 
$$
\vec T(t) = \frac{\vec r\,'(t)}{\lvert \vec r\,'(t) \rvert}
$$

## 3. Arc Length
> [!important] Arc length formula
> $$L = \int_a^b \lvert \vec r\,'(t) \rvert \, dt$$
 
> [!warning] Don't mix these up
> $$\int_a^b \lvert \vec r\,'(t) \rvert\,dt \;\neq\; \left\lvert \int_a^b \vec r\,'(t)\,dt \right\rvert = \lvert \vec r(b) - \vec r(a) \rvert$$
> The right side is the **displacement** (straight-line distance between endpoints), not the length of the path.

### Example: Arc length of a helix
 
$$
\vec r(t) = \langle \cos t,\ \sin t,\ t \rangle, \qquad 0 \le t \le 2\pi
$$
 
$$
s = \int_0^{2\pi} \lvert \langle -\sin t,\ \cos t,\ 1 \rangle \rvert \, dt
= \int_0^{2\pi} \sqrt{2}\, dt
= \boxed{2\pi\sqrt{2}}
$$

## 4. Reparameterization
 
> [!definition] Smooth reparameterization
> Consider a smooth curve $\vec r(t)$ for $a \le t \le b$. A **smooth reparameterization** is a choice of scalar function $f(s)$ with
> $$f'(s) > 0, \quad f(c) = a, \quad f(d) = b$$
> such that
> $$\vec q(s) = \vec r\big(f(s)\big)$$
> traces out the **same path**.

### Arc length as a function
 
$$
s = f(t) = \int_a^t \lvert \vec r\,'(u) \rvert \, du
$$
 
- By FTC: $\dfrac{ds}{dt} = \lvert \vec r\,'(t) \rvert$
- For smooth $\vec r$, $f$ is invertible: $t = f^{-1}(s)$
**Key fact — the arc-length parameterization has unit speed:**
 
$$
\frac{d}{ds}\, \vec r\big(f^{-1}(s)\big)
= \vec r\,'\big(f^{-1}(s)\big)\,\big(f^{-1}\big)'(s)
= \vec r\,'(t)\, \frac{1}{f'\big(f^{-1}(s)\big)}
= \frac{\vec r\,'(t)}{\lvert \vec r\,'(t) \rvert}
= \vec T
$$
### Example: Reparameterize by arc length
 
$$
\vec r(t) = \langle e^{-t},\ 1 - 2e^{-t},\ 2e^{-t} \rangle
$$
 
$$
\begin{aligned}
s &= \int_0^t \lvert \langle -e^{-u},\ 2e^{-u},\ -2e^{-u} \rangle \rvert \, du \\
  &= \int_0^t e^{-u}\, \lvert \langle -1,\ 2,\ -2 \rangle \rvert \, du \\
  &= \int_0^t 3e^{-u} \, du = 3\left(1 - e^{-t}\right)
\end{aligned}
$$
 
Solve for $e^{-t}$:
 
$$
e^{-t} = 1 - \frac{s}{3}
$$
 
Substitute back:
 
$$
\begin{aligned}
\vec q(s) &= \left\langle 1 - \frac{s}{3},\ 1 - 2\left(1 - \frac{s}{3}\right),\ 2\left(1 - \frac{s}{3}\right) \right\rangle \\
&= \langle 1,\ -1,\ 2 \rangle + \frac{s}{3}\,\langle -1,\ 2,\ -2 \rangle
\end{aligned}
$$
 
> [!note]
> This is a **line**: starting point $\langle 1, -1, 2 \rangle$ with unit direction $\tfrac{1}{3}\langle -1, 2, -2\rangle$ (unit speed, as expected).
### Example: Circle of radius $R$
 
$$
\vec r(t) = \langle R\cos t,\ R\sin t \rangle
$$
 
$$
s = \int_0^t R \, du = Rt \quad\implies\quad t = \frac{s}{R}
$$
 
$$
\vec q(s) = \left\langle R\cos\!\left(\frac{s}{R}\right),\ R\sin\!\left(\frac{s}{R}\right) \right\rangle
$$
 
Since $\vec q\,'(s) = \vec T$:
 
$$
\kappa = \left\lvert \frac{d\vec T}{ds} \right\rvert
= \lvert \vec q\,''(s) \rvert
= \left\lvert \left\langle \frac{R}{R^2}\left(-\cos\frac{s}{R}\right),\ \frac{R}{R^2}\left(-\sin\frac{s}{R}\right) \right\rangle \right\rvert
= \boxed{\frac{1}{R}}
$$
 