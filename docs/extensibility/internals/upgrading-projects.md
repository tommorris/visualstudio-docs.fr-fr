---
title: La mise à niveau des projets | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea5c29819d0035e45f97122fd108ea1f51d60806
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057528"
---
# <a name="upgrading-projects"></a>Mise à niveau des projets

Modifications du modèle de projet à partir d’une version de Visual Studio à l’autre peuvent nécessiter que les projets et solutions être mis à niveau afin qu’ils puissent exécuter sur la version plus récente. Le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fournit des interfaces qui peuvent être utilisées pour implémenter la mise à niveau de prise en charge dans vos propres projets.

## <a name="upgrade-strategies"></a>Stratégies de mise à niveau

Pour prendre en charge une mise à niveau, votre implémentation de système de projet doit définir et implémenter une stratégie de mise à niveau. Pour déterminer votre stratégie, vous pouvez choisir de prendre en charge la sauvegarde de la côte à côte (SxS), sauvegarde de copie ou les deux.

-   Sauvegarde de la côte à côte signifie qu’un projet copie seulement les fichiers que vous avez besoin de la mise à niveau en place, ajout d’un suffixe de nom fichier approprié, par exemple, « .old ».

-   Sauvegarde de copie signifie qu’un projet copie tous les éléments de projet à un emplacement de sauvegarde fourni par l’utilisateur. Les fichiers appropriés à l’emplacement du projet d’origine sont ensuite mis à niveau.

## <a name="how-upgrade-works"></a>Comment mettre à niveau Works

Quand une solution créée dans une version antérieure de Visual Studio est ouvert dans une version plus récente, l’IDE vérifie le fichier de solution pour déterminer si elle doit être mis à niveau. Si la mise à niveau est requise, le **Assistant Mise à niveau** est lancée automatiquement pour guider l’utilisateur au long du processus de mise à niveau.

Lorsqu’une solution a besoin de la mise à niveau, il interroge chaque fabrique de projet pour sa stratégie de mise à niveau. La stratégie détermine si la fabrique de projet prend en charge la sauvegarde de copie ou côte à côte. Les informations sont envoyées à la **Assistant Mise à niveau**, qui collecte les informations requises pour la sauvegarde et présente les options applicables à l’utilisateur.

### <a name="multi-project-solutions"></a>Solutions à projets multiples

Si une solution contient plusieurs projets et les stratégies de mise à niveau sont différents, tels que lorsqu’un projet C++ qui prend uniquement en charge la sauvegarde de la côte à côte et un projet Web qui prennent uniquement en charge la sauvegarde de copie, les fabriques de projet doivent négocier la stratégie de mise à niveau.

La solution interroge chaque fabrique de projet pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Il appelle ensuite <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> pour vérifier si les fichiers de projets globale doivent être de la mise à niveau et à déterminer les stratégies de mise à niveau pris en charge. Le **Assistant Mise à niveau** est ensuite appelée.

Une fois que l’utilisateur a terminé l’Assistant, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> est appelée sur chaque fabrique de projet pour effectuer la mise à niveau réelle. Pour faciliter les sauvegardes, les méthodes de IVsProjectUpgradeViaFactory fournissent la <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> service pour consigner les détails de la mise à niveau. Ce service ne peut pas être mis en cache.

Après la mise à jour tous les fichiers globales pertinents, chaque fabrique de projet peut choisir instancier un projet. L’implémentation de projet doit prendre en charge <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> méthode est ensuite appelée pour mettre à niveau tous les éléments de projet approprié.

> [!NOTE]
> Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> méthode ne fournit pas le service SVsUpgradeLogger. Ce service peut être obtenu en appelant <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.

## <a name="best-practices"></a>Meilleures pratiques

Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> service pour vérifier si vous pouvez modifier un fichier avant de le modifier et que vous pouvez l’enregistrer avant de l’enregistrer. Cela vous aidera votre sauvegarde et gérer les implémentations de mise à niveau des fichiers de projet sous contrôle de code source, les fichiers dotés d’autorisations suffisantes et ainsi de suite.

Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> service pendant toutes les phases de la sauvegarde et de mettre à niveau des informations sur la réussite ou l’échec de la mise à niveau.

Pour plus d’informations sur la sauvegarde et la mise à niveau des projets, consultez les commentaires pour IVsProjectUpgrade dans vsshell2.idl.

