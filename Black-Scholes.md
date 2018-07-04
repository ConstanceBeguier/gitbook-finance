# Lemme d'Itô et formules de Black-Scholes

## Processus stochastiques

Un **processus stochastique** est une suite de variables aléatoires indexées par le temps utilisé pour décrire l'évolution aléatoire d'une variable au cours du temps.

Un **processus de Markov** est un processus stochastique pour lequel seule la valeur actuelle est utile pour prévoir la distribution future (les valeurs passées n'influent pas sur le futur).

D'après l'**efficience des marchés**, le cours actuel intègre toutes les informations contenues dans l'historique des cours. Par conséquent, le cours actuel peut être modélisé par un processus de Markov.

Un **processus de Wiener standard** (semblable à un mouvement brownien) est un processus décrivant l'évolution d'une variable dont les variations sont normalement distribuées. Si la variable vaut $$x_0$$ à $$t=0$$, alors à $$T$$, la variable suit une loi normale de moyenne $$x_0$$ et d'écart type $$\sqrt{T}$$. Le **drift** de ce processus (espérance de variation du processus par unité de temps) est nul et son **paramètre de variance** est égal à 1 par unité de temps.

En temps continu, la formule d'un processus de Wiener standard est $$\Delta x = \epsilon \sqrt{\Delta t}$$ avec $$\epsilon$$ une loi normale centrée réduite.

Un **processus de Wiener général** est un processus décrivent l'évolution d'une variable normale de **drift** $$a$$ et de **paramètre de variance** $$b^2$$ avec $$a, b$$ contants. Si la variable vaut $$x_0$$ à $$t=0$$, alors à $$T$$, la variable suit une loi normale de moyenne $$x_0 + aT$$ et d'écart type $$b \sqrt{T}$$.

En temps discret, la formule d'un processus de Wiener général est $$dx = a dt + b dz$$

En temps continu, la formule d'un processus de Wiener général est $$\Delta x = a \Delta t + b \epsilon \sqrt{\Delta t}$$ avec $$\epsilon$$ une loi normale centrée réduite.

Un **processus d'Itô** est un processus de Wiener général dont le drift et le paramètre de variance peuvent être des fonctions de $$x$$ et $$t$$.

En temps discret, la formule d'un processus d'Itô est $$dx = a(x,t)) dt + b(x,t) dz$$

En temps continu, la formule d'un processus d'Itô est $$\Delta x = a(x,t) \Delta t + b(x,t) \epsilon \sqrt{\Delta t}$$ avec $$\epsilon$$ une loi normale centrée réduite.
Cette relation contient une petite approximation. Il est supposé que $$a(x,t)$$ et $$b(x,t)$$ sont constants sur l'intervalle de temps $$[t, t+ \Delta t]$$

Une **simulation de Monte Carlo d'un processus stochastique** est une procédure permettant de créer un échantillon aléatoire du processus. La méthode consiste à couper l'intervalle d'étude en petits intervalles de temps et à évaluer, pour chacun des intervalles, un tirage aléatoire parmi les trajectoires possibles de la variable.

**Evolution du cours d'une action:**

Le processus de fluctuation des cours d'actions peut être représenté par le processus stochastique suivant:

En temps discret: $$dS = \mu S dt + \sigma S dz$$

En temps continu: $$\Delta S = \mu S \Delta t + \sigma S \epsilon \sqrt{\Delta t}$$ où
* $$\epsilon$$ suit une loi normale centre réduite
* $$S$$ valeur de l'action à la date $$t$$
* $$\mu$$ rentabilité espérée de l'action par unité de temps
* $$\sigma$$ volatilité de l'action (égal à l'écart type de la variation du cours de l'action sur une année)
* $$z$$ suit un processus de Wiener standard (un mouvement brownien)

Cette équation montre que $$\frac{\Delta S}{S}$$ suit une distribution normale de moyenne $$\mu \Delta t$$ et d'écart type $$\sigma \sqrt{\Delta t}$$

