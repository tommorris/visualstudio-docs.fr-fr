---
title: 'Erreur : ASP.NET ne pas installé | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: fd660ea2cdeaaae5d37811406221a7d150ab9bef
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056659"
---
# <a name="error-aspnet-not-installed"></a>Erreur : ASP.NET n'est pas installé
Cette erreur se produit quand [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n'est pas installé correctement sur l'ordinateur que vous tentez de déboguer. Cela peut signifier qu'[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n'a jamais été installé ou qu'[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a été installé avant les services IIS (Internet Information Services).  
  
### <a name="to-reinstall-aspnet"></a>Pour réinstaller ASP.NET  
  
1.  À partir d'une invite de commandes, exécutez la commande suivante :  
  
    ```cmd
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     où *version* représente le numéro de version du .NET Framework installée sur votre ordinateur, par exemple v1.0.370. Vous pouvez déterminer la version du framework en consultant le `\WINDOWS\Microsoft.NET\Framework` directory.  
  
    > [!NOTE]
    >  Avec Windows Server 2003, vous pouvez installer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] à l’aide de **Ajout / Suppression de programmes** dans le panneau de configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
