# Value at Risk (VaR)

L'objectif d'un calcul de VaR est de pouvoir assurer qu'au seuil de $$X\%$$, la perte sur un portefeuille ne dépassera pas un montant $$V$$ dans les $$N$$ prochains jours. La variable $$V$$ est la VaR, $$X$$ est le seuil de confiance et $$N$$ est l'horizon temporel. La VaR sera notée dans cette section $$V(N, X)$$. Le plus souvent, la VaR est calculée avec un horizon de 10 jours et un seuil de confiance de $$99\%$$.

Si les variations successives du portefeuille sont normales, indépendantes et centrées, alors $$V(N,X) = V(1, X) \cdot \sqrt{N}$$. Il est souvent difficile d'évaluer correctement la VaR pour des horizons éloignés. Elle est donc estimée pour un horizon de 1 jour puis elle est caclulée pour un horizon de $$N$$ jours grâce à la formule précédente.

Le montant des capitaux propres que doit détenir une institution financière est un multiple de la VaR. Le régulateur choisit ce coefficient multiplicateur pour chaque institution financière. Ce coefficient est toujours supérieur ou égal à 3.

## Estimation de la VaR à l'aide des données historiques

Nous avons les valeurs du portefeuille pour les 500 derniners jours. Nous voulons estimer $$V(10, 99\%)$$ de ce portefeuille.

Notations:
 - $$v_i$$: valeur du portefeuille pour la $i$-ième donnée historique
 - $$v_n$$: valeur du portefeuille aujourd'hui
 - $$\frac{v_i}{v_{i-1}}$$: variation possible du portefeuille entre deux jours consécutifs

Calcul de $$V(1, 99\%)$$:
1. Calculer $$\forall i, v_n \frac{v_i}{v_{i-1}}$$ (valeurs estimées du portefeuille pour demain)
2. Trouver la 5e variation la plus défavorable (car nous avons 500 estimations et un seuil de confiance de $$99\%$$)
Cette 5e variation la plus défavorable est égale $$V(1, 99\%)$$.

Pour obtenir, $$V(10, 99\%)$$, il suffit d'utiliser la formule $$V(10, 99\%) = V(1, 99\%) sqrt{10}$$.

## Estimation de la VaR avec la variance-covariance

### Portefeuilles sans actif dérivé

Si nous avons un portefeuille ne comportant pas d'actifs dérivés, nous pouvons utiliser un modèle linéaire.

Supposons que nous avons un portefeuille $$P$$ contenant $n$ actifs différents et $$\alpha_i$$ est le montant investi pour le $i$-ième actif. Soit $$\Delta x_i$$ la rentabilité journalière du $$i$$-ième actif et $$\Delta P$$ la variation journalière du portefeuille. On a:
$$\Delta P \alpha_i \Delta x_i$$

Soit $$C$$ la **matrice de variance-covariance** du portefeuille

$$C =
\begin{pmatrix}
var_1 & cov_{1,2} & cov_{1,3} & \cdots & cov_{1,n} \\
cov_{2,1} & var_2 & cov_{2,3} & \cdots & cov_{2,n} \\
\vdots & \vdots & \vdots & \vdots & \vdots \\
cov_{n,1} & cov_{n,2} & cov_{n,3} & \cdots & var_n 
\end{pmatrix}$$

avec
- $$var_i = \sigma_i^2$$: variance journalière du $$i$$-ième actif (égale au carré de la volatilité journalière)
- $$cov_{i,j} = \rho_{i,j} \sigma_i \sigma_j$$: covariance entre les actifs $$i$$ et $$j$$ (égal au produit des volatilités journalières et de la corrélation)

Les variances et les covariances sont souvent estimées à partir de données historiques à l'aide du modèle de GARCH(1,1).

Nous pouvons alors calculer la variance du portefeuille:
$$\sigma_P^2 = \alpha^T C \alpha$$

En supposant que les variations du portefeuille sont normalement distribuées, la variation de la valeur du portefeuille a une probabilité inférieure à $$1\%$$ d'être supérieure à $$2.326$$. Alors l'écart type vaut $$V(1, 99\%) = 2.326 \cdot \sigma_P$$.

En utilisant la formule habituelle, nous pouvons calcule $$V(N, 99\%) = 2.326 \cdot \sigma_P \cdot \sqrt{N}$$.

### Portefeuilles contenant des options

Si toutes les options sont sur le même sous-jacent côté $S$, alors d'après la définition du delta:
$$\Delta P = \delta \Delta S = \delta S \Delta x$$
avec $$\Delta S = S \Delta x$$

Si toutes les options ne sont pas sur le même sous-jacent alors
$$\Delta P = \sum_i \delta_i S_i \Delta x_i = \sum_i \alpha_i \Delta x_i$$
avec $$\alpha_i = S_i \delta_i$$

Nous pouvons alors réutiliser la méthode précédente en utilisant $$\alpha_i = \S_i \delta_i$$:
$$\sigma_P^2 = \alpha^T C \alpha$$
$$V(N, 99\%) = 2.326 \cdot \sigma_P \cdot \sqrt{N}$$

