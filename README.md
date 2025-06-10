# Segmentation Clientèle - Online Retail Dataset

Ce projet vise à réaliser une segmentation clientèle basée sur l'historique des transactions d'une entreprise de vente au détail en ligne. La problématique métier choisie est **d'identifier des groupes de clients distincts afin d'adapter les stratégies marketing et d'améliorer la fidélisation.**

---

## Contexte du Projet

Dans un marché concurrentiel, comprendre les différents types de clients est crucial pour le succès d'une entreprise. La segmentation clientèle permet de diviser une base de clients hétérogène en sous-groupes homogènes. Chaque segment peut ensuite être ciblé avec des offres, des communications et des stratégies marketing personnalisées, maximisant ainsi l'efficacité des campagnes et optimisant l'allocation des ressources.

---

## Problématique Métier Détaillée

Notre objectif est de répondre à la question suivante : 
> Comment pouvons-nous regrouper nos clients en fonction de leur comportement d'achat pour mieux comprendre leurs besoins et optimiser nos actions marketing ?

Plus précisément, nous chercherons à :

-   Identifier les segments de clients les plus rentables pour des programmes de fidélité ou des offres VIP.
-   Détecter les clients à risque de désabonnement (churn) afin de mettre en place des stratégies de rétention proactives.
-   Cibler les clients avec des promotions spécifiques basées sur leurs préférences d'achat passées (e.g., promotions croisées, ventes incitatives).
-   Personnaliser l'expérience client en adaptant les communications et les recommandations de produits.

--- 

## Le Jeu de Données : Online Retail

Le jeu de données utilisé pour ce projet est le Online Retail Dataset. Il contient l'historique des transactions d'une entreprise de vente au détail basée au Royaume-Uni.

Source : UCI Machine Learning Repository


**Description des colonnes clés :**

`InvoiceNo`: Numéro de facture. Chaque transaction reçoit un numéro unique. Les numéros commençant par 'C' indiquent une annulation.
`StockCode`: Code article.
`Description`: Description de l'article.
`Quantity`: Quantité de chaque article par transaction. Peut être négative pour les retours.
`InvoiceDate`: Date et heure de la facture.
`UnitPrice`: Prix unitaire de l'article.
`CustomerID`: Identifiant unique du client. Les transactions sans CustomerID seront ignorées pour la segmentation.
`Country`: Nom du pays où la transaction a eu lieu.

---

## Objectif et métrique

- **Objectif technique du projet:** Faire une **segmentation RFM** sur la clientèle de cette entreprise 

    - **R** --> Récence (Nombre de jours depuis la dernière commande)
    - **F** --> Fréquence (Nombre total de commandes de décembre 2010 à décembre 2011)
    - **M** --> Montant (montant total dépensé)

    Le but est d'identifier:
    - Les **plus fidèles**,
    - Les **plus rentables**, 
    - Ceux à **réactiver**,
    - Ceux qui **risquent de partir**

- **Métrique:** Comme il s'agit d'un apprentissage non-supervisé (clustering), nous voulons juste minimiser **l'inertia** (variance) entre les points d'un cluster.

---

## Approche methodologique

Le projet suivra les étapes suivantes:

1. **Nettoyage des Données :**

- Gestion des valeurs manquantes (notamment CustomerID).
- Traitement des transactions annulées et des quantités/prix négatifs.
- Analyse de la distribution des variables clés.

2. **Ingénierie des Caractéristiques (Feature Engineering) et Analyse du nouveau dataset :**

- Calcul de métriques RFM (Récence, Fréquence, Montant) pour chaque client.
    - Récence (R) : Nombre de jours depuis le dernier achat.
    - Fréquence (F) : Nombre total de transactions.
    - Montant (M) : Somme totale dépensée.

- Analyse exploratoire des liens entre **les nouvelles variables ( Récence, fréquence, montant).**

3. **Mise à l'échelle des Données (Scaling) :**

- Normalisation ou standardisation des caractéristiques RFM pour éviter que certaines caractéristiques ne dominent l'algorithme de clustering.

4. **Clustering :**

- Application d'algorithmes de clustering non supervisé tels que K-Means pour regrouper les clients.
- Détermination du nombre optimal de clusters à l'aide de méthodes comme la méthode du coude ou le coefficient de silhouette.

5. **Analyse et Interprétation des Segments :**

- Caractérisation de chaque cluster en fonction de ses métriques RFM moyennes et d'autres comportements d'achat.
- Attribution de noms descriptifs à chaque segment (e.g., "Clients VIP", "Nouveaux Clients", "Clients à risque").

6. **Recommandations Marketing :**
Formulation de stratégies marketing concrètes et adaptées à chaque segment identifié.

---

## Technologies Utilisées

- **Python**
- **Pandas** : Manipulation et analyse de données.
- **NumPy** : Opérations numériques.
- **Scikit-learn** : Algorithmes de clustering (K-Means), préprocessing des données.
- **Matplotlib / Seaborn / plotly** : Visualisation des données.

##  Organisation du projet

```bash
Customer_segmentation/
│
├── Online Retail.xlsx                      # Données (Dataset)
├── README.md                                  # Documentation
├── Visualisation3D_clientèle               # Image de la visualisation 3D de la clientèle
├── Visualisation3D_clientèle_segmentée      # Image de la visualisation 3D de la clientèle segmentée
├── segmentation.ipynb                       # Jupyter notebook (EDA, modèle, etc.)
├── requirements.txt                         # Bibliothèques nécessaires          