## <a name="upgrading-custom-projects"></a> La mise à niveau de projets personnalisés

Si vous modifiez les informations persistantes dans le fichier projet entre des versions Visual Studio différentes de votre produit, vous devez prendre en charge la mise à niveau de votre fichier projet vers la version la plus récente. Pour prendre en charge la mise à niveau qui vous permet de participer les **Assistant Conversion de Visual Studio**, implémenter la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface. Cette interface fournit le seul mécanisme disponible pour mettre à niveau une copie. La mise à niveau du projet est une étape du processus d’ouverture de la solution. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface est implémentée par la fabrique de projet ou au moins doit être obtenue à partir de la fabrique de projets.

L’ancien mécanisme qui utilise le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface est toujours pris en charge, mais conceptuellement met à niveau le système de projet dans le cadre du projet ouvert. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface est donc appelée par le Visual Studio environnement même si le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface est appelée ou implémentée. Cette approche vous permet d’utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> implémenter la copie et de projeter uniquement les parties de la mise à niveau et de déléguer le reste du travail à effectuer sur place (éventuellement au nouvel emplacement) par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface.

Pour un exemple d’implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, consultez [exemples d’extensibilité Visual Studio](http://aka.ms/vs2015sdksamples).

Scénarios possibles lors d’une mise à niveau de projet :

-   Si le fichier présente un format récent non pris en charge par le projet, il doit retourner une erreur indiquant ce problème. Cela suppose que l’ancienne version de votre produit inclut le code de vérification de la version.

-   Si le <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> indicateur est spécifié dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> (méthode), la mise à niveau va être implémentée comme une mise à niveau sur place avant l’ouverture du projet.

-   Si le <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> indicateur est spécifié dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> (méthode), la mise à niveau est implémentée comme une mise à niveau de la copie.

-   Si le <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> indicateur est spécifié dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> appeler, puis l’utilisateur a été invité par l’environnement pour mettre à niveau le fichier projet comme une mise à niveau sur place, une fois que le projet est ouvert. Par exemple, l’environnement invite l’utilisateur à effectuer la mise à niveau quand celui-ci ouvre une version antérieure de la solution.

-   Si le <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> indicateur n’est pas spécifié dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> appeler, vous devez inviter l’utilisateur à mettre à niveau le fichier projet.

     Voici un exemple de message d’invite de mise à niveau :

     « Le projet '%1' a été créé avec une version antérieure de Visual Studio. Si vous l’ouvrez avec cette version de Visual Studio, vous ne pourrez peut-être plus l’ouvrir avec les versions antérieures de Visual Studio. Voulez-vous continuer et ouvrir ce projet ? »

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Pour implémenter IVsProjectUpgradeViaFactory

1.  Implémentez la méthode de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> d’interface, en particulier le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> méthode dans votre implémentation de fabrique de projet, ou rendre les implémentations pouvant être appelé à partir de votre implémentation de fabrique de projet.

2.  Si vous souhaitez effectuer une mise à niveau sur place dans le cadre de la solution d’ouverture, spécifiez l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> en tant que le `VSPUVF_FLAGS` paramètre dans votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implémentation.

3.  Si vous souhaitez effectuer une mise à niveau sur place dans le cadre de la solution d’ouverture, spécifiez l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> en tant que le `VSPUVF_FLAGS` paramètre dans votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implémentation.

4.  Pour les étapes 2 et 3, le fichier réel étapes mise à niveau, à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, peut être implémenté comme décrit dans la « implémentation `IVsProjectUpgade`» ci-dessous, ou vous pouvez déléguer la mise à niveau de fichier réel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

5.  Utilisez les méthodes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> pour valider la mise à niveau des messages pour l’utilisateur à l’aide de l’Assistant de Migration Visual Studio connexes.

6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> interface est utilisée pour implémenter n’importe quel type de mise à niveau de fichier qui doit se produire dans le cadre de la mise à niveau du projet. Cette interface n’est pas appelée à partir de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, mais n’est fourni comme un mécanisme pour mettre à niveau des fichiers qui font partie du système de projet, mais le système de projet principal n’est peut-être pas directement connaissance. Par exemple, cette situation peut se produire si les fichiers et les propriétés liés au compilateur ne sont pas gérés par la même équipe de développement que celle qui gère le reste du système de projet.

### <a name="ivsprojectupgrade-implementation"></a>Implémentation d’IVsProjectUpgrade

Si votre système de projet implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> uniquement, il ne peut pas être utilisé dans le **Assistant Conversion de Visual Studio**. Toutefois, même si vous implémentez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface, vous pouvez déléguer la mise à niveau fichier <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implémentation.

#### <a name="to-implement-ivsprojectupgrade"></a>Pour implémenter IVsProjectUpgrade

1.  Lorsqu’un utilisateur tente d’ouvrir un projet, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> méthode est appelée par l’environnement après l’ouverture du projet et avant tout autre utilisateur peut prendre des mesures sur le projet. Si l’utilisateur avait déjà été invité à mettre à niveau de la solution, puis le <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> indicateur est passé dans le `grfUpgradeFlags` paramètre. Si l’utilisateur ouvre un projet directement, ce type comme à l’aide de la **ajouter un projet existant** commande, puis le <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> indicateur n’est pas passé et le projet doit inviter l’utilisateur à mettre à niveau.

2.  En réponse à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> appel, le projet doit évaluer si le fichier projet est mis à niveau. Si le projet n’a pas besoin mettre à niveau le type de projet vers une nouvelle version, il peut simplement retourner la <xref:Microsoft.VisualStudio.VSConstants.S_OK> indicateur.

3.  Si le projet doit mettre à niveau le type de projet vers une nouvelle version, elle doit déterminer si le fichier de projet peut être modifié en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (méthode) et en passant une valeur de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> pour le `rgfQueryEdit` paramètre. Ensuite, le projet doit effectuer les opérations suivantes :

    -   Si le `VSQueryEditResult` valeur retournée dans le `pfEditCanceled` paramètre est <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, puis la mise à niveau peut continuer, car le fichier projet peut être écrites.

    -   Si le `VSQueryEditResult` valeur retournée dans le `pfEditCanceled` paramètre est <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> et `VSQueryEditResult` valeur a le <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> bit défini, puis <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> doit retourner une erreur, étant donné que les utilisateurs doivent résoudre les autorisations émettre eux-mêmes. Le projet doit alors effectuer les opérations suivantes :

         Signaler l’erreur à l’utilisateur en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> et retourner le <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> code d’erreur à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

    -   Si le `VSQueryEditResult` valeur est <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> et `VSQueryEditResultFlags` valeur a le <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bit défini, puis le fichier de projet doit être extrait en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...).

