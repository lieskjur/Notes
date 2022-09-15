---
title: Bellmanův princip optimality
draft: false
---

# Bellmanův princip optimality

Pro dynamický systém ve tvaru
{{< k display >}}
\dot{\bm{x}} = \bm{f}(\bm{x},\bm{u},τ)
{{< /k >}}
kde {{<k>}} \bm{x}(τ) {{</k>}} jsou stavy systému a {{<k>}} \bm{u} {{</k>}} vstupy, můžeme definovat pro trajektorii ze stavu {{<k>}} \bm{x}(t) {{</k>}} do stavu {{<k>}} \bm{x}(T) {{</k>}} kritérium optimality
{{< k display >}}
J_{⟨t,T⟩}(\bm{u},τ) = ∫_{t}^{T} L(\bm{x},\bm{u},τ)\,dτ
{{< /k >}}
Také můzeme definovat tzv. *cenou do cíle* {{<k>}} J^*_{⟨t,T⟩}(τ) {{</k>}} pro zpětnovazební řízení {{<k>}} \bm{u}(\bm{x}(τ)) {{</k>}}.

---

Pak musí existovat minimalizující zpětnovazební řízení {{<k>}} \bm{u}_\text{opt} {{</k>}}
{{< k display >}}
\bm{u}_\text{opt} = \argmin_{\bm{u}} J^*_{⟨t,T⟩}
{{< /k >}}
které budeme nazývat optimálním. *Bellmanovou funkcí* nazýváme cenu do cíle při optimálním řízení
{{< k display >}}
V_{⟨t,T⟩} = \min_{\bm{u}} J^*_{⟨t,T⟩}
{{< /k >}}

## Bellmanova rovnice

Pokud hledáme optimální řízení ve stavu {{<k>}} \bm{x}(t) {{</k>}}, můžeme rozdělit celou trajektorii na dva úseky:

1. {{<k>}} \bm{x}(τ) \,,\; τ ∈ ⟨t,t+Δt) {{</k>}} s kritériem optimality {{<k>}} \int_t^{t+Δt} L\,dτ {{</k>}}
2. {{<k>}} \bm{x}(τ) \,,\; τ ∈ ⟨t+Δt,T⟩ {{</k>}} s cenou do cíle {{<k>}} J^*_{⟨t+Δt,T⟩} {{</k>}}

![trajektorie](trajektorie.png)

S definovanými úseky můžeme Bellmanovu funkci rozepsat do tvaru tzv. *Bellmanovy rovnice*
{{< k display >}}
V_{⟨t,T⟩} = \min_{\bm{u}} \left( \int_t^{t+Δt} L\,dτ + J^*_{⟨t+Δt,T⟩} \right)
{{< /k >}}

## Bellmanova diferenciání rovnice

Člen {{<k>}} J_{⟨t+Δt,T⟩} {{</k>}} můžeme rozepsat jako
{{< k display >}}
J^*_{⟨t+Δt,T⟩}
=
J^*_{⟨t,T⟩}
+
∫_{t}^{t+Δt} \frac{dJ^*}{dτ} dτ
{{< /k >}}
kdy dosazením získáme
{{< k display >}}
V_{⟨t,T⟩}
=
\min_{\bm{u}} \left(
	∫_t^{t+Δt} L\,dτ
	+
	J^*_{⟨t,T⟩}
	+
	∫_{t}^{t+Δt} \frac{dJ^*}{dτ} dτ
\right)
{{< /k >}}
Jelikož platí
{{< k display >}}
V_{⟨t,T⟩} = \min_{\bm{u}} \left( J^*_{⟨t,T⟩} \right)
{{< /k >}}
člen {{<k>}} J^*_{⟨t,T⟩} {{</k>}} můžeme vykrátit s levou stranou a dále provést úpravu
{{< k display >}}
\frac{dJ^*}{dτ}
=
\frac{∂J^*}{∂\bm{x}} \bm{f}
+
\frac{∂J^*}{∂τ}
{{< /k >}}
Výsledkem je po-té rovnice
{{< k display >}}
0
=
\min_{\bm{u}} \left(
∫_t^{t+Δt}
\left(
L + \frac{∂J^*}{∂\bm{x}}\bm{f} + \frac{∂J^*}{∂τ}
\right)
\ dτ
\right)
{{< /k >}}

---

Pokud {{<k>}} Δt→0 {{</k>}}, můžeme aproximovat integrál pomocí Reimannova součtu a výslednou rovnici upravit do tvaru tzv. *Bellmanovy diferenciální rovnice*
{{< k display >}}
%\left.
-\frac{∂J^*}{∂τ}
%\right|_{τ=t}
=
%\left.
\min_{\bm{u}} \left(
	L
	+
	\frac{∂J^*}{∂\bm{x}}	
	\bm{f}
\right)
%\right|_{τ=t}
{{< /k >}}
vyjádřené v čase {{<k>}} τ = t {{</k>}}, kde předpokládáme, že člen {{<k>}} \frac{∂J^*}{∂τ} {{</k>}} je nezávislý na {{<k>}} \bm{u} {{</k>}}. Z ní lze přímo odvodit [LQR]({{< ref "LQR.md" >}}) a s úpravou, [Pontrjaginův princip minima]({{< ref "Pontrjagin.md" >}}).