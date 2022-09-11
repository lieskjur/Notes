---
title: Bellman's principle of optimality
draft: false
---

# Bellman's principle of optimality

For a dynamic system with state feedback in the form
{{< katex display >}}
\dot{\bm{x}} = \bm{f}(\bm{x},\bm{u},τ) \;,\quad \bm{u} = \bm{u}(\bm{x})
{{< /katex >}}
where {{< katex >}} \bm{x}(τ) {{< /katex >}} are the system's states and {{< katex >}} \bm{u}(\bm{x}) {{< /katex >}} a function of state feedback inputs, we may define for the trajectory from state {{< katex >}} \bm{x}(t) {{< /katex >}} to state {{< katex >}} \bm{x}(T) {{< /katex >}} an objective function
{{< katex display >}}
J_{t→T} = ∫_{t}^{T} L(\bm{x},\bm{u},τ)\,dτ
{{< /katex >}}

---

For any state {{< katex >}} \bm{x}(\tau) {{< /katex >}} there exists an optimal input {{< katex >}} \bm{u}^*(τ) {{< /katex >}} for achieving the desired state at time {{< katex >}} T {{< /katex >}}
{{< katex display >}}
\bm{u}^* = \argmin_{\bm{u}} J_{t→T}
{{< /katex >}}
where an objective function achieved with optimal inputs will be referred to as *Bellman function*
{{< katex display >}}
J_{t→T}^* = \min_{\bm{u}} J_{t→T}
{{< /katex >}}

## Bellman's equation

If we are searching for the optimal input at state {{< katex >}} \bm{x}(t) {{< /katex >}}, we may separate the entire trajectory into two segments:

1. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t,t+Δt) {{< /katex >}} with an objective function {{< katex >}} \int_t^{t+Δt} L\,dτ {{< /katex >}}
2. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t+Δt,T⟩ {{< /katex >}} with an objective function {{< katex >}} J_{t+Δt→T} {{< /katex >}}

![trajektory](trajectory.png)

For the defined segments we may write the Bellman function in the form of the so-called *Bellman equation*
{{< katex display >}}
J_{t→T}^* = \min_{\bm{u}} \left( \int_t^{t+Δt} L\,dτ + J_{t+Δt→T} \right)
{{< /katex >}}

## Bellman's differential equation

The term {{< katex >}} J_{t+Δt→T} {{< /katex >}} can be expanded into
{{< katex display >}}
J_{t+Δt→T}
=
J_{t→T}
+
∫_{t}^{t+Δt} \frac{dJ_{t→T}}{dτ} dτ
{{< /katex >}}
whereby its substitution we attain
{{< katex display >}}
J_{t→T}^*
=
\min_{\bm{u}} \left(
	∫_t^{t+Δt} L\,dτ
	+
	J_{t→T}
	+
	∫_{t}^{t+Δt} \frac{dJ_{t→T}}{dτ} dτ
\right)
{{< /katex >}}
As
{{< katex display >}}
J_{t→T}^* = \min_{\bm{u}} \left( J_{t→T} \right)
{{< /katex >}}
the term {{< katex >}} J_{t→T} {{< /katex >}} cancels out with the left side of the equation
{{< katex display >}}
0
=
\min_{\bm{u}} \left(
	∫_t^{t+Δt}
	L +
    \frac{dJ_{t→T}}{dτ}
    \ dτ
\right)
{{< /katex >}}
and we may perform the manipulation
{{< katex display >}}
\frac{dJ_{t→T}}{dτ}
=
\frac{∂J_{t→T}}{∂\bm{x}} \bm{f}
+
\frac{∂J_{t→T}}{∂τ}
{{< /katex >}}
Its substitution results in the equation
{{< katex display >}}
0
=
\min_{\bm{u}} \left(
∫_t^{t+Δt}
L + \frac{∂J_{t→T}}{∂\bm{x}}\bm{f} + \frac{∂J_{t→T}}{∂τ}
\ dτ
\right)
{{< /katex >}}

---

If {{< katex >}} Δt→0 {{< /katex >}}, we may approximate the integral with a Reimann sum and manipulate the resulting equation into the general form (independent from the interval) of the *Bellman's differential equation*
{{< katex display >}}
%\left.
-\frac{∂J^*}{∂τ}
%\right|_{τ=t}
=
%\left.
\min_{\bm{u}} \left(
	L
	+
	\frac{∂J}{∂\bm{x}}	
	\bm{f}
\right)
%\right|_{τ=t}
{{< /katex >}}
evaluated at time {{< katex >}} τ = t {{< /katex >}} from which we may derive the Linear Quadratic Regulator and with modifications, Pontrjagin's minimum principle.