Ce processus de fluctuation est appelé **mouvement brownien géométrique**.

## Le lemme d'Itô

Le lemme d'Itô permet de déterminer le processus stochastique suivi par une fonction de la variable étudiée.

**Lemme d'Itô:**

Soit un processus stochastique de la forme $$dX_t = \mu_t dt + \sigma_t dB_t$$ où $$B_t$$ est un processus de Wiener. Si $$F(X_t, t)$$ est une fonction de classe $$\mathcal{C}^2(\mathbb{R} \times\mathbb{R}_+, \mathbb{R})$$, alors le lemme d'Itô s'écrit

$$df = (\frac{\partial f}{\partial t} + \mu_t \frac{\partial f}{\partial X} +  \frac{\sigma_t^2}{2} \frac{\partial^2 f}{\partial X^2}) dt + \sigma_t \frac{\partial f}{\partial X} dB_t$$


**Application du lemme d'Itô aux contrats forwards:**

Soit un contrat forward sur une action ne versant pas de dividende. A la date $$t \in [0,T]$$, le contrat forward vaut $$F = S e^{r(T-t)}$$. Si $$S$$ suit le processus de Wiener $$dS = \mu S dt + \sigma S dz$$ alors $$F$$ suit le processus suivant

$$dF = (-rSe^{r(T-t)} + \mu  S e^{r(T-t)} + 0) dt + \sigma S s^{r(T-t)} dz = (\mu - r) F dt + \sigma F dz$$

Par conséquent, le prix forward suit aussi un mouvement brownien géométrique d'espérance de taux de croissance $$(\mu - r)$$.

**Propriété de log-normalité:**

Utilisation du lemme d'Itô pour déduire le processus suivi par $$G = ln(S)$$ avec $$dS = \mu S dt + \sigma S dz$$

D'après le lemme d'Itô, $$dG = (0 + \mu S \frac{1}{S} - \frac{(\sigma S)^2}{2} \frac{1}{S^2}) dt + \sigma S \frac{1}{S} dz = ( \mu - \frac{\sigma^2}{2}) dt + \sigma dz$$

Par conséquent, $$G = ln(S)$$ suit un processus de Wiener général de drift $$(\mu - \frac{\sigma^2}{2})$$ et de paramètre de variance $$\sigma^2$$. Donc la variation de $$ln(S)$$ entre $$t=0$$ et $$T$$ suit une loi normale de moyenne $$(\mu - \frac{\sigma^2}{2})T$$ et de variance $$\sigma^2 T$$.

$$ln(S_T) - ln(S_0) \sim \Phi ((\mu - \frac{\sigma^2}{2})T, \sigma \sqrt{T})$$

$$ln(S_T) \sim \Phi (ln(S_0) + (\mu - \frac{\sigma^2}{2})T, \sigma \sqrt{T})$$

Par conséquent, $$ln(S_T)$$ suit une distribution normale. Cela signifie que $$S_T$$ suit une distribution log-normale.

Nous avons
$$E[S_T] = exp[ln(S_0) +(\mu - \sigma^2/2)T + (\sigma \sqrt{T})^2/2] = S_0^2 e^{\mu T}$$

$$Var(S_T) = S_0^2 (e^{\sigma^2 T} - 1) e^{2 \mu T}$$

## Le modèle de Black, Scholes et Merton

Pour rappel, le cours d'une action suit le processus $$dS = \mu S dt + \sigma S dz$$.

Soit $$f$$ le prix d'une action d'achat sur action. $$f$$ dépend de $$S$$ et de $$t$$.

Application du lemme d'Itô à $$f$$:
$$df = (\frac{\partial f}{\partial S} \mu S + \frac{\partial f}{\partial t} + \frac{1}{2} \frac{\partial^2 f}{\partial S^2} \sigma^2 S^2) dt + \frac{\partial f}{\partial S}\sigma S dz$$

Sous la forme discrète: $$\Delta S = \mu S \Delta t + \sigma S \Delta z$$ et

