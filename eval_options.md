# Evaluation des options

## Evaluation des options sur actions

Dans un premier temps, nous supposons que l'action ne verse pas de dividendes.

### Notations
 - $$K$$: prix d'exercice de l'option (strike)
 - $$S_0$$: cours de l'action à la date $$0$$ (date de la transaction)
 - $$S_T$$: cours de l'action à la date $$T$$ (échéance de l'option)
 - $$T$$: maturité de l'option
 - $$\sigma$$: volatilité du prix de l'action
 - $$r$$: taux d'intérêt sans risque annuel
 - $$C$$: valeur d'un call américain sur une option
 - $$c$$: valeur d'un call européen sur une option
 - $$P$$: valeur d'un put américain sur une option
 - $$p$$: valeur d'un put européen sur une option

### Variation des prix d'une option en fonction des caractéristiques

Pour un **call européen ou américain**, le prix de l'option
 - augmente lors d'une augmentation
   - du cours actuel de l'action $$S_0$$
   - de la volatilité du prix de l'action $$\sigma$$
   - du taux d'intérêt sans risque $$r$$
 - diminue lors d'une augmentation
   - du prix d'exercice $$K$$

Pour un **put européen ou américain**, le prix de l'option
 - augmente lors d'une augmentation
   - du prix d'exercice $$K$$
   - de la volatilité du prix de l'action $$\sigma$$
   - des dividendes
 - diminue lors d'une augmentation
   - du cours actuel de l'action $$S_0$$
   - du taux d'intérêt sans risque $$r$$

De plus, pour les puts et calls américains, le prix de l'option augmente lors d'une augmentation de la maturité $$T$$.

### Méthode d'évaluation des prix d'une option à l'aide de portefeuilles

Par la suite, nous noterons $$V(P_A, t)$$, la valeur du portefeuille $$P_A$$ à l'instant $$t$$.

Soit $$P_A$$ et $$P_B$$ deux portefeuilles financiers tels que $$V(P_A, T) = V(P_B, T)$$ (resp $$V(P_A, T) > V(P_B, T)$$). Alors $$\forall 0 \le t \le T, V(P_A, t) = V(P_B, t)$$ (resp $$V(P_A, t) > V(P_B, t)$$).


Si $$V(P_A, t) < V(P_B, t)$$, alors un arbitragiste ferait les transactions suivantes:
 - à $$t$$
   - vente à découvert de $$P_B$$
   - achat de $$P_A$$
   - placement de $$V(P_B, t) - V(P_A, t)$$
 - à $$T$$
   - remboursement de $$P_B$$
   - vente de $$P_A$$
   - récupération des intérêts de son placemente $$(V(P_B, t) - V(P_A, t))e^{r(T-t)}$$

### La parité call-put

La **parité call-put** est une équation qui relie le prix d'un call européen au prix d'un put européen. La valeur d'un call (resp put) européen peut donc être déduite à partir de la valeur d'un put (resp call) européen ayant les mêmes caractéristiques.

**Relation de parité call-put:** $$c + Ke^{-rT} = p + S_0$$

Portefeuille A noté $$P_A$$:
 - call européen
 - trésorerie de $$Ke^{-rT}$$
Portefeuille B noté $$P_B$$:
 - put européen
 - action

Valeur du portefeuille A à $$T$$ noté $$V(P_A, T)$$:
 - la trésoserie a été placée au taux sans risque et vaut donc à $$T$$ la valeur de $$Ke^{-rT}e^{rT} = K$$
 - si $$K > S_T$$, alors le call n'est pas exercé. Donc $$V(P_A, T) = K$$
 - si $$K < S_T$$, alors le call est exercé. Le call a un gain de $$S_T - K$$. Donc $$V(P_A, T) = S_T - K + K = S_T$$.
Dans tous les cas, $$V(P_A, T) = max(K, S_T)$$.

Valeur du portefeuille B à $$T$$ noté $$V(P_B, T)$$:
 - si $$K < S_T$$, alors le put n'est pas exercé. Donc $$V(P_B, T) = S_T$$.
 - si $$K > S_T$$, alors le put est exercé. Notre action est utilisé pour l'exercicé du put. Donc $$V(P_B, T) = K$$.
Dans tous les cas, $$V(P_B, T) = max(K, S_T)$$.

Les deux portefeuilles sont égaux à l'instant $$T$$. En l'absence d'opportunités d'arbitrage, ils doivent donc être égaux à l'instant $$t=0$$.

Valeur du portefeuille A à $$t=0$$ noté $$V(P_A, 0) = c + Ke^{-rT}$$

Valeur du portefeuille B à $$t=0$$ noté $$V(P_B, T) = p + S_0$$

