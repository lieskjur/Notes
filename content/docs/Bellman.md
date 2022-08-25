---
title: Bellmanův princip optimality
draft: true
---

# Bellmanův princip optimality

Pro systému se stavovou zpětnou vazbou ve tvaru {{< katex >}} \bm{\dot{x}}(τ) = \bm{f}(\bm{x}(τ),\bm{u}(\bm{x}(τ)),τ) {{< /katex >}} můžeme definovat pro trajektorii ze stavu {{< katex >}} \bm{x}(t_0) = \bm{x}_0 {{< /katex >}} do stavu {{< katex >}} \bm{x}(t_1) {{< /katex >}} kritérium optimality
{{< katex display >}}
J = ∫_{t_0}^{t_1} L(\bm{x}(τ),\bm{u}(\bm{x}(τ)),τ)\,dτ
{{< /katex >}}
V libovolném čase {{< katex >}} t {{< /katex >}} pak můžeme určit optimální řízení ze stavu {{< katex >}} \bm{x}(t) {{< /katex >}} do koncového stavu {{< katex >}} \bm{x}(t_1) {{< /katex >}}
{{< katex display >}}
\bm{u}^*(\bm{x}(τ)) = \argmin_{\bm{u}(\bm{x}(τ))} ∫_{t}^{t_1} L(\bm{x}(τ),\bm{u}(\bm{x}(τ)),τ)\,dτ
{{< /katex >}}
*Bellmanovou funkcí* budeme nazýváme kritérium optimality z bodu {{< katex >}} \bm{x}(t) {{< /katex >}} do cíle, při optimálním řízení
{{< katex display >}}
J^*(\bm{x}(t),t) = \min_{\bm{u}(\bm{x}(τ))} ∫_{t}^{t_1} L(\bm{x}(τ),\bm{u}(\bm{x}(τ)),τ)\,dτ
{{< /katex >}}

---

Pokud hledáme optimální řízení v bodě {{< katex >}} \bm{x}(t) {{< /katex >}} můžeme rozdělit celou trajektorii na tři úseky:

2. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t_0,t) {{< /katex >}} který byl už absolvován (byť neoptimálně)
2. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t,t+Δt) {{< /katex >}} s kritériem optimality {{< katex >}} \int_t^{t+Δt} L(\bm{x}(τ),\bm{u}(\bm{x}(τ)),τ) + \,dτ {{< /katex >}}, pro který hledáme optimální řízení
3. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t+Δt,t_1⟩ {{< /katex >}} na kterém předpokládáme optimální řízení a tudíž kritérium optimality {{< katex >}} J^*(\bm{x}(t+Δt),t+Δt) {{< /katex >}}

![trajektorie](/Trajektorie.png)

S definovanými úseky můžeme Bellmanovu funkci rozepsat do tvaru tzv. *Bellmanovy rovnice*
{{< katex display >}}
J^*(\bm{x}(t),t) = \min_{\bm{u}(\bm{x}(τ))} \left( \int_t^{t+Δt} L(\bm{x}(τ),\bm{u}(\bm{x}(τ)),τ)\,dτ + J^*(\bm{x}(t+Δt),t+Δt) \right)
{{< /katex >}}
kde
{{< katex display >}}
J^*(\bm{x}(t+Δt),t+Δt)
=
J^*(\bm{x}(t),t)
+
∫_{t}^{t+Δt} \frac{dJ^*(\bm{x}(t),t)}{dτ} dτ
{{< /katex >}}
Dosazením pak získáme
{{< katex display >}}
J^*(\bm{x}(t),t)
=
\min_{\bm{u}(\bm{x}(τ))} \left(
	∫_t^{t+Δt} L(\bm{x}(τ),\bm{u}(\bm{x}(τ)),τ)\,dτ
	+
	J^*(\bm{x}(t),t)
	+
	∫_{t}^{t+Δt} \frac{dJ^*(\bm{x}(t),t)}{dτ} dτ
\right)
{{< /katex >}}

---
Člen {{< katex >}} J^*(\bm{x}(t),t) {{< /katex >}} můžeme vykrátit, vzhledem k tomu že předpokládá optimální řízení
{{< katex display >}}
0
=
\min_{\bm{u}(\bm{x}(τ))} \left(
	∫_t^{t+Δt} L(\bm{x}(τ),\bm{u}(\bm{x}(τ)),τ)
	+
    \frac{dJ^*(\bm{x}(t),t)}{dτ} \ dτ
\right)
{{< /katex >}}
a provést úpravu
{{< katex display >}}
\frac{dJ^*(\bm{x}(t),t)}{dτ}
=
\frac{∂J^*(\bm{x}(t),t)}{∂\bm{x}(τ)} \bm{f}(\bm{x}(τ),\bm{u}^*(\bm{x}(τ)),τ)
+
\frac{∂J^*(\bm{x}(t),t)}{∂τ}
{{< /katex >}}
Výsledkem jejího dosazení je rovnice [^1]
{{< katex display >}}
0
=
\min_{\bm{u}}
∫_t^{t+Δt}
L(\bm{x},\bm{u},τ) + \frac{∂J^*(\bm{x}(t),t)}{∂\bm{x}}\bm{f}(\bm{x},\bm{u},τ) + \frac{∂J^*(\bm{x}(t),t)}{∂τ}
\ dτ
{{< /katex >}}
pro kterou, aby byla splněna s {{< katex >}} Δt→0 {{< /katex >}} musí platit tzv *Bellmanova diferenciální rovnice*
{{< katex display >}}
\left. -\frac{∂J^*(\bm{x}(t),t)}{∂τ} \right|_{τ=t}
=
\min_{\bm{u}(\bm{x}(t))} \left(
	L(\bm{x}(t),\bm{u}(t),t)
	+
	\left.
		\frac{∂J^*(\bm{x}(t),t)}{∂\bm{x}(τ)}
	\right|_{τ=t}
	\bm{f}(\bm{x}(t),\bm{u}(t),t)
\right)
{{< /katex >}}
kde je integrál approximován pomocí Reimannova součtu a {{< katex >}} Δt {{< /katex >}} vykráceno [^2].

Z této rovnice lze přímo odvodit [LQR](LQR.md) a s úpravou [Pontrjaginův princip minima](Pontrjaginův princip minima.md).

[^1]: zde pro přehlednost a úsporu místa, vynecháváme argumenty funkcí {{< katex >}} \bm{x}(τ) {{< /katex >}} a {{< katex >}} \bm{u}(\bm{x}(τ)) {{< /katex >}}
[^2]: člen {{< katex >}} \frac{∂J^*(\bm{x}(t),t)}{∂τ} {{< /katex >}} můžeme vyjmout z minima a přesunout na levou stranu rovince, vzhledem k tomu, že předpokládá optimální řízení.