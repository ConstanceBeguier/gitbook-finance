# Les options exotiques

Les **packages**  sont des portefeuilles constitués de calls européens classiques, puts européens classiques, contrats forwards, liquidités et/ou actifs sous-jacent (ex: bull/bear spreads, straddle/strangle, ...). Le plus souvent le coût initial du package est nul.

Les **options américaines perptétuelles** sont des options sur un actif dérivé payant un montant fixe $$Q$$ à la première date à laquelle $$S=H$$.

Les **options américaines non standards** sont des options ayant une ou plusieurs des caractéristiques suivantes:
- l'exercice anticipé de l'option est limité à certaines dates (**options bermudiennes**)
- l'exercice anticipé de l'option est autorisé que pendant une période spécifique (par exemple, avec une période initiale de blocage)
- le prix d'exercice de l'option est variable pendant la durée de vie de l'option

Les **options gaps** sont des options délivrant un payoff $$(S_T - K_1)$$ quand $$S_T > K_2$$.

Les **forward start options** sont des options qui n'entrent en activité qu'à une date ultérieure (par exemple, les stock options).

Les **ratchet/cliquet options** sont une série successive de calls (ou de puts) dont les prix d'exercice sont fixés selon des règles déterminées en date initiale.

Les **compound options** sont des options sur options (calls sur calls, calls sur puts, puts sur puts ou puts sur calls).

Les **chooser options** sont des options pour lesquelles le détenteur peut choisir, après un certain délai, si l'option est un call ou un put (le prix d'exercice et la date d'échéance du call et du put ne sont pas forcément identiques).

Les **options barrières** sont des options dont le payoff dépend du passage éventuel d'un seuil par le prix de l'actif sous-jacent pendant une certaine période. Il existe deux grands types d'options barrières:
- les **options knock-out** qui cessent d'exister une fois que le prix de l'actif sous-jacent a atteint le seuil
- les **options knock-in** qui commencent à exister une fois que le prix de l'actif sous-jacent a atteint le seuil

Les **options digitales (ou binaires)** sont des options dont le payoff a des valeurs discontinues.

Les **options lookback** sont des options dont le payoff dépend de la valeur maximale ou minimale atteint par le prix du sous-jacent pendant la durée de vie de l'option.

Les **options asiatiques** sont des options dont le payoff dépend du prix moyen de l'actif sous-jacent calculé au cours de la vie de l'option.

Les **options d'échange** sont des options pour lesquelles à l'échéance un actif peut être échangé contre un autre actif.

Les **basket options** sont des options dont le payoff dépend de la valeur d'un portefeuille d'actifs.

