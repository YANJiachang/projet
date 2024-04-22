# Backtester pour Stratégies d’Investissement
cadre de backtesting pour la stratégie d'investissement en actions thématiques

## INTRODUCTION
La classe 'Backtester' est un outil complexe conçu pour simuler et analyser les performances de stratégies de trading basées sur des données historiques. Cette classe est implémentée à l'aide de plusieurs bibliothèques, notamment Pandas pour la manipulation de données, NumPy pour les opérations numériques, Matplotlib pour le dessin et yfinance pour le téléchargement de données financières. Il fournit un cadre complet pour tester les stratégies de trading, en mettant l'accent sur des mesures telles que les rendements quotidiens et annualisés, la volatilité, le ratio de Sharpe et le bêta.Focus particulier sur la stratégie de croisement de moyennes mobiles simples dans le cadre d'actifs actions.

## Clé
1.Traitement des données : il charge les données historiques sur les cours des actions à partir de fichiers CSV, s'adaptant aux scénarios dans lesquels des données pourraient manquer en vérifiant l'existence du fichier avant de tenter de le lire.

2.Daily returns et annualized returns :
Asset Daily Returns: calcule les variations quotidiennes en pourcentage des prix des actifs multipliées par les signaux de trading, indiquant la position de la stratégie (longue ou courte) ce jour particulier.

Multipliez le taux de variation quotidien (pourcentage de variation) du cours de clôture de chaque actif par son signal de trading correspondant (1 représente un achat, -1 représente une vente), ajustant ainsi la direction et la taille du rendement pour refléter la stratégie dans les performances de trading réelles.

Asset Annualized Returns: transforme les rendements quotidiens en un format annualisé pour comprendre la performance annuelle moyenne.

Calculez les rendements annualisés pour chaque actif en accumulant les rendements quotidiens et en les normalisant sur une période de négociation d'un an (252 jours) pour évaluer les performances de la stratégie ajustées en fonction du signal de négociation.

3.Volatilité :La classe calcule l'écart type des rendements quotidiens (volatilité), ce qui est crucial pour évaluer le risque associé à la stratégie de trading.

4.Indicateurs de performance :

Ratio de Sharpe : mesure le rendement de l'investissement ajusté au risque, aidant à comprendre la rentabilité par unité de risque.
Pour estimer le rendement excédentaire par unité de risque.

Valeurs bêta : calcule le risque systématique du portefeuille par rapport au marché, y compris des mesures distinctes pour les conditions lorsque le marché est en hausse et lorsqu'il est en baisse.
Le bêta global reflète le degré de corrélation d'un portefeuille avec la volatilité globale du marché. Beta up et bêta down calculent respectivement les valeurs bêta pendant les marchés haussiers et baissiers pour évaluer la sensibilité à la performance d'un portefeuille dans différentes conditions de marché.

5.Max Drawdown :
la Max Drawdown est une mesure du prix d'un actif depuis son sommet jusqu'à son creux, et est généralement utilisée pour évaluer le risque potentiel d'un actif. Cette méthode suit les sommets historiques des prix des actifs et calcule le pourcentage de baisse relative maximum entre ces sommets et les points les plus bas suivants pour obtenir le taux de retracement maximum, le stocke et le multiplie par 100 pour le convertir en pourcentage pour une compréhension plus intuitive et l'expression.

6.Stratégie :
La stratégie de trading SMA Crossover utilise des moyennes mobiles à court et à long terme pour générer des signaux d'achat et de vente. Lorsque la moyenne mobile à court terme (comme la moyenne sur 50 jours) croise la moyenne mobile à long terme (comme la moyenne sur 200 jours) par le bas, un signal d'achat est généré à l'inverse, lorsque la moyenne mobile à court terme ; passe en dessous de la moyenne mobile à long terme, un signal de vente est généré. Cette stratégie est adaptée pour profiter des tendances, en particulier sur les marchés aux tendances claires.

7.Visualisation :
Comprend des méthodes pour tracer les daily returns des actifs et de l’ensemble du portefeuille ainsi que la volatilité , offrant un aperçu visuel de la performance et du risque de la stratégie.

## Exemple d'utilisation 
Utilisez la classe Backtester pour effectuer un backtest d'une stratégie de trading basée sur des données historiques.
-Utilisez 'AAPL','AMZN','GOOGL'.('AAPL'domine le marché de l’électronique grand public. 'AMZN' représente le marché du commerce électronique et 'GOOGL' représente le marché de l'innovation technologique.)
-Téléchargez les données boursières pour une période de date personnalisée à partir de Yahoo Finance et enregistrez-les dans un fichier CSV local.
-Créez un objet Backtester et transmettez des données telles que le nom de l'action, le cours de clôture, le signal de trading, le poids, le taux sans risque et le rendement du marché.
-Exécutez la stratégie de trading nommée « strategy_a » (basée sur un simple croisement de moyenne mobile) et utilisez les données préparées.
-Résultats du calcul, y compris le taux de rendement quotidien de l'actif, le taux de rendement annualisé, la volatilité, le ratio de Sharpe, la valeur bêta, etc.
-Tracez les rendements quotidiens des actifs et des portefeuilles ainsi que la volatilité des portefeuilles.

