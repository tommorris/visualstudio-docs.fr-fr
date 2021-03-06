---
title: Publier des Applications ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Options
- Microsoft.VisualStudio.Publish.ClickOnceProvider.PublishWizard.Help
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- ClickOnce applications, publishing
- applications [Visual Studio], ClickOnce deployment
- deploying applications [ClickOnce], publishing ClickOnce applications
ms.assetid: eb6dfe79-f54c-4331-8e36-073688e70973
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a8ef8f2ae6ed1f198fc5f7661b79764d0a790bd
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279811"
---
# <a name="publish-clickonce-applications"></a>Publier des applications ClickOnce
Lorsque vous publiez une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pour la première fois, les propriétés de publication peuvent être définies à l'aide de l'Assistant Publication. Seules quelques-unes des propriétés sont disponibles dans l'Assistant ; toutes les autres sont définies à leurs valeurs par défaut.  
  
 Les modifications ultérieures apportées aux propriétés de publication sont effectuées sur le **publier** page dans le **Concepteur de projet**.  
  
## <a name="publish-wizard"></a>Assistant Publication  
 Vous pouvez utiliser l'Assistant Publication pour définir les paramètres de base de la publication de votre application. Cette définition inclut les propriétés de publication suivantes :  
  
-   Emplacement du dossier de publication : endroit où Visual Studio copie les fichiers (ordinateur local, partage de fichiers réseau, serveur FTP ou site web)  
  
-   Emplacement du dossier d'installation : endroit à partir duquel les utilisateurs finaux installent (partage de fichiers réseau, serveur FTP, site web, CD/DVD)  
  
-   Disponibilité en ligne ou hors connexion : indique si les utilisateurs finaux peuvent accéder à l'application avec ou sans connexion réseau  
  
