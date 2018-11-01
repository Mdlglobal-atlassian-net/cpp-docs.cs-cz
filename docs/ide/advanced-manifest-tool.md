---
title: Upřesnit, Nástroj Manifest, vlastnosti konfigurace, &lt;Projectname&gt; dialogové okno stránky vlastností projektu
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCManifestTool.KeyFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- VC.Project.VCManifestTool.ValidateSignature
- VC.Project.VCManifestTool.KeyContainer
ms.assetid: 3d587366-05ea-4956-a978-313069660735
ms.openlocfilehash: 10da66c690106255d34c82b066f3450c5cc8a37a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530556"
---
# <a name="advanced-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Upřesnit, Nástroj Manifest, vlastnosti konfigurace, &lt;Projectname&gt; dialogové okno stránky vlastností projektu

Umožňuje určit rozšířené možnosti pro toto dialogové okno [Mt.exe](https://msdn.microsoft.com/library/aa375649).

Pro přístup k této dialogové okno stránky vlastností, otevřete stránky vlastností projektu, nebo seznam vlastností. Rozbalte **Nástroj Manifest** pod uzlem **vlastnosti konfigurace**a pak vyberte **Upřesnit**.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Aktualizovat hodnoty hash souborů**

   Používá k určení, že nástroj manifest vypočítá hodnoty hash souborů zadaných v hashupdate `<file>` elementy a aktualizujete-the-hash atributy s vypočtená hodnota.

- **Aktualizovat cestu hledání hodnoty hash souboru**

   Určuje cestu hledání pro soubory, které jsou odkazovány v `<file>` elementy. Tato možnost také používá hashupdate.

## <a name="see-also"></a>Viz také

[\<Soubor > – Element](/visualstudio/deployment/file-element-clickonce-application)<br>
[ClickOnce – manifest aplikace ](/visualstudio/deployment/clickonce-application-manifest)<br>
[Stránky vlastností nástroje manifest](../ide/manifest-tool-property-pages.md)<br>
[Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)