$$\Delta f = (\frac{\partial f}{\partial S} \mu S + \frac{\partial f}{\partial t} + \frac{1}{2} \frac{\partial^2 f}{\partial S^2} \sigma^2 S^2) \Delta t + \frac{\partial f}{\partial S}\sigma S \Delta z$$

Soit un portefeuille contenant:
 - vente d'une unité du produit dérivé
 - achat de $$\frac{\partial f}{\partial S}$$ actions

Valeur du portefeuille:
$$\Pi = -f + \frac{\partial f}{\partial S} S$$

Variation de la valeur du portefeuille:

$$\begin{lalign} 
\Delta Pi & = & - \Delta f + \frac{\partial f}{\partial S} \Delta S \\
 & = & -[(\frac{\partial f}{\partial S} \mu S + \frac{\partial f}{\partial t} + \frac{1}{2} \frac{\partial^2 f}{\partial S^2} \sigma^2 S^2) \Delta t \\
 & & + \frac{\partial f}{\partial S}\sigma S \Delta z] + \frac{\partial f}{\partial S} (\mu S \Delta t + \sigma S \Delta z) \\
 & = & (-\frac{\partial f}{\partial t} - \frac{1}{2} \frac{\partial^2 f}{\partial S^2} \sigma^2 S^2) \Delta t
\end{lalign}$$

En l'absence d'opportunités d'arbitrage, le portefeuille doit être sans risque pendant $$\Delta t$$. Il doit donc procurer une rentabilité égale au taux sans risque $$r$$. Donc $$\Delta \Pi = r \Pi \Delta t$$. Nous obtenons alors l'équation aux dérivées partielles EDP de Black-Scholes-Merton:

$$r f = \frac{\partial f}{\partial t} + r S \frac{\partial f}{\partial S} + \frac{1}{2} \frac{\partial^2 f}{\partial S^2} \sigma^2 S^2$$

En résolvant cette EDP en utilisant la valeur des contrats à l'échéance, nous pouvons calculer pour $$t=0$$ la valeur d'un call européen $$c$$ et d'un put européen $$p$$ sur une action ne versant pas de dividende:

$$c = S_0 N(d_1) - K e^{-rT} N(d_2) = e^{-rT} N(d_2) [S_0 e^{rT} N(d_1)/N(d_2) - K]$$

$$p = K e^{-rT} N(-d_2) - S_0 N(-d1)$$

avec

$$d_1 = \frac{ln(S_0/K) + (r + \sigma^2/2)T}{\sigma \sqrt{T}}$$

$$d_2 = \frac{ln(S_0/K) + (r - \sigma^2/2)T}{\sigma \sqrt{T}} = d_1 - \sigma \sqrt{T}$$

où $$N(x)$$ est la fonction de répartition  $$P(X \le x)$$ d'une loi log-normale centrée réduite $$\Psi(0,1)$$

Si l'option européenne verse des dividendes durant la durée de vie de l'option, alors le détachement du dividende entraine une baisse du cours égale au montant de ce dividende. Par conséquent, nous pouvons encore utiliser les formules de Black-Scholes mais il faut au préalable soustraire à $$S_0$$ la valeur actualisée des dividendes versées durant la vie de l'option. Par exemple, si un dividende $$D$$ est versé à $$t$$ alors il faut remplacer $$S_0$$ par $$S_0 - D e^{-r t}$$. Si un dividende continu annuel $$q$$ est versé durant la vie de l'option, il faut alors remplacer $$S_0$$ par $$S_0 e^{-qT}$$.

## La volatilité implicite

La **volatilité implicite** est la volatilité calculée à partir des prix des options côtées sur le marché à l'aide des formules de Black et Scholes. Connaissant $$S_0$$, $$K$$, $$r$$, $$T$$ et le prix de l'option ($$c$$ ou $$p$$), il est possible à partir des formules de Black et Scholes de trouver itérativement la valeur de $$\sigma$$ qui est la valeur de la volatilité implicite.


