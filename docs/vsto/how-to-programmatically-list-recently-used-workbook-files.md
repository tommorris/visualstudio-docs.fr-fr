---
title: 'Comment : liste récemment utilisés par programmation les fichiers de classeur'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d3e909ad3e1509689d953e0ad6c6b8346ff97f91
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257587"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Comment : liste récemment utilisés par programmation les fichiers de classeur
  Le <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> propriété retourne une collection qui contient les noms de tous les fichiers qui apparaissent dans la liste de Microsoft Office Excel des fichiers récemment utilisés. La longueur de la liste varie en fonction du nombre de fichiers que l’utilisateur a choisi de conserver. Vous pouvez afficher les résultats dans une plage.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Pour répertorier récemment des classeurs utilisés dans un objet range  
  
1.  Parcourez la liste des fichiers récents et afficher les noms dans les cellules relatif à un <xref:Microsoft.Office.Interop.Excel.Range> objet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des classeurs](../vsto/working-with-workbooks.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  