---
title: Partager le rappel de journal Unity avec VSTU | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 3bf25ed2764078f2d3e0424ab34f4e4a8e470ff5
ms.sourcegitcommit: e6ef03cc415ca67f75fd1f26e0e7b8846857166d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39310018"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Partager le rappel de journal Unity avec VSTU
Visual Studio Tools pour Unity enregistre un rappel de journal avec Unity pour pouvoir diffuser sa console vers Visual Studio. Si vos scripts de l'éditeur enregistrent également un rappel de journal avec Unity, le rappel VSTU peut interférer avec votre rappel.  Pour éviter ce risque, utilisez l'événement `VisualStudioIntegration.LogCallback` pour coopérer avec VSTU.

## <a name="demonstrates"></a>Démonstrations
 Comment partager le rappel de journal Unity créé par Visual Studio Tools pour Unity.

## <a name="example"></a>Exemple

```csharp
#if ENABLE_VSTU
using System;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class LogCallbackHook
{
    static LogCallbackHook()
    {
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>
        {
            // place code that implements your log callback here
        };
    }
}
#endif
```

## <a name="see-also"></a>Voir aussi
 [Exemple : génération de fichier projet](../cross-platform/customize-project-files-created-by-vstu.md)
