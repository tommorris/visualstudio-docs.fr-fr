---
title: ProjectCollection, élément (modèles Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c91c470a9478c7015972be66afe5f41174073047
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636998"
---
# <a name="projectcollection-element-visual-studio-templates"></a>ProjectCollection, élément (modèles Visual Studio)
Spécifie l'organisation et le contenu de modèles à plusieurs projets.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<ProjectCollection >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ProjectCollection>  
    <ProjectTemplateLink> ... </ProjectTemplateLink>  
    <SolutionFolder> ... </SolutionFolder>  
</ProjectCollection>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie un projet dans un modèle à plusieurs projets.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Groupe des projets dans des modèles à plusieurs projets.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie le contenu du modèle.|  
  
## <a name="remarks"></a>Notes  
 Les modèles à plusieurs projets jouent le rôle de conteneurs pour au moins deux projets. Le `ProjectCollection` élément est utilisé pour spécifier les projets devant être contenue dans le modèle. Pour plus d’informations sur les modèles à plusieurs projets, consultez [Comment : créer des modèles à plusieurs projets](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple montre une racine de plusieurs projets simple *.vstemplate* fichier. Dans cet exemple, le modèle contient deux projets, `My Windows Application` et `My Class Library`. L'attribut `ProjectName` de l'élément `ProjectTemplateLink` définit le nom à assigner au projet dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Si le `ProjectName` attribut n’existe pas, le nom de la *.vstemplate* fichier est utilisé comme nom de projet.  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [Comment : créer des modèles à plusieurs projets](../ide/how-to-create-multi-project-templates.md)