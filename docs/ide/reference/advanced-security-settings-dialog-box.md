---
title: Paramètres de sécurité avancés, boîte de dialogue
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dce482f53f9f3e6dd0b57d6cb905f97cdfaa601a
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180514"
---
# <a name="advanced-security-settings-dialog-box"></a>Paramètres de sécurité avancés, boîte de dialogue

Cette boîte de dialogue vous permet de spécifier les paramètres de sécurité concernant le débogage dans la zone.

![Boîte de dialogue Paramètres de sécurité avancés dans Visual Studio](../media/advanced-security-settings.png)

Pour accéder à cette boîte de dialogue, sélectionnez un nœud de projet dans l’**Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**. Quand le **Concepteur de projets** apparaît, cliquez sur l’onglet **Sécurité**. Dans la page **Sécurité**, sélectionnez **Activer les paramètres de sécurité ClickOnce**, cliquez sur **Il s’agit d’une application de confiance partielle**, puis sur **Avancé**.

## <a name="uielement-list"></a>Liste UIElement

**Autoriser l’application à accéder à son site d’origine**

Si cette case est cochée, l’application peut accéder au site web ou au partage serveur sur lequel il est publié. Cette option est activée par défaut.

**Déboguer cette application comme si elle était téléchargée de l’URL suivante**

Si vous devez permettre à l’application d’accéder au site web ou au partage serveur correspondant à **l’URL d’installation** spécifiée sur la page **Publier**, entrez cette URL ici. Cette option est disponible uniquement quand l’option **Autoriser l’application à accéder à son site d’origine** est sélectionnée.

## <a name="see-also"></a>Voir aussi

- [Page Sécurité, Concepteur de projet](../../ide/reference/security-page-project-designer.md)