---
title: assemblys PIA (Primary Interop Assembly) Office
ms.custom: ''
ms.date: 09/20/2018
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies
- assemblies [Office development in Visual Studio], primary interop assemblies
- Office primary interop assemblies
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c309dcfd78ae0181905f691e1c36f407e763fc93
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542479"
---
# <a name="office-primary-interop-assemblies"></a>assemblys PIA (Primary Interop Assembly) Office

Pour utiliser les fonctionnalités d'une application Microsoft Office dans un projet Office, vous devez utiliser l'assembly PIA (Primary Interop Assembly) de l'application. L'assembly PIA permet au code managé d'interagir avec le modèle d'objet COM d'une application Microsoft Office.  
  
Quand vous créez un projet Office, Visual Studio ajoute des références aux assemblys PIA requis pour générer le projet. Dans certains scénarios, vous devrez peut-être ajouter des références à des assemblys PIA supplémentaires (par exemple, si vous voulez utiliser une fonctionnalité de Microsoft Office Word dans un projet pour Microsoft Office Excel).  
  
Cette rubrique décrit les aspects suivants de l'utilisation des assemblys PIA Microsoft Office dans des projets Office :  
  
- [Séparer les assemblys PIA pour la génération et exécution de projets](#separateassemblies)  
  
- [Utiliser les fonctionnalités de plusieurs applications Microsoft Office dans un projet unique](#usingfeatures)  
  
- [Liste complète des assemblys PIA pour les applications Microsoft Office](#pialist)  
  
Pour plus d’informations sur les assemblys PIA, consultez [assemblys PIA](http://msdn.microsoft.com/b977a8be-59a0-40a0-a806-b11ffba5c080).  

<a name="separateassemblies"></a> 

## <a name="separate-primary-interop-assemblies-to-build-and-run-projects"></a>Séparer les assemblys PIA pour la génération et exécution de projets  

Visual Studio utilise différents ensembles d'assemblys PIA sur l'ordinateur de développement. Ces différents ensembles d'assemblys se trouvent aux emplacements suivants :  
  
- Un dossier dans le répertoire program files  
  
  Ces copies des assemblys sont utilisées quand vous écrivez du code et que vous générez des projets. Visual Studio installe ces assemblys automatiquement.  
  
- Le global assembly cache  
  
  Ces copies des assemblys sont utilisées pendant certaines tâches de développement, par exemple quand vous exécutez ou déboguez des projets. Visual Studio n'installe ni n'enregistre ces assemblys. Vous devez le faire vous-même.  
  
### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Assemblys PIA dans le répertoire program files  

Quand vous installez Visual Studio, les assemblys PIA sont automatiquement installés dans le système de fichiers, en dehors du Global Assembly Cache. Quand vous créez un projet, Visual Studio ajoute automatiquement à votre projet des références à ces copies des assemblys PIA. Visual Studio utilise ces copies des assemblys PIA, au lieu des assemblys du Global Assembly Cache, pour résoudre des références de type quand vous développez et générez votre projet.  
  
Ces copies des assemblys PIA aident Visual Studio à éviter plusieurs problèmes de développement pouvant se produire quand différentes versions d'assemblys PIA sont enregistrées dans le Global Assembly Cache.  
  
Visual Studio installe ces copies des assemblys PIA aux emplacements suivants sur l'ordinateur de développement :  
  
- *%ProgramFiles%\Microsoft visual Studio 12. 0\Visual Studio Tools for Office\PIA\Office14*  
  
  (ou *% ProgramFiles (x86) %\Microsoft Visual Studio 12. 0\Visual Studio Tools for Office\PIA\Office14* sur les systèmes d’exploitation 64 bits)  
  
- *%ProgramFiles%\Microsoft visual Studio 12. 0\Visual Studio Tools for Office\PIA\Office15*  
  
  (ou *% ProgramFiles (x86) %\Microsoft Visual Studio 12. 0\Visual Studio Tools for Office\PIA\Office15* sur les systèmes d’exploitation 64 bits)  
  
### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Assemblys PIA dans le global assembly cache  

Pour effectuer certaines tâches de développement, les assemblys PIA doivent être installés et enregistrés dans le Global Assembly Cache sur l'ordinateur de développement. En général, les assemblys PIA sont installés automatiquement quand vous installez Office sur l'ordinateur de développement. Pour plus d’informations, consultez [configurer un ordinateur pour développer des solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
Les assemblys PIA Office ne sont pas obligatoires sur les ordinateurs des utilisateurs finaux pour exécuter les solutions Office. Pour plus d’informations, consultez [conception et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md).  

<a name="usingfeatures"></a>

## <a name="use-features-of-multiple-microsoft-office-applications-in-a-single-project"></a>Utiliser les fonctionnalités de plusieurs applications Microsoft Office dans un projet unique  

Tous les modèles de projet Office dans Visual Studio sont conçus pour fonctionner avec une seule application Microsoft Office. Pour utiliser des fonctionnalités dans plusieurs applications Microsoft Office ou dans une application ou composant qui ne dispose pas d'un projet dans Visual Studio, vous devez ajouter une référence aux assemblys PIA requis.  
  
Dans la plupart des cas, vous devez ajouter des références aux assemblys PIA sont installés par Visual Studio sous le `%ProgramFiles%\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\` directory. Ces versions des assemblys apparaissent sous la **Framework** onglet de la **Gestionnaire de références** boîte de dialogue. Pour plus d’informations, consultez [Comment : applications Office de cible via les assemblys PIA](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
Si vous avez installé et enregistré les assemblys PIA dans le Global Assembly Cache, ces versions des assemblys apparaissent sous l'onglet **COM** de la boîte de dialogue **Gestionnaire de références** . Vous devez éviter d'ajouter des références à ces versions d'assemblys, car des erreurs de développement peuvent se produire quand vous les utilisez. Par exemple, si vous avez enregistré différentes versions des assemblys PIA dans le Global Assembly Cache, votre projet crée automatiquement une liaison à la dernière version enregistrée de l'assembly, même si vous spécifiez une autre version de l'assembly sous l'onglet **COM** de la boîte de dialogue **Gestionnaire de références** .  
  
> [!NOTE]  
>  Certains assemblys sont ajoutés manuellement à un projet quand un assembly qui leur fait référence est ajouté. Par exemple, fait référence à la *Office.dll* et *Microsoft.Vbe.Interop.dll* assemblys sont ajoutés automatiquement lorsque vous ajoutez une référence au Word, Excel, Outlook, Microsoft Forms ou graphique assemblys.  

<a name="pialist"></a> 

## <a name="primary-interop-assemblies-for-microsoft-office-applications"></a>Assemblys PIA pour les applications Microsoft Office  

La table suivante indique les assemblys PIA disponibles pour [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] et [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  

<br/>

|Application ou composant Office|Nom de l'assembly PIA|  
|-------------------------------------|-----------------------------------|  
|Bibliothèque d'objets Microsoft Access 14.0<br /><br /> Bibliothèque d'objets Microsoft Access 15.0|Microsoft.Office.Interop.Access.dll|  
|Bibliothèque d'objets du moteur de base de données Microsoft Office Access 14.0<br /><br /> Bibliothèque d'objets du moteur de base de données Microsoft Office Access 15.0|Microsoft.Office.Interop.Access.Dao.dll|  
|Bibliothèque d'objets Microsoft Excel 14.0<br /><br /> Bibliothèque d'objets Microsoft Excel 15.0|[Microsoft.Office.Interop.Excel.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.excel?view=excel-pia)|  
|Bibliothèque d'objets Microsoft Graph 14.0 (utilisée par PowerPoint, Access et Word pour les graphiques)<br /><br /> Bibliothèque d'objets Microsoft Graph 15.0|Microsoft.Office.Interop.Graph.dll|  
|Bibliothèque de types Microsoft InfoPath 2.0 (uniquement pour InfoPath 2007)|[Microsoft.Office.Interop.InfoPath.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.infopath?view=infopath-form)|  
|Assembly d'interopérabilité XML Microsoft InfoPath (uniquement pour InfoPath 2007)|Microsoft.Office.Interop.InfoPath.Xml.dll|  
|Bibliothèque d'objets Microsoft Office 14.0 (composant partagé Office)<br /><br /> Bibliothèque d'objets Microsoft Office 15.0 (composant partagé Office)|office.dll|  
|Contrôle view Microsoft Office Outlook (peut être utilisé dans les pages web et applications pour accéder à votre Boîte de réception)|Microsoft.Office.Interop.OutlookViewCtl.dll|  
|Bibliothèque d'objets Microsoft Outlook 14.0<br /><br /> Bibliothèque d'objets Microsoft Outlook 15.0|[Microsoft.Office.Interop.Outlook.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.outlook?view=outlook-pia)|  
|Bibliothèque d'objets Microsoft PowerPoint 14.0<br /><br /> Bibliothèque d'objets Microsoft PowerPoint 15.0|Microsoft.Office.Interop.PowerPoint.dll|  
|Bibliothèque d'objets Microsoft Project 14.0<br /><br /> Bibliothèque d'objets Microsoft Project 15.0|[Microsoft.Office.Interop.MSProject.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.msproject?view=office-project-server)|  
|Bibliothèque d'objets Microsoft Publisher 14.0<br /><br /> Bibliothèque d'objets Microsoft Publisher 15.0|Microsoft.Office.Interop.Publisher.dll|  
|Bibliothèque de références d'objet web Microsoft SharePoint Designer 14.0|Microsoft.Office.Interop.SharePointDesigner.dll|  
|Bibliothèque de références d'objet Page Microsoft SharePoint Designer 14.0|Microsoft.Office.Interop.SharePointDesignerPage.dll|  
|Bibliothèque de types Microsoft Smart Tags 2.0 **Remarque :** balises actives sont déconseillées dans [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] et [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Microsoft.Office.Interop.SmartTag.dll|  
|Bibliothèque de types Microsoft Visio 14.0<br /><br /> Bibliothèque de types Microsoft Visio 15.0|Microsoft.Office.Interop.Visio.dll|  
|Bibliothèque de types Enregistrer en tant que page web Microsoft Visio 14.0<br /><br /> Bibliothèque de types Enregistrer en tant que page web Microsoft Visio 15.0|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|  
|Bibliothèque de types de contrôles de dessin Microsoft Visio 14.0<br /><br /> Bibliothèque de types de contrôles de dessin Microsoft Visio 15.0|Microsoft.Office.Interop.VisOcx.dll|  
|Bibliothèque d'objets Microsoft Word 14.0<br /><br /> Bibliothèque d'objets Microsoft Word 15.0|[Microsoft.Office.Interop.Word.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.word?view=word-pia)|  
|Microsoft Visual Basic for Applications Extensibility 5.3|Microsoft.Vbe.Interop.dll|  
  
### <a name="binding-redirect-assemblies"></a>Assemblys avec redirection de liaison  

Quand vous installez et enregistrez les assemblys PIA Office dans le Global Assembly Cache (avec Office ou en installant le package redistribuable pour les assemblys PIA), les assemblys avec redirection de liaison sont également installés uniquement dans le Global Assembly Cache. Ces assemblys contribuez à garantir que la version correcte des assemblys PIA est chargée pendant l’exécution. 

Par exemple, quand une solution faisant référence à un assembly [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] s'exécute sur un ordinateur disposant de la version [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] du même assembly PIA, l'assembly avec redirection de liaison indique au runtime [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] de charger la version [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] de l'assembly PIA. 

Pour plus d’informations, consultez [Comment : activer et désactiver la redirection de liaison automatique](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection).  
  
## <a name="see-also"></a>Voir aussi  

- [Comment : applications Office de cible via les assemblys PIA](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
- [Vue d’ensemble du modèle d’objet Excel](../vsto/excel-object-model-overview.md)   
- [Solutions InfoPath](../vsto/infopath-solutions.md)   
- [Vue d’ensemble du modèle d’objet Outlook](../vsto/outlook-object-model-overview.md)   
- [Solutions PowerPoint](../vsto/powerpoint-solutions.md)   
- [Solutions Project](../vsto/project-solutions.md)   
- [Présentation du modèle objet de Visio](../vsto/visio-object-model-overview.md)   
- [Vue d’ensemble du modèle d’objet Word](../vsto/word-object-model-overview.md)   
- [Référence générale &#40;développement Office dans Visual Studio&#41;](../vsto/general-reference-office-development-in-visual-studio.md)  
  
  
