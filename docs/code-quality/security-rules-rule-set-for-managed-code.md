---
title: Ensemble de règles des règles de sécurité pour le code managé
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6712454fad2acaf57b3cb4d8f1740366a396ec6e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31925040"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Ensemble de règles des règles de sécurité pour le code managé
Vous devez inclure la règle de règles de sécurité de Microsoft pour optimiser le nombre de problèmes potentiels de sécurité qui sont signalés.

|Règle|Description|
|----------|-----------------|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Passez en revue les requêtes SQL des failles de sécurité|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Interceptez les exceptions non CLSCompliant dans les gestionnaires généraux|
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|Vérifiez la sécurité impérative|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Ne déclarez pas les types référence mutables uniquement en lecture|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Les champs de tableau ne doivent pas être lu uniquement|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Assertions sécurisées|
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Révision méthodes deny et PermitOnly uniquement l’utilisation|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Vérifiez la sécurité déclarative dans les types valeur|
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|Passez en revue les gestionnaires d’événements visibles|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Les pointeurs ne doivent pas être visibles|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Types sécurisés ne doivent pas exposer de champs|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Sécurité de la méthode doit être un sur-ensemble du type|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Appelez GC. KeepAlive lors de l’utilisation des ressources natives|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Les méthodes APTCA doivent uniquement appeler des méthodes APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Les types APTCA doivent uniquement étendre des types de base APTCA|
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|Passez en revue l’utilisation de SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Scellez les méthodes qui satisfont les interfaces privées|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Sécuriser les constructeurs de sérialisation|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Les constructeurs statiques doivent être privés|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|N’exposez pas indirectement des méthodes avec des demandes de liaison|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Les demandes de liaison de remplacement doivent être identiques à la base|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Finally vulnérables clauses dans externe try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Liaison de types nécessitent des demandes d’héritage|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Les constantes critiques de sécurité doivent être transparentes|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Les types critiques de sécurité ne peuvent pas faire partie de l’équivalence de type|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Les délégués doivent lier les méthodes avec une transparence cohérente|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Transparence des méthodes doivent rester cohérente lors de la substitution de méthodes de base|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Les assemblys de niveau 2 ne doivent pas contenir de LinkDemands|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Les membres ne devez pas d’annotations de transparence conflictuelles|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Les méthodes transparentes doivent contenir uniquement des IL vérifiables|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Les méthodes transparentes ne doivent pas appeler les méthodes avec l’attribut SuppressUnmanagedCodeSecurity|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Les méthodes transparentes ne peuvent pas utiliser l’attribut HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Le code transparent ne doit pas faire référence à des éléments critiques de sécurité|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Les méthodes transparentes ne répondent pas aux LinkDemands|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Le code transparent ne doit pas être protégé avec des LinkDemands|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Le code transparent ne doit pas charger les assemblys depuis des tableaux d’octets|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Les méthodes transparentes ne doivent pas être décorées avec SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Types doivent être au moins aussi critiques que leurs types de base et les interfaces|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Les méthodes transparentes ne peuvent pas utiliser de sécurité des assertions|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Les méthodes transparentes ne doivent pas appeler dans du code natif|
|[CA2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Assemblys doivent avoir des noms forts valides|