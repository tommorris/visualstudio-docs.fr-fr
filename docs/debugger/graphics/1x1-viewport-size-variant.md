---
title: Variante de taille Viewport 1 x 1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 168b358bf58dcb2c91814f5460b203873255e275
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433244"
---
# <a name="1x1-viewport-size-variant"></a>Variante de taille Viewport 1x1
Réduit les dimensions de la fenêtre d'affichage sur toutes les cibles de rendu à 1x1 pixels.  
  
## <a name="interpretation"></a>Interprétation  
 Une fenêtre d’affichage plus petits réduit le nombre de pixels à ombrer. Mais, une fenêtre d’affichage plus petits ne réduit pas le nombre de vertex dont il faudra processus. Le fait de définir les dimensions de la fenêtre d'affichage à 1x1 pixels a pour effet d'éliminer en quelque sorte l'ombrage de pixels de votre application.  
  
 Si cette variante donne lieu à un gain de performances, cela peut indiquer que votre application consomme trop de ressources taux de remplissage. En outre, la résolution peut être trop élevée pour la plateforme cible ou votre application a pu consacrer beaucoup de temps à ombrer des pixels qui sont ensuite remplacés, également appelé *superposition*. Un tampon de trame plus petits ou en réduisant la quantité de superpositions améliorera les performances de votre application.  
  
## <a name="remarks"></a>Notes  
 Les dimensions de la fenêtre d'affichage sont réinitialisées à 1x1 pixels après chaque appel à `ID3D11DeviceContext::OMSetRenderTargets` ou `ID3D11DeviceContext::RSSetViewports`.  
  
## <a name="example"></a>Exemple  
 Cette variante peut être reproduite avec le code suivant :  
  
```cpp
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```
