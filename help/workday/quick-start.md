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
source-git-commit: d462ccf41fa5483cfa02f5eaf154c23f26157a1e
workflow-type: tm+mt
source-wordcount: '1352'
ht-degree: 32%

---

# [!DNL Workday] Guide de démarrage rapide{#workday-quick-start-guide}

[**Contacter le support technique Adobe Sign**](https://adobe.com/go/adobesign-support-center_fr)

## Présentation {#overview}

Ce document est conçu pour aider [!DNL Workday] les administrateurs à comprendre comment personnaliser les [!DNL Workday] processus métier pour inclure Adobe Sign afin d&#39;obtenir des signatures électroniques. Pour utiliser Adobe Sign dans [!DNL Workday], vous devez savoir comment créer et modifier des éléments [!DNL Workday] tels que :

* Structure des processus métier
* Configuration et configuration des clients
* Intégration de Reporting and [!DNL Workday] Studio

## Accès à Adobe Sign dans [!DNL Workday] {#access-adobe-sign}

La fonctionnalité de signature électronique Adobe Sign apparaît sous la forme d&#39;une action [!UICONTROL Revoir l&#39;étape du document] au sein du cadre de processus métier (BPF) et d&#39;une tâche de distribution de documents.

## [!UICONTROL Étape de Review Document (Révision de document)] {#review-document-step}

Adobe Sign pour [!DNL Workday] est exposé via l&#39;[!UICONTROL étape de révision de document] que vous pouvez ajouter à l&#39;un des plus de 400 processus métier dans [!DNL Workday], y compris l&#39;offre, la distribution de documents et de tâches, la proposition de rémunération, etc.

Vous pouvez consulter les [[!DNL Workday] articles de la communauté sur [!UICONTROL Étape de révision du document]](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg).

Il existe une relation 1:1 entre [!UICONTROL [!UICONTROL Revoir l&#39;étape du document]s] et les transactions facturables avec Adobe Sign. Vous pouvez combiner plusieurs documents au sein d’une seule [!UICONTROL étape de révision de document] et ils sont présentés sous la forme d’un package unique pour signature.

**Remarque** : Un seul document  ** dynamique peut être référencé dans une étape de révision spécifique.

Pour définir une [!UICONTROL étape de révision de document] fonctionnelle :

1. Insérez une [!UICONTROL étape de révision de document].
1. Spécifiez les groupes (rôles) qui peuvent agir sur l&#39;[!UICONTROL étape de révision de document].

![Étapes des processus métier](images/insert-review-doc-steptornm-575.png)

Pour configurer l&#39;[!UICONTROL étape de révision de document] :

1. Spécifiez *[!UICONTROL eSignature Integration type]* comme *[!UICONTROL eSign par Adobe]*.

1. Ajoutez des lignes à la grille de signatures.

   * La grille de signatures spécifie l’ordre séquentiel dans lequel le document est envoyé pour signature. Chaque ligne peut contenir un ou plusieurs rôles et chaque ligne représente une étape du processus de signature..
   * Chaque membre du rôle au cours d’une étape donnée est informé qu’un événement de signature est en attente.
   * Une fois qu’une seule personne du rôle signe, l’étape de ligne est terminée et le document est déplacé à l’étape de ligne suivante.
   * Une fois toutes les lignes signées, l&#39;[!UICONTROL étape de révision de document] est terminée.

1. Spécifiez le document à signer. S’il s’agit d’un PM Offer (d’offre), vous pouvez utiliser le document à partir d’une étape de Generate Document (Création de document). Sinon, sélectionnez un document ou un rapport existant.

1. Répétez l’étape 3 en fonction du nombre de documents nécessaire..

   ![Configuration de l’étape de Review Document (Révision de document)](images/configure-rd-stepsmaller-575.png)

1. Si vous le souhaitez, ajoutez un utilisateur de redirection pour capturer les actions de refus de signature. Lorsque les utilisateurs refusent, [!DNL Workday] redirige les documents vers un groupe de sécurité configuré pour révision.

Dans le menu Actions associées d&#39;une [!UICONTROL étape de révision de document], sélectionnez **[!UICONTROL Processus métier]** > **[!UICONTROL Conserver la redirection]**. Sélectionnez ensuite l’une des options suivantes :

* **[!UICONTROL Retour]** : Pour permettre aux membres du groupe de sécurité d&#39;envoyer une étape de retour à une étape précédente du processus métier. Le processus métier redémarre à partir de cette étape.
* **[!UICONTROL Passer à l’étape]** suivante : Pour permettre aux membres du groupe de sécurité de passer à l&#39;étape suivante du processus métier.
* **[!UICONTROL Groupes]** de sécurité : Pour rediriger les étapes du flux de processus métier. Les groupes de sécurité qui s&#39;affichent à cette invite sont sélectionnés dans la stratégie de sécurité des processus métier de la section Redirection.

## Remarques relatives aux étapes de processus métier {#business-process-step-notes}

Le cadre des processus opérationnels est puissant; toutefois, vous devez vous assurer que :

* Chaque processus métier doit être complété, ce qui est idéalement à la fin du processus métier.

* Une étape de fin est lancée à partir du menu des actions associées de l’icône de recherche. Cela n’est possible que lors de la &quot;visualisation&quot; du PM et non lors de la &quot;modification&quot;.

* Chaque étape du processus métier est exécutée de manière séquentielle.

   Vous pouvez modifier l’ordre d’une étape en modifiant la valeur de la commande. Par exemple, pour insérer une étape entre les éléments &quot;c&quot; et &quot;d&quot;, spécifiez un nouvel élément comme &quot;ca&quot;.

### Exemple : offre {#example-offer}

Le PM de l’offre est un sous-processus du PM dynamique de l’application de jobs qui doit être configuré pour exécuter le PM de l’offre. Le déclenchement s’effectue lorsque « Offer » (Offre) ou « Make Offer » (Offre une Faire) est sélectionné pour une candidature.

Dans l’exemple ci-dessous, une [!UICONTROL étape de révision de document] utilise une étape de document dynamique pour l’Amérique du Nord et le Japon.

![[!DNL Workday]Exemple d’un processus métier ](images/bp-for-offersmaller-575.png)

Ce PM permet d’effectuer les opérations suivantes :

* Demande à l&#39;initiateur du PM de proposer une compensation pour le candidat (étape b).
* Utilise une condition d’étape pour vérifier si le pays actuel n’est PAS le Japon.

   Si la valeur est true, elle exécute l’étape &quot;ba&quot; qui utilise un document en anglais.

   Si false, il exécute l’étape &quot;bb&quot; qui utilise un document en langue japonaise.

* Définit le processus de signature dans l&#39;[!UICONTROL étape de révision de document] &quot;bc&quot;.
* Définit le point de décision pour faire une offre à l&#39;étape d&#39;achèvement requise &quot;d&quot;.

Le document dynamique créé lors de l’étape « ba » est appelé [!UICONTROL Offer Letter] (Lettre d’offre), et contient un seul bloc de texte appelé [!UICONTROL Rapid Offer] (Offre rapide). Vous pouvez ajouter plusieurs blocs de texte, tels que l’en-tête, les salutations, la rémunération, les actions, la clôture, les conditions, etc. selon vos besoins.

![[!DNL Workday] page d’affichage du document](images/offer-letter-575.png)

La lettre d’offre dynamique ci-dessous est créée dans l’éditeur de texte enrichi [!DNL Workday]. Les éléments mis en surbrillance dans *gray* sont [!DNL Workday] des objets qui référencent des données contextuelles.

Les éléments entre {{accolades}} sont des [balises de texte Adobe](https://adobe.com/go/adobesign_text_tag_guide_fr).

![Exemple de formulaire dynamique](images/script.png)

Dans l’[!UICONTROL étape de révision de document], le document dynamique est référencé à partir de l’étape précédente et définit le processus de signature séquentiel via deux groupes de signature.

Le comportement illustré ci-dessous achemine d’abord le document généré dynamiquement vers le gestionnaire d’embauche, puis vers le candidat.

![[!DNL Workday] groupes de signature définis](images/configure-rd-stepsmaller-575.png)

### Exemple : Distribution de documents {#example-distribute-documents}

Introduite dans [!DNL Workday] 30, la tâche de distribution en masse de documents ou de tâches peut être utilisée pour envoyer un document unique à un grand groupe (&lt;20 000) de signataires individuels. Elle consiste en une seule signature par document. La création d’une distribution s’effectue en accédant à l’action &quot;[!UICONTROL Créer des tâches ou des documents distribués]&quot; à partir de la barre de recherche.

Exemple : envoi d’un formulaire de choix d’actions des employés à tous les responsables des Services modernes internationaux. Si vous le souhaitez, vous pouvez le filtrer davantage vers des gestionnaires individuels.

Vous pouvez également accéder au rapport **Afficher la distribution de documents ou de tâches** pour suivre la progression de la distribution.

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

Le cycle de signature [!DNL Workday] supprime toutes les notifications par e-mail envoyées par Adobe Sign. Les utilisateurs sont informés des actions en attente dans leur boîte de réception [!DNL Workday].

Une fois qu’un document est signé par tous les groupes de signature, une copie du document signé est distribuée à tous les membres du groupe de signature par courrier électronique.

Pour supprimer ce comportement, vous pouvez contacter votre responsable de réussite Adobe Sign ou l&#39;[équipe d&#39;assistance Adobe Sign](https://adobe.com/go/adobesign-support-center).

Dans [!DNL Workday], vous pouvez accéder aux documents signés sur l&#39;enregistrement de processus complet. Vous pouvez trouver :

* Documents de travail sur le profil de travail, et
* Documents des candidats (lettres d&#39;offre) sur le profil des candidats.

L&#39;image ci-dessous montre une lettre d&#39;offre signée pour le candidat Chris Foxx.

![Exemple de lettre  [!DNL Workday] d’offre](images/offer.png)

## Assistance technique {#support}

### [!DNL Workday] support {#workday-support}

[!DNL Workday]Propriétaire de l’intégration,  devra être votre premier point de contact pour toute question concernant l’intégration, les demandes relatives aux fonctionnalités ou les problèmes de fonctionnement général de l’intégration.

La communauté [!DNL Workday] a plusieurs bons articles sur la façon de résoudre les problèmes d&#39;intégration et de générer des documents :

* [Dépannage des intégrations de signature électronique](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [Étape de révision de documents](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Création de documents dynamiques](https://community.workday.com/node/176443)
* [Conseils pour la configuration de la création de documents d’offre](https://community.workday.com/node/183242)

### Prise en charge d’Adobe Sign {#adobe-sign-support}

En tant que partenaire de l’intégration, Adobe Sign doit être contacté lorsque l’intégration ne peut obtenir des signatures ou lorsque la notification de signatures en attente fait défaut.

Pour obtenir une assistance, les utilisateurs Adobe Sign doivent contacter leur responsable du succès client. Vous pouvez également contacter le support technique au 1-866-318-4100. Patientez jusqu’à l’annonce de la liste des produits, puis saisissez 4, puis 2 (lorsque vous y êtes invité).

* [Ajout de balises de texte Adobe sur des documents](https://adobe.com/go/adobesign_text_tag_guide)

<!--
[Download PDF](images/adobe-sign-for-workday-quick-start-guide-2016.pdf)
-->
