---
title: 'Comment : afficher par programme une chaîne dans une cellule de feuille de calcul'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 336ab67cd5c63a912d72b0fce3fa73c9fca5184f
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256817"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Comment : afficher par programme une chaîne dans une cellule de feuille de calcul
  Cet exemple montre comment afficher du texte dans une cellule par programme. Pour afficher le texte dans la cellule, utilisez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou un objet de plage Excel natif.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>Utiliser un contrôle NamedRange  
 Cet exemple utilise un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle nommé `message`. Le contrôle doit être ajouté à une personnalisation au niveau du document au moment du design. Le code suivant doit être placé dans une classe sheet et non dans le `ThisWorkbook` classe.  
  
### <a name="to-display-text-in-a-namedrange-control"></a>Pour afficher le texte dans un contrôle NamedRange  
  
1.  Définissez la valeur de la <xref:Microsoft.Office.Tools.Excel.NamedRange> le contrôle à **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]  
  
## <a name="use-a-native-excel-range"></a>Utiliser une plage Excel native  
 Le code suivant crée une nouvelle plage par programmation et puis lui affecte une valeur.  
  
### <a name="to-display-text-in-an-excel-range"></a>Pour afficher le texte dans une plage Excel  
  
1.  Extraire la plage à la cellule **A1** sur `Sheet1` et définissez la valeur sur **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Collecter des données à l’aide d’un formulaire Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Résoudre les problèmes des solutions Office](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  