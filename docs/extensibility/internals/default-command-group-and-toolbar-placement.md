---
title: Commande, de groupe et de positionnement de la barre d’outils par défaut | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: da5716460c428098b2b6cc3bb78a51c3831201b2
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498228"
---
# <a name="default-command-group-and-toolbar-placement"></a>Placement de commande, le groupe et barre d’outils par défaut
Pour l’uniformité de produit et la stabilité, l’interface utilisateur affiche certains groupes de commandes par défaut, et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit les définitions des commandes et des groupes de commandes. Les VSPackages peuvent également utiliser les commandes standards et les groupes de commandes.  
  
 Les groupes de commandes par défaut se répartissent en trois catégories : IDE commandes, les commandes de produits et les commandes de l’éditeur.  
  
## <a name="default-ide-commands"></a>Commandes de l’IDE par défaut  
 La barre d’outils des IDE par défaut inclut des commandes partagées par tous les produits contenus dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Celles-ci comprennent les commandes relatives aux opérations de projet générique, tel que le **enregistrer** commande et le **ajouter un élément** commande. VSPackages ne devez pas ajouter ou soustraire de cette barre d’outils, à une exception près : si le produit ou un VSPackage ajoute une nouvelle fenêtre outil, la fenêtre doit être ajoutée à la liste des fenêtres Outil disponible sur le **vue** menu. Nouveaux produits ou les VSPackages peuvent ajouter leur propre barre d’outils.  
  
## <a name="default-product-commands"></a>Commandes de produit par défaut  
 Chaque produit peut fournir l’IDE avec sa propre barre d’outils par défaut qui contient un important et commandes fréquemment utilisées. Toutefois, il est préférable, à utiliser existant des menus et barres d’outils autant que possible et de les compléter avec les autres barres d’outils spécifiques aux tâches en fonction des besoins.  
  
 Le champ priorité pour une barre d’outils détermine sa position de ligne. Zéro priorité place la barre d’outils sur la troisième ligne (ligne 3), sous la barre de menus (ligne 1) et le **Standard** la barre d’outils (ligne 2). Par conséquent, les autres barres d’outils apparaissent en ligne (priorité + 3). Barres d’outils suivants sont placés sur la même ligne, si l’espace ; Sinon, ils sont automatiquement déplacés vers la ligne suivante.  
  
## <a name="default-editor-commands"></a>Commandes de l’éditeur par défaut  
 Un VSPackage qui fournit un éditeur personnalisé doit fournir une barre d’outils par défaut qui contient les plus importants et les commandes fréquemment utilisées dans cet éditeur. La barre d’outils de l’éditeur doit apparaître lorsque l’éditeur est actif et doit être masqué lorsque l’éditeur n’est pas actif. Cette visibilité est contrôlée dans le `VisibilityConstraints` élément de la *.vsct* fichier.  
  
 Barres d’outils de l’éditeur doivent être placés au-dessous des barres d’outils IDE et produit.  
  
## <a name="see-also"></a>Voir aussi  
 [Groupes, les menus et commandes définies par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)