---
title: Adobe Sign des intégrations de produits Versions de produits et cycle de vie
description: En savoir plus sur les versions des intégrations Adobe Sign et la prise en charge du cycle de vie
audience: External
products: Adobe Sign
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: c1f22848-7951-4066-84d4-f8cf6c2f3a6f
source-git-commit: 30cb79b6856c7b623dc5118b4aa40193bf749220
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 40%

---

# Versions du produit et cycle de vie {#version}

La convention de contrôle des versions Adobe Sign et le cycle de vie de la prise en charge des services intégrés s’alignent sur d’autres produits d’Adobe que vous connaissez peut-être.

## Numéros de version

La version du package utilise un système de numérotation en trois parties pour identifier le numéro de version séquentiel de la version publiée et l’importation relative de la mise à niveau en termes de contenu nouveau ou modifié.

Le numéro de version suit ce modèle : N.m.p

Où, N = Version majeure ; m = version mineure ; p = Version corrigée.

Par exemple, la version 23.2.1 d’un package d’intégration indique l’état de la version de :

* Version majeure : 23
* Version mineure : 2
* Version du correctif : 1

Au fur et à mesure que les ingénieurs développent de nouvelles &quot;versions&quot; du pack, ils incrémentent le numéro de version en fonction de la nature des mises à jour du code.

* Les changements majeurs de version impliquent une ajout significative de fonctionnalités ou une modification importante des systèmes de base.
* Les mises à jour de version mineures comprennent des mises à jour de fonctionnalités plus réduites et des correctifs de sécurité. Adobe Sign peut nécessiter une mise à niveau vers la dernière version corrigée en cas de mises à jour de sécurité ou pour traiter un élément signalé.
* Les versions de correctifs sont presque exclusivement des correctifs de bugs et des ajustements de l’interface utilisateur.

>[!NOTE]
>
>Toutes les versions ne sont pas rendues publiques au fur et à mesure que le produit est en cours de développement. Il peut donc y avoir des sauts significatifs dans la version du correctif entre les versions.

Les administrateurs doivent conserver leur version à jour pour s’assurer que le compte a un accès complet à toutes les fonctionnalités et que tous les problèmes de sécurité connus sont corrigés. Adobe Sign peut nécessiter une mise à niveau vers la dernière version corrigée en cas de problème de sécurité ou pour résoudre un problème système critique.

## Cycle de vie de la prise en charge des versions

Le cycle de vie de la prise en charge des versions d’un produit d’intégration Adobe Sign est défini en fonction de la version principale du package et indique la période pendant laquelle Adobe Sign prend activement en charge la version individuelle de l’intégration.

Adobe Sign prend en charge la version actuelle d’un package et les deux versions principales précédentes (y compris toutes les mises à jour mineures et correctifs associées). Les versions majeures sont exprimées comme suit :

* Version actuelle (N) : la dernière version majeure du package.
* Version précédente (N-1) : une version majeure antérieure à la dernière version.
* Dernière version prise en charge (N-2) : deux versions majeures antérieures à la version actuelle.

Par exemple, si la version disponible actuelle du package est 23.2.1, alors :

* Version majeure actuelle (N) : 23.
* La version majeure précédente (N-1) de ce package est 22.
* Dernière version majeure prise en charge (N-2) de ce package : 21.
* Toutes les versions antérieures à la version 21.0.0 ne sont plus prises en charge.

![Représentation des versions](images/version_chart.png)

## Cycle de vie du service de version

Le cycle de vie du service de version définit la portée complète pendant tout le laps de temps où le service est utilisable. Le calendrier correspond au cycle de vie de la prise en charge des versions, plus une période de grâce de 90 jours qui permet aux clients de terminer leur mise à niveau.

* Pendant la période de grâce d’une version non prise en charge, la prise en charge est uniquement fournie pour la mise à niveau vers une version plus récente, et non pour la maintenance d’une version non prise en charge
* Après la période de grâce, la version n’est plus disponible

* Adobe Sign n’acceptera pas les requêtes provenant de versions hors service
* Une fois l’intégration mise à niveau vers la version actuelle, les communications entre Adobe Sign et l’intégration reprennent normalement

![Période d’arrêt](images/shutdown_period.png)

Si vous avez des questions, contactez votre revendeur ou le service clientèle.
