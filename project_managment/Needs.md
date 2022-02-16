> [Home](../../README.md) > [Documentation](../README.md)

# Expression du besoin

## Spécification

Pour encourager les utilisteurs a ne pas tous se déplacer, noous souhaitons mettre en place un système de *royalties* afin de soutenir l'utilisateur qui se déplacerai vers les points de collectes.

Afin de faciliter le déplacement des utilisateurs vers les points de collecte et les collectes en praticuliers, nous souhaitons mettre en place un système qui ouvrirait automatiquement le point dans l'application GPS par défault du support.

Les points de collecte serait collaboratif c.a.d que ce sont les utilisateurs qui propose un nouveau point de collecte découvert.

### Technologies

Cette application serait accessible sur smartphone. En effet nous souhaitons palier à un probléme de mobilité afin de pousser les utilisateurs à mieux trier mais cela implique un déplacement.

Finalement : 
- Frontend : ReactNative, technoligie web adapter au smartphone car cela permet d'utiliser les fonctionnalités natives de ces dispositifs.
- Backend : Python Django
- Base de donnée : PostgreSQL

Autre technologie : 
- Git : versionning de code source
- Docker : pour faciliter la compatibilité de certains outil entre différents système

## Fonctionnalité

### MVP

En temps qu'utilisateur je souhaite pouvoir : 
- Afficher les points de collecte
- Filtrer les points de collecte
    + en fonction d'un rayon
    + en fonction de type de déchets
- Proposer un nouveau point de collecte
- Noter/signaler un point de collecte qui ne serait pas conforme (inexistant, ne correspondant pas à la description des déchets pris en compte)
- Voir les conseils/informations lié à un déchets : 
    + informations sur le recyclage d'un déchets (% de ce qui est réellement recycler)
    + conseil sur des produits plus vertueux
- Créer une collecte en particulier
- Accéder facilement à mon GPS pour me rendre au point de collecte

En temps qu'administrateur, je souhaite pouvoir :
- Valider un point de collecte proposer par un utilisteur
- Ajouter une type de déchets / catégorie

### Secondaire

En temps qu'utilisateur je souhaite pouvoir : 
- Voir les statistiques liés à mon recyclage (bilan carbone)