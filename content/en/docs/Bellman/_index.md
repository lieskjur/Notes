---
title: Bellman's principle of optimality
draft: true
---

# Bellman's principle of optimality

For a dynamic system with state feedback in the form
{{< k display >}}
\dot{\bm{x}} = \bm{f}(\bm{x},\bm{u},τ) \;,\quad \bm{u} = \bm{u}(\bm{x})
{{< /k >}}
where {{<k>}} \bm{x}(τ) {{</k>}} are the system's states and {{<k>}} \bm{u}(\bm{x}) {{</k>}} a function of state feedback inputs, we may define for the trajectory from state {{<k>}} \bm{x}(t) {{</k>}} to state {{<k>}} \bm{x}(T) {{</k>}} an objective function
{{< k display >}}
J_{⟨t,T⟩} = ∫_{t}^{T} L(\bm{x},\bm{u},τ)\,dτ
{{< /k >}}
where {{<k>}} L(\bm{x},\bm{u},τ) {{</k>}} is the additive cost

---

For any state {{<k>}} \bm{x}(\tau) {{</k>}} there exists an optimal input {{<k>}} \bm{u}_\text{opt}(τ) {{</k>}} for achieving the desired state at time {{<k>}} T {{</k>}}
{{< k display >}}
\bm{u}_\text{opt} = \argmin_{\bm{u}} J_{⟨t,T⟩}
{{< /k >}}
where an objective function achieved with optimal inputs will be referred to as *Bellman function*
{{< k display >}}
J_{⟨t,T⟩}^* = \min_{\bm{u}} J_{⟨t,T⟩}
{{< /k >}}

## Bellman's equation

If we are searching for the optimal input at state {{<k>}} \bm{x}(t) {{</k>}}, we may separate the entire trajectory into two segments:

1. {{<k>}} \bm{x}(τ) \,,\; τ ∈ ⟨t,t+Δt) {{</k>}} with an objective function {{<k>}} \int_t^{t+Δt} L\,dτ {{</k>}}
2. {{<k>}} \bm{x}(τ) \,,\; τ ∈ ⟨t+Δt,T⟩ {{</k>}} with an objective function {{<k>}} J_{⟨t+Δt,T⟩} {{</k>}}

![trajektory](trajectory.png)

For the defined segments we may write the Bellman function in the form of the so-called *Bellman equation*
{{< k display >}}
J_{⟨t,T⟩}^* = \min_{\bm{u}} \left( \int_t^{t+Δt} L\,dτ + J_{⟨t+Δt,T⟩} \right)
{{< /k >}}

## Bellman's differential equation

The term {{<k>}} J_{⟨t+Δt,T⟩} {{</k>}} can be expanded into
{{< k display >}}
J_{⟨t+Δt,T⟩}
=
J_{⟨t,T⟩}
+
∫_{t}^{t+Δt} \frac{dJ}{dτ} dτ
{{< /k >}}
whereby its substitution we attain
{{< k display >}}
J_{⟨t,T⟩}^*
=
\min_{\bm{u}} \left(
	∫_t^{t+Δt} L\,dτ
	+
	J_{⟨t,T⟩}
	+
	∫_{t}^{t+Δt} \frac{dJ}{dτ} dτ
\right)
{{< /k >}}
As
{{< k display >}}
J_{⟨t,T⟩}^* = \min_{\bm{u}} \left( J_{⟨t,T⟩} \right)
{{< /k >}}
the term {{<k>}} J_{⟨t,T⟩} {{</k>}} cancels out with the left side of the equation
{{< k display >}}
0
=
\min_{\bm{u}} \left(
	∫_t^{t+Δt}
	L +
    \frac{dJ}{dτ}
    \ dτ
\right)
{{< /k >}}
and we may perform the manipulation
{{< k display >}}
\frac{dJ}{dτ}
=
\frac{∂J}{∂\bm{x}} \bm{f}
+
\frac{∂J}{∂τ}
{{< /k >}}
Its substitution results in the equation
{{< k display >}}
0
=
\min_{\bm{u}} \left(
∫_t^{t+Δt}
L + \frac{∂J}{∂\bm{x}}\bm{f} + \frac{∂J}{∂τ}
\ dτ
\right)
{{< /k >}}

---

If {{<k>}} Δt→0 {{</k>}}, we may approximate the integral with a Reimann sum and manipulate the resulting equation into the form of the *Bellman's differential equation*
{{< k display >}}
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
{{< /k >}}
evaluated at time {{<k>}} τ = t {{</k>}} from which we may derive the Linear Quadratic Regulator and with modifications, Pontrjagin's minimum principle.