---
title: Stránky vlastností nástroje manifest
ms.date: 07/24/2019
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.GenerateCatalogFiles
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.ReplacementsFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- vc.project.AdditionalOptionsPage
ms.assetid: f33499c4-7733-42d9-80e3-8a5018786965
ms.openlocfilehash: e1d0f1ac889cb915216ceb70d48e36efe4ad21bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336300"
---
# <a name="manifest-tool-property-pages"></a>Stránky vlastností nástroje manifest

Tyto stránky slouží k určení obecných možností pro [mt.exe](/windows/win32/sbscs/mt-exe). Tyto stránky se nacházejí v části Nástroj**Properties** > **manifestvlastností** > **Manifest Tool**konfigurace **projektu** > .

## <a name="general-property-page"></a>Stránka obecné vlastnosti

### <a name="suppress-startup-banner"></a>Potlačit spouštěcí banner

   **Ano (/nologo)** určuje, že při spuštění nástroje manifestu budou skryta standardní data společnosti Microsoft o autorských právech. Tuto možnost použijte k potlačení nežádoucího výstupu v souborech protokolu, když spustíte mt.exe jako součást procesu sestavení nebo z prostředí sestavení.

### <a name="verbose-output"></a>Podrobný výstup

   **Ano (/podrobné)** určuje, že další informace o sestavení se zobrazí během generování manifestu.

### <a name="assembly-identity"></a>Identita sestavení

Používá možnost /identity k určení řetězce identity, který obsahuje atributy [ \<pro element> identity identity sestavení](/visualstudio/deployment/assemblyidentity-element-clickonce-application). Řetězec identity začíná `name` hodnotou atributu a následuje dvojice hodnot *atributu.* = *value* Atributy v řetězci identity jsou odděleny čárkou.

Toto je příklad řetězce identity:`Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="input-and-output-property-page"></a>Stránka vstupní a výstupní vlastnosti

### <a name="additional-manifest-files"></a>Další soubory manifestu

Používá **možnost /manifest** k určení úplných cest dalších souborů manifestu, které nástroj manifestu zpracuje nebo sloučí. Úplné cesty jsou odděleny středníkem. (-manifest [manifest1] [manifest2] ...)

### <a name="input-resource-manifests"></a>Manifesty vstupních prostředků

Používá **možnost /inputresource** k určení úplné cesty prostředku typu RT_MANIFEST, k zadání do nástroje manifestu. Za cestou může následovat zadané ID prostředku. Příklad:

`dll_with_manifest.dll;#1`

### <a name="embed-manifest"></a>Vložit manifest

- **Ano** určuje, že systém projektu vloží soubor manifestu aplikace do sestavení.

- **No** určuje, že systém projektu vytvoří soubor manifestu aplikace jako samostatný soubor.

### <a name="output-manifest-file"></a>Výstupní soubor manifestu

Určuje název výstupního souboru manifestu. Tato vlastnost je volitelná, pokud je nástrojem manifestu provozován pouze jeden soubor manifestu. (-out:[soubor];#[ID prostředku])

### <a name="manifest-resource-file"></a>Soubor prostředků manifestu

Určuje soubor výstupních prostředků použitý k vložení manifestu do výstupu projektu.

### <a name="generate-catalog-files"></a>Generovat soubory katalogu

Pomocí možnosti **/makecdfs** určíte, že nástroj manifestu bude generovat definiční soubory katalogu (soubory CDF), které se používají k vytváření katalogů. (/makecdfs)

### <a name="generate-manifest-from-managedassembly"></a>Generovat manifest ze spravované sestavy

Generuje manifest ze spravovaného sestavení. (-managedassemblyname:\[file])

### <a name="suppress-dependency-element"></a>Potlačit prvek závislosti

Používá se s -managedassembly. potlačí generování prvků závislostí v konečném manifestu. (-nodependency)

### <a name="generate-category-tags"></a>Generovat značky kategorií

Používá se s -managedassembly. -category způsobí, že značky kategorií budou generovány. (kategorie)

### <a name="dpi-awareness"></a>Povědomí o DPI

Určuje, zda je aplikace podporující DPI. Ve výchozím nastavení je nastavení **Ano** pro projekty knihovny MFC a **ne** jinak, protože pouze projekty knihovny MFC mají vytvořené v povědomí O DPI. Pokud přidáte kód pro zpracování různých nastavení DPI, můžete toto nastavení přepsat na **Ano.** Aplikace může vypadat přibližné nebo malé, pokud ji nastavíte jako DPI vědomi, pokud není.

**Choices**

- **Žádné**
- **Vysoká DPI vědomá**
- **Na monitor si je vědoma vysokého dpi**

## <a name="isolated-com-property-page"></a>Stránka vlastností izolovaného com

Další informace o izolovaném modelu COM naleznete v [tématu Izolované aplikace](/windows/win32/SbsCs/isolated-applications) a [postup: Sestavení izolovaných aplikací ke spotřebování komponent modelu COM](../how-to-build-isolated-applications-to-consume-com-components.md).

### <a name="type-library-file"></a>Soubor knihovny typů

Určuje knihovnu typů, která má být používána pro podporu manifestu com bez regfree. (-tlb:[soubor])

### <a name="registrar-script-file"></a>Soubor skriptu registrátora

Určuje soubor skriptu registrátora, který má být používán pro podporu manifestů com bez regfree. (-rgs:[soubor])

### <a name="component-file-name"></a>Název souboru komponenty

Určuje název souboru součásti, která je vytvořena ze zadaného souboru .tlb nebo RGS. (-dll:[soubor])

### <a name="replacements-file"></a>Soubor nahrazení

Určuje soubor, který obsahuje hodnoty nahraditelných řetězců v souboru RGS. (náhrady:[soubor])

## <a name="advanced-property-page"></a>Stránka rozšířené vlastnosti

### <a name="update-file-hashes"></a>Aktualizovat hashe souboru

Vypočítá hodnotu hash souborů zadanou v elementech souboru a aktualizuje atribut hash touto hodnotou. (hashupdate:[cesta])

### <a name="update-file-hashes-search-path"></a>Aktualizovat cestu hledání hashesouborů

Určuje cestu hledání, která má být používána při aktualizaci hashe souborů.

### <a name="additional-options"></a>Další možnosti

Další možnosti

## <a name="see-also"></a>Viz také

[Odkaz na stránku vlastnosti projektu jazyka C++](property-pages-visual-cpp.md)
