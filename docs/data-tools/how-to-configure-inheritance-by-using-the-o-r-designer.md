---
title: 'Comment : configurer l’héritage à l’aide du Concepteur O-R'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: bb0be89627f5e7e95d7d45ebfb938bca3e4a982b
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089262"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Comment : configurer l’héritage à l’aide du Concepteur O/R
Le **concepteur objet/relationnel** (**Concepteur O/R**) prend en charge le concept d’héritage à table unique tel qu’il est souvent implémenté dans les systèmes relationnels. L'héritage à table unique fait appel à une seule table de base de données qui contient des champs pour les informations parent et enfant. Avec les données relationnelles, une colonne de discriminateur contient la valeur qui détermine à quelle classe tout enregistrement appartient.

Par exemple, considérez un `Persons` table qui contient tous les employées par une société. Certaines personnes sont des employés et d'autres des responsables. Le `Persons` table contient une colonne nommée `EmployeeType` qui a la valeur 1 pour les responsables et une valeur de 2 pour les employés ; c’est la colonne de discriminateur. Dans ce scénario, vous pouvez créer une sous-classe d'employés et remplir la classe avec uniquement des enregistrements ayant une valeur `EmployeeType` de 2. Vous pouvez également supprimer les colonnes qui ne s'appliquent à aucune de ces classes.

La création d'un modèle objet qui utilise l'héritage (et correspond aux données relationnelles) peut prêter à confusion. La procédure suivante décrit les étapes requises pour configurer l’héritage avec les **Concepteur O/R**. Suivre les étapes génériques sans faire référence à une table existante et les colonnes peut-être être difficile, donc une procédure pas à pas qui utilise des données est fourni. Pour obtenir des instructions détaillées pour configurer l’héritage à l’aide de la **Concepteur O/R**, consultez [procédure pas à pas : création d’une requête LINQ to SQL classes à l’aide d’héritage à table unique (Concepteur O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>Pour créer des classes de données héritées

1.  Ouvrez le **Concepteur O/R** en ajoutant un **Classes LINQ to SQL** élément à un projet Visual Basic ou c# existant.

2.  Faites glisser la table que vous souhaitez utiliser en tant que classe de base vers le **Concepteur O/R**.

3.  Faites glisser une deuxième copie de la table sur le **Concepteur O/R** et renommez-la. C'est la classe dérivée, ou sous-classe.

4.  Cliquez sur **héritage** dans le **concepteur objet/relationnel** onglet de la **boîte à outils**, puis cliquez sur la sous-classe (la table que vous avez renommé) et connectez-la à la classe de base.

    > [!NOTE]
    >  Cliquez sur le **héritage** d’élément dans le **boîte à outils** et relâchez le bouton de la souris, cliquez sur la deuxième copie de la classe que vous avez créé à l’étape 3, puis cliquez sur la première classe que vous avez créé à l’étape 2. La flèche sur la ligne d’héritage pointe vers la première classe.

5.  Dans chaque classe, supprimez toutes les propriétés d'objet que vous ne souhaitez pas voir apparaître et qui ne sont pas utilisées pour des associations. Vous recevez une erreur si vous tentez de supprimer des propriétés de l’objet utilisées pour les associations : [la propriété \<nom de propriété > ne peut pas être supprimé, car il participe à l’association \<nom de l’association >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    >  Comme une classe dérivée hérite des propriétés définies dans sa classe de base, les mêmes colonnes ne peuvent pas être définies dans chaque classe. (Les colonnes sont implémentées sous forme de propriétés.) Vous pouvez activer la création de colonnes dans la classe dérivée en définissant le modificateur d’héritage sur la propriété dans la classe de base. Pour plus d’informations, consultez [fondamentaux de l’héritage (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6.  Sélectionnez la ligne d’héritage dans le **Concepteur O/R**.

7.  Dans le **propriétés** fenêtre, définissez la **propriété de discriminateur** au nom de colonne qui distingue les enregistrements dans vos classes.

8.  Définir le **valeur de discriminateur de classe dérivée** valeur à la propriété dans la base de données qui désigne l’enregistrement comme type hérité. (Il s’agit de la valeur qui est stockée dans la colonne de discriminateur et est utilisée pour désigner la classe héritée.)

9. Définir le **valeur de discriminateur de classe de Base** valeur à la propriété qui désigne l’enregistrement comme type de base. (Il s’agit de la valeur qui est stockée dans la colonne de discriminateur et est utilisée pour désigner la classe de base).

10. Si vous le souhaitez, vous pouvez également définir le **héritage par défaut** propriété pour désigner un type dans une hiérarchie d’héritage qui est utilisé lors du chargement de lignes ne correspondant pas à un de défini le code d’héritage. En d’autres termes, si un enregistrement a une valeur dans la colonne de discriminateur qui ne correspond pas la valeur de la **valeur de discriminateur de classe dérivée** ou **valeur de discriminateur de classe de Base** propriétés, l’enregistrement charge dans le type désigné comme le **héritage par défaut**.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procédure pas à pas : Création de LINQ to SQL classes (Concepteur O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procédure pas à pas : Création de LINQ aux classes SQL à l’aide d’héritage à table unique (Concepteur O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Principes fondamentaux de l’héritage (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Héritage](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)