4.  Si le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> appel sur le fichier projet entraîne le fichier à extraire et la dernière version à récupérer, puis le projet est déchargé et rechargé. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> méthode est appelée à nouveau une fois qu’une autre instance du projet est créée. À ce deuxième appel, le fichier projet peut être écrit sur le disque. Il est recommandé que le projet enregistre une copie du fichier projet dans le format antérieur avec l’extension de fichier .OLD, qu’il apporte les modifications nécessaires pour la mise à niveau, puis qu’il enregistre le fichier projet dans le nouveau format. Là encore, si une partie de la mise à niveau échoue, la méthode doit indiquer une erreur en retournant <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. Le projet est alors déchargé dans l’Explorateur de solutions.

     Il est important de comprendre le processus complet qui se produit dans l’environnement pour le cas dans lequel l’appel à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (méthode) (en spécifiant une valeur de ReportOnly) retourne le <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> et <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> indicateurs.

5.  L’utilisateur tente d’ouvrir le fichier projet.

6.  L’environnement appelle votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implémentation.

7.  Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> retourne `true`, l’environnement appelle votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implémentation.

8.  L’environnement appelle votre <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implémentation pour ouvrir le fichier et initialiser l’objet de projet, par exemple, Projet1.

9. L’environnement appelle votre implémentation d’ `IVsProjectUpgrade::UpgradeProject` pour déterminer si le fichier projet doit être mis à niveau.

10. Vous appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> et passer une valeur de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> pour le `rgfQueryEdit` paramètre.

11. Retourne l’environnement <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> pour `VSQueryEditResult` et <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bit est défini dans `VSQueryEditResultFlags`.

12. Votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implémentation appelle `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

Cet appel peut entraîner l’extraction d’une nouvelle copie de votre fichier projet et la récupération de la version la plus récente, ainsi que la nécessité de recharger votre fichier projet. À ce stade, il y a deux cas de figure possibles :

-   Si vous gérez votre propre rechargement du projet, l’environnement appelle votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> mise en œuvre (VSITEMID_ROOT). Quand vous recevez cet appel, rechargez la première instance de votre projet (Projet1) et continuez la mise à niveau de votre fichier projet. L’environnement sait que vous gérez votre propre rechargement du projet si vous retournez `true` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>).

-   Si vous ne gérez pas votre propre rechargement du projet, puis vous retournez `false` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). Dans ce cas, avant <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) est retournée, l’environnement crée une autre instance de votre projet, par exemple, Project2, comme suit :

    1.  L’environnement appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> sur le premier objet de projet, Projet1, ce qui fait passer cet objet à l’état inactif.

    2.  L’environnement appelle votre implémentation d’ `IVsProjectFactory::CreateProject` pour créer une deuxième instance de votre projet (Projet2).

    3.  L’environnement appelle votre implémentation d’ `IPersistFileFormat::Load` pour ouvrir le fichier et initialiser le deuxième objet projet (Projet2).

    4.  L’environnement appelle `IVsProjectUpgrade::UpgradeProject` une deuxième fois pour déterminer si l’objet projet doit être mis à niveau. Toutefois, cet appel est effectué sur la nouvelle instance (la deuxième) du projet, Projet2. Il s’agit du projet qui est ouvert dans la solution.

        > [!NOTE]
        > Dans l’instance de votre premier projet, Projet1, est placé dans l’état inactif, puis vous devez retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK> du premier appel à votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implémentation.

    5.  Vous appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> et passer une valeur de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> pour le `rgfQueryEdit` paramètre.

    6.  Retourne l’environnement <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> et la mise à niveau peut continuer, car le fichier projet peut être écrites.

Si vous ne parvenez pas à mettre à niveau, retourner <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> de `IVsProjectUpgrade::UpgradeProject`. Si aucune mise à niveau n’est nécessaire ou si vous choisissez de ne pas faire la mise à niveau, gérez l’appel `IVsProjectUpgrade::UpgradeProject` comme une absence d’opération. Si vous retournez <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, un nœud d’espace réservé est ajouté à la solution pour votre projet.

## <a name="upgrading-project-items"></a>Mise à niveau d’éléments de projet

Si vous ajoutez ou gérez les éléments à l’intérieur des systèmes de projet que vous n’implémentez pas, vous devrez peut-être participer au processus de mise à niveau du projet. Crystal Reports est un exemple d’un élément qui peut être ajouté au système de projet.

En général, les implémenteurs d’élément de projet souhaitent tirer parti d’un projet déjà entièrement instancié et mis à niveau, car ils ont besoin de savoir quelles le projet sont des références et les autres propriétés de projet il à prendre une décision de mise à niveau.

### <a name="to-get-the-project-upgrade-notification"></a>Pour obtenir la notification de mise à niveau du projet

1.  Définir le <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> indicateur (défini dans vsshell80.idl) dans votre implémentation d’élément de projet. Cela provoque votre élément de projet VSPackage de charge automatique lors de l’interpréteur de commandes de Visual Studio détermine qu’un système de projet est en cours de la mise à niveau.

2.  Informez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> (méthode).

3.  Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface est déclenchée une fois l’implémentation de système de projet a terminé ses opérations de mise à niveau et le nouveau projet mis à niveau est créé. Selon le scénario, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface est déclenchée après le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, ou le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> méthodes.

### <a name="to-upgrade-the-project-item-files"></a>Pour mettre à niveau les fichiers d’élément de projet

1.  Vous devez gérer soigneusement le processus de sauvegarde de fichier dans votre implémentation d’élément de projet. Cela s’applique en particulier pour une sauvegarde côte à côte, où le `fUpgradeFlag` paramètre de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> méthode est définie sur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, où les fichiers qui avaient été sauvegardées sont placés le long de fichiers côté qui sont désignés comme « .old ». Les fichiers sauvegardés antérieures à l’heure système lorsque le projet a été mis à niveau peuvent être désignées comme obsolètes. En outre, ils peuvent être remplacés, sauf si vous prenez des mesures spécifiques pour éviter ce problème.

2.  Au moment où votre élément de projet reçoit une notification de la mise à niveau du projet, le **Assistant Conversion de Visual Studio** est toujours affichée. Par conséquent, vous devez utiliser les méthodes de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interface pour fournir des messages de mise à niveau à l’interface utilisateur de l’Assistant.

## <a name="see-also"></a>Voir aussi

- [Projets](../../extensibility/internals/projects.md)