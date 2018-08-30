---
title: Upřesnit, Nástroj Manifest, vlastnosti konfigurace, &lt;Projectname&gt; dialogové okno stránky vlastností projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.KeyFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- VC.Project.VCManifestTool.ValidateSignature
- VC.Project.VCManifestTool.KeyContainer
dev_langs:
- C++
ms.assetid: 3d587366-05ea-4956-a978-313069660735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b12c53f2793f7ac083ca06143be18aa6234f1de
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201581"
---
# <a name="advanced-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Upřesnit, Nástroj Manifest, vlastnosti konfigurace, &lt;Projectname&gt; dialogové okno stránky vlastností projektu
Umožňuje určit rozšířené možnosti pro toto dialogové okno [Mt.exe](https://msdn.microsoft.com/library/aa375649).  
  
 Pro přístup k této dialogové okno stránky vlastností, otevřete stránky vlastností projektu, nebo seznam vlastností. Rozbalte **Nástroj Manifest** pod uzlem **vlastnosti konfigurace**a pak vyberte **Upřesnit**.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Aktualizovat hodnoty hash souborů**  
 Používá k určení, že nástroj manifest vypočítá hodnoty hash souborů zadaných v hashupdate `<file>` elementy a aktualizujete-the-hash atributy s vypočtená hodnota.  
  
 **Aktualizovat cestu hledání hodnoty hash souboru**  
 Určuje cestu hledání pro soubory, které jsou odkazovány v `<file>` elementy. Tato možnost také používá hashupdate.  
  
## <a name="see-also"></a>Viz také  
 [\<Soubor > – Element](/visualstudio/deployment/file-element-clickonce-application)   
 [ClickOnce – Manifest aplikace](/visualstudio/deployment/clickonce-application-manifest)   
 [Stránky vlastností nástroje manifest](../ide/manifest-tool-property-pages.md)   
 [Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)   