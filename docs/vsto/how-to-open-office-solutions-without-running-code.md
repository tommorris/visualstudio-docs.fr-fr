---
title: 'Comment : solutions Open Office sans exécuter le code'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f7ced7b38a4f32d96b397e7f9eebb1d40be03ae3
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254986"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Comment : solutions Open Office sans exécuter le code
  Une solution Microsoft Office créée avec des extensions de code managé s’exécute même si le paramètre de sécurité dans l’application Office de l’utilisateur final est défini sur élevé. Il s’agit, car la sécurité du code assembly .NET est gérée par Microsoft .NET Framework, et non par Microsoft Office.  
  
 Toutefois, voici les heures lorsque vous souhaiterez ouvrir un document sans exécuter le code. Par exemple, le contenu susceptible de modifier le code qui s’exécute lorsque le document s’ouvre, mais que vous souhaitez mettre à jour de l’apparence du document avant les modifications de code il. Ou vous souhaiterez peut-être envoyer le document avec certaines informations qu’il contient, à une personne, et vous ne souhaitez pas que le code pour exécuter et éventuellement modifier le contenu.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Il existe plusieurs manières d’ouvrir un document ou classeur qui contient des extensions de code managé sans exécuter le code d’assembly.  
  
## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Pour ignorer l’assembly à l’aide de la touche MAJ enfoncée  
  
-   Ouvrir des documents et classeurs à partir de la **fichier** menu tout en maintenant enfoncée la **MAJ** clé afin d’éviter de Word et Excel de déclencher des événements d’initialisation pendant que le document s’ouvre.  
  
    > [!NOTE]  
    >  Si vous ouvrez un document ou classeur à partir de la **mise en route** volet des tâches, enfoncée **MAJ** n’ignore pas le code. En outre, maintenez la touche MAJ n’empêche pas d’événements de se déclencher après que le document est ouvert.  
  
     Cette méthode est utile si vous souhaitez ouvrir un document pour apporter des modifications sans le code en cours d’exécution et modification d’abord le document.  
  
## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Pour ignorer un assembly en renommant ou en supprimant  
  
-   Si vous avez les autorisations nécessaires sur l’ordinateur où se trouve l’assembly, vous pouvez renommer ou supprimer l’assembly afin que le document ou le classeur ne peut pas le trouver. Cela entraîne une erreur qui est déclenchée chaque fois que le document Office est ouvert.  
  
     Si la solution est utilisée par plusieurs personnes, cette méthode empêche la solution en cours d’exécution pour l’ensemble d'entre eux. Cela peut être utile si un problème se trouve dans le code ou un serveur référencé et que vous souhaitez arrêter tous les utilisateurs de l’exécuter.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)   
 [Déployer une solution Office](../vsto/deploying-an-office-solution.md)   
 [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifestes d’application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  