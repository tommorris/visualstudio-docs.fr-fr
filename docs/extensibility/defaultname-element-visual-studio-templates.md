---
title: DefaultName, élément (modèles Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03513b786c17e5bef3d8fa1fff79c1c3e73fe6a0
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500317"
---
# <a name="defaultname-element-visual-studio-templates"></a>DefaultName, élément (modèles Visual Studio)
Spécifie le nom que le système de projet Visual Studio génère pour le projet ou l’élément lors de sa création.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<DefaultName >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<DefaultName>  
    Default Project Name  
</DefaultName>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est requise.  
  
 Ce texte spécifie le nom par défaut du projet ou de l’élément.  
  
## <a name="remarks"></a>Notes  
 `DefaultName` est un élément facultatif.  
  
 Pour les projets, cet élément spécifie le nom du répertoire qui stocke le projet sur le disque. Pour les éléments, il spécifie le nom de fichier du fichier source.  
  
 Lorsque vous créez un projet ou un élément, vous pouvez modifier le nom par défaut à l’aide la **nom** option, qui est disponible à partir du **nouveau projet** boîte de dialogue ou **ajouter un nouvel élément** boîte de dialogue.  
  
 Si vous ne souhaitez pas le système de projet pour générer le nom par défaut pour le projet ou l’élément, puis définissez le [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) élément à `False`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre les métadonnées pour le modèle d’élément standard pour une [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] classe.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d’éléments](../ide/creating-project-and-item-templates.md)