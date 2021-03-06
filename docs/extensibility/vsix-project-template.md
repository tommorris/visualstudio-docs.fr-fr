---
title: Modèle de projet VSIX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2309428ffa87409bd35f1a05c2cfd591db3cc1a
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586285"
---
# <a name="vsix-project-template"></a>Modèle de projet VSIX
Vous pouvez utiliser le modèle de projet VSIX pour encapsuler une ou plusieurs extensions de Visual Studio dans un projet VSIX et puis publier le package sur le [galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site Web.  
  
 Déploiement VSIX prend en charge les VSPackages, assemblys, MEF composants, modèles de projet, modèles d’élément, les contrôles de boîte à outils et types d’extension personnalisée.  
  
> [!NOTE]
>  Pour utiliser des projets VSIX, vous devez installer le SDK Visual Studio. Pour plus d’informations sur le SDK Visual Studio, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>Où trouver le modèle de projet VSIX  
 Le modèle de projet VSIX est disponible dans le **nouveau projet** boîte de dialogue. Développez le le **Visual Basic** nœud ou le **Visual C#** nœud, puis choisissez **extensibilité**.  
  
> [!TIP]
>  Vous devez vous assurer que .NET Framework 4.5 ou version ultérieure est spécifié dans la zone de liste déroulante en haut de la **nouveau projet** boîte de dialogue.  
  
## <a name="uses-of-the-vsix-project-template"></a>Utilisations du modèle de projet VSIX  
 Le modèle de projet VSIX a deux utilisations principales :  
  
-   Pour déployer des modèles de projet, de modèles d’élément et d’autres extensions qui n’ont pas déjà la prise en charge de l’extension VSIX.  
  
-   Pour inclure les sorties de plusieurs extensions dans le package de déploiement.  
  
 Il est inutile d’utiliser le modèle de projet VSIX pour déployer des VSPackages ou autres types d’extensions n’ayant encore VSIX prennent en charge.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Empaquetage d’une extension dans un projet VSIX vide  
 Vous pouvez empaqueter une extension existante ou une extension qui ne dispose pas déjà VSIX prennent en charge, en l’encapsulant dans un projet VSIX vide. L’extension à encapsuler doit être d’un type qui est pris en charge par le [schéma VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Pour un package d’extension à l’aide d’un projet VSIX  
  
1.  Générer les projets qui composent votre extension.  
  
2.  Créez un projet VSIX à l’aide de la **projet VSIX** modèle.  
  
     *Source.extension.vsixmanifest* s’ouvre dans **Concepteur de manifeste**.  
  
3.  Sur le **actifs** , choisir le **New** bouton.  
  
     Le **ajouter un nouveau composant** boîte de dialogue s’affiche.  
  
4.  Dans le **Type** liste, choisissez le type d’extension à ajouter.  
  
5.  Pour ajouter un élément d’extension ou le contenu qui est inclus dans la solution actuelle (par exemple, un modèle d’élément ou un assembly compilé), procédez comme suit :  
  
    1.  Dans le **Source** , choisissez **un projet dans la solution actuelle**.  
  
    2.  Dans le **projet** , sélectionnez le nom de l’extension.  
  
    3.  Dans le **incorporé dans ce dossier** , entrez le nom d’un dossier dans lequel incorporer la ressource, puis choisissez le **OK** bouton.  
  
6.  Pour ajouter une extension ou un élément de contenu qui n’est pas inclus dans la solution actuelle, procédez comme suit :  
  
    1.  Dans le **Source** zone de liste, choisissez **fichier sur le système de fichiers**.  
  
    2.  Dans le **chemin d’accès** champ, entrez le chemin d’accès complet au fichier d’extension compilées ou compressé ou utilisez le **Parcourir** bouton pour accéder au fichier.  
  
    3.  Dans le **incorporé dans ce dossier** , entrez le nom d’un dossier dans lequel incorporer la ressource, puis choisissez le **OK** bouton.  
  
7.  Si vous souhaitez que votre package pour inclure des extensions supplémentaires, ajoutez-les de la même manière.  
  
8.  Générez la solution.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère un *.vsix* fichier qui contient un fichier de manifeste VSIX, un fichier [Content_Types]*.xml* fichier et toutes les ressources de l’extension que vous avez ajouté au projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de schéma 2.0 d’extension VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Rechercher et utiliser des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)