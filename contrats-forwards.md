# Les contrats forwards

## Introduction

Un contrat forward a les caractéristiques suivantes:
 - engagement ferme
 - d'achat (position longue) ou de vente (position courte) d'une certaine quantité (appelée quotité) d'un actif (appelé sous-jacent)
 - à une date future donnée $$T$$
 - à un prix convenu $$K$$
 - sur un marché de gré à gré (OTC).

**Objectifs:**
 - se protéger contre les variations du taux de change en fixant dès maintenant un taux de change futur

**Vocabulaire:**
 - $$S_T$$ est le prix au comptant (spot) de l'actif à la date $$T$$
 - $$K$$ est le prix de livraison de l'actif (prix forward ou strike)
 - le flux du contrat forward (payoff) est
   - $$S_T - K$$ pour une position longue (achat)
   - $$K - S_T$$ pour une position courte (vente)

Ce flux représente le gain ou la perte du trader sur ce contrat.

## Les stratégies de couverture

**Couverture courte (short hedge):** le hedger détient l'actif sous-jacent au contrat (ou va le recevoir) et prévoit de le vendre dans un futur proche. Il doit donc prendre une position courte pour se protéger des risques de variation de prix de ce sous-jacent. 

**Couverture longue (long hedger):** symétrique de la position courte. Elle sert à se protéger des risques de variation de prix du sous-jacent lorsque que le hedger veut acheter l'actif dans le futur.

Malheureusement, la courverture n'est pas aussi simple car:
 - l'actif à couvrir n'est pas forcément le même que le sous-jacent du contrat futur. Il faut alors prendre en compte la corrélation entre l'actif à couvrir et le sous-jacent du contrat futur. Cela est appelée la **couvertue croisée**.
 - la date de livraison de l'actif à couvrir n'appartient pas forcément aux échéances des contrats futus. Il faut alors prendre un contrat futur avec une échéance plus éloignée et dénouer sa position lors de la livraison. Il faut donc prendre en compte la différence des prix des contrats futurs entre les contrats lors de la couverture et les contrats lors de la livraison afin de calculer les gain/pertes sur cette couverture.
 - la durée de la couverture souhaitée peut être plus grande que la maturité des contrats disponibles. Le hedger doit alors faire glisser sa couverture d'une échéance à l'autre en prenant des positions successives sur des contrats à maturité plus courte.

## Les Forward Rate Agreement FRA

Le **FRA** est un contrat à terme de gré à gré par lequel le vendeur du FRA garantit à l'acheteur, au terme d'une période donnée (la période de couverture), un taux négocié (le taux garanti) pour un emprunt d'un montant et d'une durée négociés.

Au terme de la période de couverture, le vendeur verse à l'acheteur le différentiel d'intérêts entre le taux de marché (souvent le taux LIBOR) et le taux négocié, appliqués au montant et à la durée de l'emprunt sous-jacent. Si cette différence est négative, c’est-à-dire que les taux de marché ont baissé, c’est l'acheteur du FRA qui paie la différence au vendeur.

On voit que l'opérateur qui cherche à se couvrir contre une hausse des taux (position emprunteuse à terme) se portera acheteur d'un FRA. A l'inverse celui qui cherche à se couvrir contre une baisse de taux (position prêteuse) se portera vendeur.

Exemple: négociation d'un FRA d'un montant notionnel 1MEURO pour une période garantie de 3 mois, au taux garanti de 5%. A l'échéance, le taux à 3 mois du marché vaut 5.5%. Le vendeur verse à l'acheteur le différentiel d'intérêts, soit: $$1 000 000 \cdot (5.5% – 5%) \cdot 90 / 360 = 1250$$ EURO L'acheteur emprunte sur le marché à 5.5% mais la différence payée par le vendeur lui assure les conditions souhaitées, soit 5%.

