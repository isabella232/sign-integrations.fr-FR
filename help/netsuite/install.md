---
title: Adobe Sign pour [!DNL NetSuite] - Guide d’installation et de personnalisation (v4.0.4)
description: Adobe Sign pour [!DNL NetSuite] - Guide d'installation et de personnalisation
product: Adobe Sign
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: 378cac01-87c9-4288-8839-482121d49402
source-git-commit: 581b336b4a3610cfe3fd0d92f2a4eebe55b89b27
workflow-type: tm+mt
source-wordcount: '4870'
ht-degree: 36%

---

# [!DNL NetSuite] Guide d’installation et de personnalisation (v4.0.4) {#install-customize-NetSuite}

## Présentation {#overview}

Adobe Sign pour [!DNL NetSuite] offre une intégration complète des signatures électroniques avec [!DNL NetSuite]. Vous pouvez utiliser Adobe Sign pour [!DNL NetSuite] intégration pour envoyer des accords (contrats, devis, etc.) nécessitant des signatures électroniques directement aux destinataires depuis [!DNL NetSuite]. Vous pouvez créer et envoyer des accords Adobe Sign à partir de clients, de prospects, de devis et autres [!DNL NetSuite] des dossiers. Mises à jour Adobe Sign [!DNL NetSuite] avec le statut des accords et stocke les accords avec le [!DNL NetSuite] une fois qu&#39;ils sont entièrement exécutés. Vous pouvez afficher l’historique de tous les accords envoyés depuis [!DNL NetSuite] à partir du produit.

