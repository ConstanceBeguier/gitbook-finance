# Les stratégies sur les options

Nous supposons que l'actif sous-jacent de l'option est une action pour simplifier les explications. Les résultats présentés dans cette section sont aussi valables pour d'autres actifs sous-jacents.

## Les spreads

Les spreads comportent une position dans une ou plusierus options d'achat ou position dans une ou plusierus options de ventes.

**Bull spread (spread haussier):**
 - achat d'un call européen $$(K_1, T)$$
 - vente d'un call européen $$(K_2, T)$$
 - $$K_1 < K_2$$

Si $$K_2 < S_T$$ alors les revenus finaux sont $$(S_T - K_1) + (K_2 - S_T) = K_2 - K_1$$

Si $$K_1 < S_T < K_2$$ alors les revenus finaux sont $$(S_T - K_1) + 0 = S_T - K_1$$

Si $$S_T < K_1$$ alors les revenus finaux sont $$0 + 0 = 0$$

Le trader obtient des bénéfices si $$S_T$$ est grand.

![](/images/bull-spread.png)

**Bear spread (spread baissier):**
 - achat d'un put européen $$(K_2, T)$$
 - vente d'un put européen $$(K_1, T)$$
 - $$K_1 < K_2$$

Si $$K_2 < S_T$$ alors les revenus finaux sont $$0 + 0 = 0$$

Si $$K_1 < S_T < K_2$$ alors les revenus finaux sont $$(K_2 - S_T) + 0 = K_2 - S_T$$

Si $$S_T < K_1$$ alors les revenus finaux sont $$(K_2 - S_T) + (S_T - K_1) = K_2 - K_1$$

Le trader obtient des bénéfices si $$S_T$$ est petit.

![](/images/bear-spread.png)

**Butterfly spread:**
 - achat d'un call européen $$(K_1, T)$$
 - achat d'un call européen $$(K_3, T)$$
 - vente de deux calls européens $$(K_2, T)$$
 - $$K_1 < K_2 < K_3$$

Si $$K_3 < S_T$$ alors les revenus finaux sont $$(S_T - K_1) + (S_T - K_3) +2(K_2 -S_T) = 2K_2 - K_1 - K_3$$

Si $$K_2 < S_T < K_3$$ alors les revenus finaux sont $$(S_T - K_1) + 0 + 2(K_2 -S_T) = 2K_2 - K_1 - S_T$$

Si $$K_1 < S_T < K_2$$ alors les revenus finaux sont $$(S_T - K_1) + 0 + 0 = S_T - K_1$$

Si $$S_T < K_1$$ alors les revenus finaux sont $$0 + 0 + 0 = 0$$

Le trader obtient des bénéfices si $$S_T$$ est proche de $$K_2$$.

![](/images/butterfly-spread.png)

## Les combinaisons (straddles, strips, straps, strangles)

Les combinaisons comportent une position à la fois dans des options d'achat et des options de vente.

**Straddle:**
 - achat d'un call européen $$(K, T)$$
 - achat d'un put européen $$(K, T)$$

Si $$K < S_T$$ alors les revenus finaux sont $$(S_T - K) + 0 = S_T - K$$

Si $$S_T < K$$ alors les revenus finaux sont $$0 + (K-S_T) = K - S_T$$

Le trader obtient des bénéfices si $$S_T$$ est loin de $$K$$.

![](/images/straddle.png)

Deux alternatives aux straddles prennent en compte le fait que le trader estime qu'il est plus probable que l'action soit haussière ou baissière (en plus du fait qu'il parie sur une forte variation de l'action).

Dans un **strip** (un call et deux puts), le trader parie sur une forte variation du prix de l'action avec une probabilité plus importante pour la baisse que la hausse.


Dans un **strap** (deux calls et un put), le trader parie sur une forte variation du prix de l'action avec une probabilité plus importante pour la hausse que la baisse.

![](/images/strip-strap.png)

**Strangle:**
 - achat d'un call européen $$(K_2, T)$$
 - achat d'un put européen $$(K_1, T)$$
 - $$K_1 < K_2$$

Si $$K_2 < S_T$$ alors les revenus finaux sont $$(S_T - K_2) + 0 = S_T - K_2$$

Si $$K_1 < S_T < K_2$$ alors les revenus finaux sont $$0 + 0 = 0$$

Si $$S_T < K_1$$ alors les revenus finaux sont $$0 + (K_1 - S_T) = K_1 - S_T$$

Le trader obtient des bénéfices si $$S_T$$ est largement inférieur à $$K_1$$ ou largement supérieur à $$K_2$$.

![](/images/strangle.png)

