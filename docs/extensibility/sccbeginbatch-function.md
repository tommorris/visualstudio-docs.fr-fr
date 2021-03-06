---
title: Fonction SccBeginBatch | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f9593496f36fba4a56334a206cf39e9a6ad96ad2
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639787"
---
# <a name="sccbeginbatch-function"></a>Fonction SccBeginBatch
Cette fonction démarre une séquence de traitement par lots des opérations de contrôle de code source. Le [SccEndBatch](../extensibility/sccendbatch-function.md) sera appelé pour terminer le lot. Ces lots ne peuvent pas être imbriqués.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccBeginBatch(void);  
```  
  
### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Lot d’opérations a démarré avec succès.|  
|SCC_E_UNKNOWNERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 Lots de contrôle source sont utilisés pour exécuter les mêmes opérations sur plusieurs projets ou de plusieurs contextes. Lots peuvent être utilisés pour éliminer les boîtes de dialogue de projet redondante à partir de l’expérience utilisateur lors d’une opération par lot. Le `SccBeginBatch` (fonction) et le [SccEndBatch](../extensibility/sccendbatch-function.md) sont utilisés comme une paire de fonction pour indiquer le début et la fin d’une opération. Ils ne peuvent pas être imbriquées. `SccBeginBatch` définit un indicateur qui indique qu’une opération par lot est en cours.  
  
 Pendant une opération par lot est en vigueur, le plug-in de contrôle de code source doit présenter au maximum une boîte de dialogue pour toute question à l’utilisateur et s’appliquent de la réponse à partir de cette boîte de dialogue sur toutes les opérations suivantes.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API source contrôle plug-in](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)