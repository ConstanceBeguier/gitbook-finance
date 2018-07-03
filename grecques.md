# Les grecques

Les lettres grecques sont des indicateurs de risques sur les positions en options. Les traders les utilisent pour couvrir les risques d'un protefeuille d'options. Chaque lettre grecque mesure une dimension différente (prix du sous-jacent, volatilité, temps, ...) du risque d'une position en option.

## Le delta

Le **delta** d'une option mesure la sensibilité du prix de l'option à une variation donée du cours du sous-jacent.

$$ \delta = \frac{\partial P}{\partial S}$$
avec $$P$$ le prix de l'option et $$S$$ le cours du sous-jacent.

Pour se couvrir de la vente d'une option, le trader doit acheter $$\delta$$ actions. Lorsque le $$\delta$$ d'un portefeuille est nul, le trader est couvert contre une variation du cours du sous-jacent. Cette position est appelée **delta-neutre** ($$\delta = 0$$). Le trader doit régulièrement réajuster son portefeuille car le $\delta$ varie au cours du temps.

Delta d'une option européenne sur action ne versant pas de dividende:

$$\delta(call) = N(d_1) > 0 $$

$$\delta(put) = N(d_1) - 1 < 0$$

![](/images/delta.png)

Delta d'une option européenne sur action versant un dividende de taux $$q$$:

$$\delta(call) = e^{-qT} N(d_1)$$

$$\delta(put) = e^{-qT} (N(d_1) - 1)$$

Le delta d'un portefeuille d'options est la somme des deltas des options qui le composent.

## Le gamma

Le **gamma** d'une option représente la courbure  de la fonction liant le prix de l'option au cours du sous-jacent c'est-à-dire si le prix de l'option a tendance à évoluer rapidement ou pas par rapport à l'évolution du prix du sous-jacent.

$$\gamma = \frac{\partial^2 P}{\partial S^2}$$
avec $$P$$ le prix de l'option et $$S$$ le cours du sous-jacent.

Si le gamma est faible, le delta varie lentement. Il n'est donc pas nécessaire d'ajuster fréquemment le portefeuille pour maintenir une position delta-neutre.

Le trader peut adopter une position **gamma-neutre** afin de se protéger contre l'impact de cette courbure. Pour cela, il est nécessaire de prendre des positions sur des options (et non sur des actifs ou des forwards) car une option n'est pas linéairement liée à l'actif sous-jacent.

Gamma d'une option européenne sur action ne versant pas de dividende:

$$\gamma(call) = gamma(put) = \frac{N'(d_1)}{S \sigma \sqrt{T}} \ge 0 $$

avec $$N'(x) = \frac{1}{\sqrt{2 \Pi}} e^{-x^2/2}$$

![](/images/gamma.png)

Gamma d'une option européenne sur action versant un dividende de taux $$q$$:

$$\gamma(call) = gamma(put) = \frac{N'(d_1) e^{-qT}}{S \sigma \sqrt{T}} \ge 0 $$

Pour avoir un portefeuille delta-neutre et gamma-neutre, il faut d'abord prendre des positions sur des options pour rendre le portefeuille gamma-neutre (cela modifie le delta du portefeuille). Puis il faut prendre des positions sur l'actif sous-jacent pour rendre le portefeuille delta-neutre (cela ne modifie pas le gamma du portefeuille car l'actif sous-jacent est linéairement lié à l'option).

## Le thêta 

Le **thêta** d'une option mesure la sensibilité du prix de l'option à la variation de la durée de vie de l'option.

$$\theta = - \frac{\partial P}{\partial T}$$
avec $$P$$ le prix de l'option et $$T$$ la durée de vie de l'option.

Thêta d'une option européenne sur action ne versant pas de dividende:

$$\theta(call) = - \frac{S N'(d_1) \sigma}{2 \sqrt{T}} - r K e^{-rT} N(d_2)$$

$$\theta(put) = - \frac{S N'(d_1) \sigma}{2 \sqrt{T}} + r K e^{-rT} N(-d_2)$$

![](/images/theta.png)

Thêta d'une option européenne sur action versant un dividende de taux $$q$$:

$$\theta(call) = - \frac{S N'(d_1) \sigma e^{-qT}}{2 \sqrt{T}} + q S N(d_1) e^{-qT} - r K e^{-rT} N(d_2)$$

$$\theta(put) = - \frac{S N'(d_1) \sigma e^{-qT}}{2 \sqrt{T}} - q S N(-d_1) e^{-qT} + r K e^{-rT} N(-d_2)$$

Pour rappel, l'EDP de Back-Scholes-Merton pour un produit dérivé sur une action ne versant pas de dividende est

$$ r f = \frac{\partial f}{\partial t}  + r S \frac{\partial f}{\partial S} \frac{1}{2} \sigma^2 S^2 \frac{\partial^2 f}{\partial S^2}$$

Nous pouvons en déduire une relation liant $$\delta$$, $$\theta$$ et $$\gamma$$:

$$r f = \theta + rS \delta + \frac{1}{2} \sigma^2 S^2 \gamma$$

## Le véga

Le **véga** mesure la sensibilité du prix de l'option à la volatilité implicite.

$$\nu = \frac{\partial P}{\partial \sigma}$$
avec $$P$$ le prix de l'option et $$\sigma$$ sa volatilité implicite.

Pour obtenir une position **véga-neutre**, il est nécessaire de prendre des positions sur des options (comme pour obtenir une position gamma-neutre). Si nous voulons obtenir une position véga-neutre et gamma-neutre, il est nécessaire de prendre des positions sur au moins deux options différentes.

Véga d'une option européenne sur action ne versant pas de dividende:

$$\nu(call) = \nu(put) = S \sqrt{T} N'(d_1)$$

![](/images/vega.png)

Véga d'une option européenne sur action versant un dividende de taux $$q$$:

$$\nu(call) = \nu(put) = S \sqrt{T}N'(d_1) e^{-qT}$$

## Le rhô

Le **rhô** mesure la sensibilité du prix d'une option au taux d'intérêt sans risque.

$$\rho = \frac{\partial P}{\partial r}$$
avec $$P$$ le prix de l'option et $$\rho$$ sa volatilité implicite.

Rhô d'une option européenne sur action ne versant pas de dividende:

$$\rho(call) = K T e^{-rT} N(d_2)$$

$$\rho(put) = - K T e^{-rT} N(-d_2)$$

Rhô d'une option européenne sur action versant un dividende de taux $$q$$:

$$\rho(call) = K T e^{-rT} N(d_2)$$

$$\rho(put) = - K T e^{-rT} N(-d_2)$$

## Les grecques pour les options sur indices, devises, contrats futures

Comme précédemment, il suffit de réutiliser les formules des grecques sur option européenne sur action versant un dividende de taux $$q$$ en remplaçant:
 - $$q$$ par le taux de versement de dividendes de l'indice, pour les **options sur indices**
 - $$q$$ par le taux sans risque étranger, pour les **options sur devises**
 - $$q$$ par le taux sans risque $$r$$, pour les **options sur contrats futures**