Nous retrouvons bien la relation de parité call-put.

### Bornes supérieures et inférieures des prix d'une option européenne

**Borne supérieure d'un call européen:** $$c \le S_0$$

Sinon un arbitragiste fait les transactions suivantes:
 - à $$t=0$$
   - achat de l'option à la valeur de $$S_0$$
   - vente d'un call
 - à $$T$$
   - si $$S_T > K$$, l'option sera exercée et l'arbitragiste gagnera $$c - S_0$$
   - si $$S_T < K$$, l'option ne sera pas exercée et l'arbitragiste gagnera $$c - S_0 + S_T$$

**Borne supérieure d'un put européen:** $$p \le K e^{-rT}$$

Sinon un arbitragiste fait les transactions suivantes:
 - à $$t=0$$
   - vente d'un put à la valeur $$p$$
   - placement de $$p$$
 - à $$T$$
   - si $$S_T < K$$, l'option sera exercée et l'arbitragiste gagnera $$p e^{rT} - K + S_T$$
   - si $$S_T > K$$, l'option ne sera pas exercée et l'arbitragiste gagnera $$p e^{rT}$$

**Borne inférieure d'un call européen:** $$max(S_0 - K e^{-rT}, 0) \le c$$

Portefeuille A:
 - un call européen
 - une trésorerie de $$K e^{-rT}$$ (à l'instant $$t=0$$)
Portefeuille B:
 - une action

A l'instant $$T$$, le portefeuille A vaut
 - si $$S_T > K$$, 
   - l'option sera exercée et vaudra $$S_T - K$$
   - la trésorerie aura été placée entre l'instant $$t=0$$ et $$T$$ et vaudra $$K$$
   - Donc $$V(P_A, T) = S_T - K + K = S_T$$
 - si $$S_T < K$$,
   - l'option ne sera pas exercée et vaudra $$0$$
   - la trésorerie aura été placée entre l'instant $$t=0$$ et $$T$$ et vaudra $$K$$
   - Donc $$V(P_A, T) = K$$
Dans tous les cas, $$V(P_A, T) = max(S_T, K)$$.

A l'instant $$T$$, le portefeuille B vaut $$V(P_B, T) = S_T$$

Donc nous avons $$V(P_A, T) \ge V(P_B, T)$$. En l'absence d'opportunités d'arbitrage, nous avons donc $$V(P_A, 0) \ge V(P_B, 0)$$.

A l'instant $$t=0$$, le portefeuille A vaut $$V(P_A, 0) = c + K e^{-rT}$$.

A l'instant $$t=0$$, le portefeuille B vaut $$V(P_B, 0) = S_0$$

Nous avons donc $$c + K e^{-rT} \ge S_0$$.

**Borne inférieure d'un put européen:** $$max(K e^{-rT} - S_0, 0) \le p$$

Portefeuille A:
 - un put européen
 - une action
Portefeuille B:
 - une trésorerie de $$K e^{-rT}$$ (à l'instant $$t=0$$)

A l'instant $$T$$, le portefeuille A vaut
 - si $$S_T < K$$,
   - l'option sera exercée et donc $$V(P_A, T) = K$$
 - si $$S_T > K$$, 
   - l'option ne sera pas exercée et donc $$V(P_A, T) = S_T$$
Dans tous les cas, $$V(P_A, T) = max(S_T, K)$$.

A l'instant $$T$$, le portefeuille B vaut $$V(P_B, T) = K$$

Donc nous avons $$V(P_A, T) \ge V(P_B, T)$$. En l'absence d'opportunités d'arbitrage, nous avons donc $$V(P_A, 0) \ge V(P_B, 0)$$.

A l'instant $$t=0$$, le portefeuille A vaut $$V(P_A, 0) = p + S_0$$.

A l'instant $$t=0$$, le portefeuille B vaut $$V(P_B, 0) = K e^{-rT}$$

Nous avons donc $$p + S_0 \ge K e^{-rT}$$.

### Bornes supérieures et inférieures des prix d'une option américaine

Il n'est jamais optimal d'exercer avant la date d'échéance un call américain dont l'action ne verse pas de dividendes à cause de l'assurance de l'option (protection contre une baisse des cours) et de la valeur temps de la monnaie (nous pouvons placer notre liquidité plutôt que de la dépensée en exerçant l'option). Par conséquent, un call américain a le même prix qu'un call européen $$c=C$$ et nous retrouvons les mêmes inéglités $$max(S_0 - K e^{-rT}, 0) \le C \le S_0$$

Il peut être optimal d'exercer prématurément un put européen car cela nous ajoute de la liquidité. De plus dans le cas extrême où l'action vaudrait $$0$$, il faudrait immédiatement exercer le put afin d'obtenir un gain maximal sur cette transaction.

Pour rappel, un put européen a les bornes suivantes $$max(K e^{-rT} -S_0, 0) \le p \le K e^{-rT}$$.

Puisque que l'exercice d'un put américain est possible à n'importe quel moment, $$max(K -S_0, 0) \le P \le K e^{-rT}$$

### Effet des dividends sur les équations précédentes

Nous supposons que l'action verse un dividende durant la vie de l'option et que la valeur actuelle des dividendes à $$t=0$$ est de $$D$$.

En reprenant les portefeuilles précédents et en replaçant la trésorerie de $$K e^{-rT}$$ par $$D + K e^{-rT}$$, nous obtenons les bornes suivantes $$max(S_0 - D - K e^{-rT}, 0) \le c$$ et $$max(D + K e^{-rT} -S_0, 0) \le p$$ et $$c + D + Ke^{-rT} = p + S_0$$

Nous pouvons considérer que le détachement de ce dividende entraine une baisse du cours égale au montant de ce dividende. Par conséquent, il faut remplacer dans les équations précédentes $$S_0$$ par $$S_0 -D$$ avec $$D$$ la valeur actualisée du dividende à $$t=0$$.

## Evaluation des options sur indices

En l'absence d'opportunités d'arbitrage, l'indice boursier est analogue à une action payant un taux de dividende continu. Ce taux de dividende continu est égale à la moyenne des taux de dividende des différentes actions composant l'indice. Il suffit alors de remplacer $$S_0$$ par $$S_0 e^{-qt}$$ dans les formules précédentes (bornes, parité call-put, formule de Black-Scholes). Nous obtenons alors les formules suivantes:

$$c \ge max(S_0 e^{-qT} - K e^{-rT}, 0)$$ 

$$p \ge max(K e^{-rT} - S_0 e^{-qT}, 0)$$ 

$$c + Ke^{-rT} = p + S_0 e^{-qT}$$ 

$$c = S_0 e^{-qT} N(d_1) - K e^{-rT} N(d_2)$$ 

$$p = Ke^{-rT} N(-d_2) - S_0 e^{-qT} N(-d_1)$$ 

avec 

$$d_1 = \frac{ln(S_0/K) + (r _ q + \sigma^2/2)T}{\sigma \sqrt{T}}$$ 

$$d_2 = d_1 - \sigma \sqrt{T}$$

## Evaluation des options sur futures

### La parité call-put 
 
Parité call-put: $$c + K e^{-rT} = p + F_0 e^{-rT}$$ 
 
Portefeuille A: 
 - call européen sur future 
 - trésorerie de $$Ke^{-rT}$$ 
Portefeuille B: 
 - put européen sur future 
 - position longue sur contrat future de strike $$F_0$$ 
 - trésorerie de $$F_0 e^{-rT}$$ 
 
Valeur du portefeuille A à $$T$$: 
 - si $$F_T > K$$, alors le call est exercé et il a un payoff de $$F_T - K$$ 
 - si $$F_T < K$$, alors le call n'est pas exercé et il a un payoff de $$0$$ 
 - le placement de la trésorerie donne $$K$$ 
Donc le portefeuille A à $$T$$ vaut $$V(P_A, T) = max(F_T, K)$$. 
 
Valeur du portefeuille B à $$T$$: 
 - si $$F_T < K$$, alors le put est exercé et il a un payoff de $$K - F_T$$ 
 - si $$F_T > K$$, alors le put n'est pas exercé et il a un payoff de $$0$$ 
 - le placement de la trésorerie donne $$F_0$$ 
 - le contrat future a un payoff de $$F_T - F_0$$ 
Donc le portefeuille B à $$T$$ vaut $$V(P_B, T) = max(F_T, K)$$. 
 
Les deux portefeuilles ont la même valeur à $$T$$. En l'absence d'opportunités d'arbitrage, ils vallent aussi la même valeur à $$t=0$$. 
 
A $$t=0$$, le portefeuille A vaut $$V(P_A, 0) = c + K e^{-rT}$$. 
 
A $$t=0$$, la position longue sur le contrat future vaut $$0$$ à cause des appels de marge quotidiens. Par conséquent, à $$t=0$$, le portefeuille B vaut $$V(P_B, 0) = p + F_0 e^{-rT}$$. 
 
Cela nous donne bien la parité call-put. 

### Les bornes des options sur futures 
 
Nous avons les équations suivantes: 
 - $$c + K e^{-rT} = p + F_0 e^{-rT}$$ (parité call-put) 
 - $$c \ge 0$$ 
 - $$p \ge 0$$ 
 
Par conséquent,  
 - $$c \ge max((F_0 - K) e^{-rT}, 0)$$ 
 - $$p \ge max((K - F_0) e^{-rT}, 0)$$ 
 
 
Les options américaines peuvent être exercées à n'importe quel moment donc: 
 - $$C \ge max(F_0 - K, 0)$$ 
 - $$P \ge max(K - F_0, 0)$$ 

### Le modèle de Black 
 
En calculant le taux de croissance d'un prix future dans un univers risque-neutre, nous allons montré que les options sur futures se comportent comme des options sur actions versant un dividende dont le taux est égal au taux sans risque $$r$$. 
 
Soit $$F_t$$ le prix future à $$t$$. Soit $$0$$, $$\Delta t$$, $$2 \Delta t$$, ... les dates de réglement. Nous supposons que nous avons un portefeuille contenant une position longue sur un contrat future à $$t=0$$. A cause des appels de marge quotidiens, ce portefeuille a une valeur nulle à $$t=0$$. 
 
A $$\Delta t$$, le payoff de ce portefeuille est $$F_{\Delta t} - F_0$$. En actualisant cette valeur à $$t=0$$, nous obtenons une nouvelle valeur du portefeuille à $$t=0$$: $$e^{-r \Delta t} E[F_{\Delta t} - F_0]$$. Nous avons donc dans un univers risque-neutre, $$0 = e^{-r \Delta t} E[F_{\Delta t} - F_0]$$ soit $$E[F_{\Delta t}] = F_0$$. En faisant un raisonnement similaire sur les atures dates de réglement,  nous obtenons $$E[F_T] = 0$$ pour tout $$T$$. Le taux de croissance du prix future dans un univers-risque neutre est donc nul. $$F$$ suit donc le processus suivant $$dF = \sigma F dz$$. Le prix future se comporte donc comme le prix d'une action versant un taux de dividende $$q$$ égal au taux sans risque $$r$$. 
 
Par conséquent, nous pouvons réutiliser les formules de Black-Scholes pour les actions versant un taux de dividende $$q$$ en remplaçant au préalable $$q$$ par $$r$$ et $$S_0$$ par $$F_0$$. Nous obtenons le prix des options sur futures: 

$$c = e^{-rT}(F_0 N(d_1) - K N(d_2))$$ 

$$p = e^{-rT}(K N(-d_1) - F_0 N(-d_2))$$ 

avec 

$$d_1 = \frac{ln(F_0/K) + \sigma^2T/2}{\sigma \sqrt{T}}$$ 

$$d_2 = \frac{ln(F_0/K) - \sigma^2T/2}{\sigma \sqrt{T}} = d_1 - \sigma \sqrt{T}$$ 

## Evaluation des options sur devises

En l'absence d'opportunités d'arbitrage, une devise est analogue à une action payant n taux de dividende continu égal au taux sans risque dans la devise étrangère.Si nous notons: 
 - $$S_0$$ la valeur d'une unité de devise étrangère en devise domestique 
 - $$r$$ le taux d'intérêt sans risque dans la devise domestique 
 - $$r_{f}$$ le taux d'intérêt sans risque dans la devise étrangère 
alors les équations précédentes sont valables après avoir remplacé $$q$$ par $$r_{f}$$. 

## Les courbes de volatilité

Le modèle de Black-Scholes suppose que la distribution de probabilité de l'actif sous-jacent suit une loi log-normale à toute date. Cette hyopthèse est erronées. Les traders supposent que les queues de cette distribution sont asymétriques (plus épaisses à gauche qu'à droite). Pour tenir compte des écarts de distribution par rapport à la loi log-normale, les traders utilisent différentes courbes de volatilité:
 - le **smile de volatiilité**: courbre représentant la volatilité implicite d'une option en fonction de son prix d'exercice
 - la **structure par termes**: courbre représentant la volatilité implicite d'une option en fonction de sa durée de vie
 - la **surface de volatilité**: surface représentant la volatilité implicite d'une option en fonction de son prix d'exercice et de sa durée de vie

Pour rappel, la volatilité implicite d'un put est égale à la volatilité implicite du call ayant les mêmes charactéristiques (prix d'exercice et durée de vie).

Pour les options sur actions, le smile de volatilité est une fonction légèrement décroissante. Cela signifie que les puts en dehors de la monnaie et le call dans la monnaie ont des volatilités implicites élevées alors que les puts dans la monnaie et les call en dehors de la monnaie ont des volatilités implicites faibles.

![](/images/smile_options_actions.png)

Pour les options de change, le smile de volatilité est en forme de U. Cela signifie que les options très en dehors de la monnaie ou très dans la monnaie ont des volatilités implicites plus élevées que les les options à la monnaie.

![](/images/smile_options_change.png)
