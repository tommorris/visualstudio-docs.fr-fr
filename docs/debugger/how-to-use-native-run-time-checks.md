---
title: 'Comment : utiliser des contrôles d’exécution natifs | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 6d47b39086f0363bd0bc610ec047213142fb7fec
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480600"
---
# <a name="how-to-use-native-run-time-checks"></a>Comment : utiliser les contrôles natifs à l'exécution
En Visual C++, vous pouvez utiliser des [runtime_checks](/cpp/preprocessor/runtime-checks) natifs pour dépister les erreurs d’exécution courantes, telles que :  
  
-   Un pointeur de pile détérioré.  
  
-   Des dépassements de tableaux locaux.  
  
-   Une pile détériorée.  
  
-   Des dépendances avec des variables locales non initialisées.  
  
-   Une perte de données par suite d'une assignation à une variable plus courte.  
  
 Si vous utilisez **/RTC** dans une version optimisée (**/O**), il en résulte une erreur du compilateur. Un pragma `runtime_checks` n'a aucun effet s'il est utilisé dans une version optimisée.  
  
 Si les contrôles à l'exécution sont activés dans le programme que vous déboguez, par défaut, le programme s'arrête et entre dans le débogueur en cas d'erreur. Vous pouvez modifier ce comportement par défaut pour tout contrôle d'exécution. Pour plus d’informations, consultez [la gestion des Exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Les procédures suivantes décrivent comment activer des contrôles d'exécution natifs dans une génération Debug et comment modifier le comportement du contrôle d'exécution natif.  
  
 Les autres rubriques de cette section fournissent des informations sur :  
  
-   [Personnalisation des contrôles d'exécution avec la bibliothèque Runtime C](../debugger/native-run-time-checks-customization.md)  
  
-   [Utilisation de contrôles d'exécution sans la bibliothèque Runtime C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Pour activer les contrôles natifs à l'exécution dans une version Debug  
  
-   Utilisez l'option **/RTC** et établissez une liaison avec la version Debug d'une bibliothèque Runtime C (/MDd, par exemple).  
  
### <a name="to-modify-native-run-time-check-behavior"></a>Pour modifier le comportement du contrôle natif à l'exécution  
  
-   Utilisez le pragma `runtime_checks` .  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage dans Visual Studio](../debugger/index.md)  
 [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)   
 [runtime_checks](/cpp/preprocessor/runtime-checks)   
 [Vérifications des erreurs au moment de l’exécution](/cpp/c-runtime-library/run-time-error-checking)