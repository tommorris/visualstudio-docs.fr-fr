---
title: Installer et utiliser Visual Studio et les services Azure derrière un pare-feu ou un serveur proxy | Microsoft Docs
description: Passez en revue les URL de domaine à ajouter à la liste verte, ainsi que les ports et protocoles à ouvrir, si votre organisation utilise un pare-feu ou un serveur proxy
ms.custom: ''
ms.date: 07/10/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3a3b798b704111c8afdbaaaa3b219b876ebf6ff
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280582"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Installer et utiliser Visual Studio et les services Azure derrière un pare-feu ou un serveur proxy

Si vous ou votre organisation utilisez des mesures de sécurité tel qu’un pare-feu ou un serveur proxy, il existe des URL de domaine que vous pouvez vouloir mettre sur « liste verte » et des ports et protocoles que vous pouvez vouloir ouvrir afin d’obtenir une meilleure expérience lorsque vous installez et utilisez Visual Studio et les services Azure.

* **[Installer Visual Studio](#install-visual-studio)**  : ces tables incluent les URL de domaine à la liste verte, afin que vous ayez accès à tous les composants et charges de travail que vous souhaitez.

* **[Utiliser Visual Studio et les services Azure](#use-visual-studio-and-azure-services)**  : Cette table inclut les URL de domaine à la liste verte et les ports et protocoles à ouvrir pour avoir accès à toutes les fonctionnalités et tous les services désirés.

## <a name="install-visual-studio"></a>Installer Visual Studio

### <a name="urls-to-whitelist"></a>URL à la liste verte

Étant donné que le programme d’installation Visual Studio télécharge des fichiers à partir de différents domaines et leurs serveurs de téléchargement, vous trouverez ici les URL de domaine nécessaires à la mise sur liste verte tel qu’approuvé dans l’interface utilisateur ou dans vos scripts de déploiement.

#### <a name="microsoft-domains"></a>Domaines Microsoft

| Domaine | Objectif |
| ------ | ------- |
| go.microsoft.com | Résolution de l’URL d’installation |
| aka.ms | Résolution de l’URL d’installation |
| download.visualstudio.microsoft.com | Emplacement de téléchargement des packages d’installation |
| download.microsoft.com | Emplacement de téléchargement des packages d’installation |
| download.visualstudio.com | Emplacement de téléchargement des packages d’installation |
| dl.xamarin.com | Emplacement de téléchargement des packages d’installation |
| visualstudiogallery.msdn.microsoft.com | Emplacement de téléchargement des extensions Visual Studio |
| visualstudio.microsoft.com | Emplacement de la documentation |
| docs.microsoft.com | Emplacement de la documentation |
| msdn.microsoft.com | Emplacement de la documentation |
| www.microsoft.com | Emplacement de la documentation |
| *.windows.net | Emplacement de connexion |
| *.microsoftonline.com | Emplacement de connexion |
| *.live.com | Emplacement de connexion |
|  |  | |

#### <a name="non-microsoft-domains"></a>Domaines non-Microsoft

| Domaine | Installe ces charges de travail |
| ------ | ------- |
| archive.apache.org |  Développement mobile avec JavaScript (Cordova) |
| cocos2d-x.org | Développement de jeux avec C++ (Cocos) |
| download.epicgames.com | Développement de jeux avec C++ (Unreal Engine) |
| download.oracle.com | Développement mobile avec JavaScript (Kit de développement logiciel (SDK) Java) <br /><br />Développement mobile en .NET (Kit de développement logiciel (SDK) Java) |
| download.unity3d.com | Développement de jeux avec Unity (Unity) |
| netstorage.unity3d.com | Développement de jeux avec Unity (Unity) |
| dl.google.com | Développement mobile avec JavaScript (Android SDK et NDK, émulateur) <br /><br />Développement mobile avec .NET (Android SDK et NDK, émulateur) |
| www.incredibuild.com | Développement de jeux avec C++ (Incredibuild) |
| incredibuildvs2017i.azureedge.net | Développement de jeux avec C++ (Incredibuild) |
| www.python.org | Développement Python (Python) <br /><br />Applications de science des données et analytiques (Python) |
|  |  | |

## <a name="use-visual-studio-and-azure-services"></a>Utiliser Visual Studio et les services Azure

### <a name="urls-to-whitelist-and-ports-and-protocols-to-open"></a>URL à la liste verte et ports et protocoles à ouvrir

Pour vous assurer que vous avez accès à tout ce dont vous avez besoin lorsque vous utilisez Visual Studio ou les services Azure derrière un pare-feu ou un serveur proxy, vous trouverez ici les URL que vous devez mettre sur liste verte et les ports et protocoles que vous souhaitez ouvrir.

| Scénario ou service | Point de terminaison DNS | Protocole | Port | Description |
| --- | --- | --- | --- | --- |
| URL<br>résolution | go.microsoft.com<br><br>aka.ms | | |Permet de raccourcir les URL, puis les résoudre en URL plus longues
| Page de démarrage | vsstartpage.blob.core.windows.net | | 443| Permet d’afficher les actualités sur les développeurs affichées sur la page de démarrage dans Visual Studio |
| Ciblé<br> Notification <br>Service | targetednotifications.azurewebsites.net <br><br>www.research.net | | 80<br><br>443| Permet de filtrer une liste de notifications globale sur une liste qui s’applique uniquement à certains types de scénarios de machines/d’utilisation |
| Extension <br>Vérification de mise à jour | visualstudiogallery.msdn.microsoft.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com  | | 443 | Permet de fournir des notifications lorsqu’une extension installée a une mise à jour disponible <br><br> Utilisé comme emplacement de connexion|
| Projet IA <br>Intégration | az861674.vo.msecnd.net  | | 443<br> | Permet de configurer de nouveaux projets pour envoyer des données d’utilisation à votre compte Application Insights enregistré |
| CodeLens | codelensprodscus1su0.app.<br>codelens.visualstudio.com | |443 | Permet de fournir des informations dans l’éditeur relatives à la dernière mise à jour d’un fichier, à la chronologie des modifications, aux éléments de travail auxquels sont associées des modifications, aux auteurs et bien plus encore|
|Expérimental <br>activation des fonctionnalités  | visualstudio-devdiv-c2s.msedge.net | |80 | Permet d’activer de nouvelles fonctionnalités expérimentales ou des modifications de fonctionnalités |
| « Badge » d’identité <br>(nom d'utilisateur et avatar)<br>et <br>Paramètres d'itinérance | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net  | |443 | Permet d’afficher le nom et l’avatar de l’utilisateur dans l’IDE <br><br> Permet de vous assurer que les modifications de paramètres utilisent un profil itinérant d’un ordinateur à un autre |
| Paramètres distants | az700632.vo.msecnd.net | | 443| Permet de désactiver des extensions qui sont connues pour poser des problèmes dans Visual Studio   |
| Outils Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com |https |443 | Utilisé pour les scénarios de magasin d’applications Windows  |
| Schéma JSON <br>découverte, <br><br>Schéma JSON <br>Définition<br><br>Schéma JSON <br>Prise en charge de <br>Ressources Azure| json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com| http<br>https<br><br>http<br><br>https |80<br>443 <br><br> 443<br><br>443 | Permet de détecter et de télécharger des schémas JSON que l’utilisateur peut utiliser lors de la modification des documents JSON <br><br>Permet d’obtenir le schéma de validation de métadonnées pour JSON<br><br>Permet d’obtenir le schéma actuel pour les modèles de déploiement Azure Resource Manager|
| Package NPM <br>découverte  |Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io  | https<br><br>http/s<br><br>https | 443<br><br>80/443<br><br>443| Requis pour la recherche de packages NPM et utilisé pour l’installation de packages de scripts côté client dans les projets Web |
|Package de Bower<br> icônes<br><br>Package de Bower <br>search  |Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http<br><br>https<br>http<br>https|80<br><br>443<br>80<br>443 |Fournit l’icône de package Bower par défaut  <br><br>Offre la possibilité de rechercher des packages Bower |
|NuGet<br><br>Package NuGet<br> découverte | Api.nuget.org <br>www.nuget.org <br>Nuget.org<br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com  | https<br><br>http/s |443<br><br>80/443<br> |Permet de vérifier les packages NuGet signés.<br><br>Requis pour la recherche des versions et packages NuGet |
|Informations de dépôt GitHub  |api.github.com  |https | 443| Requis pour l’obtention d’informations supplémentaires sur les packages Bower |
| Linters Web|Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org  | http|80 | |
| Cookiecutter<br>Modèle Explorer<br>découverte <br><br>Cookiecutter <br>Projet Explorer<br> création | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org  | https | 443<br> | Permet de détecter les modèles en ligne à partir de notre flux recommandé et de dépôts Github <br><br>Permet de créer un projet à partir d’un modèle cookiecutter qui requiert une installation à la demande unique d’un package Python cookiecutter à partir de l’index du package Python (PyPI)|
| Package Python <br>découverte<br><br>Package Python <br>gestion<br><br>Python <br>Nouveau projet <br>C++| pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com| https| 443| Offre la possibilité de rechercher des packages pip<br><br>Permet d’installer le pip automatiquement s’il est manquant <br><br> Permet de créer le <br><br>Permet de résoudre les modèles de projets Python suivants dans la boîte de dialogue Nouveau projet pour les URL du modèle de cookiecutter :<br> - Projet Classifier<br>- Projet clustering <br> - Projet Regression <br> - PyGame avec PyKinect <br> - Projet Pyvot |
| Office Web <br>complément <br> manifeste <br>Vérification <br>Service | verificationservice.osi.office.net | https | 443 | Permet de valider les manifestes pour les compléments Office Web |
| SharePoint et <br>Compléments Office | sharepoint.com | https | 443 | Permet de publier et tester des compléments Office et SharePoint sur SharePoint Online |
| Workflow Manager <br>Service de test<br> Hôte |  | http | 12292 | Une règle de pare-feu créée automatiquement pour le test des compléments SharePoint avec des workflows |
| Collectées automatiquement <br>statistiques de fiabilité <br>et autre <br>Expérience utilisateur <br>Programmes d’amélioration du produit (CEIP)<br> pour le kit de développement logiciel (SDK) et <br>pour les outils SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com |https | 443| Permet d’envoyer des statistiques de fiabilité (données d’incident/blocage) depuis l’utilisateur vers Microsoft. Les vidages sur incident/blocage réels seront toujours téléchargés si le rapport d’erreurs Windows est activé ; seules les informations statistiques seront supprimées ; <br>Permet de révéler des modèles d’utilisation anonymes pour l’extension du Kit de développement logiciel Azure Tools pour Visual Studio et pour les modèles d’utilisation des outils SQL de Visual Studio |
| Visual Studio <br> Expérience utilisateur <br>Programme d’amélioration du produit (CEIP) <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https| 443 | Permet de collecter des modèles d’utilisation anonymes et des journaux d’erreurs <br><br>Permet de suivre des problèmes de gel de l’interface utilisateur|
| Création et<br>Gestion de <br>Ressources Azure | management.azure.com <br>management.core.windows.net   | https | 443 | Permet de créer des sites Web Azure ou d’autres ressources pour prendre en charge la publication d’applications web, des fonctions Azure ou WebJobs |
| Outils de publication Web mis à jour <br>vérifications et extension <br>recommandations  | marketplace.visualstudio.com  <br> visualstudiogallery.msdn.microsoft.com  | https | 443 | Utilisé pour la vérification de la disponibilité des outils de publication mis à jour. Si désactivé, une extension potentielle recommandée pour la publication Web ne peut pas être affichée |
| Azure Ressource mis à jour <br>Création des informations sur le point de terminaison  | *.blob.core.windows.net | https | 443 | Permet de mettre à jour les points de terminaison utilisés pour la création des ressources Azure pour certains services Azure. Si désactivé, les derniers emplacements de points de terminaison téléchargés ou intégrés sont utilisés à la place |
| Débogage distant et <br>Profilage à distance de <br>Sites web Azure | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | | 4022 | Permet d’attacher le débogueur distant à des sites Web Azure. Si désactivé, l’attachement du débogueur distant à des sites Web Azure ne fonctionnera pas |
| Active Directory <br>Graphique | graph.windows.net | https | 443 | Permet de configurer les nouvelles applications Azure Active Directory. Également utilisé par le fournisseur de service connecté Office 365 MSGraph- |
| Azure Functions <br>Mise à jour de l’interface CLI <br>Valider | functionscdn.azureedge.net | https | 443 | Utilisé pour la vérification des versions mises à jour de l’interface CLI Azure Functions. Si désactivé, une copie mise en cache (ou la copie effectuée par le composant Azure Functions) de l’interface CLI sera utilisée à la place |
| Cordova | npmjs.org<br>gradle.org | http/s | 80/443 | Le protocole HTTP est utilisé pour les téléchargements de Gradle lors de la génération ; HTTPS est utilisé pour inclure les plug-ins Cordova aux projets|
| Cloud Explorer | 1. &#60;clusterendpoint&#62; <br>Service Fabric <br>2. &#60;point de terminaison de gestion&#62;<br>Exp Cloud général <br>3. &#60;point de terminaison de graphique&#62;<br>Exp Cloud général<br>4. &#60;point de terminaison du compte de stockage&#62;<br>Nœuds de stockage <br>5. &#60;URL du portail Azure&#62;<br>Exp Cloud général <br>6. &#60;points de terminaison du coffre de clés&#62; <br>Nœuds de machine virtuelle Azure Resource Manager<br>7. &#60;PublicIPAddressOfCluster&#62;<br>Débogage distant et traces ETW Service Fabric |   <br>1. https<br>2. https<br>3. https<br>4. https<br>5. https<br>6. https<br>7 : tcp| 1. 19080<br>2. 443 <br>3. 443 <br>4. 443 <br>5. 443 <br>6. 443 <br>7. dynamique   | 1. Exemple : test12.eastus.cloudapp.com<br>2. Récupère les abonnements et récupère/gère les ressources Azure<br>3. Récupère les abonnements Azure Stack<br>4. Gère les ressources de stockage (exemple : mystorageaccount.blob.core.windows.net)<br>5. Option de menu contextuel « Ouvrir dans le portail » (ouvre une ressource dans le portail Azure)<br>6. Crée et utilise des coffres de clé pour le débogage de la machine virtuelle (exemple : myvault.vault.azure.net) <br><br>7. Alloue dynamiquement un bloc de ports en fonction du nombre de nœuds dans le cluster et des ports disponibles. <br><br>Un bloc de ports tentera d’obtenir trois fois le nombre de nœuds avec un minimum de 10 ports.<br><br>Pour les traces de diffusion en continu, une tentative est effectuée pour obtenir le bloc de ports à partir de 810. Si un de ces blocs de ports est déjà utilisé, une tentative est alors effectuée pour obtenir le bloc suivant et ainsi de suite. (Si l’équilibreur de charge est vide, les ports à partir de 810 sont très probablement utilisés) <br><br>De même pour le débogage, quatre jeux de ces blocs de ports sont réservés : <br>- connectorPort : 30398, <br>- forwarderPort : 31398, <br>- forwarderPortx86 : 31399,<br>- fileUploadPort : 32398<br>|
| Services cloud | 1. Protocole RDP (Remote Desktop Protocol)<br><br>2. core.windows.net <br><br>3.  management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;service de cloud utilisateur &#62;.cloudapp.net <br> &#60;Machine virtuelle de l’utilisateur&#62;.&#60;région&#62;.azure.com | 1. rdp <br><br> 2. https <br><br> 3. https <br><br> 4. https <br><br> 5. https <br><br>6. tcp | 1. 3389 <br><br> 2. 443 <br><br> 3. 443 <br><br>4. 443 <br><br>5. 443 <br><br> 6. a) 30398 <br> 6. b) 30400 <br> 6. c) 31398 <br> 6. d) 31400 <br> 6. e) 32398 <br> 6. f) 32400 | 1.  Bureau à distance vers la machine virtuelle des services Cloud <br><br> 2.  Composant de compte de stockage de la configuration des diagnostics privés <br><br> 3.  portail Azure <br><br> 4. Explorateur de serveurs - stockage Azure  &#42;  est le compte de stockage nommé par l’utilisateur  <br><br> 5.  Liens permettant d’ouvrir le portail &#47; Télécharger le certificat d’abonnement &#47; Publier le fichier de paramètres <br><br>6. a)  Port local du connecteur pour le débogage à distance pour le service de cloud et la machine virtuelle<br> 6. b)  Port public du connecteur pour le débogage à distance pour le service de cloud et la machine virtuelle <br> 6. c)  Port local redirecteur pour le débogage à distance pour le service de cloud et la machine virtuelle <br> 6. d) Port public redirecteur pour le débogage à distance pour le service de cloud et la machine virtuelle  <br> 6. e) Port local chargeur de fichiers pour le débogage à distance pour le service de cloud et la machine virtuelle <br> 6. f) Port public chargeur de fichiers pour le débogage à distance pour le service de cloud et la machine virtuelle |
| Service Fabric | 1. <br>ocs.Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | https | 443 | 1. Documentation <br><br> 2. Créer la fonctionnalité de cluster <br><br>3. Le &#42; est le nom du coffre de clés Azure (Exemple :- test11220180112110108.vault.azure.net  <br><br>  4. Le &#42 ; est dynamique (exemple : vsspsextprodch1su1.vsspsext.visualstudio.com) |
| Instantané <br>Débogueur | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;azurewebsites.net <br> 4. &#42;scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. msvsmon | 1. https <br>2. https  <br>3. http <br>4. https <br>5. https <br>6. Concord <br> | 1. 443<br> 2. 443<br>3. 80  <br>4. 443<br> 5. 443<br> 6. 4022 (dépendant de la version Visual Studio) | 1. Fichier .json de requête sur la taille de la référence (SKU) du service d’applications <br>2. Différents appels du Gestionnaire de ressources Azure <br>3. Appel de préparation de site via  <br>4. Point de terminaison Kudu du service d’application ciblé du client <br>5. Version de l’Extension de site de requête publiée dans nuget.org <br>6. Canal de débogage à distance |
|Azure Stream Analytics <br><br>HDInsight | Management.azure.com |https|443 |Permet d’afficher, soumettre, exécuter et gérer des travaux ASA <br><br> Permet de parcourir des clusters HDI et soumettre, diagnostiquer et déboguer des travaux HDI |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https | 443 | Permet de compiler, soumettre, afficher, diagnostiquer et déboguer des travaux ; utilisé pour parcourir des fichiers ADLS ; permet de charger et télécharger des fichiers |
| Service d’empaquetage | [compte].visualstudio.com <br/> [compte].*.visualstudio.com <br/> *.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https | 443 | *.npmjs.org, *.nuget.org et *.nodejs.org ne sont nécessaires que dans certains scénarios de tâches de build (par exemple, le programme d’installation d’outils de NuGet ou de Node), ou pour utiliser des flux ascendants publics. Les trois autres domaines sont requis pour les fonctionnalités de base du service de création de packages. |
| Azure DevOps Services | *.vsassets.io <br/> static2.sharepointonline.com  |  |  | Utilisé pour se connecter avec Azure DevOps Services |
|||||||

## <a name="troubleshoot-network-related-errors"></a>Résoudre les erreurs liées au réseau

Parfois, exécuté pour des erreurs liées au réseau ou au proxy lorsque vous installez ou utilisez Visual Studio derrière un pare-feu ou un serveur proxy. Pour plus d’informations sur les solutions à ces messages d’erreur, consultez la page [Dépannage des erreurs liées au réseau lorsque vous installez ou utilisez Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="get-support"></a>Obtenir de l’aide

Nous offrons une option de support par [**Conversation en direct**](https://visualstudio.microsoft.com/vs/support/#talktous) (en anglais uniquement) pour les problèmes liés à l’installation.

Voici d’autres options de support :

* Signalez-nous les problèmes au niveau d’un produit via l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) qui apparaît dans Visual Studio Installer et dans l’IDE Visual Studio.
* Faites-nous part d’une suggestion sur un produit via [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Suivez les problèmes au niveau d’un produit et trouvez des réponses dans la [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/).
* Utilisez [GitHub](https://github.com/) pour communiquer avec nous et d’autres développeurs Visual Studio en prenant part à la [conversation Visual Studio dans la communauté Gitter](https://gitter.im/Microsoft/VisualStudio).

## <a name="see-also"></a>Voir aussi

* [Créer une installation réseau de Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Résoudre les problèmes liés aux erreurs réseau dans Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)

