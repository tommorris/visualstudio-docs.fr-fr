---
title: IDebugEventCallback2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 68d29d928f310cb045ed712a151f9275446465a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116202"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Cette interface est utilisée par le moteur de débogage (DE) pour envoyer des événements de débogage pour le Gestionnaire de session de débogage (SDM).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implémente cette interface pour recevoir les événements à partir d’un moteur de débogage.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Un moteur de débogage reçoit généralement cette interface lorsque le SDM appelle [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), ou [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Un moteur de débogage envoie les événements dans le SDM en appelant [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugEventCallback2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Envoie une notification de débogage des événements pour le SDM.|  
  
## <a name="remarks"></a>Notes  
 Bien que [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) et [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) spécifier qu’ils prennent une `IDebugEventCallback2` interface, cela n’est pas le cas, et le pointeur d’interface sera toujours une valeur null. Au lieu de cela, le moteur de débogage doit utiliser le `IDebugEventCallback2` interface reçu dans l’appel à [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), ou [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Si un package implémente [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) en code managé, il est fortement recommandé que <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> appelée sur les diverses interfaces qui sont passées à [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Joindre](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)