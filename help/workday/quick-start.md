---
title: Workday – Guide de démarrage rapide
description: Guide de démarrage rapide pour les clients qui souhaitent utiliser Adobe Sign dans leurs environnements Workday.
uuid: 10bf8ee8-9075-44d1-a836-e454950e2d9a
products: Adobe Sign
content-type: reference
discoiquuid: 13135c88-4c39-4707-b7ba-63ff94769258
locnotes: All languages; screenshots to follow what's there already (seems there is a mix within a given language version of the article)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 8b6fa8b4-e240-4ebe-ae2a-8807d75a6c69
source-git-commit: 5ac9dc27dcdb6cab19281e6aafd4ea0524cc01d6
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 26%

---

# [!DNL Workday] Guide de démarrage rapide{#workday-quick-start-guide}

[**Contacter le support technique Adobe Sign**](https://www.adobe.com/go/adobesign-support-center)

## Présentation {#overview}

Ce document est conçu pour vous aider [!DNL Workday] les administrateurs comprennent comment personnaliser le [!DNL Workday] Processus métier à inclure Adobe Sign pour l’obtention de signatures électroniques. Pour utiliser Adobe Sign dans [!DNL Workday], vous devez savoir comment créer et modifier [!DNL Workday] éléments tels que :

* [!UICONTROL Structure des processus métier]
* Configuration et configuration des clients
* Rapports et [!DNL Workday] Intégration Studio

## Accès à Adobe Sign dans [!DNL Workday] {#access-adobe-sign}

[!UICONTROL Capacité de signature électronique Adobe Sign] est affiché comme [!UICONTROL Étape de révision de document] action au sein de [!UICONTROL Cadre des processus métier (BPF)] et en tant que tâche de distribution de documents.

## [!UICONTROL Étape de Review Document (Révision de document)] {#review-document-step}

Adobe Sign pour [!DNL Workday] est exposé via la [!UICONTROL Étape de révision de document] que vous pouvez ajouter à l&#39;un des plus de 400 processus métier au sein de [!DNL Workday], y compris [!UICONTROL Offre], [!UICONTROL Distribution de documents et de tâches], [!UICONTROL Proposer une compensation], etc.

Vous pouvez vous référer au fichier [[!DNL Workday] articles de la communauté [!UICONTROL Étape de révision de document]](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg).

Il existe une relation 1:1 entre [!UICONTROL [!UICONTROL Étape de révision de document]s] et les transactions facturables avec Adobe Sign. Vous pouvez combiner plusieurs documents en une seule [!UICONTROL Étape de révision de document] et ils sont présentés sous la forme d’un package unique pour signature.

**Note**: Une seule *Dynamique* peut être référencé dans un document spécifique [!UICONTROL Étape de révision de document].

Pour définir une fonction [!UICONTROL Étape de révision de document]:

1. Insérer une [!UICONTROL Étape de révision de document].
1. Spécifiez les groupes (rôles) qui peuvent agir sur la [!UICONTROL Étape de révision de document].

![Étapes des processus métier](images/insert-review-doc-steptornm-575.png)

Pour configurer le [!UICONTROL Étape de révision de document]:

1. Spécifiez la *[!UICONTROL Type d’intégration eSignature]* comme *[!UICONTROL eSign par Adobe]*.

1. Ajoutez des lignes à la grille de signatures.

   * La grille de signatures spécifie l’ordre séquentiel dans lequel le document est envoyé pour signature. Chaque ligne peut contenir un ou plusieurs rôles et chaque ligne représente une étape du processus de signature..
   * Chaque membre du rôle au cours d’une étape donnée est informé qu’un événement de signature est en attente.
   * Une fois qu’une seule personne du rôle signe, l’étape de ligne est terminée et le document est déplacé à l’étape de ligne suivante.
   * Lorsque toutes les lignes ont été signées, la propriété [!UICONTROL Étape de révision de document] est terminé.

1. Spécifiez le document à signer. Si le document est un [!UICONTROL Offre BP], vous pouvez l’utiliser à partir d’une étape Générer le document. Sinon, sélectionnez un document ou un rapport existant.

1. Répétez l’étape 3 en fonction du nombre de documents nécessaire..

   ![Configuration de l’étape de Review Document (Révision de document)](images/configure-rd-stepsmaller-575.png)

1. Si vous le souhaitez, ajoutez un utilisateur de redirection pour capturer les actions de refus de signature. Lorsque les utilisateurs refusent, [!DNL Workday] renvoie les documents à un groupe de sécurité configuré pour révision.

Dans le menu Actions associées d’un [!UICONTROL Étape de révision de document], sélectionnez **[!UICONTROL Processus métier]** > **[!UICONTROL Tenir à jour la redirection]**. Sélectionnez ensuite l’une des options suivantes :

* **[!UICONTROL Retour]**: Pour permettre aux membres du groupe de sécurité d&#39;envoyer une étape de retour à une étape précédente du processus métier. Le processus métier redémarre à partir de cette étape.
* **[!UICONTROL Passer à l’étape suivante]**: Pour permettre aux membres du groupe de sécurité de passer à l&#39;étape suivante du processus métier.
* **[!UICONTROL Groupes de sécurité]**: Pour rediriger les étapes du flux de processus métier. Les groupes de sécurité qui s&#39;affichent à cette invite sont sélectionnés dans la stratégie de sécurité des processus métier de la section Redirection.

## Remarques relatives aux étapes de processus métier {#business-process-step-notes}

[!UICONTROL Cadre des processus métier] est puissant ; toutefois, vous devez vous assurer que :

* Chaque processus métier doit être complété, ce qui est idéalement à la fin du processus métier.

* Une étape de fin est définie sur le menu Actions associées de l’icône de recherche. Cela n’est possible que lors de la &quot;visualisation&quot; du PM et non lors de la &quot;modification&quot;.

* Chaque étape du processus métier est exécutée de manière séquentielle.

   Vous pouvez modifier l’ordre d’une étape en modifiant la valeur de la commande. Par exemple, pour insérer une étape entre les éléments &quot;c&quot; et &quot;d&quot;, spécifiez un nouvel élément comme &quot;ca&quot;.

### Exemple : offre {#example-offer}

Le PM de l’offre est un sous-processus de [!UICONTROL PM Application dynamique BP] qui doit être configuré pour exécuter le PM de l’offre. Elle est déclenchée lorsque l&#39;état Application de la tâche est déplacé vers &quot;[!UICONTROL Offre]&quot; ou &quot;[!UICONTROL Faire une offre]&quot;.

Dans l’exemple ci-dessous, une [!UICONTROL Étape de révision de document] utilise une étape de document dynamique pour l’Amérique du Nord et le Japon.

![[!DNL Workday]Exemple d’un processus métier ](images/bp-for-offersmaller-575.png)

Ce PM permet d’effectuer les opérations suivantes :

* Demande à l&#39;initiateur du PM de proposer une compensation pour le candidat (étape b).
* Utilise une condition d’étape pour vérifier si le pays actuel n’est PAS le Japon.

   Si la valeur est true, elle exécute l’étape &quot;ba&quot; qui utilise un document en anglais.

   Si false, il exécute l’étape &quot;bb&quot; qui utilise un document en langue japonaise.

* Définit le processus de signature dans le noeud [!UICONTROL Étape de révision de document] &quot;bc&quot;.
* Définit le point de décision pour faire une offre à l&#39;étape d&#39;achèvement requise &quot;d&quot;.

Le document dynamique créé lors de l’étape « ba » est appelé [!UICONTROL Offer Letter] (Lettre d’offre), et contient un seul bloc de texte appelé [!UICONTROL Rapid Offer] (Offre rapide). Vous pouvez ajouter plusieurs blocs de texte, tels que l’en-tête, les salutations, la rémunération, les actions, la clôture, les conditions, etc. selon vos besoins.

![[!DNL Workday] page d’affichage du document](images/offer-letter-575.png)

La lettre d’offre dynamique ci-dessous est créée dans le fichier [!DNL Workday] éditeur de texte enrichi. Les éléments mis en surbrillance dans *gris* sont [!DNL Workday] fournit des objets qui référencent des données contextuelles.

Les éléments entre {{accolades}} sont des [balises de texte Adobe](https://adobe.com/go/adobesign_text_tag_guide_fr).

![Exemple de formulaire dynamique](images/script.png)

Dans le noeud [!UICONTROL Étape de révision de document], le document dynamique est référencé à partir de l’étape précédente et définit le processus de signature séquentiel via deux groupes de signature.

Le comportement illustré ci-dessous achemine d’abord le document généré dynamiquement vers le gestionnaire d’embauche, puis vers le candidat.

![[!DNL Workday] groupes de signature définis](images/configure-rd-stepsmaller-575.png)

### Exemple : Distribution de documents {#example-distribute-documents}

Introduit dans [!DNL Workday] 30, la tâche de distribution en masse de documents ou de tâches peut être utilisée pour envoyer un document unique à un grand groupe (&lt;20 000) de signataires individuels. Elle consiste en une seule signature par document. La création d’une distribution s’effectue en accédant à la[!UICONTROL Créer des tâches ou des documents distribués]&quot; à partir de la barre de recherche.

Exemple : Envoyer un formulaire de choix d&#39;équité à tous les gestionnaires avec [!UICONTROL Services modernes globaux]. Si vous le souhaitez, vous pouvez le filtrer davantage vers des gestionnaires individuels.

Vous pouvez également accéder au fichier **Afficher la distribution de documents ou de tâches** pour suivre la progression de la distribution.

![](images/create-distributedocumentsortasks.png)

### Exemple : création de rapports {#example-reporting}

[!DNL Workday] propose une puissante infrastructure de création de rapports. Pour obtenir un aperçu détaillé du processus d’Adobe Sign, consultez les informations concernant le processus *Review Document Event* (Révision l’évènement du document).

Vous trouverez ci-dessous un rapport simple et personnalisé pouvant être exécuté dans tous les PM pour rechercher les transactions ainsi que les états associés Adobe Sign.

![[!DNL Workday]Exemple d’un rapport personnalisé ](images/review-document-eventsmaller-575.png)

Le rapport suivant a été généré grâce à la recherche des PM suivants : Offer (Offre), Onboarding (Accueil et Intégration), et Propose Compensation (Proposer une rémunération) dans le client d’implémentation.

Vous pouvez consulter :

* Les documents envoyés en vue de leur signature
* L’étape PM associée
* La prochaine personne devant signer

![[!DNL Workday]Exemple d’un rapport généré avec trois éléments](images/workday-reportsmaller-575.png)

## Documents signés {#signed-documents}

Le [!DNL Workday] le cycle de signature supprime toutes les notifications par e-mail d’Adobe Sign. Les utilisateurs sont informés des actions en attente au sein de leur [!DNL Workday] Boîte de réception.

Une fois qu’un document est signé par tous les groupes de signature, une copie du document signé est distribuée à tous les membres du groupe de signature par courrier électronique.

Pour supprimer ce comportement, vous pouvez contacter votre [!UICONTROL Adobe Sign Success Manager] ou [Équipe d’assistance Adobe Sign](https://adobe.com/go/adobesign-support-center).

Dans [!DNL Workday], vous pouvez accéder aux documents signés sur l’enregistrement de processus complet. Vous pouvez trouver :

* Documents de travail sur le profil de travail, et
* Documents des candidats (lettres d&#39;offre) sur le profil des candidats.

L&#39;image ci-dessous montre une lettre d&#39;offre signée pour le candidat Chris Foxx.

![Exemple [!DNL Workday] lettre d&#39;offre](images/offer.png)

## Assistance technique {#support}

### [!DNL Workday] support {#workday-support}

[!DNL Workday]Propriétaire de l’intégration,  devra être votre premier point de contact pour toute question concernant l’intégration, les demandes relatives aux fonctionnalités ou les problèmes de fonctionnement général de l’intégration.

Le [!DNL Workday] La communauté propose plusieurs bons articles sur la façon de résoudre les problèmes d’intégration et de générer des documents :

* [Dépannage des intégrations de signature électronique](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [Étape de révision de documents](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Création de documents dynamiques](https://community.workday.com/node/176443)
* [Conseils pour la configuration de la création de documents d’offre](https://community.workday.com/node/183242)

### Prise en charge d’Adobe Sign {#adobe-sign-support}

En tant que partenaire de l’intégration, Adobe Sign doit être contacté lorsque l’intégration ne peut obtenir des signatures ou lorsque la notification de signatures en attente fait défaut.

Les clients Adobe Sign doivent contacter leur responsable clientèle pour obtenir de l’aide. Sinon, [!UICONTROL Support technique Adobe] peut être contacté par téléphone : 1-866-318-4100, attendre la liste des produits, puis entrer : 4, puis 2 (à l’invite).

* [Ajout de balises de texte Adobe sur des documents](https://www.adobe.com/go/adobesign_text_tag_guide)

<!--
[Download PDF](images/adobe-sign-for-workday-quick-start-guide-2016.pdf)
-->
