# COVID-19 Notes de mise à jour

> ***N.B.*** : Ce document est uniquement destiné à ceux qui installent la nouvelle version (v0.3.x) du paquet indiqué par rapport à la version précédente (v0.2/v0.1). Veuillez consulter les instructions d'installation complètes si vous installez sur une nouvelle instance.
>
> Instructions d'installation complètes :
>
> [Surveillance basée sur des cas et Recherche de contacts](https://docs.google.com/document/d/1iILgYYYDXDKpizkxY08syMfrw_9POzMMIMwd5Nb7yl4/edit?usp=sharing)
>
>[Programme de surveillance des événements](https://docs.google.com/document/d/1eY3n_oJlHoZroL_gXYRJoKwsFK4JSslnAk1DN-gBlxs/edit?usp=sharing)
>
> [Rapports de surveillance agrégés](https://docs.google.com/document/d/1zQxrtc5qWf8L4pk8dzOXBbyKF0XZcBiwHMJ4rNhkrds/edit?usp=sharing)


## Surveillance basée sur des cas & le Paquet de recherche des contacts, le Programme des événements de surveillance

Vous pouvez installer ces progiciels (v0.3.3/v.0.3.2) directement au dessus du paquet existant. Comme toujours, cela doit être fait dans un environnement de test et de développement.

1. Renommer le type d'indicateur "pourcentage" actuel (par exemple [supprimer] - Pourcentage)
2. Importez les nouveaux paquets dans l'ordre suivant si vous installez plusieurs paquets
    1. Surveillance basée sur des cas : + Enregistrement et suivi de la recherche des contacts : v0.3.3 sont intégrés dans un seul paquet
    2. Programme de surveillance des événements : v0.3.2
3. Supprimez le type d'indicateur de pourcentage que vous avez renommé

Si vous n'installez qu'un des paquets et non les deux, vous pouvez importer le paquet unique après avoir renommé l'indicateur, puis supprimer le type d'indicateur précédent après son importation.

Il s'agit de veiller à l'alignement des types d'identification des indicateurs dans l'ensemble des agrégats et les ensembles de suivi.

## Rapport de surveillance globale

Vous pouvez installer ce paquet (v0.3.2) directement au dessus du paquet existant (v0.1). Comme toujours, cela doit être fait dans un environnement de test et de développement.

1. Lors de l'importation de ce paquet, utilisez le mode de fusion "Remplacer" plutôt que "Fusionner". Fusionner est le mode par défaut, vous devrez donc le changer lors de l'importation, ou le définir si vous importez via l'API.

![Mode de fusion : Remplacer](img/merge-mode-replace.png "Mode de fusion : Choisissez Remplacer")

1. Une fois que vous avez importé ce paquet, effectué les opérations suivantes :
    1. Accès à l'application Administration des données
    2. Allez à "Maintenance"
    3. Sélectionnez "Effacer le cache des applications" et "Recharger les applications".
    4. Sélectionnez "Effectuer la maintenance"
