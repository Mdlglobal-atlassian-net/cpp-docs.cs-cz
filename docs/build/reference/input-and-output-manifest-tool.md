---
title: Nástroj manifest C++ vstupní a výstupní vlastnosti
ms.date: 08/27/2018
f1_keywords:
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.DependencyInformationFile
- VC.Project.VCManifestTool.OutputResourceManifest
- VC.Project.VCManifestTool.GenerateCatalogFiles
ms.assetid: a8bb20f6-7ace-45ca-bab0-b4f4a5caf170
ms.openlocfilehash: 1731665ffa6117896490115028b4744e195beae2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823373"
---
# <a name="input-and-output-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Vstup a výstup, Nástroj Manifest, vlastnosti konfigurace, &lt;Projectname&gt; dialogové okno stránky vlastností projektu

Pomocí tohoto dialogového můžete určit vstupní a výstupní možnosti pro [Mt.exe](/windows/desktop/SbsCs/mt-exe).

Pro přístup k této dialogové okno stránky vlastností, otevřete stránky vlastností projektu, nebo seznam vlastností. Rozbalte **Nástroj Manifest** pod uzlem **vlastnosti konfigurace**a pak vyberte **vstupní a výstupní**.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

**Další soubory manifestu**<br/>
Používá **/manifest** možnost určení úplné cesty další soubory manifestu, které budou zpracovávat nástroj manifest nebo sloučení. Úplné cesty jsou oddělené středníky.

**Manifesty vstupních prostředků**<br/>
Používá **/inputresource** lze zadat úplnou cestu k prostředku typu RT_MANIFEST vstup na nástroj manifest. Cesta může být následován ID zadaného prostředku. Příklad:

`dll_with_manifest.dll;#1`

ID prostředku je nepovinný a výchozí hodnota je CREATEPROCESS_MANIFEST_RESOURCE_ID v winuser.

**Vložit Manifest**<br/>
- **Ano** Určuje, že bude systém projektu vložit soubor manifestu aplikace do sestavení.

- **Ne** Určuje, že bude systém projektu vytvořit soubor manifestu aplikace jako samostatný soubor.

**Výstupní soubor manifestu**<br/>
Určuje název výstupního souboru manifestu. Tato vlastnost je volitelná, pokud pouze jeden soubor manifestu je provozován v nástroji manifestu.

**Soubor prostředků manifestu**<br/>
Určuje výstupní soubory prostředků použít pro vložení manifestu do výstupu projektu.

**Generovat soubory katalogů**<br/>
Používá **/makecdfs** možnost určit, že nástroj manifest bude generovat soubory definice katalogu (CDF), které se používají k zajištění katalogy.

**Generovat Manifest z ManagedAssembly**<br/>
Generuje manifest ze spravovaného sestavení. (**- managedassemblyname:**<em>souboru</em>).

**Potlačit Element závislosti**<br/>
Používá se **- managedassembly** možnost. Tato značka potlačí generování elementů závislostí v posledním manifestu.

**Generovat značky kategorií**<br/>
Používá se **- managedassembly** možnost. Tato značka způsobí, že se budou generovat značky kategorií.

**Povolit rozpoznání nastavení dpi**<br/>
Určuje, zda je aplikace s ohledem na DPI. Ve výchozím nastavení je **Ano** pro projekty MFC a **ne** jinak, protože pouze projekty MFC vytvořili rozpoznání nastavení dpi. Můžete přepsat nastavení **Ano** Pokud přidáte kód pro zpracování různých nastavení DPI. Vaše aplikace může zobrazit fuzzy logikou nebo malé, pokud ji nastavíte jako rozlišením DPI když není.

## <a name="see-also"></a>Viz také:

[ClickOnce – manifest aplikace ](/visualstudio/deployment/clickonce-application-manifest)<br/>
[Stránky vlastností nástroje manifest](manifest-tool-property-pages.md)<br/>
[Nastavení kompilátoru jazyka C++ a vlastnosti v sadě Visual Studio sestavení](../working-with-project-properties.md)<br/>