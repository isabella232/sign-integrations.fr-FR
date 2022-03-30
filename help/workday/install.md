---
title: Guide d’installation de Workday
description: Guide d’installation pour l’activation de l’intégration Adobe Sign avec Workday
uuid: 56478222-fe66-4fa5-aac3-0ecdf2863197
product: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
discoiquuid: 29d55a25-6e2f-4c59-ae7c-c21bb82cecba
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: 8f12b524-2123-45d4-98d5-b2b23580a5ea
source-git-commit: 4d73ff36408283805386bd3266b683bc187d6031
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 23%

---

# [!DNL Workday] Guide d’installation{#workday-installation-guide}

[**Contacter le support technique Adobe Sign**](https://adobe.com/go/adobesign-support-center_fr)

## Présentation {#overview}

Ce document explique comment intégrer Adobe Sign dans votre [!DNL Workday] client. Pour utiliser Adobe Sign dans [!DNL Workday], vous devez savoir comment créer et modifier [!DNL Workday] des éléments tels que :

* Framework de processus métier
* Configuration et configuration du client
* Rapports et [!DNL Workday] intégration studio

Les étapes générales pour terminer l’intégration sont les suivantes :

* Activation de votre compte d’administrateur dans Adobe Sign (nouveaux clients uniquement)
* Configurez un groupe dans Adobe Sign pour qu’il contienne le [!DNL Workday] utilisateur d&#39;intégration
* Établir la relation OAuth entre [!DNL Workday] et Adobe Sign

## Activation de votre compte Adobe Sign {#activating-your-adobe-sign-account}

Les clients existants disposant déjà d’un compte peuvent ignorer le [Configuration d’Adobe Sign pour [!DNL Workday]](#config) rubrique.

Pour les clients qui découvrent Adobe Sign et n’ont pas de connexion préexistante, un spécialiste de l’intégration d’Adobe configure votre compte (dans Adobe Sign) pour [!DNL Workday]. Une fois l’opération terminée, vous recevrez un e-mail de confirmation, comme indiqué ci-dessous.

![Image de l’e-mail de bienvenue de l’équipe Adobe Sign](images/welcome-email-2020.png)

Vous devez suivre les instructions de l’e-mail pour initialiser votre compte et accéder à votre Adobe Sign [!UICONTROL Accueil] s&#39;affiche.

![Page du tableau de bord Adobe Sign](images/classic-home.png)

## Configuration d’Adobe Sign pour [!DNL Workday] {#config}

Pour configurer Adobe Sign pour [!DNL Workday], vous devez générer les deux objets dédiés suivants dans le système Adobe Sign :

* **A [!DNL Workday] groupe**: [!DNL Workday] nécessite un &quot;groupe&quot; dédié dans le compte Adobe Sign pour activer la fonctionnalité d’intégration. Le groupe Adobe Sign est utilisé pour contrôler uniquement le fichier [!DNL Workday] utilisation d’Adobe Sign. Toute autre utilisation potentielle, telle que Salesforce.com ou Arriba, n’est pas affectée. Les notifications par courrier électronique sont supprimées dans [!DNL Workday] afin que la [!DNL Workday] les utilisateurs ne reçoivent des notifications que dans leur [!DNL Workday] boîte de réception.

* **Un utilisateur chargé de l’authentification doit détenir la clé d’intégration**: A [!DNL Workday] le groupe ne doit avoir qu’un seul administrateur de niveau groupe, qui est le titulaire autorisé de la clé d’intégration. Nous recommandons à l’administrateur d’utiliser une adresse électronique fonctionnelle telle que `HR@MyDomain.com` au lieu d’un e-mail personnel pour réduire le risque de désactivation ultérieure de l’utilisateur et, par conséquent, de désactivation de l’intégration.

### Création d’un utilisateur et d’un groupe dans Adobe Sign {#create-a-user-and-group-in-adobe-sign}

Création d’un utilisateur dans Adobe Sign :

1. Connectez-vous à Adobe Sign en tant qu’administrateur de compte.
1. Accédez à **[!UICONTROL Compte]** > **[!UICONTROL Utilisateurs]**.
1. Cliquez sur le bouton ![image d’icône plus](images/icon_plus.png) pour créer un nouvel utilisateur.

   ![Image du chemin de navigation pour la création d’un nouvel utilisateur](images/navigate-to-group-unbranded.png)

1. Dans la boîte de dialogue qui s’ouvre, indiquez les détails du nouvel utilisateur :

   * Fournissez une adresse e-mail fonctionnelle à laquelle vous pouvez accéder.
   * Entrez un prénom et un nom appropriés.
   * Sélectionner **[!UICONTROL Créer un groupe pour cet utilisateur]** dans le groupe d’utilisateurs.
   * Indiquez le **[!UICONTROL Nouveau nom de groupe]** avec un nom intuitif du type *[!DNL Workday]*.

   ![Panneau de création d’un utilisateur](images/create-user.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

   Cela vous ramène à la [!UICONTROL Utilisateurs] qui répertorie le nouvel utilisateur avec un attribut **[!UICONTROL CRÉÉ]** état.

   ![Vue du nouvel utilisateur créé](images/post-user-creation.png)

Pour vérifier l’adresse électronique de l’utilisateur avec le statut &quot;Créé&quot; :

1. Connectez-vous à l’adresse e-mail du nouvel utilisateur.
2. Recherchez l’e-mail &quot;Bienvenue dans Adobe Sign&quot;.
3. Cliquez à l&#39;endroit indiqué **[!UICONTROL Cliquez ici pour définir votre mot de passe]**.
4. Définissez le mot de passe.

Une fois que vous avez vérifié l’adresse électronique, l’état de l’utilisateur change de [!UICONTROL CRÉÉ] à [!UICONTROL ACTIVE].

![Image du nouvel utilisateur activé](images/actived-users-575.png)

### Définition de l’utilisateur authentifiant {#define-the-authenticating-user}

Pour promouvoir le nouvel utilisateur dans le [!DNL Workday] groupe :

1. Accédez à l’onglet [!UICONTROL Utilisateurs] (si ce n’est pas déjà fait).
2. Cliquez deux fois sur l’utilisateur dans le [!DNL Workday] groupe.

   Une boîte de dialogue [!UICONTROL Modifier] pour les autorisations utilisateur.

3. Vérifiez le **[!UICONTROL Administrateur de groupe]**.
4. Cliquez sur **[!UICONTROL Enregistrer]**.

![](images/user-permissions-edit1-575.png)

## Configurez le fichier [!DNL Workday] client {#configure-workday}

Pour terminer la connexion entre le [!DNL Workday] et Adobe Sign, nous devons établir une relation de confiance entre les services. Une fois l’opération terminée, nous pouvons ajouter une étape de révision de document qui active le processus de signature via Adobe Sign.

>[!NOTE]
>
>Adobe Sign est appelé Adobe Document Cloud dans l’ensemble du [!DNL Workday] environnement.

Pour établir la relation de confiance :

1. Se connecter à [!DNL Workday] en tant qu’administrateur de compte.
1. Ouvrez le **[!UICONTROL Modifier les paramètres Client - Processus métier]** s&#39;affiche.
1. Recherchez la section [!UICONTROL Configuration de la signature électronique] :

   ![](images/esignature_configurations.png)

1. Cliquez **[!UICONTROL Authentifier avec Adobe]**.

   La séquence d&#39;authentification OAuth2.0 démarre.

1. Lorsque vous y êtes invité, fournissez les informations d’identification de l’administrateur de groupe Adobe Sign que vous avez créées précédemment.
1. Approuvez l’accès à Adobe Sign.

>[!NOTE]
>
>Assurez-vous de vous déconnecter complètement de toute autre instance Adobe Sign avant de continuer.

Une fois connecté, la case Configuration Adobe activée est cochée et vous pouvez commencer à utiliser Adobe Sign avec [!DNL Workday].

### Configuration de l’étape de révision de document {#configure-review}

Le document pour l’étape de révision de document peut être l’un des suivants :

* Un document statique
* Un document généré par une étape Générer le document dans le même processus métier
* Un rapport formaté créé avec le fichier [!DNL Workday] Concepteur de rapports

Vous pouvez ajouter n’importe lequel de ces documents avec [Balises de texte Adobe](https://adobe.com/go/adobesign_text_tag_guide_fr) pour contrôler l’apparence et la position des composants spécifiques de la signature d’Adobe. La source du document doit être spécifiée dans la définition du processus métier. Il n’est pas possible de télécharger un document ad hoc lors de l’exécution du processus métier.

L’utilisation d’Adobe Sign avec une étape de révision de document se caractérise uniquement par la possibilité d’avoir des groupes de signataires sérialisés. Cela vous permet de spécifier un ordre de signature en fonction de groupes établis selon des rôles définis. Adobe Sign ne prend pas en charge les groupes de signature parallèles.

Pour obtenir de l’aide sur l’étape de révision de document, consultez [Guide de démarrage rapide](https://adobe.com//go/adobesign_workday_quick_start){target=&quot;_blank&quot;}.

## Assistance technique {#support}

### [!DNL Workday] support {#workday-support}

[!DNL Workday]Propriétaire de l’intégration,  devra être votre premier point de contact pour toute question concernant l’intégration, les demandes relatives aux fonctionnalités ou les problèmes de fonctionnement général de l’intégration.

Vous pouvez vous référer à ce qui suit [!DNL Workday] articles de la communauté sur la façon de résoudre les problèmes d’intégration et de générer des documents :

* [Dépannage des intégrations de signature électronique](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [Étape de révision des documents](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Génération dynamique de documents](https://community.workday.com/saml/login?destination=/articles/176443)
* [Conseils pour la génération de documents](https://community.workday.com/node/183242)

### Support Adobe Sign {#adobe-sign-support}

En tant que partenaire de l’intégration, Adobe Sign doit être contacté lorsque l’intégration ne peut obtenir des signatures ou lorsque la notification de signatures en attente fait défaut.

Pour obtenir une assistance, les utilisateurs Adobe Sign doivent contacter leur responsable du succès client. Vous pouvez également contacter le support technique au 1-866-318-4100. Patientez jusqu’à l’annonce de la liste des produits, puis saisissez 4, puis 2 (lorsque vous y êtes invité).

* [Ajout de balises de texte Adobe aux documents](https://adobe.com/go/adobesign_text_tag_guide)
* [Configuration du document et exemples](https://www.adobe.com//go/adobesign_workday_quick_start)

## Questions fréquentes {#faq}

### Pourquoi le statut n’est-il pas mis à jour dans [!DNL Workday] même lorsque le document est entièrement signé ? {#why-is-the-status-not-being-updated-within-workday-even-the-document-is-fully-signed}

Statut du document dans [!DNL Workday] peut ne pas refléter si le candidat ne clique pas sur le bouton[!UICONTROL Envoyer]&quot; après vous être connecté à Adobe Sign.

Selon [!DNL Workday] tâche Vérifier l’état de signature électronique : Pour lancer le processus, l&#39;utilisateur peut soumettre la tâche de boîte de réception associée.

Selon [!DNL Workday] Développement : La signature d’origine ne termine le processus que si l’utilisateur envoie la tâche de boîte de réception après avoir signé le document. Après la signature, l’iframe est fermé et l’utilisateur est redirigé vers la même tâche où il peut cliquer sur le bouton [!UICONTROL Envoyer] pour terminer le processus.
