---
layout: Publier
title: "Indicateurs de performance centrés sur l'utilisateur"
authors:
  - philipwalton
date: '2019-11-08'
description: |2

 "Les mesures de performance centrées sur l'utilisateur sont un outil essentiel pour comprendre et"

 "améliorer l'expérience de votre site d'une manière qui profite à de vrais"

  utilisateurs.
tags:
  - performance
  - métrique
---

Nous avons tous entendu à quel point la performance est importante. Mais quand nous parlons de performances et de rendre les sites Web « rapides », qu'entendons-nous précisément par là ?

La vérité est que la performance est relative :

- Un site peut être rapide pour un utilisateur (sur un réseau rapide avec un appareil puissant) mais lent pour un autre utilisateur (sur un réseau lent avec un appareil bas de gamme).
- Deux sites peuvent terminer le chargement dans exactement le même laps de temps, mais l'un peut *sembler* se charger plus rapidement (s'il charge le contenu progressivement plutôt que d'attendre la fin pour afficher quoi que ce soit).
- Un site peut *sembler* se charger rapidement, mais ensuite répondre lentement (ou pas du tout) à l'interaction de l'utilisateur.

Ainsi, lorsqu'on parle de performance, il est important d'être précis et de se référer à la performance en termes de critères objectifs qui peuvent être mesurés quantitativement. Ces critères sont appelés *métriques* .

Mais juste parce qu'une métrique est basée sur des critères objectifs et peut être mesurée quantitativement, cela ne signifie pas nécessairement que ces mesures sont utiles.

## Définir des métriques

Historiquement, les performances Web ont été mesurées avec l'événement <code>[load](https://developer.mozilla.org/en-US/docs/Web/API/Window/load_event)</code> Cependant, même si le <code>load</code> est un moment bien défini dans le cycle de vie d'une page, ce moment ne correspond pas nécessairement à tout ce qui intéresse l'utilisateur.

Par exemple, un serveur peut répondre avec une page minimale qui se « charge » immédiatement, mais reporte ensuite la récupération du contenu et l'affichage de quoi que ce soit sur la page jusqu'à plusieurs secondes après le déclenchement de l'événement de `load` Bien qu'une telle page puisse techniquement avoir un temps de chargement rapide, ce temps ne correspondrait pas à la façon dont un utilisateur expérimente réellement le chargement de la page.

Au cours des dernières années, les membres de l'équipe Chrome, en collaboration avec le [groupe de travail sur les performances Web](https://www.w3.org/webperf/) du W3C, ont travaillé à la normalisation d'un ensemble de nouvelles API et métriques qui mesurent plus précisément la manière dont les utilisateurs perçoivent les performances d'une page Web.

Pour nous assurer que les métriques sont pertinentes pour les utilisateurs, nous les encadrons autour de quelques questions clés :

<table id="questions">
  <tr>
    <td><strong>Est-ce que ça se passe?</strong></td>
    <td>La navigation a-t-elle démarré avec succès ? Le serveur a répondu ?</td>
  </tr>
  <tr>
    <td><strong>Est-ce utile?</strong></td>
    <td>Assez de contenu rendu pour que les utilisateurs puissent s'y engager ?</td>
  </tr>
  <tr>
    <td><strong>Est-ce utilisable ?</strong></td>
    <td>Les utilisateurs peuvent-ils interagir avec la page ou est-elle occupée ?</td>
  </tr>
  <tr>
    <td><strong>Est-ce délicieux ?</strong></td>
    <td>Les interactions sont-elles fluides et naturelles, sans décalage ni saccade ?</td>
  </tr>
</table>

## Comment les métriques sont mesurées

Les mesures de performance sont généralement mesurées de l'une des deux manières suivantes :

- **En labo :** utiliser des outils pour simuler un chargement de page dans un environnement cohérent et contrôlé
- **Sur le terrain** : sur de vrais utilisateurs chargeant et interagissant réellement avec la page

Aucune de ces options n'est nécessairement meilleure ou pire que l'autre. En fait, vous souhaitez généralement utiliser les deux pour garantir de bonnes performances.

### Dans le laboratoire

Tester les performances en laboratoire est essentiel lors du développement de nouvelles fonctionnalités. Avant que les fonctionnalités ne soient publiées en production, il est impossible de mesurer leurs caractéristiques de performances sur de vrais utilisateurs. Par conséquent, les tester en laboratoire avant la publication de la fonctionnalité est le meilleur moyen d'éviter les régressions de performances.

### Sur le terrain

D'un autre côté, bien que les tests en laboratoire soient un indicateur raisonnable des performances, ils ne reflètent pas nécessairement la façon dont tous les utilisateurs perçoivent votre site dans la nature.

Les performances d'un site peuvent varier considérablement en fonction des capacités de l'appareil de l'utilisateur et des conditions de son réseau. Cela peut également varier selon si (ou comment) un utilisateur interagit avec la page.

De plus, les chargements de pages peuvent ne pas être déterministes. Par exemple, les sites qui chargent du contenu ou des publicités personnalisés peuvent présenter des caractéristiques de performances très différentes d'un utilisateur à l'autre. Un test de laboratoire ne saisira pas ces différences.

