---
title: Concepteur de flux de travail - Concepteur d’activités InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b210b5e0d3d0f3638e78331d9db093f7e86079e
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117171"
---
# <a name="initializecorrelation-activity-designer"></a>Concepteur d'activités InitializeCorrelation

Le **InitializeCorrelation** ActivityDesigner est utilisé pour créer et configurer un <xref:System.ServiceModel.Activities.InitializeCorrelation> activité. Le <xref:System.ServiceModel.Activities.InitializeCorrelation> activité établit une corrélation entre les messages avant l’envoi ou leur réception.

## <a name="the-initializecorrelation-activity"></a>Activité InitializeCorrelation

Une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> est utilisée pour initialiser des corrélations sans envoyer ou recevoir de message. En général, la corrélation est initialisée lors de l'envoi ou de la réception d'un message. Si la corrélation doit être établie avant l'envoi ou la réception d'un message, utilisez <xref:System.ServiceModel.Activities.InitializeCorrelation> pour initialiser la corrélation.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilisation du concepteur d'activités InitializeCorrelation

Accès le **InitializeCorrelation** Concepteur d’activités dans le **Messaging** catégorie de la **boîte à outils**.

Le **InitializeCorrelation** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail. Suppression du Concepteur d’activités crée un <xref:System.ServiceModel.Activities.InitializeCorrelation> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de InitializeCorrelation. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **InitializeCorrelation** Concepteur d’activités ou dans le **DisplayName** boîte de le **propriétés** fenêtre.

Le <xref:System.ServiceModel.Activities.CorrelationHandle> peut être spécifie dans le **corrélation** champ **propriétés** fenêtre sur le **InitializeCorrelation** aire du Concepteur d’activités.

Pour afficher le **initialiser la corrélation** boîte de dialogue où vous pouvez spécifier le handle de corrélation et les paires clé-valeur utilisées pour initialiser, sélectionnez le bouton de sélection à côté du **CorrelationData** champ **propriétés** fenêtre. Sinon, sélectionnez le texte d’indication « Afficher... » sur le **InitializeCorrelation** aire du Concepteur d’activités. Pour plus d’informations sur l’utilisation de cette boîte de dialogue, consultez la [boîte de dialogue Éditeur de Type Collection](../workflow-designer/type-collection-editor-dialog-box.md) article.

### <a name="the-initializecorrelation-properties"></a>Propriétés d'InitializeCorrelation

Le tableau suivant présente le <xref:System.ServiceModel.Activities.InitializeCorrelation> propriétés et décrit leur utilisation dans le concepteur. Ces propriétés peuvent être modifiées dans **propriétés** fenêtre ou sur l’aire du Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.ServiceModel.Activities.InitializeCorrelation>. La valeur par défaut est InitializeCorrelation.<br /><br /> Bien que l’utilisation d’une valeur par défaut pour le nom convivial <xref:System.Activities.Activity.DisplayName%2A> n’est pas strictement obligatoire, il est recommandé.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour associer des activités de workflow dans la corrélation.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Dictionnaire des données de corrélation qui lie les messages à l'instance de workflow.<br /><br /> Utilisez le **initialiser la corrélation** boîte de dialogue pour configurer le <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Pour plus d’informations sur l’utilisation cette boîte de dialogue, consultez la [boîte de dialogue Éditeur de Type Collection](../workflow-designer/type-collection-editor-dialog-box.md) article.|

## <a name="see-also"></a>Voir aussi

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Réception](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Envoyer](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)