Reportez-vous au [Notes de mise à jour d’Adobe Sign pour NetSuite](https://experienceleague.adobe.com/docs/sign-integrations/using/netsuite/release-notes.html?lang=en) pour plus d’informations.

## Installez l’offre groupée et configurez OAuth {#install}

Seulement un [!DNL NetSuite] l’administrateur peut installer ou mettre à jour l’offre groupée. Pour configurer OAuth, la boîte de dialogue [!DNL NetSuite] L’administrateur doit disposer d’un accès administrateur à Adobe Sign. Avant d’installer l’offre groupée dans votre compte de production, vous devez l’installer et la tester dans un fichier [!DNL NetSuite] Compte Sandbox.

Voir [Création d’un accord Adobe Sign](#createagreement) pour plus d&#39;informations sur testing.

>[!CAUTION]
>
>Les clients effectuant une mise à niveau vers la version 4.0.4 NE doivent PAS supprimer leur clé API existante.
>
>Voir [Définition des préférences personnalisées](#configure) pour plus d’informations sur l’utilisation de la clé API.

### Installez l’offre groupée pour la première fois.

1. Accédez à [!UICONTROL **Personnalisation > SuiteBundler > Rechercher et installer une offre groupée**].

1. Dans le *Offres groupées de recherche et d’installation* , entrez **Adobe Sign** comme mot-clé et sélectionnez **[!UICONTROL Rechercher]**.

1. Sélectionnez le fichier **Adobe Sign** nom du lot.

   ![Recherche de l’offre groupée](images/search-for-the-bundle.png)

1. Dans le *[!UICONTROL Détails du lot]* , sélectionnez **[!UICONTROL Installer]**.
1. Dans le *[!UICONTROL Installation de l’offre groupée]* , sélectionnez **[!UICONTROL Installer le bundle]**.

   (Aucune valeur par défaut ne doit être modifiée sur la page.)

   ![Installation de l’offre groupée](images/bundle-details-install.png)

1. Dans la boîte de dialogue Installer qui s’affiche, sélectionnez **[!UICONTROL OK]** pour continuer.

   Pendant le processus d’installation, l’offre groupée affiche le statut *[!UICONTROL En attente]*.

   ![Installation des offres groupées](images/installing-bundles.png)

1. Pour afficher un état mis à jour, sélectionnez **[!UICONTROL Actualiser]**.

   Une fois l’installation de l’offre groupée terminée, *Adobe Sign pour[!DNL NetSuite]* s’affiche sur la page *[!UICONTROL Offres groupées installées]*.

   ![Offres groupées installées](images/installed-bundles.png)

1. Si vous êtes déjà un compte client Adobe Sign, suivez les étapes pour  [Configuration d’OAuth après installation ou mise à niveau](#oauth).

   Si vous ne disposez pas d’un compte Adobe Sign, vous pouvez vous [inscrire pour une version d’essai de compte](https://esign.adobe.com/fr/adobe-sign-netsuite-trial-registration.html) d’entreprise afin de tester le système. Suivez les étapes d’enregistrement en ligne pour activer votre compte Adobe Sign.

## Configuration d’OAuth après installation ou mise à niveau {#oauth}

Adobe Sign utilise Oauth 2.0 pour authentifier votre compte Adobe Sign dans [!DNL NetSuite].

Ce protocole autorise votre [!DNL NetSuite] pour communiquer avec Adobe Sign sans demander votre mot de passe. Dans la mesure où les informations sensibles ne sont pas directement partagées entre les applications, votre compte est moins susceptible d’être piraté.

Cette authentification n’a aucun impact sur votre implémentation, mais vous devez effectuer une configuration unique après avoir installé ou mis à niveau l’offre groupée dans votre compte de production ou Sandbox.

La [!DNL NetSuite] L’administrateur qui configure OAuth doit également disposer d’un accès administrateur au niveau du compte pour Adobe Sign.

1. Dans [!DNL NetSuite], accédez à l’onglet *Configuration Adobe Sign* page de liste.

1. Recherche de **[!UICONTROL Configuration Adobe Sign]** (type d’enregistrement personnalisé) à l’aide du champ Rechercher dans l’en-tête.

1. Dans la page Résultats de la recherche, sélectionnez **Affichage** pour le *Configuration Adobe Sign* enregistrement.

   ![Recherchez Adobe Sign](images/search-for-adobesignconfig.png).

1. Sur la page Liste des configurations Adobe Sign , sélectionnez **[!UICONTROL Affichage]** pour le *Utilisation d’OAuth pour accéder aux API Adobe Sign* enregistrement.

   ![Liste des configurations d’Adobe Sign](images/adobe-sign-configlist.png)

1. Sur la page Configuration Adobe Sign , sélectionnez **[!UICONTROL Connexion Avec Adobe Sign]**

   ![Connectez-vous ](images/log-in-with-adobesign.png)

1. Dans la page de connexion Adobe Sign qui s’affiche, saisissez vos informations de connexion et sélectionnez **[!UICONTROL Se connecter]**.

   ![Authentification Adobe Sign](images/8-authenticate-toadobesign-2020.png)

1. Dans la page Confirmer l’accès (pour OAuth) qui s’affiche, sélectionnez **[!UICONTROL Autoriser l’accès]**

   ![Autoriser l’accès](images/confirm-access.png)

1. Une fois l’autorisation terminée, vous êtes redirigé vers la page Configuration Adobe Sign dans [!DNL NetSuite], comme indiqué ci-dessous.

   ![Authentification OAuth réussie](images/successful-oauth.png)

   >[!NOTE]
   >
   >Lors de la configuration d’OAuth dans votre compte Sandbox, vous pouvez rencontrer l’erreur &quot;Impossible de déterminer l’ID de composition client&quot; une fois l’autorisation terminée.
   >
   >
   >Pour continuer, vous devez modifier la partie du domaine du compte de l’URL (system.netsuite.com) dans votre navigateur pour qu’elle renvoie à l’élément [!DNL NetSuite] Sandbox comme suit :
   >
   >
   >Changer:
   >
   >
   >system.netsuite.com/app/site/hosting/scriptlet.nl?script=745&amp;deploy=1&amp;web_access_point=https://echosign.com
   >
   >
   >À :
   >
   >
   >system.**sandbox.** netsuite.com/app/site/hosting/scriptlet.nl?script=745&amp;deploy=1&amp;web_access_point=https://echosign.com

## Mettre à jour l’offre groupée (utilisateurs existants)

[!DNL NetSuite] les mises à jour du bundle sont régulièrement publiées par Adobe. Utilisateurs existants d’Adobe Sign pour [!DNL NetSuite] l’intégration peut passer à la dernière offre groupée.

>[!CAUTION]
>
>Les clients effectuant une mise à niveau vers une version plus récente ne doivent PAS supprimer leur clé API existante.
>
>Voir [Définition des préférences personnalisées ](#configure)pour plus d’informations sur l’utilisation de la clé API.

### Conditions préalables {#prerequisites}

Le temps nécessaire pour effectuer une mise à jour vers l’offre groupée v4.0.4 dépend du nombre d’accords dont l’état est actuellement Émis pour signature. En règle générale, la mise à jour de 100 accords prend entre 7 et 10 minutes. Notez le nombre d’enregistrements pour estimer le temps de mise à jour.

Pour déterminer le nombre d’accords envoyés pour signature :

1. Accédez à **[!UICONTROL Personnalisation > Listes, enregistrements et fichiers > Types d’enregistrement]**, puis localisez *Accord Adobe Sign.*

   Ou recherchez Accords Adobe Sign dans la barre de recherche.

1. Pour le fichier [!UICONTROL Accords Adobe Sign] enregistrement, sélectionnez **[!UICONTROL Rechercher]**.

   ![Recherche des types d’enregistrements](images/search-adobe-signagreements.png)

1. Dans le **[!UICONTROL Statut]** , sélectionnez l’option **[!UICONTROL Émis pour signature]** , puis sélectionnez **[!UICONTROL Envoyer]**.

   ![Envoi pour signature](images/submit-search-foragreements.png)

   Notez le nombre d’enregistrements pour estimer le temps de mise à jour.

   ![Notez le nombre.](images/search-results.png)

### Mise à jour du coffret {#updating-the-bundle}

1. Accédez à **[!UICONTROL Personnalisation > SuiteBundler > Rechercher et installer > Liste]** et localisez votre offre groupée actuelle, comme indiqué ci-dessous.

   >[!NOTE]
   >
   >S’il existe une nouvelle version de l’offre groupée, une icône de point d’exclamation s’affiche à droite du *Version* numéro de votre offre groupée actuelle.

1. Dans le menu déroulant Action, sélectionnez **[!UICONTROL Mettre à]**.

   ![Action de mise à jour](images/update-action.png)

1. Sur la page Prévisualiser la mise à jour de l’offre groupée , sélectionnez **[!UICONTROL Mettre à jour]** sans modifier les valeurs par défaut affichées sur la page.

   Lors de l’installation, l’offre groupée affiche le statut suivant : *En attente*.

   ![Aperçu de la mise à jour de l’offre groupée](images/preveiw-bundles-update.png).

   >[!NOTE]
   >
   >Lors de la mise à jour de l’offre groupée, vous pouvez recevoir un message d’avertissement comme indiqué ci-dessous. Si vous n’avez pas personnalisé votre [!DNL NetSuite] Enregistrements de signature électronique, vous pouvez continuer. En cas de doute, il est conseillé d’installer l’offre groupée sur un compte Sandbox pour la tester avant de la mettre à jour dans un compte de production.

   ![Message d’erreur](images/netsuite-error.png)

1. Pour afficher un état mis à jour, sélectionnez **[!UICONTROL Actualiser]**.

   ![Installation de la mise à niveau](images/installing-upgrade.png)

   >[!NOTE]
   >
   >Si la mise à jour prend beaucoup de temps en raison de plusieurs accords avec un *Émis pour signature* , vous pouvez vérifier la **[!UICONTROL Journal d’exécution]** de la boîte de dialogue *Installation de l’offre groupée Adobe Sign* pour déterminer la progression de votre mise à jour. Voir [Détermination de la progression de la mise à jour ](#determineprogress)pour plus d’informations.

   Une fois la mise à jour de l’offre groupée terminée, *Adobe Sign pour[!DNL NetSuite]* s’affiche sur la page *Offres groupées installées*.

   ![Package installé](images/4-installed-bundles.png)

## Configuration de l’offre groupée {#configure}

### Définition des préférences personnalisées  {#set-custom-preferences}

Vous pouvez utiliser des préférences personnalisées pour spécifier la façon dont les accords sont créés et stockés dans [!DNL NetSuite]. En outre, la préférence *Configurer automatiquement l’utilisateur dans Adobe Sign*[!DNL NetSuite] vous permet de spécifier si les utilisateurs de sont configurés automatiquement dans les services Sign lorsqu’ils envoient des accords depuis [!DNL NetSuite].

1. Accédez à **[!UICONTROL Configuration > Société > Préférences générales]**.
1. Faites défiler la page vers le bas, puis sélectionnez l’élément **[!UICONTROL Préférences personnalisées]** sous-onglet.

   ![Préférences personnalisées](images/custom-preferences.png)

1. Activez et configurez vos préférences Adobe Sign selon vos besoins :

   * **Entrez la clé API EchoSign pour votre compte**: N’ajoutez ni ne modifiez aucune valeur dans ce champ.
   * **Utiliser le contact de l’enregistrement parent comme signataire**: Si cette option est activée, le contact de l’enregistrement parent est par défaut le premier signataire lors de la création des accords. L’expéditeur peut facilement supprimer ou modifier le signataire par défaut ou ajouter des signataires supplémentaires à l’accord avant l’envoi.
   * **Utiliser le contact de transaction Contact en tant que signataire le cas échéant**: Cette préférence n’est valide que si l’attribut *Utiliser le contact de l’enregistrement parent comme signataire* est également activée. Si cette option est activée, lors de la génération d’un accord à partir d’un enregistrement de transaction (par exemple, un devis), le contact de transaction principal est par défaut le premier signataire. Pour plus d’informations, voir[ Enregistrements de transaction. ](#transrecords) S’il n’existe aucun contact de transaction principal ou si vous envoyez depuis [!DNL NetSuite] enregistrement objet (par exemple, enregistrement client, enregistrement partenaire), le destinataire par défaut est le contact principal pour l’adresse e-mail du client. L’expéditeur peut facilement supprimer ou modifier le signataire par défaut ou ajouter des signataires supplémentaires à l’accord avant l’envoi.
   * **Autoriser le marquage des destinataires comme approbateurs**: Si cette option est activée, les expéditeurs peuvent marquer les destinataires comme approbateurs. Les destinataires marqués comme approbateurs peuvent réviser et approuver les accords, mais ils ne sont pas tenus de les signer. Les approbateurs peuvent être tenus de saisir des données dans les champs pendant le processus d’approbation.
   * **ID de dossier d’accord préféré**: Permet de spécifier le dossier dans lequel les accords signés finaux sont stockés. Si vous ne définissez pas de valeur pour ce champ, les accords signés finaux sont enregistrés par défaut dans le même dossier que le fichier du document d’origine. L’ID de dossier doit être un nombre.
   * **Joindre automatiquement le PDF de transactions**: Si cette option est activée, les PDF de transaction sont automatiquement associés aux accords lorsque de nouveaux accords sont créés à partir d’enregistrements de transaction.
   * **Ajouter le PDF signé en tant que (Pièce jointe ou Lien)**: Si *Liste* est sélectionné dans la liste déroulante, le mot de PDF signé est automatiquement ajouté en tant que lien vers le fichier. Si l’option *Pièce jointe* est sélectionnée dans la liste déroulante, le fichier PDF signé est stocké dans en tant que pièce jointe dans l’enregistrement de l’accord.[!DNL NetSuite]
   * **Inclure le PDF de piste d’audit avec l’accord**: Si cette option est activée, les PDF de piste d’audit sont automatiquement joints aux enregistrements d’accord une fois les accords signés.
   * **Méthode de vérification de l’identité**: L’activation de l’une des méthodes de vérification de l’identité détermine à qui la méthode est appliquée. Les options sont les suivantes : *Tous les signataires, signataires externes uniquement*, ou *Signataires internes uniquement*.

   **Méthodes de vérification de l’identité** {#identity-verification-methods}

   La ou les méthodes de vérification de l’identité activées peuvent être sélectionnées lors de la création d’un accord. Si plusieurs méthodes de vérification de l’identité sont activées ici, la page Accord Adobe Sign affiche un **[!UICONTROL Vérification de l’identité du signataire]** s&#39;affiche.

   * **Activer le mot de passe requis pour la signature**: Demandez aux signataires de saisir un mot de passe unique que vous spécifiez.

   * **Activer l’authentification fondée sur les connaissances**: Demandez aux signataires de fournir leur nom, leur adresse et éventuellement les quatre derniers chiffres de leur numéro de sécurité sociale, puis de répondre à une liste de questions vérifiant les informations qu’ils ont fournies. Disponible uniquement aux États-Unis.

   * **Activer l’authentification d’identité web**: Demandez aux signataires de vérifier leur identité en se connectant à l’un des sites suivants : Facebook, Google, LinkedIn, Microsoft Live, Twitter ou Yahoo!.

   * **Configurer automatiquement l’utilisateur dans Adobe Sign**: Si cette option est activée, les utilisateurs qui envoient des accords dans [!DNL NetSuite] sont automatiquement configurés avec un compte utilisateur Adobe Sign.


1. Sélectionner **[!UICONTROL Enregistrer]** pour enregistrer vos préférences.

## Configuration des mises à jour automatiques {#asu}

L’offre d’intégration Adobe Sign vous permet de recevoir automatiquement les mises à jour dans [!DNL NetSuite] concernant le statut des accords qui ont été envoyés depuis [!DNL NetSuite]. Lorsque cette fonctionnalité est activée, [!DNL NetSuite] reflète toujours le statut de vos accords. Vous pouvez activer les mises à jour automatiques de statut comme suit :

1. Accédez à **[!UICONTROL Configuration > Société > Activer les fonctionnalités].**
1. Sélectionnez le fichier **[!UICONTROL SuiteCloud]** sous-onglet.
1. Activez les options suivantes :

   * Dans la section SuiteBuilder, activez l’option **[!UICONTROL Enregistrements personnalisés]**.

   * Dans la section SuiteScript, activez les options **[!UICONTROL Client SuiteScript]** et **[!UICONTROL Serveur SuiteScript]** et acceptez les conditions d’utilisation pour les deux.

1. Sélectionnez **[!UICONTROL Enregistrer]**.

   Vos options sont définies comme indiqué sur l’image.

   ![Activation des fonctionnalités SuiteCloud](images/enable-suitecloudfeatures.png)

## Objets et types d’enregistrement {#objects}

L’offre d’intégration Adobe Sign présente déjà l’objet Accord Adobe Sign avec de nombreuses normes [!DNL NetSuite] objets, notamment : Enregistrements client, estimation, piste, opportunité et partenaire. Vous pouvez également utiliser l’offre groupée Adobe Sign avec d’autres types d’enregistrements, y compris des enregistrements personnalisés.

L’onglet Accord peut s’afficher avec deux types de [!DNL NetSuite] enregistrements : Enregistrements d’entité et de transaction. Nous supposons généralement qu’un enregistrement Transaction est un enregistrement (tel qu’un devis) qui peut être converti en document PDF ; alors qu&#39;un enregistrement d&#39;entité ne peut pas être converti en mot de PDF.

## Enregistrements de transactions {#transrecords}

Si l’accord est créé à partir d’un enregistrement de transaction, le premier document de l’enregistrement d’accord est la version PDF de l’enregistrement d’origine et le premier destinataire est l’adresse e-mail de l’enregistrement. Si vous ne souhaitez pas que le premier document soit une version PDF de l’enregistrement d’origine, accédez à **[!UICONTROL Sous-onglet Configuration > Société > Préférences générales > Préférences personnalisées]** et désactivez l&#39;option **[!UICONTROL Joindre automatiquement le PDF de transactions]** s&#39;affiche. Voir [Définition des préférences personnalisées](#configure) pour plus d’informations.

Sous Préférences personnalisées, vous pouvez également activer la préférence **[!UICONTROL Utiliser le contact de transaction comme premier signataire]** si vous souhaitez que le contact de transaction principal soit automatiquement ajouté en tant que premier signataire. Lorsqu&#39;il est associé à un enregistrement de transaction, il affiche le **[!UICONTROL Accords]** et le **[!UICONTROL Send for Signature]** des boutons.

![Estimation](images/quote.png)

## Enregistrements d’entités {#entity-records}

Si l’accord est créé à partir d’un enregistrement d’entité, le premier destinataire est l’adresse e-mail de l’enregistrement. Lorsqu’il est associé à un enregistrement d’entité, seul l’onglet Accords s’affiche.

## Personnalisation de l&#39;offre groupée {#customize}

La personnalisation de l’offre groupée comprend les éléments suivants :

* Déploiement des scripts pour le sous-onglet Accords  et le bouton Envoyer pour signature pour les types d’enregistrement appropriés.
* Définition des autorisations de rôle pour vos types d’enregistrements Adobe Sign.
* Modification des autorisations pour accorder l’accès au sous-onglet *Accords* et au bouton *Envoyer pour signature*.

![Scripts](images/scripts.png)

### Configuration des accords Adobe Sign pour d’autres types d’enregistrement  {#configuring-adobe-sign-agreements-for-additional-record-types}

Pour déployer le fichier *Accords* et le sous-onglet *Send for Signature* pour les types d’enregistrement appropriés :

1. Accédez à **[!UICONTROL Personnalisation > Génération de scripts > Scripts].**

1. Dans le *Scripts* qui s’affiche, recherchez le script à déployer, puis sélectionnez ****[!UICONTROL Affichage]****.

   * Pour ajouter le fichier *Send for Signature* , sélectionnez **[!UICONTROL Bouton d’estimation Adobe Sign]** script.

   * Pour ajouter le fichier *Accords* , sélectionnez **[!UICONTROL Chargeur d’accord Adobe Sign]** script.

1. Sur la page Script , sélectionnez **[!UICONTROL Déployer le script]**.

   ![Déploiement du script](images/deploly-script.png)

1. Sur la page Déploiement du script, procédez comme suit :

   * Dans la liste *S’applique à*, sélectionnez le type d’enregistrement.
   * Si vous le souhaitez, entrez l’ID de déploiement du script.

      Reportez-vous au *Création d&#39;un ID de déploiement de script personnalisé* dans la boîte de dialogue [!DNL NetSuite] Centre d’aide pour plus d’informations. Si vous ne saisissez pas d’ID, celui-ci est généré.

   * Cochez la case **[!UICONTROL Déployé]**.

   ![Déploiement du script](images/execute-as-admin.png)

   * Définissez *Statut* sur **[!UICONTROL Publié]**.

      Vous ne devez pas spécifier de *Type d&#39;événement* ou *Niveau du journal*.

   * Dans le [!UICONTROL *Rôle Exécuter en tant que]* , sélectionnez l’option **[!UICONTROL Exécuter en tant qu’administrateur]**.

   * Avec le **[!UICONTROL Audience]** (actif par défaut), sélectionnez les rôles ou utilisateurs spécifiques auxquels vous souhaitez accorder l’accès. Si vous souhaitez accorder l’accès à tous les rôles et utilisateurs, activez les options **[!UICONTROL Tout sélectionner]** correspondantes.

   * Sélectionnez **[!UICONTROL Enregistrer]**. Lorsque la confirmation de modification s’affiche, sélectionnez **[!UICONTROL Retour]**.


1. sélectionner **[!UICONTROL Liste]** en haut de la page Déploiement du script pour revenir à l’onglet *Scripts* page de liste.
1. Répétez les étapes 2 et 3 ci-dessus pour l’autre script.

## Définition des autorisations de rôle pour les types d’enregistrements Adobe Sign {#setting-role-permissions-for-adobe-sign-record-types}

Maximum [!DNL NetSuite] Les rôles doivent être autorisés à utiliser Adobe Sign sans personnalisation supplémentaire. Cependant, vous pouvez accorder des autorisations pour tous les rôles personnalisés supplémentaires qui ont été créés.

1. Accédez à&#x200B;**[!UICONTROL Personnalisation > Listes, enregistrements et fichiers > Types d’enregistrement]**.

   ![SiteBuilder - Enregistrements personnalisés](images/sitebuilder-customrecords.png)

   >[!NOTE]
   >
   >Si vous ne voyez pas l’élément *Types d’enregistrement*, accédez à l’onglet **[!UICONTROL Configuration > Société > Activer les fonctionnalités > Suite Cloud]** et activez l’option *Enregistrements personnalisés*.

1. Dans le *Types d’enregistrement* , sélectionnez **[!UICONTROL Accord Adobe Sign]** pour le sélectionner

   ![Types d’enregistrements d’un accord](images/search-adobe-signagreementsforedit.png)

1. Dans le *Type d’enregistrement personnalisé* , sélectionnez **[!UICONTROL Utiliser la liste des autorisations]** dans le *Type d’accès* de la barre de macro.

   ![Type d’enregistrement personnalisé](images/custom-record-type.png)

   >[!NOTE]
   >
   >Le type d’enregistrement *Accord Adobe Sign* est le seul type d’enregistrement Adobe Sign qui requiert le type d’accès *Utiliser la liste d’autorisations*.
   >
   >
   >Voir l’étape 6 pour obtenir des instructions sur la définition du type d’accès pour les autres types d’enregistrements Adobe Sign.

1. Sélectionnez le fichier **[!UICONTROL Autorisations]** sous-onglet.

   La liste des rôles et des autorisations s’affiche.

   ![Rôles et autorisations](images/roles-and-permissions.png)

1. Définissez les autorisations comme suit pour les rôles personnalisés supplémentaires ajoutés au &quot;[!UICONTROL Accord Adobe Sign]&quot; type d&#39;enregistrement.

   >[!NOTE]
   >
   >Pour plus d’informations, voir la rubrique *[Setting Up a Permissions List for a Custom Record Type](https://system.netsuite.com/app/help/helpcenter.nl?fid=section_N2879931.html)* dans le Centre d’aide NetSuite.

   1. Sélectionnez le rôle dans la liste *Rôle*.
   1. Définir *Niveau* à **[!UICONTROL Complet]**.
   1. Définir *Formulaire par défaut* à **[!UICONTROL Formulaire d’accord EchoSign personnalisé]**.
   1. Sélectionner **[!UICONTROL Restreindre le formulaire]** s&#39;affiche.
   1. Sélectionner **[!UICONTROL Ajouter]** pour enregistrer les modifications pour la ligne du rôle.

   ![Définition des autorisations](images/set-permissions.png)

   La nouvelle ligne s’affiche comme indiqué ci-dessous :

   ![Définition des autorisations pour le type d’enregistrement Accord](images/set-permissions-foragreementrecordtype.png)

   Répétez les étapes a à e ci-dessus pour tous les autres rôles personnalisés.

   * sélectionner **[!UICONTROL Enregistrer]** dans le *Type d’enregistrement personnalisé* lorsque les autorisations pour tous les rôles ont été définies.
   La *[!UICONTROL Type d&#39;enregistrement client]* s’affiche.

1. Répétez les étapes 1 à 3 ci-dessus pour définir le *type d’accès* pour tous les autres types d’enregistrements Adobe Sign sur

   **[!UICONTROL Aucune autorisation requise].** Cela s’applique aux types d’enregistrement suivants :

   * Configuration Adobe Sign
   * Document Adobe Sign
   * Événement Adobe Sign
   * Langue Adobe Sign
   * Erreurs de script Adobe Sign
   * Accord signé Adobe Sign
   * Signataire Adobe Sign

### Octroi d’accès à l’onglet Accord et au bouton Send for Signature  {#granting-access-to-the-agreement-tab-and-send-for-signature-button}

L’offre d’intégration Adobe Sign présente déjà l’objet Accord Adobe Sign avec de nombreuses normes [!DNL NetSuite] objets (Client, Estimation) [Devis], Prospect, etc.). Le sous-onglet *Accord* est automatiquement activé pour les types d’objets suivants : Client, Client potentiel, Opportunité, Partenaire, Prospect, Devis et Facture fournisseur.

La *[!UICONTROL Send for Signature]* est automatiquement activé **o[!UICONTROL Uniquement pour l’objet Devis]**.

[!DNL NetSuite]Les administrateurs peuvent étendre la possibilité de créer des accords sur d’autres objets CRM en modifiant les autorisations d’ajout du sous-onglet *Accord*, du bouton *Envoyer pour signature* ou des deux à ces objets.

#### Modification des autorisations d’accès au bouton Envoyer pour signature  {#modifying-permissions-to-grant-access-to-the-send-for-signature-button}

1. Accédez à **[!UICONTROL Personnalisation > Génération de scripts > Scripts]**.

   La page de la liste *Scripts* s’affiche.

   * Si nécessaire, utilisez les filtres pour localiser les scripts Adobe Sign

1. Dans le *Scripts* , recherchez l&#39;élément *Bouton d’estimation Adobe Sign* script (contrôle la *Send for Signature* ), puis sélectionnez **Affichage**.

   ![Affichage du Bouton d’estimation Adobe Sign](images/view-adobe-sign-estimatesbutton.png)

1. Sur la page *Script*, procédez comme suit :

   * sélectionnez le **[!UICONTROL Déploiements]** sous-onglet

   * Sous &quot;*S’applique à*&quot; sélectionnez le lien de l&#39;entité que vous souhaitez modifier.

      * **[!UICONTROL Devis]** dans cet exemple

   ![sélectionnez le sous-onglet Déploiements .](images/click-the-deploymentssub-tab.png)

   * sélectionnez le **[!UICONTROL Modifier]** dans la *Déploiement du script* page

   ![Modification du déploiement de script](images/edit-script-deployment.png)

   * Avec le sous-onglet **[!UICONTROL Public]** actif, sélectionnez les rôles ou utilisateurs spécifiques auxquels vous souhaitez accorder l’accès.

      * Si vous souhaitez accorder l’accès à tous les rôles et utilisateurs, activez les options **[!UICONTROL Tout sélectionner]** correspondantes
   * sélectionner **[!UICONTROL Enregistrer]**

   ![Sélection des rôles spécifiques](images/save-script-deployment-quote.png)

#### Modification des autorisations pour accorder l’accès à l’onglet Accords  {#modifying-permissions-to-grant-access-to-the-agreements-tab}

1. Accédez à **[!UICONTROL Personnalisation > Génération de scripts > Scripts]**.
1. Dans le [!UICONTROL Scripts] , recherchez l&#39;élément *[!UICONTROL Chargeur d’accord Adobe Sign]* script (contrôle la *Onglet Accords*), puis sélectionnez **[!UICONTROL Affichage]**.
1. Sur la page *Script*, procédez comme suit :

   1. Sélectionnez le fichier **[!UICONTROL Déploiements]** sous-onglet
   1. Sous &quot;*[!UICONTROL S’applique à]*&quot; sélectionnez le lien de l&#39;entité pour laquelle vous souhaitez modifier l&#39;accès
   1. Dans le *[!UICONTROL Déploiement du script]* , sélectionnez l&#39;élément **[!UICONTROL Modifier]** bouton
   1. Avec le sous-onglet **[!UICONTROL Public]** actif (il est actif par défaut), sélectionnez les rôles ou utilisateurs spécifiques auxquels vous souhaitez accorder l’accès. Si vous souhaitez accorder l’accès à tous les rôles et utilisateurs, activez les options **[!UICONTROL Tout sélectionner]** correspondantes
   1. sélectionner **[!UICONTROL Enregistrer]**

## Utilisation d’Adobe Sign pour [!DNL NetSuite] offre

Pour envoyer des accords à partir de [!DNL NetSuite] et recevoir des mises à jour sur ces accords, les utilisateurs doivent avoir le même ID de connexion (adresse e-mail) dans [!DNL NetSuite] et dans Adobe Sign.

### Création d’un accord Adobe Sign

Après avoir installé une nouvelle offre groupée dans un compte Sandbox ou de production, vous devez tester l’offre groupée en créant un nouvel accord. Vous pouvez créer des accords Adobe Sign à partir d’un enregistrement d’entité, d’un enregistrement de transaction ou d’un accord autonome.

>[!NOTE]
>
>Le processus de création d’un accord diffère légèrement selon la manière dont il est créé. Le processus général consiste à spécifier les options de votre accord, à ajouter un ou plusieurs documents d’accord et à indiquer les destinataires. Le processus décrit ci-dessous suppose que vous créez l’accord à partir d’un enregistrement client.

1. Sélectionnez ou créez un enregistrement client à partir duquel vous souhaitez envoyer un accord ou sélectionnez-en un autre [!DNL NetSuite] Type d’enregistrement pour lequel l’onglet Accords est activé.

1. Dans l’enregistrement, sélectionnez le fichier **[!UICONTROL Accords]** sous-onglet.
1. Sélectionner **[!UICONTROL Nouvel accord]**.

   ![Nouvel accord](images/new-agreement.png)

1. Dans le *[!UICONTROL Accord Adobe Sign]* , sélectionnez **[!UICONTROL Modifier]**.

   ![Modification d’un nouvel accord](images/edit-new-agreement.png)

1. Spécifiez les options de votre accord comme suit :

   * **Nom de contrat** — Saisissez un nom pour l&#39;accord.
   * **Message**-Saisissez un message personnalisé pour le destinataire.
   * **Type de signature** : sélectionnez le type de signature accepté pour le document. Les options sont les suivantes : *Signature électronique :* et *Signature par fax*.

   * **Je dois également signer cet accord** : activez cette option pour indiquer que l’expéditeur doit également signer l’accord.
   * **Ordre des signatures**-Si la *Je dois également signer cet accord* est activée, sélectionnez l’ordre dans lequel l’expéditeur et les destinataires doivent signer. Les options disponibles sont « Je signe, puis les destinataires signent », « Les destinataires signent, puis je signe » et « Aucun ».

   * **Prévisualiser le document ou positionner les signatures (ou les champs de formulaire)** : activez cette option pour permettre aux expéditeurs de prévisualiser l’accord et d’ajouter des champs (glisser-déposer de la signature, champs initiaux et autres champs de formulaire) à l’accord avant son envoi aux destinataires.
   * **Vérification de l’identité du signataire** — Activez cette option, puis sélectionnez l&#39;une des options de vérification d&#39;identité suivantes :

      * Cette option s’affiche uniquement lorsque plusieurs des trois méthodes de vérification de l’identité des signataires répertoriées ci-dessous sont activées dans Préférences personnalisées. (Voir [Définition des préférences personnalisées](#customize) pour plus d’informations.) Si une seule préférence est activée, l’option **[!UICONTROL Vérification de l’identité du signataire]** ne s’affiche pas.

   **Méthodes de vérification de l’identité**

   * **Mot de passe requis pour la signature** — Exiger des signataires qu&#39;ils saisissent un mot de passe unique que vous spécifiez.
   * **Authentification fondée sur les connaissances** — Demandez aux signataires de fournir leur nom, leur adresse et éventuellement les quatre derniers chiffres de leur numéro de sécurité sociale, puis de répondre à une liste de questions vérifiant les informations qu’ils ont fournies. Disponible uniquement aux États-Unis.
   * **Authentification d’identité web** — Exiger des signataires qu&#39;ils vérifient leur identité en se connectant à l&#39;un des sites suivants : Facebook, Google, LinkedIn, Twitter, Yahoo ! ou Microsoft Live.
   * **Mot De Passe Requis Pour Afficher Le Mot De PDF** : activez cette option pour exiger qu’un destinataire saisisse un mot de passe avant d’ouvrir un mot de PDF de l’accord ou de l’accord signé. Le fichier de mot de PDF envoyé à tout le monde est chiffré et nécessite le mot de passe pour être ouvert. Ne perdez pas votre mot de passe car il est irrécupérable. Si vous perdez le mot de passe, vous devez supprimer cette transaction et recommencer.
   * **Mot de passe/Confirmer le mot de passe** — Si la *Mot De Passe Requis Pour Afficher Le Mot De PDF* est activée, saisissez le mot de passe qui doit être utilisé pour afficher l’accord.
   * **Rappeler aux destinataires de signer** : indiquez si des rappels sont envoyés aux destinataires et à quelle fréquence. Les options disponibles sont *Jamais*, *Quotidien* ou *Hebdomadaire*.
   * **Langue :** Spécifiez la langue dans laquelle la page de signature et les notifications électroniques s’affichent pour les destinataires.
   * **Hébergement de la signature pour le premier signataire** : activez cette option pour autoriser l’hôte de l’expéditeur à signer en personne pour le premier signataire.
   * **Jours avant l’échéance de signature** — Saisissez un nombre entier pour indiquer le délai de signature de l’accord (date du jour + nombre de jours).
   * **Enregistrement parent** — Le cas échéant, sélectionnez un enregistrement parent pour le lier à l’accord.

   ![Configuration de l’accord](images/configure-agreement-2.png)

1. Sélectionnez le fichier **[!UICONTROL Documents]** .

   ![Onglet Documents](images/documents-tab.png)

1. Dans le *Documents* , joignez un document existant à partir de l’armoire à fichiers à l’aide du *Document Adobe Sign* , puis sélectionnez l’option **[!UICONTROL Joindre]**.

   Ou cliquez sur **[!UICONTROL Nouveau document Adobe Sign]** pour accéder à la *[!UICONTROL Document Adobe Sign]* , puis saisissez le nom d’un document dans votre [!DNL NetSuite] , sélectionnez des fichiers dans votre enregistrement de transaction (le cas échéant) ou joignez un nouveau document.

   Vous pouvez ajouter plusieurs documents à un accord.

1. Sélectionner **[!UICONTROL Destinataires]** et indiquez le destinataire en le sélectionnant dans la liste des contacts ou en saisissant une adresse électronique.

   ![Ajouter des destinataires](images/add-recipients.png)

   Chacun de vos destinataires peut être marqué comme signataire ou destinataire en copie. Si la préférence personnalisée *Autoriser le marquage des destinataires comme signataires approbateurs* est activée, les destinataires peuvent être également marqués comme approbateurs. Voir [Définition des préférences personnalisées](#customize) pour plus d’informations.

   * Les **Signataires** doivent signer l’accord.
   * **Approbateurs** doit approuver l’accord, mais ne le signe pas, et peut éventuellement ajouter des données à un accord.
   * **Destinataires en copie** sont avertis des mises à jour de l’accord et lorsque l’accord est signé et terminé. Les destinataires en copie ne prennent pas part au processus de signature ou d’approbation.

      Si la préférence personnalisée *Utiliser le contact de l’enregistrement parent comme signataire* est activée seule ou conjointement avec la préférence *Utiliser le contact de transaction comme signataire*, le premier destinataire est défini par défaut, mais peut être modifié.

1. Sélectionner **[!UICONTROL Ajouter]** après avoir saisi chaque destinataire.

1. Sélectionner **[!UICONTROL Enregistrer]** pour enregistrer l’accord.

### Envoi d’accords pour signature

Lorsque l’accord est prêt à être envoyé, sélectionnez l’option **[!UICONTROL Send for Signature]** du menu.

* Si la *Aperçu du document ou positionnement des signatures* est activée, cliquez sur **[!UICONTROL Send for Signature]**. Dans la fenêtre qui s’ouvre, prévisualisez le document ou faites glisser des champs de formulaire vers le document avant de l’envoyer. Sélectionner **[!UICONTROL Envoyer]** pour envoyer l’accord au destinataire.

* Si la *[!UICONTROL Héberger signature pour 1er signataire]* est activée, cliquez sur **[!UICONTROL Send for Signature]**. Dans la fenêtre qui s’ouvre, autorisez le signataire à signer le document avec l’expéditeur présent.

   Un lien *Héberger signature pour le signataire actuel* pour le signataire actuel s’affiche également en regard du champ *Héberger signature pour 1er signataire*, accessible jusqu’à ce que le document soit signé. Utilisez ce lien pour héberger la signature de l’accord pour plusieurs signataires ou pour rouvrir la fenêtre contextuelle si elle a été fermée par erreur.

Une fois l’accord envoyé, les destinataires reçoivent un e-mail les informant des documents en attente de leur signature.

Une fois que les destinataires ont signé le document, l’expéditeur reçoit une notification par e-mail pour l’informer que le document a été signé.

#### Envoyer à partir d’un devis

Adobe Sign s’intègre directement aux devis dans [!DNL NetSuite] afin qu’un PDF du devis soit automatiquement généré et joint à l’enregistrement de l’accord.

Lorsque vous consultez un devis, sélectionnez **[!UICONTROL Send for Signature]**. Il génère et affiche le devis joint à l’accord. Vous pouvez également ajouter le bouton *Envoyer pour signature* à d’autres types d’enregistrements de transaction. Pour plus d’informations, voir [Objets et types d’enregistrements.](#objects)

![Devis - Envoyer pour signature](images/quote-send-forsignature.png)

### Suivi du statut et envoi de rappels

Après avoir envoyé un accord :

* Le statut du document est remplacé par *Émis pour signature* dans la section Détails de l’accord.
* La *Send for Signature* est remplacé par les trois boutons suivants :

   * **Mettre à jour** — Pour mettre à jour manuellement l&#39;état si les mises à jour d&#39;état n&#39;ont pas été configurées. Pour plus d’informations, voir [Configuration des mises à jour automatiques de statut.](#asu)
   * **Envoyer le rappel** : pour envoyer un rappel au signataire actif.
   * **Annuler l’accord** — Pour annuler un accord. Un accord peut être annulé après avoir été envoyé pour signature si tous les destinataires n’ont pas encore signé.

![Émis pour signature](images/out-for-signature.png)

Un nouveau sous-onglet *Événements* s’affiche dans l’enregistrement de l’accord, dans lequel vous pouvez suivre le statut de l’accord.

Vous pouvez afficher l’historique des événements de l’accord, qui inclut des informations sur le moment où l’accord a été envoyé, affiché et signé.

![Événements d’accord signés](images/agreement-events.png)

Une fois l’accord signé :

* Son statut est remplacé par *Signé*..
* Vous pouvez renvoyer à l’enregistrement parent de cet accord à l’aide du lien.
* Vous pouvez utiliser les liens de téléchargement sous Document signé et Piste d’audit pour accéder à ces documents.
* Un *Document signé* s’affiche pour afficher les vignettes du document signé.

![Accord signé](images/signed-agreement.png)

>[!NOTE]
>
>Une fois qu’un accord a été envoyé pour signature, vous ne pouvez pas modifier l’enregistrement. Ceci est prévu pour conserver l’enregistrement des événements.

## Désinstallation de l’offre groupée

Pour désinstaller l’offre groupée, suivez les étapes indiquées dans la boîte de dialogue [!DNL NetSuite] Aide. Consultez la *[Désinstallation d’une offre groupée](https://docs.oracle.com/en/cloud/saas/netsuite/ns-online-help/section_N3400972.html)* dans la boîte de dialogue [!DNL NetSuite] Centre d’aide pour plus d’informations.

Lorsque vous désinstallez l’offre groupée, les accords non signés sont supprimés. Les accords signés et les fichiers de mot de PDF d’audit correspondants ne sont pas affectés.

Ne désinstallez PAS l’offre groupée si vous devez conserver vos accords non signés.

## Dépannage

### Déterminer la progression de la mise à jour  {#determineprogress}

Si la mise à jour prend du temps, vous pouvez vérifier le sous-onglet Journal d’exécution du script Installation de l’offre groupée Adobe Sign pour déterminer la progression de votre mise à jour comme suit :

1. Accédez à **[!UICONTROL Personnalisation > Génération de scripts > Scripts]**.
1. Dans le [!UICONTROL Scripts] , recherchez l&#39;élément *[!UICONTROL Installation de l’offre groupée Adobe Sign]* script, puis sélectionnez **[!UICONTROL Modifier]**.
1. Dans le [!UICONTROL Scripts] , sélectionnez l&#39;élément **Journal d’exécution** sous-onglet.
1. sélectionner **Actualiser**.

   Le journal d’exécution est mis à jour pour refléter l’état. La colonne *Détails* affiche la progression des mises à jour de vos accords.

   ![Actualisation de la progression](images/refresh-progress.png)

### Résolution des problèmes de jeton d’accès

Vous pouvez rencontrer un message &quot;Le jeton d’accès fourni n’est pas valide ou a expiré&quot; lors de l’interaction avec des accords.

Cela peut se produire pour les raisons suivantes :

* La [!DNL NetSuite]/L’administrateur Adobe Sign qui a configuré OAuth a révoqué le jeton d’accès.
* Le jeton d’accès a expiré car aucun accord n’a été envoyé à partir de [!DNL NetSuite] au cours des 60 derniers jours
* La [!DNL NetSuite]/L’administrateur Adobe Sign n’a pas terminé la configuration OAuth initiale

Pour résoudre ce problème, exécutez à nouveau le processus de configuration OAuth. Pour plus d’informations, voir [Configuration d’OAuth après l’installation ou la mise à niveau](#oauth).

![Jeton non valide](images/invalid-token.png)

### Résolution des problèmes de statut du document {#resolvestatus}

Si [mises à jour automatiques](#asu) sont configurés mais l’état de l’accord n’est pas mis à jour après l’envoi des accords, essayez les solutions suivantes :

1. Consultez le journal d’exécution du déploiement du script *Mise à jour externe d’Adobe Sign* pour voir si vous recevez des appels d’Adobe Sign comme suit :

   1. Accédez à **[!UICONTROL Personnalisation > Génération de scripts > Déploiements de scripts.]**
   1. Dans le *Déploiements de scripts* , recherchez l&#39;élément *Mise à jour externe Adobe Sign* script, puis sélectionnez **[!UICONTROL Modifier]**
      1. Dans le *[!UICONTROL Déploiement du script]* , sélectionnez l&#39;élément **[!UICONTROL Journal d’exécution]** sous-onglet.
      * Vous devriez voir un *Enregistrement d’accord mis à jour* entrée pour chaque ID d’accord


1. Consultez le journal d’exécution du déploiement du script *Accords de mise à jour d’Adobe Sign* pour voir si des erreurs sont présentes. Pour ce faire, procédez comme suit :

   1. Accédez à **[!UICONTROL Personnalisation > Génération de scripts > Déploiements de scripts]**.
   1. Dans le [!UICONTROL Déploiements de scripts] , recherchez l&#39;élément *[!UICONTROL Adobe Sign Update Agreements]* avec le &quot;[!UICONTROL Planifié]&quot;, puis sélectionnez **[!UICONTROL Modifier]**.
   1. Dans le [!UICONTROL Déploiement du script] , sélectionnez l&#39;élément **[!UICONTROL Journal d’exécution]** sous-onglet.
   1. Sous [!UICONTROL Type], sélectionnez **[!UICONTROL Erreur]** pour filtrer les résultats.

1. Enfin, vérifiez si des erreurs sont présentes dans le journal d’exécution du script *Gestionnaire Adobe Sign* en suivant les instructions de l’étape 2 ci-dessus.

### Résolution des erreurs de type MIME  {#resolving-mime-type-errors}

Si vous obtenez une erreur de type MIME lors de l’envoi d’un accord, cela peut être dû au fait que le nom dans le champ Nom de fichier ne correspond pas au nom et à l’extension du fichier téléchargé. Si vous laissez le champ Nom de fichier vide, il est automatiquement renseigné avec le nom de fichier et l’extension corrects.

### Affichage des journaux de script {#viewing-script-logs}

Vous pouvez également afficher les journaux d’exécution de déploiement pour les scripts qui ne sont pas liés à des problèmes de statut de document. Pour plus d’informations, voir [Résolution des problèmes liés au statut du document.](#resolvestatus)

1. Accédez à **[!UICONTROL Personnalisation > Génération de scripts > Scripts]**.

   La page de la liste *Scripts* s’affiche. Si nécessaire, utilisez les filtres pour localiser le script approprié.

1. Sélectionnez **[!UICONTROL Affichage]** pour le script correspondant.

1. Sélectionnez le fichier **[!UICONTROL Journal d’exécution]** sur la page pour afficher le journal du script.

## Assistance technique {#support}

Accédez à l’onglet [Portail de support Adobe Sign](https://adobe.com/go/adobesign-support-center_fr) pour accéder aux FAQ, à la documentation, aux articles de la base de connaissances ou pour contacter le support de l’Adobe.