-   Fréquence des mises à jour : fréquence à laquelle l'application vérifie la présence de nouvelles mises à jour.  
  
 Pour plus d’informations, consultez [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## <a name="publish-page"></a>Page Publier  
 La page **Publier** du **Concepteur de projets** permet de configurer les propriétés du déploiement ClickOnce. Le tableau suivant répertorie les rubriques.  
  
|Titre|Description|  
|-----------|-----------------|  
|[Comment : spécifier l’endroit où Visual Studio copie les fichiers](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Décrit comment définir l'emplacement où Visual Studio place les fichiers d'application et les manifestes.|  
|[Comment : spécifier l’emplacement où les utilisateurs finaux installent à partir](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Décrit comment définir l'emplacement à partir duquel les utilisateurs téléchargent et installent l'application.|  
|[Comment : spécifier le ClickOnce en mode hors connexion ou en mode d’installation en ligne](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|Décrit comment définir si l'application est disponible hors connexion ou en ligne.|  
|[Comment : définir la publication ClickOnce version](../deployment/how-to-set-the-clickonce-publish-version.md)|Explique comment définir le ClickOnce **Version de publication** propriété qui détermine si l’application que vous publiez sera traitée comme une mise à jour.|  
|[Comment : incrémenter automatiquement la publication ClickOnce version](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Décrit comment incrémenter automatiquement le numéro de révision de la **PublishVersion** chaque fois que vous publiez l’application.|  
  
 Pour plus d’informations, consultez [Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md)  
  
### <a name="application-files-dialog-box"></a>Boîte de dialogue de fichiers application  
 Cette boîte de dialogue vous permet de spécifier comment les fichiers de votre projet sont classés pour la publication, le téléchargement dynamique et la mise à jour. Elle contient une grille qui répertorie les fichiers projet qui ne sont pas exclus par défaut ou qui ont un groupe de téléchargement.  
  
 Pour exclure des fichiers, marquer des fichiers comme fichiers de données ou les composants requis et créer des groupes de fichiers pour une installation conditionnelle dans l’interface utilisateur de Visual Studio, consultez [Comment : spécifier les fichiers publiés par ClickOnce](../deployment/how-to-specify-which-files-are-published-by-clickonce.md). Vous pouvez également marquer des fichiers de données à l'aide de Mage.exe. Pour plus d’informations, consultez [Comment : inclure un fichier de données dans une application ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
### <a name="prerequisites-dialog-box"></a>Composants requis, boîte de dialogue  
 Cette boîte de dialogue spécifie quels composants requis sont installés, ainsi que la manière dont ils sont installés. Pour plus d’informations, consultez [Comment : installer les composants requis avec une application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) et [boîte de dialogue composants requis](../ide/reference/prerequisites-dialog-box.md).  
  
### <a name="application-updates-dialog-box"></a>Boîte de dialogue application mises à jour  
 Cette boîte de dialogue spécifie comment l'installation de l'application doit vérifier les mises à jour. Pour plus d’informations, consultez [Comment : gérer les mises à jour pour une application ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md).  
  
### <a name="publish-options-dialog-box"></a>Boîte de dialogue Options de publication  
 La boîte de dialogue Options de publication spécifie les options de déploiement d'une application.  
  
|||  
|-|-|  
|[Comment : modifier la langue de publication pour une application ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Explique comment spécifier une langue et une culture correspondant à la version localisée.|  
|[Comment : spécifier un nom de menu Démarrer pour une application ClickOnce](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|Décrit comment modifier le nom complet d'une application ClickOnce.|  
|[Comment : spécifier un lien pour le Support technique](../deployment/how-to-specify-a-link-for-technical-support.md)|Explique comment définir le **URL du support technique** propriété, qui identifie une page Web ou un partage de fichiers où les utilisateurs peuvent accéder à obtenir des informations sur l’application.|  
|[Comment : spécifier une URL de prise en charge pour chaque composant requis dans un déploiement ClickOnce](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|A montré comment modifier manuellement un manifeste d'application pour inclure les URL de support technique de chaque composant requis.|  
|[Comment : spécifier une page de publication pour une application ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|Décrit comment générer et publier une page web par défaut (publish.htm) en même temps que l’application|  
|[Comment : personnaliser la page de Web ClickOnce par défaut](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Décrit comment personnaliser la page web qui est automatiquement générée et publiée avec l’application.|  
|[Comment : activer le démarrage automatique pour les installations de CD](../deployment/how-to-enable-autostart-for-cd-installations.md)|Décrit comment activer le démarrage automatique afin que l'application ClickOnce soit lancée automatiquement lorsque le média est inséré.|  
  
## <a name="related-tpics"></a>Tpics connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Comment : créer des associations de fichiers pour a ClickOnce application](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|Décrit comment ajouter la prise en charge d’extension de nom de fichier à une application ClickOnce.|  
|[Comment : récupérer les informations de chaîne de requête dans une application ClickOnce en ligne](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|Montre comment récupérer des paramètres passés dans l'URL utilisée pour exécuter une application ClickOnce.|  
|[Comment : suspendre l’activation des URL des applications ClickOnce à l’aide du Concepteur](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Décrit comment forcer les utilisateurs à démarrer l’application à partir de la **Démarrer** menu à l’aide du concepteur.|  
|[Comment : suspendre l’activation des URL des applications ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Décrit comment forcer les utilisateurs à démarrer l’application à partir de la **Démarrer** menu.|  
|[Procédure pas à pas : Téléchargement d’assemblys à la demande avec l’API à l’aide du concepteur du déploiement ClickOnce](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Explique comment télécharger les assemblys d'application uniquement lors de leur première utilisation par l'application à l'aide du concepteur.|  
|[Procédure pas à pas : Téléchargement d’assemblys à la demande avec l’API du déploiement ClickOnce](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Explique comment télécharger les assemblys d'application uniquement lors de leur première utilisation par l'application.|  
|[Procédure pas à pas : Téléchargement d’assemblys satellites à la demande avec l’API du déploiement ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Décrit comment marquer vos assemblys satellites comme facultatifs et télécharger uniquement l'assembly nécessaire à un ordinateur client pour ses paramètres de culture actuels.|  
|[Procédure pas à pas : Déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|Explique comment utiliser les outils du .NET Framework pour déployer votre application ClickOnce.|  
|[Procédure pas à pas : Déployer manuellement une application ClickOnce qui ne nécessite pas de nouvelle signature et qui conserve les informations de personnalisation](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)|Explique comment utiliser les outils du .NET Framework pour déployer votre application ClickOnce sans signer à nouveau les manifestes.|  
|[Comment : configurer des projets pour cibler les plateformes](../ide/how-to-configure-projects-to-target-platforms.md)|Explique comment publier pour un processeur 64 bits en modifiant le **unité centrale cible** ou **plateforme cible** propriété dans votre projet.|  
|[Procédure pas à pas : Activer une application ClickOnce s’exécuter sur plusieurs versions du .NET Framework](https://msdn.microsoft.com/library/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|Explique comment permettre à une application ClickOnce de s'installer et de s'exécuter sur plusieurs versions du .NET Framework.|  
|[Procédure pas à pas : Créer un programme d’installation personnalisé pour une application ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|Explique comment créer un programme d'installation personnalisé pour installer une application ClickOnce.|  
|[Comment : publier une application WPF avec les styles visuels activés](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Fournit les instructions pas à pas pour résoudre une erreur qui s'affiche lorsque vous essayez de publier une application WPF pour laquelle les styles visuels sont activés.|  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Référence de ClickOnce](../deployment/clickonce-reference.md)