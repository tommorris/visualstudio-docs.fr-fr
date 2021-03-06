---
title: Création de contrôles réutilisables pour les composants WebPart ou les Pages d’Application | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a621bb8c0f14cfb2c1869b98bb8bdbdd9c2d30bb
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327269"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application
  Dans Visual Studio, vous pouvez créer des contrôles personnalisés et réutilisables qui peuvent être utilisés par les pages d’application et les composants WebPart qui s’exécutent dans SharePoint. Ces contrôles sont appelés contrôles utilisateur. Un contrôle utilisateur est un type de contrôle composite qui fonctionne comme une page Web ASP.NET, vous pouvez ajouter des contrôles serveur Web existants et le balisage pour un contrôle utilisateur et définir les propriétés et méthodes pour le contrôle. Vous pouvez ensuite les incorporer dans des pages Web ASP.NET, où ils agissent comme une unité.  
  
## <a name="create-a-user-control"></a>Créer un contrôle utilisateur
 Pour créer un contrôle utilisateur, ajoutez un **contrôle utilisateur** à un **projet SharePoint vide**. Pour plus d’informations, consultez [Comment : créer un contrôle utilisateur pour une application SharePoint partie web ou de page](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).  
  
 Lorsque vous ajoutez un **contrôle utilisateur** élément, Visual Studio crée un dossier dans votre projet, puis ajoute plusieurs fichiers au dossier. Le tableau suivant décrit chaque fichier.  
  
|Fichier|Description|  
|----------|-----------------|  
|Fichier de contrôle utilisateur|Définit le contrôle utilisateur. Concevoir le contrôle utilisateur en ajoutant des contrôles et le balisage à ce fichier.|  
|Fichier de code|Contient le code-behind du contrôle utilisateur. Ajoutez du code pour gérer les événements pour ce fichier.|  
|Fichier de code du Concepteur|Contient le code généré par le concepteur et ne doit pas être modifié directement.|  
  
## <a name="design-the-user-control"></a>Concevoir le contrôle utilisateur
 Concevoir le contrôle utilisateur à l’aide du concepteur Visual Web Developer dans Visual Studio. Ce concepteur s’affiche lorsque vous ouvrez le fichier de contrôle utilisateur dans votre projet et choisissez le **conception** onglet.  

## <a name="consume-the-user-control"></a>Utiliser le contrôle utilisateur
 Contrôles utilisateur n’apparaissent pas dans SharePoint, jusqu'à ce que vous les incluez dans une page d’application ou un composant WebPart.  
  
 Pour inclure un contrôle utilisateur dans une page d’application, ouvrez la page Web à laquelle vous souhaitez ajouter le contrôle utilisateur ASP.NET. Basculez en mode Design, puis sélectionnez votre fichier de contrôle utilisateur personnalisé dans l’Explorateur de solutions et faites-le glisser sur la page. Le contrôle utilisateur ASP.NET est ajouté à la page, et le concepteur crée la directive @ Register, qui est requise pour la page de reconnaître le contrôle utilisateur. Vous pouvez désormais travailler avec des propriétés publiques et les méthodes du contrôle.  
  
 Pour inclure un contrôle utilisateur dans un composant WebPart, ajoutez le contrôle utilisateur au composant WebPart <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> collection dans le fichier de code du composant WebPart. L’exemple suivant ajoute un contrôle utilisateur pour le <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> collection d’un composant WebPart.  
  
 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]  
  
## <a name="debug-a-user-control"></a>Déboguer un contrôle utilisateur
 Pour déboguer un contrôle utilisateur, assurez-vous que le contrôle utilisateur est inclus dans une page d’application ou un composant WebPart dans votre projet SharePoint. Vous pouvez ensuite déboguer le code dans le contrôle utilisateur simplement comme pour tout code dans n’importe quel projet Visual Studio.  
  
 Lorsque vous démarrez le débogueur Visual Studio, Visual Studio ouvre le site SharePoint.  
  
 Dans SharePoint, ouvrez la page d’application qui inclut le contrôle utilisateur. Si le contrôle utilisateur est inclus dans un composant WebPart, ajoutez le composant WebPart à une page WebPart dans SharePoint.  
  
 Pour plus d’informations sur le débogage des projets SharePoint, consultez [solutions SharePoint de résoudre les problèmes](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="related-topics"></a>Rubriques connexes
  
|Titre|Description|  
|-----------|-----------------|  
|[Comment : créer un contrôle utilisateur pour une application SharePoint partie web ou de page](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Vous montre comment créer des contrôles personnalisés et réutilisables qui peuvent être utilisés par les pages d’application et les composants WebPart qui s’exécutent dans SharePoint.|  
  
