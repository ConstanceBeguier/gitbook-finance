# Les options

Une **option** a les caractéristiques suivantes:
 - engagement non ferme donnant le droit à son détenteur
 - d'acheter (**call**) ou de vendre (**put**) une certaine quantité (appelé **quotité**) d'un actif (appelé **sous-jacent**)
 - à une date future $$T$$ (**option européenne**) ou jusqu'à une date future $$T$$ (**option américaine**)
 - à un prix d'exercice convenu $$K$$ (**strike**)

La majorité des options sont des options américaines.
Le prix d'une option pour une action (**premium**) est le prix à payer pour détenir cette option.

Il y a donc quatre positions différentes possibles:
 - l'achat d'un call
 - la vente d'un call
 - l'achat d'un put
 - la vente d'un put.

Les acheteurs (d'un call ou d'un put) ont une **position longue**.
Alors que les vendeurs d'un call ou d'un put) ont une **position courte**.

Une option est **dans la monnaie** si l'acheteur de l'option a intérêt à exercer son option (pour un call, $$S_T > K$$ et pour un put, $$S_T < K$$). Une option est **à la monnaie** si $$S_T = K$$. Une option est **en dehors de la monnaie** si l'acheteur de l'option n'a pas intérêt à l'exercer (pour un call, $$S_T < K$$ et pour un put, $$S_T > K$$).

Une **classe d'options** contient l'ensemble des options de même type (call ou put) sur le même sous-jacent (par exemple, les calls sur IBM).
Une **série d'options** contient l'ensemble des options d'une même classe ayant le même prix d'exercice et la même échéance (par exemple, les calls IBM-200-octobre 2018). 

Le contrat d'une option est souvent ajustée en cas d'opérations sur titres (e.g. split).

Pour dénouer une option, il suffit de prendre la position symétrique. Par exemple, pour dénouer l'achat d'un call, il suffit de vendre un call ayant les mêmes caractéristiques.

## Profit et payoff d'une option

**Notations:**
 - $$K$$: prix d'exercice de l'option (strike)
 - $$S_T$$: prix du sous-jacent à l'échéance de l'option $$T$$
 - $$P$$: prix payé pour acquérir l'option (premium)

**Achat d'un call:**

Si à $$T$$, $$K < S_T$$ alors l'acheteur de l'option va exercer son option pour acheter le sous-jacent au prix $$K$$ et va le revendre au prix du marché $$S_T$$. Par conséquent, il va gagner $$K-S_T -P$$.

Si à $$T$$, $$K > S_T$$, alors l'acheteur de l'option ne va pas exercer son option et il va alors perder uniquement le prix d'achat de l'option $$P$$.

Par conséquent, l'acheteur d'un call gagne $$max(S_T - K, 0) -P$$.

Par un raisonnement similaire sur les autres positions nous obtenons les gains suivants:
 - **achat d'un call**: $$max(S_T - K, 0) - P$$
 - **achat d'un put**: $$max(K - S_T, 0) - P$$
 - **vente d'un call**: $$P - max(S_T - K, 0) = P + min(K - S_T, 0)$$
 - **achat d'un put**: $$P - max(K - S_T, 0) = P + min(S_T - K, 0)$$

Les profits précédent sont pour un unique actif sous-jacent. Il faut donc multiplier le résultat par la quotité pour obtenir le profit sur l'option totale.

Le **payoff** d'une option correspond aux gains/pertes réalisés à l'échéance de l'option. Par conséquent, nous avons les payoffs suivants:
 - **achat d'un call**: $$max(S_T - K, 0)$$
 - **achat d'un put**: $$max(K - S_T, 0)$$
 - **vente d'un call**: $$- max(S_T - K, 0) = min(K - S_T, 0)$$
 - **achat d'un put**: $$- max(K - S_T, 0) = min(S_T - K, 0)$$

## Les options sur futures

Les **options sur futures** sont des options donnant le droit d'acheter ou de vendre une position sur un future à un certain prix à une certaine date future. Ces options sont le plus souvent américaines.

Lors de l'exercice d'un call (resp put), le détenteur prend une position longue (resp courte) sur le future et reçoit la différence entre le prix future et le prix d'exercice (resp la différence entre le prix d'exercice et le prix future). Le payoff d'un call européen sur future est donc $$max(F_T - K, 0)$$ et le payoff d'un put européen sur future est $$max(K-F_T, 0)$$ avec $$F_T$$ le prix du future à l'échéance de l'option.

Les options sur futures sont très populaires car les futures sont plus liquides que les actifs.

## Les stock-options

Les **stock-options** sont des options d'achat sur les actions d'une société accordées par cette société à ses employés. Il y a tout d'abord une période d'acquisition des droits pendant laquelle l'option ne peut pas être exercée (si un cadre part de l'entreprise pendant cette période, le plus souvent il perd cette option). Quand un employé exerce une stock-option, l'entreprise émet de **nouvelles actions** et les lui vend au prix d'exercice. Le plus souvent le prix d'exercice d'une stock-option est égal au prix de l'action au moment de l'attribution des stock-options.

Jusque 2005, les stock-options ne rentraient pas dans le bilan comptable des entreprises. Par conséquent, elles permettaient une augmentation importante du revenu des employés sans aucun impact sur le compte de résultats.

## Les options sur indices

Les **options sur indices** sont échangés sur les marchés de gré à gré et sur les marchés organisés. Le dénouement de ces options est effectué en cash. A L'échéance, le détenteur d'un call (resp put) reçoit $$(S-K)$$ (resp $$(K-S)$$) par le vendeur du call (resp put). Ces options sont souvent utilisées pour limiter les risques de perte sur les portefeuilles répliquant la rentabilité des indices.

## Les options sur devises

Les **options sur devises** sont principalement échangées sur les marchés de gré à gré. Elles sont très utilisées par les entrepises pour se protéger contre les risques de change tout en bénéficiant de variations favorables du taux de change. 

## Les options quanto

Les **options quanto** sont des actifs dérivés (call ou put) fondés sur deux devises distinctes. Le payoff est payé dans une devise particulière mais les sous-jacents sont issus d'un marché étranger donc libellés dans une autre devise. Le taux de change utilisé à l'échéance est fixé dès le début du contrat. Cela permet donc aux investisseurs de limiter leurs expositions aux variations du taux de change.

## Les options de taux

Les **options de taux (caps et floors)** permettent de définir dès maintenant un taux d'emprunt ou de prêt qui pourra être utilisé dans le futur. Un **cap** est une option de taux définissant un taux d'emprunt. Un **floor** est une option de taux définissant un taux de prêt. Les options de taux permettent de se couvrir contre une variation des taux d'intérêts.

## Les swaptions

Les **swaptions** sont échangés sur les marchés de gré à gré. Ce sont des options sur swap. Les swaptions sont utilisés pour couvrir les portefeuilles de taux.

