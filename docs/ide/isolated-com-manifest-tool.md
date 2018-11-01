---
title: Nástroj manifest izolované modely COM vlastnosti (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
ms.openlocfilehash: 9eea3b2765bad6bd08cc9ee91a801e2b891511e5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546514"
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Izolované modely COM, Nástroj Manifest, vlastnosti konfigurace, &lt;Projectname&gt; dialogové okno stránky vlastností projektu

Použít toto dialogové okno k zadání **izolovaná komponenta COM** možnosti pro [Mt.exe](https://msdn.microsoft.com/library/aa375649).

Pro přístup k této dialogové okno stránky vlastností, otevřete stránky vlastností projektu, nebo seznam vlastností. Rozbalte **Nástroj Manifest** pod uzlem **společné vlastnosti**a pak vyberte **izolovaná komponenta COM**.

## <a name="task-list"></a>Seznam úloh

- [Postupy: Sestavení izolovaných aplikací pro zpracování součástí modelu COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Soubor knihovny typů**

   Pomocí možnosti/tlb lze zadat název souboru knihovny typů (souboru .tlb), který nástroj manifest použije k vygenerování souboru manifestu.

- **Soubor skriptu registrátoru**

   Rgs používá k určení názvu soubor skriptu registrátoru (souboru .rgs), nástroj manifest použije k vygenerování souboru manifestu.

- **Název souboru komponenty**

   Možnost/DLL používá k určení názvu prostředku, který vygeneruje nástroj manifest. Musíte zadat hodnotu pro tuto vlastnost při hodnoty pro buď **soubor knihovny typů** nebo **soubor skriptu registrátoru** jsou uvedeny.

- **Soubor náhrad**

   Pomocí replacements Určuje úplnou cestu k souboru, který obsahuje hodnoty pro nahraditelné řetězce v souboru .rgs.

## <a name="see-also"></a>Viz také

[Izolované aplikace](/windows/desktop/SbsCs/isolated-applications)<br>
[ClickOnce – manifest aplikace ](/visualstudio/deployment/clickonce-application-manifest)<br>
[Stránky vlastností nástroje manifest](../ide/manifest-tool-property-pages.md)<br>
[Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)