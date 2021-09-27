---
title: Notes de mise à jour d’Adobe Sign pour NetSuite
description: 'Découvrez les nouvelles fonctionnalités et modifications incluses dans la version actuelle de l’intégration Adobe Sign pour NetSuite.  '
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
source-git-commit: 924813403d8e13f816347dd548a68a16d78d866e
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 69%

---


# Notes de mise à jour d’Adobe Sign pour NetSuite

## Mise à jour du package v4.0.4

La version 4.0.4 est entièrement adaptée pour l’utilisation de domaines spécifiques au compte pour tout nouveau trafic généré.

L’icône Adobe Sign a été mise à jour avec la nouvelle image.

## Versions précédentes

### Adobe Sign pour NetSuite 4.0.4

La version 4.0.4 est entièrement adaptée pour l’utilisation de domaines spécifiques au compte pour tout nouveau trafic généré.

L’icône Adobe Sign a été mise à jour avec la nouvelle image.

### Adobe Sign pour NetSuite 4.0.2

Redéfini sur **Adobe Sign** (à partir des *services eSign de Adobe Document Cloud*)\
Vous verrez *Adobe Sign* où vous avez précédemment vu *Adobe eSign Services* comme preuve du changement de marque.

### Adobe Sign pour NetSuite 4.0.1

La sortie du nouveau package (v4.0.1) fait suite à une régression de l’API survenue lors de la mise à jour de la plateforme de NetSuite.

Nous conseillons à nos utilisateurs de procéder à la mise à jour.

### Adobe Sign pour NetSuite 4.0

**Ajout de la configuration automatique des utilisateurs via NetSuite**

Un système de préférences personnalisées a été ajouté à la version 4.0. Lorsque celles-ci sont activées, les utilisateurs qui envoient des accords dans NetSuite sont automatiquement configurés avec un compte utilisateur des services eSign d’Adobe Document Cloud.

**Certifié avec &quot;Construit pour NetSuite&quot;**

Cette version a obtenu l’homologation « Built for NetSuite » et applique toutes les meilleures pratiques récentes en matière de conception de NetSuite.

**Services eSign d’Adobe Document Cloud (auparavant EchoSign)**

Là où auparavant apparaissait « Adobe EchoSign », apparaît désormais « Services eSign d’Adobe Document Cloud » (ou « Services eSign d’Adobe »).

**Sécurité renforcée avec OAuth**

Pour renforcer la sécurité des données, les services eSign utilisent désormais OAuth 2.0 pour authentifier votre compte des services eSign d’Adobe Document Cloud dans NetSuite. Ce nouveau protocole permet à NetSuite de communiquer avec les services eSign sans avoir besoin de vous demander votre mot de passe pour les services eSign. Dans la mesure où les informations sensibles ne sont pas directement partagées entre les applications, votre compte est moins susceptible d’être piraté. Cette amélioration n’a aucune incidence sur votre mise en œuvre. Vous devrez toutefois effectuer une configuration unique pour autoriser votre package NetSuite à communiquer avec Adobe Document Cloud. Cette configuration est effectuée pendant le processus d’installation. Pour les utilisateurs qui mettent à jour une ancienne version du package (v3.5.9 et antérieures), la clé API utilisée est remplacée par un jeton OAuth, généré lors du processus d’autorisation.

**Migration des services eSign des API SOAP aux API REST**

Pour améliorer l’efficacité, la flexibilité et la vitesse de traitement, les services Adobe Document Cloud eSign, et par conséquent l’intégration v4.0 pour NetSuite, ont migré des API SOAP vers des API REST.

### Adobe Sign pour NetSuite 3.0

**Rôles avancés des participants - Approbateur**

* Le rôle d’approbateur peut être donné à plusieurs destinataires d’un accord.
* Les approbateurs doivent réviser et approuver le document.
* Les approbateurs peuvent également être amenés à ajouter des données à l’accord avant de l’approuver.

**Aperçu du document ou placement des champs de formulaire par glisser-déposer avant l’envoi**

Prévisualisez l’accord ou faites glisser et déposez les champs de formulaire avant de les envoyer pour signature.

**Envoi d’un rappel au signataire actuel**

Envoie un rappel immédiat au signataire actuel.

**Stratégies avancées d’authentification des signataires**

* **Authentification fondée sur les connaissances :** répondez aux questions pour vérifier l’identité des signataires.
   * Le signataire doit répondre à des questions visant à vérifier son identité. Ces questions sont extraites de centaines de bases de données publiques et commerciales.
   * Le nom pris en compte pour la signature est le nom authentifié de l’utilisateur. Celui-ci ne peut pas être modifié au moment de la signature.
   * Solution d’authentification RSA.
   * L’utilisation de l’authentification fondée sur les connaissances est limitée par compte et par mois. Pour plus d’informations, contactez le support commercial.

* **Identité Web :** connectez-vous avec Facebook, LinkedIn, Google ou un autre service Web tiers avant de signer.

   * Le signataire ne peut signer qu’après avoir vérifié son identité à l’aide d’un service Web tiers.
   * Le nom pris en compte pour la signature est celui qui figure sur le profil de service web de l’utilisateur. Celui-ci ne peut pas être modifié au moment de la signature.
   * Un journal d’audit enregistre les détails de la vérification d’identité.

* **Mot de passe à usage unique**
   * Appliquez certaines méthodes d’authentification selon si le signataire est interne, externe ou appliquez les à l’ensemble des signataires. Les signataires externes doivent utiliser un mot de passe ou utiliser l’authentification fondée sur les connaissances, contrairement aux signataires internes.

**Préférences personnalisées supplémentaires**

* Ajout d’un PDF signé en tant que lien vers l’URL !le ou en tant que pièce jointe hébergée dans NetSuite
* Ajoutez un journal d’audit à l’enregistrement de l’accord après la signature de celui-ci.
* Désignez le contact de transaction comme signataire par défaut, plutôt que l’adresse électronique du client.
* Autorisez les expéditeurs à donner aux destinataires le rôle d’approbateur.

**Fichiers de transaction**

Vous pouvez sélectionner les fichiers à joindre à partir de la transaction en cours avec la nouvelle liste déroulante &quot;Fichiers de transaction&quot;.

**Certification Adobe PDF pour tous les documents EchoSign**

* Tous les fichiers PDF envoyés ou téléchargés depuis EchoSign seront certifiés avec un certificat numérique Adobe EchoSign
* Acrobat ou Reader affichera la certification garantissant que le document n&#39;a pas été falsifié pour plus de confiance et de tranquillité d&#39;esprit.

**Collecte de documents annexes**

* Les expéditeurs ont la possibilité de récupérer des pièces justificatives supplémentaires de la part des signataires, au moment de la signature (permis de conduire, extrait K-bis, etc.)
* Les documents ainsi récupérés sont ajoutés à l’enregistrement officiel de l’accord signé.

**Champs de données conditionnels**

* Définissez la logique conditionnelle pour les champs de l’accord.
* Les conditions peuvent reposer sur les valeurs d’un ou plusieurs champs de l’accord.
* Les conditions peuvent être définies via l’interface de création de formulaires à glisser-déposer ou via des balises de texte.
* Le signataire se voit présenter les champs appropriés lors de la signature d’un document en fonction des conditions de De ! ned.

**Autres améliorations de champs de formulaires EchoSign**

* Menus déroulants
* Masquage de champs
* Cases d’option
* Créez des balises de textes plus courtes pour garder la structure du document.
