---
title: Insérer des contrôles et modifier leur comportement dans le concepteur XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 739c43b0ed6665684f0a38b35dfd6eccdf8f5b2c
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38977802"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Insérer des contrôles et modifier leur comportement dans le concepteur XAML

Les contrôles permettent aux utilisateurs d'interagir avec votre application. Elles peuvent s'avérer utiles pour collecter des informations et effectuer des actions, comme animer un objet ou interroger une source de données.

## <a name="add-controls-to-the-artboard"></a>Ajouter des contrôles à la planche graphique

Vous pouvez faire glisser des contrôles du panneau **Composants** vers la **planche graphique**, puis les modifier dans la fenêtre **Propriétés** .

![Contrôles d’onglet Composants Blend](../designers/media/blend_assetsflipview_xaml.png)

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Créer un contrôle à partir d’une image, d’une forme ou d’un tracé

Vous pouvez transformer n'importe quel objet en contrôle.

![Créer un contrôle dans Blend, boîte de dialogue](../designers/media/blend_makeintocontrol_xaml.png)

Par exemple, imaginez une image de téléviseur au milieu d'une page. Vous pourriez créer des contrôles à partir de petites images représentant des boutons de téléviseur. Les utilisateurs pourraient ensuite cliquer sur ces boutons pour changer de chaîne.

Cela serait possible, car les boutons seraient dès lors des contrôles. Les contrôles permettent de répondre aux interactions de l'utilisateur (dans ce cas, le clic de l'utilisateur sur un bouton).

Pour créer un contrôle, sélectionnez un objet. Ensuite, dans le menu **Outils** , cliquez sur **Créer un contrôle**.

## <a name="make-controls-do-things"></a>Rendre les contrôles actifs

Les contrôles peuvent effectuer des actions quand les utilisateurs interagissent avec eux. Par exemple, ils peuvent démarrer une animation, mettre à jour une source de données ou lire une vidéo.

Pour rendre des contrôles actifs, vous devez utiliser des *déclencheurs*, des *comportements*et des *événements* .

### <a name="triggers"></a>déclencheurs

Un *déclencheur* modifie une propriété ou effectue une tâche en réponse à un événement ou à une modification apporté à une autre propriété. Par exemple, vous pouvez faire en sorte qu'un bouton change de couleur quand les utilisateurs le pointent avec la souris.

![Volet Déclencheurs](../designers/media/custom_button_blend_propertytriggerinfo.png)

### <a name="behaviors"></a>comportements

Un *comportement* est un ensemble de code réutilisable. Il permet de faire un peu plus que modifier les propriétés. Il permet d'effectuer certaines actions, comme interroger un service de données. Blend propose une petite collection de comportements, mais vous pouvez en ajouter d’autres. Faites glisser un comportement sur un objet dans la planche graphique, puis personnalisez-le en définissant des propriétés.

![FluidMoveBehavior dans le volet Propriétés](../designers/media/b4_fluidmovebehaviorproperties_sample.png)

**Regardez une vidéo :** ![Icône de lecture](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Conseils sur Blend : introduction à l’utilisation des comportements - Partie 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).

### <a name="events"></a>Événements

Pour un maximum de souplesse, traitez un *événement*. Vous devrez écrire un peu de code.