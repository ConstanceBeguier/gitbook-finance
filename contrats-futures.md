# Les contrats futures

## Introducion

Un contrat future a des charactéristiques similaires au contrat forward:
 - engagement ferme
 - d'achat (position longue) ou de vente (position courte) d'une certaine quantité (appelée quotité) d'un actif (appelé sous-jacent)
 - à une date future donnée $$T$$
 - à un prix convenu $$K$$
 - sur un marché organisé.

## Le fonctionnement des marchés des futures

La majorité des contrats futures sont dénoués avant l'expiration en prenant la position inverse (achat ou  vente du même contrat future). Le gain ou la perte du trader est défini par la différence de prix entre les deux contrats.

A l'approche de l'échéance, le prix future d'un contrat converge ver le prix de l'actif sous-jacent (sinon arbitrage possible).

Afin d'éviter les risques de défaut, sur les marchés organisés, la chambre de compensation est responsable des appels de marges. Tout d'abord le client verse un depôt de marge initial lors de l'achat du contrat. A la fin de chaque journée durant la vie du contrat, le compte du client est ajusté en fonction des gains et pertes journalières sur son contrat: ce sont les appels de marge (marking to market). Si le client est incapable de répondre à l'appel de marge, sa position est dénouée par l'acquisition du contrat inverse en utilisant l'argent sur son compte à la chambre de compensation. Plus la volatilité du sous-jacent est grande, plus les marges sont élevées. Le plus souvent, le deposit et les appels de marge sont payés à l'aide de bons du Trésor estimés à 90% de leur valeur.

Les traders peuvent effectuer différents types d'ordre:
 - ordre à tout prix (= ordre au prix du marché): ordre exécuté au meilleur prix disponible au moment où il arrive sur le marché
 - ordre limite: ordre exécuté uniqueemnt si le prix du marché satisfait les conditions (ex: prix maximal pour une position longue)
 - ordre stop: similaire à l'ordre limite mais le but est de limiter ses pertes en cas de mouvement défavorable du cours (ex: dénouement d'une position si le prix passe en dessous de 100 euros)
 - ordre à prix touché: ordre exécuté au meilleur prix du marché si une trasaction a eu lieu au prix spécifié ou à un prix plus favorable

## Les futures sur obligations

Dans les contrats futures sur obligations, l'actif sous-jacent n'existe pas (obligation notionnelle). Ces obligations fictives ont toujours la même durée de vie et le même coupon. Cela permet une standardisation des contrats (la maturité ne varie pas d'un jour à l'autre) et facilite le dénouement de ces contrats. Pour le dénouement de ces contrats, les autorités de marché définissent une liste d'obligations réelles qui pourront être livrées à l'échéance. De plus, un facteur de concordance sert à ajuster les termes du contrat pour tenir en compte que les taux de coupons des obligations livrables sont le plus souvent différents du taux de coupon du notionnel.

