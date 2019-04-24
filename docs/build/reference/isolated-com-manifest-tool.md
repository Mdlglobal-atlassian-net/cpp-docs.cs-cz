---
title: Nástroj manifest izolované modely COM vlastnosti
ms.date: 12/10/2018
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
ms.openlocfilehash: 2fda169ecf304373d27d699bf313bde124dc399f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269710"
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Izolované modely COM, Nástroj Manifest, vlastnosti konfigurace, &lt;Projectname&gt; dialogové okno stránky vlastností projektu

Použít toto dialogové okno k zadání **izolovaná komponenta COM** možnosti pro [Mt.exe](https://msdn.microsoft.com/library/aa375649).

Pro přístup k této dialogové okno stránky vlastností, otevřete stránky vlastností projektu, nebo seznam vlastností. Rozbalte **Nástroj Manifest** pod uzlem **společné vlastnosti**a pak vyberte **izolovaná komponenta COM**.

## <a name="task-list"></a>Seznam úkolů

- [Postupy: Sestavení izolovaných aplikací pro zpracování součástí modelu COM](../how-to-build-isolated-applications-to-consume-com-components.md)

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Soubor knihovny typů**

   Pomocí možnosti/tlb lze zadat název souboru knihovny typů (souboru .tlb), který nástroj manifest použije k vygenerování souboru manifestu.

- **Soubor skriptu registrátoru**

   Rgs používá k určení názvu soubor skriptu registrátoru (souboru .rgs), nástroj manifest použije k vygenerování souboru manifestu.

- **Název souboru komponenty**

   Možnost/DLL používá k určení názvu prostředku, který vygeneruje nástroj manifest. Musíte zadat hodnotu pro tuto vlastnost při hodnoty pro buď **soubor knihovny typů** nebo **soubor skriptu registrátoru** jsou uvedeny.

- **Soubor náhrad**

   Pomocí replacements Určuje úplnou cestu k souboru, který obsahuje hodnoty pro nahraditelné řetězce v souboru .rgs.

## <a name="see-also"></a>Viz také:

[Izolované aplikace](/windows/desktop/SbsCs/isolated-applications)<br>
[ClickOnce – manifest aplikace ](/visualstudio/deployment/clickonce-application-manifest)<br>
[Stránky vlastností nástroje manifest](manifest-tool-property-pages.md)<br>
[Nastavení vlastností kompilátoru a sestavení C++ v sadě Visual Studio](../working-with-project-properties.md)