La seule façon de vraiment savoir comment votre site fonctionne pour vos utilisateurs est de mesurer réellement ses performances au fur et à mesure que ces utilisateurs le chargent et interagissent avec lui. Ce type de mesure est communément appelé [Real User Monitoring,](https://en.wikipedia.org/wiki/Real_user_monitoring) ou RUM en abrégé.

## Types de métriques

Il existe plusieurs autres types de métriques qui sont pertinentes pour la façon dont les utilisateurs perçoivent les performances.

- **Vitesse de chargement perçue : à** quelle vitesse une page peut-elle charger et afficher tous ses éléments visuels à l'écran.
- **Réactivité au chargement : à** quelle vitesse une page peut-elle charger et exécuter tout code JavaScript requis afin que les composants répondent rapidement à l'interaction de l'utilisateur
- **Réactivité à l'exécution :** après le chargement de la page, à quelle vitesse la page peut-elle répondre à l'interaction de l'utilisateur.
- **Stabilité visuelle :** les éléments de la page changent-ils d'une manière inattendue et interfèrent-ils potentiellement avec leurs interactions ?
- **Fluidité :** les transitions et les animations sont-elles rendues à une fréquence d'images constante et passent-elles de manière fluide d'un état à l'autre ?

Compte tenu de tous les types de mesures de performances ci-dessus, il est clair qu'aucune mesure unique n'est suffisante pour capturer toutes les caractéristiques de performances d'une page.

## Des métriques importantes à mesurer

- **[First contentful paint (FCP)](/fcp/) :** mesure le temps écoulé entre le début du chargement de la page et le moment où une partie du contenu de la page est affichée à l'écran. *( [laboratoire](#in-the-lab) , [terrain](#in-the-field) )*
- **[La plus grande peinture de contenu (LCP)](/lcp/) :** mesure le temps entre le début du chargement de la page et le rendu du plus grand bloc de texte ou élément d'image à l'écran. *( [laboratoire](#in-the-lab) , [terrain](#in-the-field) )*
- **[Délai de première entrée (FID)](/fid/) :** mesure le temps entre le moment où un utilisateur interagit pour la première fois avec votre site (c'est-à-dire lorsqu'il clique sur un lien, appuie sur un bouton ou utilise un contrôle personnalisé alimenté par JavaScript) jusqu'au moment où le navigateur est réellement capable pour répondre à cette interaction. *( [champ](#in-the-field) )*
- **[Time to Interactive (TTI)](/tti/) :** mesure le temps écoulé entre le début du chargement de la page et son rendu visuel, le chargement de ses scripts initiaux (le cas échéant) et sa capacité à répondre rapidement et de manière fiable aux entrées de l'utilisateur. *( [laboratoire](#in-the-lab) )*
- **[Temps de blocage total (TBT)](/tbt/) :** mesure le temps total entre FCP et TTI où le thread principal a été bloqué suffisamment longtemps pour empêcher la réactivité des entrées. *( [laboratoire](#in-the-lab) )*
- **[Changement de mise en page cumulatif (CLS)](/cls/) :** mesure le score cumulé de tous les changements de mise en page inattendus qui se produisent entre le début du chargement de la page et le moment où son [état de cycle de vie](https://developers.google.com/web/updates/2018/07/page-lifecycle-api) passe à masqué. *( [laboratoire](#in-the-lab) , [terrain](#in-the-field) )*

Bien que cette liste comprenne des métriques mesurant de nombreux aspects des performances pertinents pour les utilisateurs, elle n'inclut pas tout (par exemple, la réactivité et la fluidité de l'exécution ne sont pas actuellement couvertes).

Dans certains cas, de nouvelles métriques seront introduites pour couvrir les zones manquantes, mais dans d'autres cas, les meilleures métriques sont celles spécifiquement adaptées à votre site.

## Métriques personnalisées

Les mesures de performances répertoriées ci-dessus sont utiles pour obtenir une compréhension générale des caractéristiques de performances de la plupart des sites Web. Ils sont également utiles pour disposer d'un ensemble commun de mesures permettant aux sites de comparer leurs performances à celles de leurs concurrents.

Cependant, il peut arriver qu'un site spécifique soit unique d'une manière ou d'une autre, nécessitant des métriques supplémentaires pour capturer l'image complète des performances. Par exemple, la métrique LCP est destinée à mesurer quand le contenu principal d'une page a fini de se charger, mais il peut y avoir des cas où le plus grand élément ne fait pas partie du contenu principal de la page et donc LCP peut ne pas être pertinent.

Pour résoudre de tels cas, le groupe de travail sur les performances Web a également standardisé des API de niveau inférieur qui peuvent être utiles pour implémenter vos propres métriques personnalisées :

- [API de chronométrage utilisateur](https://w3c.github.io/user-timing/)
- [API de tâches longues](https://w3c.github.io/longtasks/)
- [API de synchronisation des éléments](https://wicg.github.io/element-timing/)
- [API de synchronisation de navigation](https://w3c.github.io/navigation-timing/)
- [API de synchronisation des ressources](https://w3c.github.io/resource-timing/)
- [Synchronisation du serveur](https://w3c.github.io/server-timing/)

Reportez-vous au guide sur les [métriques personnalisées](/custom-metrics/) pour savoir comment utiliser ces API pour mesurer les caractéristiques de performances spécifiques à votre site.
