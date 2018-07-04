# Evaluation des contrats forwards

Nous supposons que les opérateurs profitent des opérations d'arbitrage dès qu'elles apparaissent. Cela permet de définir une relation théorique entre prix forward et prix spot.

## Sans flux intermédiaire ni rendement continu

**Notations:**
 - $$t_0$$: date de la transaction
 - $$S_0$$: prix de l'actif à $$t_0$$
 - $$F_0$$: prix du contrat forward à $$t_0$$
 - $$T$$: délai en année entre la date de la transaction $$t_0$$ et la date de la livraison $$t_0+T$$
 - $$r$$: taux sans risque annuel continu d'un emprunt et d'un placement

**Prix d'un contract forward:** $$F_0 = S_0 e^{rT}$$

Si $$F_0 > S_0 e^{rT}$$, un arbitragiste fera les opérations suivantes:
 - emprunt de $$S_0$$ sur une durée $$T$$
 - achat de l'actif à $$t_0$$ au prix $$S_0$$
 - vente d'un contrat forward à $$t_0$$
 - vente de l'actif au prix $$F_0$$ à $$t_0 + T$$
 - remboursement du prêt $$S_0 e^{rT}$$ à $$t_0 + T$$

L'arbitragiste a donc gagné $$F_0 - S_0 e^{rT}$$

Si $$F_0 < S_0 e^{rT}$$, un arbitragiste fera les opérations suivantes:
 - vente de l'actif à $$t_0$$ au prix $$S_0$$
 - placement de $$S_0$$ sur une durée $$T$$ (argent obtenu de la vente de l'actif)
 - achat d'un contrat forward à $$t_0$$
 - achat de l'actif au prix $$F_0$$ à $$t_0 + T$$ (grâce au contrat forward)
 - récupération de l'argent prêté $$S_0 e^{rT}$$ à $$t_0 + T$$

L'arbitragiste a donc gagné $$S_0 e^{rT} - F_0$$

## Avec flux intermédiaire connu (e.g. dividende, coupon)

Nous supposons dans cette section que l'actif du contrat forward paie un flux pendant la durée du contrat. Nous supposons que le flux verse un montant $$V$$ à $$t_0 + T_V$$ avec $$T_V < T$$.

**Nouveau prix du contrat forward:** $$F_0 = (S_0 - V e^{-rT_V}) e^{rT}$$

$$I = V e^{-rT_V}$$ est appelée la **valeur actuelle du flux**

Si $$F_0 > (S_0 - V e^{-rT_V}) e^{rT}$$, un arbitragiste fera les opérations suivantes:
 - à $$t_0$$
   - emprunts d'un montant total de $$S_0$$
     - emprunt $$E_1$$ d'un montant de $$Ve^{-rT_V}$$ sur une durée $$T_V$$
     - emprunt $$E_2$$ d'un montant de $$S_0 - Ve^{-rT_V}$$ sur une durée $$T$$
   - achat de l'actif au prix $$S_0$$
   - achat d'un contrat forward
 - à $$t_0 + T_V$$
   - récupération du flux $$V$$
   - remboursement de l'emprunt $$E_1$$ grâce au flux $$V$$
     - montant à rembourser: $$V e^{-rT_V} e^{rT_V} = V$$
 - à $$t_0 + T$$
   - dénouement du contrat: vente de l'actif au prix $$F_0$$
   - remboursement de l'emprunt $$E_2$$
     - montant à rembourser: $$(S_0 - Ve^{-rT_V})e^{rT}$$

L'arbitragiste a donc gagné $$F_0 - (S_0 - Ve^{-rT_V})e^{rT}$$.

Si $$F_0 < (S_0 - V e^{-rT_V}) e^{rT}$$, un arbitragiste fera les opérations suivantes:
 - à $$t_0$$
   - placements d'un montant total de $$S_0$$
     - placement $$P_1$$ d'un montant de $$Ve^{-rT_V}$$ sur une durée $$T_V$$
     - placement $$P_2$$ d'un montant de $$S_0 - Ve^{-rT_V}$$ sur une durée $$T$$
   - vente de l'actif au prix $$S_0$$
   - vente d'un contrat forward
 - à $$t_0 + T_V$$
   - paiement du flux $$V$$
   - encaissement du placement $$P_1$$
     - montant à encaisser: $$V e^{-rT_V} e^{rT_V} = V$$
 - à $$t_0 + T$$
   - dénouement du contrat: achat de l'actif au prix $$F_0$$
   - encaissement du placement $$P_2$$
     - montant à encaisser: $$(S_0 - Ve^{-rT_V})e^{rT}$$

L'arbitragiste a donc gagné $$(S_0 - Ve^{-rT_V})e^{rT} - F_0$$.

## Avec rendement continu connu

Nous supposons dans cette section que l'actif du contrat forward paie un rendement continu au taux annuel $$q$$.

**Nouveau prix du contrat forward:** $$F_0 = S_0 e^{(r-q)T}$$

## Contrat forward sur devises

**Notations:**
 - $$S_0$$: prix en dollairs US d'une unité de devise étrangère à $$t_0$$
 - $$S_0$$: prix du contrat forward d'une durée $$T$$ à $$t_0$$
 - $$r$$: taux sans risque en dollars US
 - $$r_f$$: taux sans risque du pays étranger

**Prix d'un contract forward:** $$F_0 = S_0 e^{(r-r_f)T}$$

Si l'arbitragiste détient 1000 unités d'une devise étrangère qu'il aimerait convertir en dollars US à la date $$t_0 + T$$.
 - Première méthode:
   - à $$t_0$$
     - placer les 1000 unités dans la devise étrangère pour une durée $$T$$
     - prendre une position courte sur un contrat forward
   - à $$t_0 + T$$
     - encaissement du placement: $$1000 \cdot e^{r_f T}$$
     - convertir l'argent du placement à l'aide du contrat forward: $$1000 \cdot e^{r_f T} F_0$$ dollars US
   - l'arbitragiste obtient donc $$1000 \cdot e^{r_f T} F_0$$ dollars US 
 - Deuxième méthode:
   - à $$t_0$$
     - convertir les 1000 unités en dollars US: $$1000 \cdot S_0$$ dollars US
     - placer les $$1000 \cdot S_0$$ dollars US pour une durée $$T$$
   - à $$t_0 + T$$
     - encaissement du placement: $$1000 \cdot S_0 \cdot e^{rT}$$ dollars US
   - l'arbitragiste obtient donc $$1000 \cdot S_0 \cdot e^{rT}$$ dollars US 

En l'absence d'arbitrage, les deux méthodes doivent nous donner la même somme: $$1000 \cdot F_0 e^{r_f T} = 1000 \cdot S_0  e^{rT}$$. Cela nous donne bien le prix du contrat forward $$F_0 = S_0 e^{(r - r_f)T}$$.

Par conséquent, si le taux étranger est plus élevé que le taux domestique ($$r_f > r$$), alors $$F_0 < S_0$$ et $$F_0$$ est d'autant plus faible que la maturité est éloignée.

Le prix d'un contrat forward sur devise est similaire au prix d'un contrat forward avec rendement continu. Cela est normal car une devise peut être vue comme un actif dont le rendement est égal à son taux sans risque.

