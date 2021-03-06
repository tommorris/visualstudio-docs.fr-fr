---
title: 'Comment : ajouter un volet Actions à des documents Word ou de classeurs Excel'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ebf4896411a46b2c75edd8216bd61623bc9b728f
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548555"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Comment : ajouter un volet Actions à des documents Word ou à des classeurs Excel
  Pour ajouter un volet actions à un document Microsoft Office Word ou un classeur Microsoft Excel, d’abord créer un contrôle utilisateur Windows Forms. Ensuite, ajoutez le contrôle utilisateur à la <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> propriété de la `ThisDocument.ActionsPane` champ (Word) ou `ThisWorkbook.ActionsPane` champ (Excel) dans votre projet.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-the-user-control"></a>Création du contrôle utilisateur  
 La procédure suivante montre comment créer un mot de contrôle utilisateur ou un projet d’Excel. Il ajoute également un bouton au contrôle utilisateur qui écrit du texte dans le document ou le classeur lorsqu’il est activé.  
  
#### <a name="to-create-the-user-control"></a>Pour créer le contrôle utilisateur  
  
1.  Ouvrez votre projet au niveau du document Word ou Excel dans Visual Studio.  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **contrôle de volet Actions**, nommez-le **HelloControl**, puis cliquez sur **ajouter**.  
  
    > [!NOTE]  
    >  Vous pouvez également ajouter un **contrôle utilisateur** élément à votre projet. Les classes générées par le **contrôle de volet Actions** et **contrôle utilisateur** éléments sont fonctionnellement équivalents.  
  
4.  À partir de la **Windows Forms** onglet de la **boîte à outils,** faites glisser un **bouton** contrôle sur le contrôle.  
  
    > [!NOTE]  
    >  Si le contrôle n’est pas visible dans le concepteur, double-cliquez sur **HelloControl** dans **l’Explorateur de solutions**.  
  
5.  Ajoutez le code à le <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements du bouton. L’exemple suivant montre le code d’un document Microsoft Office Word.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  En c#, vous devez ajouter un gestionnaire d’événements pour le clic de bouton. Vous pouvez placer ce code dans le `HelloControl` constructeur après l’appel à `IntializeComponent`.  
  
     Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="add-the-user-control-to-the-actions-pane"></a>Ajoutez le contrôle utilisateur au volet actions  
 Pour afficher le volet actions, ajoutez le contrôle utilisateur à la <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> propriété de la `ThisDocument.ActionsPane` champ (Word) ou `ThisWorkbook.ActionsPane` champ (Excel).  
  
### <a name="to-add-the-user-control-to-the-actions-pane"></a>Pour ajouter le contrôle utilisateur au volet actions  
  
1.  Ajoutez le code suivant à la `ThisDocument` ou `ThisWorkbook` classe comme une déclaration au niveau de la classe (n’ajoutez pas ce code à une méthode).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  Ajoutez le code suivant à la `ThisDocument_Startup` Gestionnaire d’événements de la `ThisDocument` classe ou la `ThisWorkbook_Startup` Gestionnaire d’événements de la `ThisWorkbook` classe.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)   
 [Procédure : Insérer du texte dans un document à partir d’un volet actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Comment : gérer la disposition des contrôles dans les volets actions](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Procédure : Insérer du texte dans un document à partir d’un volet actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  