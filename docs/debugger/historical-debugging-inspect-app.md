---
title: Inspecter votre application avec le débogage d’historique | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2309a3213344607fa0f5b2f626fc67af2eff8f79
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542336"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio"></a>Inspecter votre application avec débogage dans Visual Studio historique d’IntelliTrace
Vous pouvez utiliser [le débogage d’historique](../debugger/historical-debugging.md) à déplacer vers le haut et les transférer via l’exécution de votre application et inspecter son état.  
  
Vous pouvez utiliser IntelliTrace dans Visual Studio Enterprise edition, mais pas les éditions Professional ou Community.  
  
## <a name="navigate-your-code-with-historical-debugging"></a>Parcourir votre code avec le débogage d’historique  
 Commençons par un programme simple qui comporte un bogue. Dans une application de console C#, ajoutez le code suivant :  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 Nous supposerons que la valeur attendue de `resultInt` après avoir appelé `AddAll()` est 20 (le résultat de l’incrémentation `testInt` 20 fois). (Nous supposons également que vous ne voyez pas le bogue dans `AddInt()`). Mais le résultat est bien 44. Comment trouver le bogue sans parcourir 10 fois `AddAll()` ? Nous pouvons utiliser le débogage d’historique pour rechercher le bogue plus rapidement et plus facilement. Voici comment :  
  
1.  Dans **Outils > Options > IntelliTrace > Général**, vérifiez qu’IntelliTrace est activé, puis sélectionnez **événements IntelliTrace et informations d’appels**. Si vous ne sélectionnez pas cette option, vous ne verrez pas la marge de navigation (comme expliqué ci-dessous).  
  
2.  Définissez un point d'arrêt sur la ligne `Console.WriteLine(resultInt);`.  
  
3.  Démarrez le débogage. Le code s'exécute jusqu'au point d'arrêt. Dans le **variables locales** fenêtre, vous pouvez voir que la valeur de `resultInt` est 44.  
  
4.  Ouvrez le **outils de Diagnostic** fenêtre (**Déboguer > Afficher les outils de Diagnostic**). La fenêtre de code doit ressembler à ce qui suit :  
  
     ![Fenêtre de code sur le point d’arrêt](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  Vous devez voir une double flèche en regard de la marge de gauche, juste au-dessus du point d'arrêt. Cette zone est appelée la marge de navigation et est utilisée pour le débogage d’historique. Cliquez sur la flèche.  
  
     Dans la fenêtre de code, vous devez voir que la ligne de code précédente (`int resultInt = AddIterative(testInt);`) est de couleur rose. Au-dessus de la fenêtre, vous devez voir un message qui vous êtes maintenant dans le débogage d’historique.  
  
     La fenêtre de code doit maintenant ressembler à ceci :  
  
     ![fenêtre de code en mode débogage d’historique](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  Maintenant que vous pouvez entrer dans le `AddAll()` (méthode) (**F11**, ou le **pas à pas détaillé** bouton dans la marge de navigation. Avancez (**F10**, ou **accédez à l’appel suivant** dans la marge de navigation. Le trait rose est désormais sur la ligne `j = AddInt(j);`. **F10** dans ce cas ne pas d’accéder à la ligne de code suivante. En fait, vous accédez à l'appel de fonction suivant. Le débogage d'historique permet de naviguer d'un appel à l'autre. Il ignore les lignes de code qui n'incluent pas d'appel de fonction.  
  
7.  Maintenant, effectuez un pas à pas détaillé de la méthode `AddInt()`. Vous devez voir immédiatement le bogue dans ce code.  

## <a name="next-steps"></a>Étapes suivantes

Cette procédure ne présente que succinctement ce que vous pouvez faire avec le débogage d’historique.

- Pour afficher les instantanés pendant le débogage, consultez [Inspecter les États d’application précédent à l’aide d’IntelliTrace](../debugger/view-historical-application-state.md).
- Pour en savoir plus sur les différents paramètres et les effets des différents boutons dans la marge de navigation, consultez [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md).