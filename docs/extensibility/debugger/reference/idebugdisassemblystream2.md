---
title: IDebugDisassemblyStream2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c1598ec8a6e5fca5275384c00433d74d22ce3505
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107892"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Cette interface représente un flux d’instructions.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un moteur de débogage implémente cette interface pour prendre en charge le désassemblage du code d’un programme.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Un appel à la [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) méthode retourne cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugDisassemblyStream2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[En lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Lit les instructions à partir de la position actuelle dans le flux de code machine.|  
|[Rechercher](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Déplace le pointeur de la lecture dans le flux de code machine un nombre donné d’instructions par rapport à une position spécifiée.|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Retourne un identificateur d’emplacement de code pour un contexte de code particulier.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Retourne un objet de contexte de code correspondant à un identificateur d’emplacement de code spécifié.|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Retourne un identificateur d’emplacement de code qui représente l’emplacement du code en cours.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Obtient le document source associé à ce flux de code machine.|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Obtient la portée de ce flux de code machine.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Obtient la taille de ce flux de code machine.|  
  
## <a name="remarks"></a>Notes  
 Le flux de code machine peut être créé pour représenter l’espace d’adressage entière ou simplement une fonction ou un module au sein de l’espace. Chaque instruction est représentée par un [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) structure retournée par un appel à la [en lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)