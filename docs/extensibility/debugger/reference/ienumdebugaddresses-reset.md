---
title: IEnumDebugAddresses::Reset | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugAddresses::Reset
helpviewer_keywords:
- IEnumDebugAddresses::Reset method
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a7cd9b20dc550db8f2543fe7e214885c0544333
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119430"
---
# <a name="ienumdebugaddressesreset"></a>IEnumDebugAddresses::Reset
Cette méthode réinitialise l’énumération au premier élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Une fois que cette méthode est appelée, l’appel suivant à [suivant](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) retourne le premier élément de l’énumération.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)   
 [Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)