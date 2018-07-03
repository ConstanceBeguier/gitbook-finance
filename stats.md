# Quelques rappels de statistiques

## Les statistiques

**Variable discrète:** $$X(\Omega) = \{x_1, x_2, ..., x_k, ... \}$$

* $$P(a \le X \le b) = \sum_{a \le x_k \le b} P(X=x_k)$$
* **Fonction de répartition:** $$F(x) = P(X \le x) = \sum_{x_k \le b} P(X = x_k)$$
* **Espérance \(expectation\):** $$E[X] = \sum x_k P(X=x_k)$$ (similaire à une moyenne pondérée par les probabilités)
* $$E[g(X)] = \sum g(X_k) P(X=x_k)$$
* **Variance:** $$Var(X) = E[X - E[X]]^2$$ (mesure de dispersion)
* **Ecart type \(standard deviation std\):** $$\sigma = \sqrt{Var(X)}$$
* **Covariance:** $$Cov(X,Y)=E[(X-E[X])(Y-E[Y])]$$. Si $$X$$ et $$Y$$ sont indépendantes, $$cov(X, Y) = 0$$.

**Variable continue à densité $$f$$:** $$X(\Omega) \in \mathbb{R}$$

* $$P(a \le X \le b) = \int_{a}^{b} f(t) dt$$
* **Fonction de répartition:** $$F(x) = P(X \le x) = \int_{-\infty}^{x} f(t) dt$$
* **Espérance \(expectation\):** $$E[X] = \int_{-\infty}^{\infty} t \cdot f(t) dt$$ (similaire à une moyenne pondérée par les probabilités)
* $$E[g(X)] = \int{-\infty}^{infty} g(t) f(t) dt$$
* **Variance:** $$Var(X) = E[X - E[X]]^2$$ (mesure de dispersion)
* **Ecart type \(standard deviation std\):** $$\sigma = \sqrt{Var(X)}$$
* **Covariance:** $$Cov(X,Y)=E[(X-E[X])(Y-E[Y])]$$. Si $$X$$ et $$Y$$ sont indépendantes, $$cov(X, Y) = 0$$.

## Loi normale

La **loi normale** est une des lois de probabilités les plus adaptées pour modéliser des phénomènes aléatoires. Sa densité de probabilité est
$$ f(x) = \frac{1}{\sigma \sqrt{2 \pi}} exp( \frac{-(x - \mu)^2}{\sigma^2})$$
avec $$\mu$$ son espérance et $$\sigma$$ son écart-type

![](/images/loi_normale_densite.png)

La **loi normale centrée réduite** est la loi normale d'espérance nulle et d'écart-type égal à 1.

Lorsque qu'une variable aléatoire $$X$$ suit une loi normale, nous noterons par la suite $$X \sim (\mu, \sigma)$$

**Théorème central limite:** convergence en loi de la somme d'une suite de variables aléatoires vers la loi normale

**Table de valeurs des intervalles de confiance:**

$$P(\mu - \sigma \le x \le \mu + \sigma) \approx 0.6827$$

![](/images/loi_normale_distribution.png)

## Loi log-normale

Un variable aléatoire $X$ suit une **loi log-normale** $$(\mu, \sigma)$$ si $$Y = ln(X)$$ suit une loi normale $$(\mu, \sigma)$$. La densité de probabilité de $$X$$ est

$$f(x) = \left\{ \begin{array}{ll} \frac{1}{x \sigma \sqrt{2 \pi}} exp( \frac{-(ln(x)-\mu)^2}{2 \sigma^2}) & \text{si} x>0 \\ 0 & \text{sinon} \end{array} \right.$$

![](/images/loi_log_normale_densite.png)

**Espérance d'une loi log-normale:** 
$$E[X] =  e^{\mu + \sigma^2 / 2}$$

**Variance d'une loi log-normale:**
$$Var(X) = (e^{\sigma^2} - 1) e^{2 \mu + \sigma^2}$$

