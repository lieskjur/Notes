---
title: Bellmanův princip optimality
draft: true
---

# Bellmanův princip optimality

Pro systému se stavovou zpětnou vazbou ve tvaru
{{< katex display >}}
\frac{d\bm{x}}{dτ} = \bm{f}(\bm{x},\bm{u},τ)
{{< /katex >}}
kde {{< katex >}} \bm{x} = \bm{x}(τ) \,,\; \bm{u} = \bm{u}(\bm{x}(τ)) {{< /katex >}} <!-- dále jen {{< katex >}} \bm{\dot{x}} = \bm{f}(\bm{x},\bm{u},τ) {{< /katex >}} -->
můžeme definovat pro trajektorii ze stavu {{< katex >}} \bm{x}(t_0) = \bm{x}_0 {{< /katex >}} do stavu {{< katex >}} \bm{x}(t_1) {{< /katex >}} kritérium optimality
{{< katex display >}}
J = ∫_{t_0}^{t_1} L(\bm{x},\bm{u},τ)\,dτ
{{< /katex >}}
V libovolném čase {{< katex >}} t {{< /katex >}} pak můžeme určit optimální řízení {{< katex >}} \bm{u}^* = \bm{u}^*(τ) {{< /katex >}} ze stavu {{< katex >}} \bm{x}(t)=\bm{x}_t {{< /katex >}} do koncového stavu {{< katex >}} \bm{x}(t_1) {{< /katex >}}
{{< katex display >}}
\bm{u}^* = \argmin_{\bm{u}} ∫_{t}^{t_1} L(\bm{x},\bm{u},τ)\,dτ
{{< /katex >}}
*Bellmanovou funkcí* budeme nazýváme kritérium optimality ze stavu {{< katex >}} \bm{x}_t {{< /katex >}} v čase {{< katex >}} t {{< /katex >}} do cíle, při optimálním řízení
{{< katex display >}}
J^*(\bm{x}_t,t) = \min_{\bm{u}} ∫_{t}^{t_1} L(\bm{x},\bm{u},τ)\,dτ
{{< /katex >}}

---

Pokud hledáme optimální řízení v bodě {{< katex >}} \bm{x}(t) = \bm{x}_t {{< /katex >}} můžeme rozdělit celou trajektorii na tři úseky:

2. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t_0,t) {{< /katex >}} který byl už absolvován (byť neoptimálně)
2. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t,t+Δt) {{< /katex >}} s kritériem optimality {{< katex >}} \int_t^{t+Δt} L(\bm{x},\bm{u},τ)\,dτ {{< /katex >}}, pro který hledáme optimální řízení
3. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t+Δt,t_1⟩ {{< /katex >}} na kterém předpokládáme optimální řízení a tudíž kritérium optimality {{< katex >}} J^*(\bm{x}_{t+Δt},t+Δt) {{< /katex >}}

![trajektorie](/Trajektorie.png)

S definovanými úseky můžeme Bellmanovu funkci rozepsat do tvaru tzv. *Bellmanovy rovnice*
{{< katex display >}}
J^*(\bm{x}_t,t) = \min_{\bm{u}} \left( \int_t^{t+Δt} L(\bm{x},\bm{u},τ)\,dτ + J^*(\bm{x}_{t+Δt},t+Δt) \right)
{{< /katex >}}
kde <!-- {{< katex >}} \bm{x}_{t+Δt} = \bm{x}(t+Δt) {{< /katex >}} a -->
{{< katex display >}}
J^*(\bm{x}_{t+Δt},t+Δt)
=
J^*(\bm{x}_t,t)
+
∫_{t}^{t+Δt} \frac{dJ^*(\bm{x}_t,t)}{dτ} dτ
{{< /katex >}}
Dosazením pak získáme
{{< katex display >}}
J^*(\bm{x}_t,t)
=
\min_{\bm{u}} \left(
	∫_t^{t+Δt} L(\bm{x},\bm{u},τ)\,dτ
	+
	J^*(\bm{x}_t,t)
	+
	∫_{t}^{t+Δt} \frac{dJ^*(\bm{x}_t,t)}{dτ} dτ
\right)
{{< /katex >}}

---
Člen {{< katex >}} J^*(\bm{x}_t,t) {{< /katex >}} můžeme vykrátit, vzhledem k tomu že předpokládá optimální řízení
{{< katex display >}}
0
=
\min_{\bm{u}} \left(
	∫_t^{t+Δt} L(\bm{x},\bm{u},τ)
	+
    \frac{dJ^*(\bm{x}_t,t)}{dτ} \ dτ
\right)
{{< /katex >}}
a provést úpravu
{{< katex display >}}
\frac{dJ^*(\bm{x}_t,t)}{dτ}
=
\frac{∂J^*(\bm{x}_t,t)}{∂\bm{x}(τ)} \bm{f}(\bm{x},\bm{u}^*,τ)
+
\frac{∂J^*(\bm{x}_t,t)}{∂τ}
{{< /katex >}}
Výsledkem jejího dosazení je rovnice
{{< katex display >}}
0
=
\min_{\bm{u}}
∫_t^{t+Δt}
L(\bm{x},\bm{u},τ) + \frac{∂J^*(\bm{x}_t,t)}{∂\bm{x}}\bm{f}(\bm{x},\bm{u},τ) + \frac{∂J^*(\bm{x}_t,t)}{∂τ}
\ dτ
{{< /katex >}}
pro kterou, aby byla splněna s {{< katex >}} Δt→0 {{< /katex >}} musí platit tzv *Bellmanova diferenciální rovnice*
{{< katex display >}}
\left. -\frac{∂J^*(\bm{x}_t,t)}{∂τ} \right|_{τ=t}
=
\left.
\min_{\bm{u}} \left(
	L(\bm{x},\bm{u},τ)
	+
	\frac{∂J^*(\bm{x}_t,t)}{∂\bm{x}}	
	\bm{f}(\bm{x},\bm{u},τ)
\right)
\right|_{τ=t}
{{< /katex >}}
kde je integrál approximován pomocí Reimannova součtu, {{< katex >}} Δt {{< /katex >}} vykráceno a člen {{< katex >}} \frac{∂J^*(\bm{x}_t,t)}{∂τ} {{< /katex >}} vyjmut z minima a přesunout na levou stranu rovince, vzhledem k tomu, že předpokládá optimální řízení.

Z této rovnice lze přímo odvodit [LQR]({{< ref "LQR.md" >}}) a s úpravou Pontrjaginův princip minima.