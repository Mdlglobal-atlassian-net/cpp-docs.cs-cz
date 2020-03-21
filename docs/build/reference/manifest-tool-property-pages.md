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
ms.openlocfilehash: 20ca118b3aacb02333d49b67d13de30f11dc5d8d
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079502"
---
# <a name="manifest-tool-property-pages"></a>Stránky vlastností nástroje manifest

Pomocí těchto stránek můžete zadat obecné možnosti pro [Mt. exe](/windows/win32/sbscs/mt-exe). Tyto stránky se nacházejí v části **vlastnosti** **projektu** >  > **Vlastnosti konfigurace** > **Nástroj manifest**.

## <a name="general-property-page"></a>Obecná stránka vlastností

### <a name="suppress-startup-banner"></a>Potlačit úvodní nápis

   **Ano (/nologo)** určuje, že při spuštění nástroje manifest budou skryta standardní data copyrightu Microsoftu. Tuto možnost použijte, pokud chcete potlačit nechtěné výstupy v souborech protokolu, když spustíte Mt. exe jako součást procesu sestavení nebo z prostředí sestavení.

### <a name="verbose-output"></a>Podrobný výstup

   **Yes (/verbose)** určuje, že se během generování manifestu budou zobrazovat další informace o sestavení.

### <a name="assembly-identity"></a>Identita sestavení * *

Používá možnost/identity k určení řetězce identity, který obsahuje atributy pro [> prvek\<assemblyIdentity](/visualstudio/deployment/assemblyidentity-element-clickonce-application). Řetězec identity začíná hodnotou atributu `name` a za ním následuje dvojice *atributů* = *hodnota* . Atributy v řetězci identity jsou odděleny čárkou.

Toto je příklad řetězce identity: `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="input-and-output-property-page"></a>Vstupní a výstupní stránka vlastností

###  <a name="additional-manifest-files"></a>Další soubory manifestu

Používá možnost **/manifest** k určení úplných cest dalších souborů manifestu, které nástroj manifest zpracuje nebo sloučí. Úplné cesty jsou odděleny středníkem. (-manifest [manifest1] [manifest2]...)

###  <a name="input-resource-manifests"></a>Manifesty vstupních prostředků

Používá možnost **/inputresource** k určení úplné cesty prostředku typu RT_MANIFEST pro vstup do nástroje manifest. Za cestou může následovat zadané ID prostředku. Příklad:

`dll_with_manifest.dll;#1`

###  <a name="embed-manifest"></a>Vložit manifest

- Hodnota **Ano** určuje, že systém projektu bude do sestavení vkládat soubor manifestu aplikace.

- **Ne** určuje, že systém projektu vytvoří soubor manifestu aplikace jako samostatný soubor.

###  <a name="output-manifest-file"></a>Výstupní soubor manifestu

Určuje název výstupního souboru manifestu. Tato vlastnost je volitelná, pokud nástroj manifest pracuje pouze s jedním souborem manifestu. (-out: [soubor]; # [ID prostředku])

###  <a name="manifest-resource-file"></a>Soubor prostředků manifestu

Určuje výstupní soubor prostředků, který se používá k vložení manifestu do výstupu projektu.

###  <a name="generate-catalog-files"></a>Generovat soubory katalogu

Pomocí možnosti **/makecdfs** určíte, že nástroj manifest vygeneruje soubory definic katalogu (soubory. CDF), které se použijí k vytváření katalogů. /makecdfs

###  <a name="generate-manifest-from-managedassembly"></a>Generovat Manifest z ManagedAssembly

Generuje manifest ze spravovaného sestavení. (-managedassemblyname: [soubor])

###  <a name="suppress-dependency-element"></a>Potlačit element závislosti

Používá se s-managedassembly. potlačí generování prvků závislosti v konečném manifestu. (-nezávislá)

###  <a name="generate-category-tags"></a>Generovat značky kategorií

Používá se s-managedassembly. – kategorie způsobí vygenerování značek kategorií. (-Category)

###  <a name="dpi-awareness"></a>Sledování DPI

Určuje, zda je aplikace zohledňující rozlišení DPI. Ve výchozím nastavení je nastavení **Ano** pro projekty knihovny MFC a **žádné** jiné, protože v rámci sledování dpi byly vytvořeny pouze projekty knihovny MFC. Pokud přidáte kód pro zpracování různých nastavení DPI, můžete toto nastavení přepsat na **Ano** . Pokud se vaše aplikace nastaví jako DPI, může se zdát, že se tato aplikace zobrazuje v přibližné nebo malé.

**Vlastnit**

- **NTato**
- **Vysoká úroveň DPI**
- **Pro monitor s vysokým rozlišením DPI**

## <a name="isolated-com-property-page"></a>Izolovaná stránka vlastností COM

Další informace o izolovaném modelu COM naleznete v tématu [izolované aplikace](/windows/win32/SbsCs/isolated-applications) a [Postupy: sestavování izolovaných aplikací pro využívání komponent modelu COM](../how-to-build-isolated-applications-to-consume-com-components.md).

###  <a name="type-library-file"></a>Soubor knihovny typů

Určuje knihovnu typů, která se má použít pro podporu manifestu RegFree COM. (-TLB: [soubor])

###  <a name="registrar-script-file"></a>Soubor skriptu registrátora

Určuje soubor skriptu registrátoru, který se má použít pro podporu manifestu RegFree COM. (-RGS: [soubor])

###  <a name="component-file-name"></a>Název souboru komponenty

Určuje název souboru součásti, která je sestavena z určeného. tlb nebo. rgs. (-DLL: [soubor])

###  <a name="replacements-file"></a>Soubor nahrazení

Určuje soubor, který obsahuje hodnoty pro nahraditelné řetězce v souboru RGS. (nahrazení: [soubor])

## <a name="advanced-property-page"></a>Upřesnit stránku vlastností

###  <a name="update-file-hashes"></a>Aktualizovat hodnoty hash souborů

Vypočítá hodnotu hash souborů specifikovaných v prvcích souboru a aktualizuje atribut hash touto hodnotou. (hashupdate: [cesta])

###  <a name="update-file-hashes-search-path"></a>Aktualizovat cestu pro hledání hodnot hash souborů

Určuje cestu hledání, která se má použít při aktualizaci hodnot hash souborů.

###  <a name="additional-options"></a>Další možnosti

Další možnosti

## <a name="see-also"></a>Viz také

[C++odkaz na stránku vlastností projektu](property-pages-visual-cpp.md)
