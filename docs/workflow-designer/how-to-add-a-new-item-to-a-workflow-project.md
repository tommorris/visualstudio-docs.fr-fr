---
title: 'Concepteur de flux de travail - Comment : ajouter un nouvel élément à un projet de flux de travail'
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c3f1202c87986eab6af899a3d4c3b7a5f62e5af6
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757677"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Comment : ajouter un nouvel élément à un projet de flux de travail

Une fois que vous avez créé un projet de flux de travail, vous pouvez ajouter des activités de flux de travail, les concepteurs et les autres éléments Visual Studio familiers à votre projet.

Le tableau suivant répertorie les éléments Windows Workflow Foundation (WF) que vous pouvez ajouter à un projet de flux de travail :

|Name|Description|
|----------|-----------------|
|Activité|Activité à composer d'autres activités. Sélection de cet élément ajoute le même fichier XAML au projet que ceux obtenus lors de la sélection du **bibliothèque d’activités** modèle pour un nouveau projet. Pour plus d’informations sur cette procédure, consultez [Comment : créer une bibliothèque d’activités](../workflow-designer/how-to-create-an-activity-library.md).|
|Concepteur d'activités|Concepteur pour personnaliser l’expérience au moment du design d’une activité. Sélection de cet élément ajoute les mêmes fichiers au projet que ceux obtenus lors de la sélection du **Bibliothèque ActivityDesigner** modèle pour un nouveau projet. Pour plus d’informations sur cette procédure, consultez [Comment : créer une bibliothèque ActivityDesigner](../workflow-designer/how-to-create-an-activity-designer-library.md).|
|Activité de code|Activité avec logique d'exécution écrite dans le code. Un fichier de code source avec substitution de la méthode <xref:System.Activities.CodeActivity.Execute%2A> est déjà généré automatiquement.|
|Service de workflow WCF|Service [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] construit à l'aide d'activités de workflow. Sélection de cet élément ajoute les mêmes fichiers au projet que ceux obtenus lors de la sélection du **Application de Service de Workflow WCF** modèle pour un nouveau projet. Pour plus d’informations sur cette procédure, consultez [Comment : créer une Application de Service de Workflow WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Pour ajouter un nouvel élément à un projet de workflow

1. Sur le **projet** menu, sélectionnez **ajouter un nouvel élément**.

   La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

1. Dans le volet gauche, sélectionnez le **Workflow** catégorie et sélectionnez un modèle d’élément de flux de travail.

   > [!NOTE]
   > Si vous ne voyez pas le **Workflow** catégorie, la première installation du **Windows Workflow Foundation** composant de Visual Studio 2017. Pour obtenir des instructions détaillées, consultez [installer Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Entrez un nom pour l’élément dans le **nom** zone située au bas de la boîte de dialogue.

1. Sélectionnez **ajouter** pour ajouter l’élément au projet.

## <a name="see-also"></a>Voir aussi

- [Créer un projet de flux de travail](../workflow-designer/creating-a-workflow-project.md)