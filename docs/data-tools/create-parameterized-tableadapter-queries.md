---
title: Créer des requêtes TableAdapter paramétrées
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fe77d3622e9c41d98ff89972e522bb25aae58b9d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756007"
---
# <a name="create-parameterized-tableadapter-queries"></a>Créer des requêtes TableAdapter paramétrées
Une requête paramétrable retourne des données remplissant les conditions d'une clause WHERE dans la requête. Par exemple, vous pouvez paramétrer une liste de clients de sorte à n'afficher que les clients d’une certaine ville en ajoutant `WHERE City = @City` à la fin de l'instruction SQL qui retourne une liste de clients.

 Vous créez des requêtes TableAdapter paramétrées dans le **Concepteur de Dataset**. Vous pouvez également les créer dans une application Windows avec le **paramétrer la Source de données** commande sur le **données** menu. Le **paramétrer la Source de données** commande crée des contrôles sur votre formulaire où vous pouvez entrer les valeurs de paramètre et exécuter la requête.

> [!NOTE]
> Lors de la construction d’une requête paramétrée, utilisez la notation de paramètre spécifique à la base de données que vous codez par rapport à. Par exemple, les sources de données Access et OleDb utilisent le point d'interrogation « ? » pour désigner des paramètres, la clause WHERE sera donc de type : `WHERE City = ?`.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l’aide, en fonction de vos paramètres actifs ou de l’édition que vous utilisez. Pour modifier vos paramètres, accédez à la **outils** menu et sélectionnez **importation et exportation de paramètres**. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-parameterized-tableadapter-query"></a>Créer une requête TableAdapter paramétrée

#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Pour créer une requête paramétrée dans le Concepteur de DataSet

-   Créez un TableAdapter, en ajoutant une clause WHERE avec les paramètres souhaités à l'instruction SQL. Pour plus d’informations, consultez [créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).

     - ou -

-   Ajoutez une requête à un TableAdapter existant, en ajoutant une clause WHERE avec les paramètres souhaités à l'instruction SQL.

#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Pour créer une requête paramétrée pendant la conception d'un formulaire lié aux données

1.  Sélectionnez un contrôle dans votre formulaire déjà lié à un dataset. Pour plus d’informations, consultez [lier les formulaires Windows contrôle aux données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2.  Sur le **données** menu, sélectionnez **ajouter une requête**.

3.  Terminer la **Générateur de critères de recherche** boîte de dialogue, ajout d’une clause WHERE avec les paramètres souhaités à l’instruction SQL.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Pour ajouter une requête à un formulaire lié aux données existant

1.  Ouvrez le formulaire dans le **Concepteur Windows Forms**.

2.  Sur le **données** menu, sélectionnez **ajouter une requête** ou **balises actives de données**.

    > [!NOTE]
    >  Si **ajouter une requête** n’est pas disponible sur le **données** menu, sélectionnez un contrôle sur le formulaire qu’affiche les source de données vous souhaitez ajouter le paramétrage. Par exemple, si le formulaire affiche des données dans un contrôle <xref:System.Windows.Forms.DataGridView>, sélectionnez-le. Si le formulaire affiche des données dans des contrôles individuels, sélectionnez n'importe quel contrôle lié aux données.

3.  Dans le **table de source de données Sélectionnez** zone, sélectionnez la table à laquelle vous souhaitez ajouter le paramétrage.

4.  Tapez un nom dans la **nouveau nom de requête** zone Si vous créez une nouvelle requête.

     - ou -

     Sélectionnez une requête dans le **nom de requête existant** boîte.

5.  Dans le **texte de la requête** , tapez une requête qui accepte des paramètres.

6.  Sélectionnez **OK**.

     Un contrôle pour le paramètre d’entrée et un **charge** bouton sont ajoutés au formulaire dans un <xref:System.Windows.Forms.ToolStrip> contrôle.

#### <a name="querying-for-null-values"></a>Interrogation des valeurs null
Les valeurs null peuvent être assignées aux paramètres TableAdapter lorsque vous souhaitez interroger les enregistrements qui n’ont aucune valeur actuelle. Par exemple, considérez la requête suivante qui a un `ShippedDate` paramètre dans son `WHERE` clause :

 ```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

 S’il s’agissait d’une requête sur un TableAdapter, vous pouvez rechercher toutes les commandes qui n’ont pas été fournis par le code suivant :

 [!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
 [!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

 Pour activer une requête d’accepter les valeurs null :

1.  Dans le **Concepteur de Dataset**, sélectionnez la requête TableAdapter qui doit accepter les valeurs de paramètre null.

2.  Dans le **propriétés** fenêtre, sélectionnez **paramètres**, puis cliquez sur le bouton de sélection (**...** ) pour ouvrir la **éditeur de collections Parameters**.

3.  Sélectionnez le paramètre qui autorise les valeurs null et définissez le **AllowDbNull** propriété `true`.

## <a name="see-also"></a>Voir aussi

- [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)