---
title: 'CA2135 : Les assemblys de niveau 2 ne doivent pas contenir de LinkDemands'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d41310ba5c6e52add891a4a8d034c774f9f74d2
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549600"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135 : Les assemblys de niveau 2 ne doivent pas contenir de LinkDemands
|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 À l’aide d’une classe ou un membre de classe un <xref:System.Security.Permissions.SecurityAction> dans une application qui utilise la sécurité de niveau 2.

## <a name="rule-description"></a>Description de la règle
 L’utilisation de LinkDemands est déconseillée dans l’ensemble de règles de sécurité de niveau 2. Au lieu d’utiliser LinkDemands pour implémenter la sécurité au moment de la compilation juste-à-temps (JIT), marquez les méthodes, types, champs et avec le <xref:System.Security.SecurityCriticalAttribute> attribut.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez le <xref:System.Security.Permissions.SecurityAction> et marquez le type ou le membre avec le <xref:System.Security.SecurityCriticalAttribute> attribut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 Dans l’exemple suivant, le <xref:System.Security.Permissions.SecurityAction> doivent être supprimés et la méthode marquée avec le <xref:System.Security.SecurityCriticalAttribute> attribut.

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]