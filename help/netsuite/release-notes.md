---
title: Notes de mise à jour d’Adobe Sign pour NetSuite
description: Découvrez les nouvelles fonctionnalités et les modifications de la version actuelle de l’intégration Adobe Sign pour NetSuite.
type: Documentation
solution: Acrobat Sign, Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 6317723e-447a-4506-a621-4d967bdd6561
source-git-commit: b326a9afa2c16333d390cac3b30a2c7c741a4360
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 49%

---

# Notes de mise à jour d’Adobe Sign pour NetSuite

## Mise à jour vers le package v4.0.4

La version 4.0.4 est entièrement adaptée pour l’utilisation de domaines spécifiques au compte pour tout nouveau trafic généré.

L’icône Adobe Sign a été mise à jour avec la nouvelle image.

## Versions précédentes

### Adobe Sign pour NetSuite 4.0.4

La version 4.0.4 est entièrement adaptée pour l’utilisation de domaines spécifiques au compte pour tout nouveau trafic généré.

L’icône Adobe Sign a été mise à jour avec la nouvelle image.

### Adobe Sign pour NetSuite 4.0.2

Nouvelle image de marque **Adobe Sign** (de *Services eSign de Adobe Document Cloud*)\
Vous voyez maintenant *Adobe Sign* où vous avez précédemment vu *Services eSign Adobe* comme preuve du changement de marque.

### Adobe Sign pour NetSuite 4.0.1

La sortie du nouveau package (v4.0.1) fait suite à une régression de l’API survenue lors de la mise à jour de la plateforme de NetSuite.

Nous conseillons à nos utilisateurs de procéder à la mise à jour.

### Adobe Sign pour NetSuite 4.0

**Ajout de la configuration automatique des utilisateurs via NetSuite**

Une nouvelle préférence personnalisée a été ajoutée pour la version 4.0. Lorsque cette option est activée, les utilisateurs qui envoient des accords dans NetSuite sont automatiquement configurés avec un compte d’utilisateur des services eSign de Adobe Document Cloud.

**Certifié &quot;Conçu pour NetSuite&quot;**

Cette version a obtenu la certification &quot;Conçu pour NetSuite&quot; et respecte toutes les meilleures pratiques de conception NetSuite les plus récentes.

**Services eSign d’Adobe Document Cloud (auparavant EchoSign)**

Vous voyez maintenant les services eSign de Adobe Document Cloud (ou les services eSign d’Adobe pour faire court) où vous voyiez auparavant Adobe EchoSign comme une preuve du changement de marque.

**Sécurité renforcée avec OAuth**

Pour améliorer la sécurité des données, les services eSign utilisent désormais OAuth 2.0 pour authentifier votre compte des services eSign Adobe Document Cloud dans NetSuite. Ce nouveau protocole permet à NetSuite de communiquer avec les services eSign sans avoir besoin de vous demander votre mot de passe pour les services eSign. Dans la mesure où les informations sensibles ne sont pas directement partagées entre les applications, votre compte est moins susceptible d’être piraté. Cette amélioration n’a aucune incidence sur votre implémentation, mais vous devez effectuer une configuration unique pour autoriser votre package NetSuite à communiquer avec Adobe Document Cloud. Cette configuration est effectuée pendant le processus d’installation. Pour les clients effectuant une mise à niveau à partir d’une version précédente du package (v3.5.9 et versions antérieures), la clé API précédemment utilisée est remplacée par un jeton OAuth généré pendant le processus d’autorisation.

**Migration des services eSign des API SOAP aux API REST**

Afin d’améliorer l’efficacité, la flexibilité et la vitesse de traitement, les services eSign de Adobe Document Cloud, et par conséquent l’intégration v4.0 pour NetSuite, ont migré des API SOAP vers les API REST.

### Adobe Sign pour NetSuite 3.0

**Rôles avancés des participants - Approbateur**

* Le rôle d’approbateur peut être donné à plusieurs destinataires d’un accord.
* Les approbateurs doivent réviser et approuver le document
* Les approbateurs peuvent également être amenés à ajouter des données à l’accord avant de l’approuver.

**Aperçu du document ou placement des champs de formulaire par glisser-déposer avant l’envoi**

Prévisualiser l’accord ou faire glisser et déposer les champs de formulaire avant l’envoi pour signature

**Envoi d’un rappel au signataire actuel**

Envoie un rappel immédiat au signataire actuel.

**Stratégies avancées d’authentification des signataires**

* **Authentification fondée sur les connaissances :** Répondez aux questions pour vérifier l’identité du signataire
   * Le signataire doit répondre à des questions visant à vérifier son identité. Ces questions sont extraites de centaines de bases de données publiques et commerciales.
   * Le nom pris en compte pour la signature est le nom authentifié de l’utilisateur. Celui-ci ne peut pas être modifié au moment de la signature.
   * Solution d’authentification RSA.
   * L’utilisation de l’authentification fondée sur les connaissances est limitée par compte et par mois. Pour plus d’informations, contactez le support commercial.

* **Identité web :** Connectez-vous avec Facebook, LinkedIn, Google ou un autre service web tiers avant de signer.

   * Le signataire ne peut signer qu’après avoir vérifié son identité à l’aide d’un service Web tiers.
   * Le nom pris en compte pour la signature est celui qui figure sur le profil de service web de l’utilisateur. Celui-ci ne peut pas être modifié au moment de la signature.
   * Un journal d’audit enregistre les détails de la vérification d’identité.

* **Mot de passe à usage unique**
   * Appliquez certaines méthodes d’authentification selon si le signataire est interne, externe ou appliquez les à l’ensemble des signataires. Les signataires externes doivent utiliser un mot de passe ou une authentification fondée sur les connaissances, contrairement aux signataires internes.

**Préférences personnalisées supplémentaires**

* Ajouter le mot de PDF signé en tant que lien vers l’URL ou pièce jointe hébergée dans NetSuite
* Ajoutez un journal d’audit à l’enregistrement de l’accord après la signature de celui-ci.
* Utiliser le contact de transaction comme signataire par défaut, au lieu de l’adresse e-mail du client
* Autorisez les expéditeurs à donner aux destinataires le rôle d’approbateur.

**Fichiers de transaction**

Vous pouvez sélectionner les fichiers à joindre à partir de la transaction actuelle avec la nouvelle liste déroulante &quot;Fichiers de transaction&quot;.

**Certification Adobe PDF pour tous les documents EchoSign**

* Tous les fichiers de PDF envoyés ou téléchargés depuis EchoSign sont certifiés avec un certificat numérique Adobe EchoSign
* Acrobat ou Reader affiche la certification garantissant que le document n’a pas été falsifié pour plus de fiabilité et de tranquillité d’esprit

**Collecte de documents annexes**

* Les expéditeurs peuvent collecter des documents supplémentaires auprès des signataires pendant la signature, tels qu’un permis de conduire, un certificat professionnel, etc.
* Les documents ainsi récupérés sont ajoutés à l’enregistrement officiel de l’accord signé.

**Champs de données conditionnels**

* Définissez la logique conditionnelle pour les champs de l’accord.
* Les conditions peuvent reposer sur les valeurs d’un ou plusieurs champs de l’accord.
* Les conditions peuvent être définies via l’interface de création de formulaires à glisser-déposer ou via des balises de texte.
* Les champs appropriés sont présentés au signataire lors de la signature d&#39;un document en fonction des conditions de ! end

**Autres améliorations de champs de formulaires EchoSign**

* Menus déroulants
* Masquage de champs
* Cases d’option
* Créez des balises de textes plus courtes pour garder la structure du document.
