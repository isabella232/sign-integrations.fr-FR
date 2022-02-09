---
title: Guide de l'utilisateur Veeva Vault
description: Guide de l'utilisateur de Veeva Vault sur l'intégration d'Adobe Sign avec Veeva
products: Adobe Sign
content-type: reference
locnotes: All languages; screenshots to follow what's there already (seems there is a mix within a given language version of the article)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 39a43637-af3f-432e-a784-8f472aa86df5
source-git-commit: e1394c24aebd1e026eb6c5a33935149f33ef8ea4
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 1%

---

# Adobe Sign pour [!DNL Veeva Vault]: Guide utilisateur {#veeva-vault-user-guide}

[**Contacter le support technique Adobe Sign**](https://adobe.com/go/adobesign-support-center_fr)

Ce document est conçu pour vous aider [!DNL Veeva Vault] les clients découvrent comment utiliser Adobe Sign pour [!DNL Veeva Vault] pour envoyer un accord.

## Présentation {#overview}

Intégration d&#39;Adobe Sign avec [!DNL Veeva Vault] facilite le processus d’obtention d’une signature ou d’une approbation pour tout document nécessitant des signatures légales ou un traitement de document vérifiable.

Le processus global d’envoi de documents pour signature est similaire à l’envoi d’un e-mail, il est donc facile à adopter pour la plupart des utilisateurs.

Intégration d&#39;Adobe Sign avec [!DNL Veeva Vault] rationalise et accélère vos workflows documentaires et de signature. En utilisant le flux de travaux d’intégration, vous :

* Gagnez du temps et économisez des ressources dans le courrier postal, la nuit et les télécopies.
* Envoyer des contrats pour signature électronique ou approbation depuis [!DNL Veeva Vault], accédez à l’historique des contrats en temps réel et consultez les contrats enregistrés.
* Suivez les transactions en temps réel dans l’ensemble de votre organisation et recevez des informations à jour lorsque les accords sont consultés, signés, annulés ou refusés.
* eSign dans plus de 20 langues et prise en charge du service de télécopie dans plus de 50 langues dans le monde.
* Créer des modèles d’accord réutilisables pour les options d’envoi.

## Envoyer un accord à l’aide d’Adobe Sign pour [!DNL Veeva Vault] {#send-sign-vault-agreement}

Pour envoyer un accord à l’aide d’Adobe Sign pour Veeva :

1. Accédez à l’onglet [[!DNL Veeva Vault] page de connexion](https://login.veevavault.com/) et entrez votre nom d’utilisateur et votre mot de passe. Elle ouvre la page d&#39;accueil de votre chambre forte, comme indiqué ci-dessous.

   ![](images/vault-home.png)

1. Sélectionner **[!UICONTROL Bibliothèque]** , puis sélectionnez **[!UICONTROL Créer]** dans le coin supérieur droit.

   ![](images/create-library.png)

1. Sélectionner **[!UICONTROL Télécharger et continuer]**.

1. Chargez n’importe quel document à partir de votre lecteur local.

1. Dans la boîte de dialogue qui s’affiche, sélectionnez **[!UICONTROL Type]** comme *[!UICONTROL Clinique]* , puis sélectionnez un élément **[!UICONTROL Sous-type]** et **[!UICONTROL Classification]**, si nécessaire.

   ![](images/choose-document-type.png)

1. Sélectionner **[!UICONTROL Ok]** pour fermer la boîte de dialogue.

1. Sélectionner **[!UICONTROL Suivant]**.

1. Dans la fenêtre qui s’affiche, renseignez tous les champs requis dans la section Métadonnées et sélectionnez **[!UICONTROL Enregistrer]**.

   ![](images/metadata-details.png)

1. Il crée un document test dans **[!UICONTROL Brouillon]** , comme illustré ci-dessous.

   ![](images/document-draft.png)

1. Dans le coin supérieur droit, sélectionnez ![icône de roue dentée](images/icon-gear.png) , puis sélectionnez **[!UICONTROL Commencer la révision]**.

   ![](images/start-review.png)

1. Sélectionnez le fichier **[!UICONTROL Réviseur]** et **[!UICONTROL Date d&#39;échéance]**.

1. Sélectionner **[!UICONTROL Début]**. L’état du document est remplacé par [!UICONTROL EN COURS DE RÉVISION].

   ![](images/in-review.png)

1. Effectuez la tâche affectée au nom des réviseurs. Une fois que vous avez terminé, l’état du document est remplacé par [!UICONTROL RÉVISÉ].

   ![](images/reviewed-status.png)

1. Sélectionner ![icône de roue dentée](images/icon-gear.png) , puis sélectionnez **[!UICONTROL Adobe Sign]**.

   ![](images/select-adobe-sign.png)

1. Dans la fenêtre iFrame qui s’ouvre dans Vault, saisissez l’adresse e-mail du destinataire et sélectionnez **[!UICONTROL Suivant]**.

   ![](images/iframe.png)

   **Remarque :** S’il n’existe aucun compte utilisateur Adobe Sign pour l’adresse e-mail de l’expéditeur, la fenêtre iFrame affiche un message, comme indiqué ci-dessous. Il envoie également à l’utilisateur un e-mail contenant les instructions d’activation du compte.

   ![](images/iFrame-registration-message.png)

   ![](images/iFrame-confirm-email.png)

   Toutefois, si *Configurer automatiquement les utilisateurs Sign* est désactivée, la création d’utilisateurs Adobe Sign échoue et la fenêtre iFrame affiche un message demandant à l’utilisateur de contacter son administrateur de compte Adobe Sign. L’administrateur de compte Adobe Sign peut effectuer l’une des actions suivantes :

   * Activez la *Configurer automatiquement les utilisateurs Sign* pour le compte.
   * Créez l’utilisateur dans Adobe Sign avant d’utiliser l’intégration Veeva Vault Adobe Sign.

   ![](images/iFrame-contact-administrator.png)

1. Une fois le document traité, faites glisser les champs de signature depuis le panneau de droite et sélectionnez **[!UICONTROL Envoyer]**.

   ![](images/add-signature-fields.png)

1. Il envoie le document au destinataire pour signature. Une fois que le destinataire reçoit l’e-mail du document, l’état du document change de [!UICONTROL Révisé] à [!UICONTROL En Adobe Signature].

   ![](images/in-adobe-signing.png)

1. Une fois toutes les signatures capturées et complétées dans Adobe Sign, le statut du document dans le coffre devient [!UICONTROL Approuvé].

1. Sélectionner **[!UICONTROL Fichiers document]** et développez l&#39;élément **[!UICONTROL Rendus]** dans le coffre-fort. Une fois le document approuvé, un nouveau format associé nommé &quot;Adobe Sign Format associé&quot; est automatiquement créé.

   ![](images/document-files.png)

1. Téléchargez le rendu Adobe Sign pour valider la signature du destinataire.

   ![](images/verify-signature.png)

## Annulation d’un accord avec Adobe Sign pour [!DNL Veeva Vault] {#cancel-sign-vault-agreement}

1. Accédez à l’onglet [[!DNL Veeva Vault] page de connexion](https://login.veevavault.com/) et entrez votre nom d’utilisateur et votre mot de passe. Elle ouvre la page d&#39;accueil de votre chambre forte, comme indiqué ci-dessous.

   ![](images/vault-home.png)

1. Sélectionner **[!UICONTROL Bibliothèque]** , puis sélectionnez le document. Le statut du document peut être : [!UICONTROL Dans Adobe Sign Draft], [!UICONTROL Dans la création Adobe Sign], ou [!UICONTROL En Adobe Signature].

   ![](images/document-adobe-sign-authoring.png)

1. Sélectionner **[!UICONTROL Annuler Adobe Sign]**.

   ![](images/cancel-document.png)

1. Il déclenche l’action Web et charge la fenêtre iFrame dans [!UICONTROL Vault].

   ![](images/cancelled-document.png)

1. Le statut du document devient automatiquement [!UICONTROL Révision].

   ![](images/cancel-reviewed.png)

Une fois que le statut du document est remplacé par Révision, vous pouvez à nouveau l’envoyer pour signature.
