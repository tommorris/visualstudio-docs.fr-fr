---
title: Vue Arborescence des appels - Données de conflit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40e28eb246b2c4611a15dc4ce2cf6b1b02dd0100
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263179"
---
# <a name="call-tree-view---contention-data"></a>Vue Arborescence des appels - Données de conflit
La vue Arborescence des appels affiche les chemins d’exécution de la fonction empruntés dans l’application profilée. La racine de l’arborescence correspond au point d’entrée de l’application ou du composant. Chaque nœud de fonction répertorie toutes les fonctions appelées, le nombre de fois où la fonction a été bloquée, et la durée pendant laquelle la fonction a été bloquée car elle était en conflit pour une ressource avec d’autres threads ou processus.  
  
 Les valeurs qui s’affichent dans la vue Arborescence des appels sont celles des instances de fonction qui ont été appelées par la fonction parent dans l’arborescence des appels. Les valeurs en pourcentage sont calculées en comparant la valeur des instances de fonctions au nombre total de conflits de l’exécution du profilage.  
  
## <a name="highlight-the-execution-hot-path"></a>Mettre en surbrillance le chemin réactif d’exécution  
 La vue Arborescence des appels peut être développée pour mettre en surbrillance le chemin d’exécution du processus ou de la fonction ayant créé le plus de conflits.  
  
-   Pour afficher le chemin le plus actif, cliquez avec le bouton droit sur le processus ou la fonction, puis cliquez sur **Développer le chemin réactif**.  
  
## <a name="set-the-call-tree-root-node"></a>Définir le nœud racine de l’arborescence des appels  
 Chaque processus de l’exécution du profilage s’affiche sous forme de nœud racine. Pour définir le nœud de départ de la vue Arborescence des appels, cliquez avec le bouton droit sur le nœud que vous souhaitez définir comme nœud de départ, puis cliquez sur **Définir la racine**.  
  
 En définissant le nœud racine, vous supprimez toutes les autres entrées de l’affichage, à l’exception de la sous-arborescence du nœud sélectionné. Pour réinitialiser le nœud racine au nœud d’origine, cliquez avec le bouton droit dans la Vue Arborescence des appels, puis cliquez sur **Réinitialiser la racine**.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps bloqué exclusif**|Durée pendant laquelle des instances de cette fonction dans ce chemin d’exécution n’ont pas pu s’exécuter au cours de l’exécution du profilage. Cette durée n’inclut pas le temps bloqué des fonctions enfants qui ont été appelées par la fonction.|  
|**% de temps bloqué exclusif**|Pourcentage de tout le temps bloqué au cours de l’exécution de profilage qui était du temps bloqué exclusif pour cette fonction dans ce chemin d’exécution.|  
|**Conflits exclusifs**|Nombre de conflits qui se sont produits dans des instances de cette fonction dans ce chemin d’exécution. Ce nombre n’inclut pas les conflits des fonctions enfants appelées par la fonction.|  
|**% de conflits exclusifs**|Pourcentage de tous les conflits au cours de l’exécution du profilage qui étaient des conflits exclusifs des instances de cette fonction appelées par la fonction parente dans l’arborescence des appels.|  
|**Adresse de la fonction**|Adresse de la fonction.|  
|**Nom de la fonction**|Nom complet de la fonction.|  
|**Temps bloqué inclusif**|Durée totale pendant laquelle les instances de cette fonction dans ce chemin d’exécution n’ont pas pu s’exécuter au cours de l’exécution du profilage. Cette durée inclut le temps bloqué des fonctions enfants appelées par la fonction.|  
|**% de temps bloqué inclusif**|Pourcentage de tout le temps bloqué au cours de l’exécution de profilage qui était du temps bloqué inclusif pour les instances de cette fonction dans ce chemin d’exécution.|  
|**Conflits inclusifs**|Nombre total de conflits ayant bloqué des instances de cette fonction dans ce chemin d’exécution. Ce nombre inclut les conflits des fonctions enfants appelées par la fonction.|  
|**% de conflits inclusifs**|Pourcentage de tous les conflits au cours de l’exécution de profilage qui étaient des conflits inclusifs des instances de cette fonction dans ce contexte d’exécution.|  
|**Niveau**|Niveau de la fonction dans l’arborescence des appels. Uniquement dans les rapports en ligne de commande VSReport. Pour plus d’informations, consultez [VSPerfReport](../profiling/vsperfreport.md).|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nom de module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d’accès du module qui contient la fonction.|  
|**ID du processus**|ID du processus (PID) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Fichier source**|Fichier source contenant la définition pour cette fonction.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Mode Arborescence des appels](../profiling/call-tree-view.md)   
 [Vue Arborescence des appels - Instrumentation](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Vue Arborescence des appels - Échantillonnage](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Mode Arborescence des appels](../profiling/call-tree-view-instrumentation-data.md)   
 [Mode Arborescence des appels](../profiling/call-tree-view-sampling-data.md)