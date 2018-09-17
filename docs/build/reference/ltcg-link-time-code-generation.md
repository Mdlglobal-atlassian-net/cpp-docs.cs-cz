---
title: / LTCG (generování kódu při propojování) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
dev_langs:
- C++
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e60bb086adbb1c573b21cafb54c61203c888e9a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725164"
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (vytváření kódu v době propojování)

Použití **parametru/LTCG** provádět optimalizaci celého programu, nebo k vytvoření instrumentace optimalizace na základě profilu (PGO), proveďte školení a vytvořit na základě profilu optimalizovat sestavení.

## <a name="syntax"></a>Syntaxe

> **/ LTCG**[**:**{**PŘÍRŮSTKOVÉ**|**NOSTATUS**|**STAV** | **OFF**}]<br/>

Tyto možnosti jsou zastaralé od verze Visual Studio 2015:

> **/ LTCG:**{**PGINSTRUMENT**|**PGOPTIMIZE**|**PGUPDATE**}<br/>

### <a name="arguments"></a>Arguments

**PŘÍRŮSTKOVÉ**<br/>
(Volitelné) Určuje, zda linker pouze vztahuje celého programu optimalizace nebo propojování generování kódu (LTCG) do sady souborů, které jsou ovlivněny editací namísto celého projektu. Ve výchozím nastavení, není tento příznak nastaven při **parametru/LTCG** není zadán, a celý projekt je spojen s použitím optimalizace celého programu.

**NOSTATUS** &AMP;#124; **STAV**<br/>
(Volitelné) Určuje, zda linker zobrazí indikátor průběhu, který ukazuje, jaké je procento odkazu je dokončena. Ve výchozím nastavení nezobrazí tato informace o stavu.

**VYPNOUT**<br/>
(Volitelné) Zakáže generování kódu při propojování. Toto chování je stejné jako při **parametru/LTCG** není zadán v příkazovém řádku.

**PGINSTRUMENT**<br/>
(Volitelné) Tato možnost je zastaralé od verze Visual Studio 2015. Místo toho použijte **parametru/LTCG** a [/genprofile nebo /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) ke generování instrumentované sestavení pro optimalizace na základě profilu. Data, která se shromažďují ze spuštění instrumentované slouží k vytvoření optimalizované bitové kopie. Další informace najdete v tématu [optimalizace na základě profilu](profile-guided-optimizations.md). Je zkratka pro tuto možnost **/LTCG:PGI**.

**PGOPTIMIZE**<br/>
(Volitelné) Tato možnost je zastaralé od verze Visual Studio 2015. Místo toho použijte **parametru/LTCG** a [/useprofile](useprofile.md) k vytvoření optimalizované bitové kopie. Další informace najdete v tématu [optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md). Je zkratka pro tuto možnost **/LTCG:PGO**.

**PGUPDATE**<br/>
(Volitelné) Tato možnost je zastaralé od verze Visual Studio 2015. Místo toho použijte **parametru/LTCG** a **/useprofile** optimalizovanou bitovou kopii znovu sestavit. Další informace najdete v tématu [optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md). Je zkratka pro tuto možnost **/LTCG:PGU**.

## <a name="remarks"></a>Poznámky

**Parametru/LTCG** přikazuje linkeru, volání kompilátoru a provádět optimalizaci celého programu. Můžete také provést profilově řízené optimalizace. Další informace najdete v tématu [optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md).

S následujícími výjimkami, nelze přidat možnosti linkeru pro PGO kombinací **parametru/LTCG** a **/useprofile** , který není zadané v předchozím PGO inicializace kombinace  **/ LTCG** a **/genprofile** možnosti:

- [/ BASE](../../build/reference/base-base-address.md)

- [/ FIXED](../../build/reference/fixed-fixed-base-address.md)

- **/LTCG**

- [/MAP](../../build/reference/map-generate-mapfile.md)

- [/ MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)

- [/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)

- [/ OUT](../../build/reference/out-output-file-name.md)

- [/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)

- [/PDB](../../build/reference/pdb-use-program-database.md)

- [/ PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)

- [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)

- [/ VERBOSE](../../build/reference/verbose-print-progress-messages.md)

Všechny možnosti linkeru, které jsou zadány společně s **parametru/LTCG** a **/genprofile** není potřeba zadat při sestavení s použitím možnosti, jak inicializovat PGO **parametru/LTCG** a **/Useprofile**; jsou implicitní.

Zbývající část tohoto článku popisuje **parametru/LTCG** z hlediska generování kódu při propojování.

**/ LTCG** je vyjádřena pomocí [/GL](../../build/reference/gl-whole-program-optimization.md).

Linker vyvolá generování kódu při propojování, je-li předán modulu, který byl zkompilován pomocí **/GL** nebo modul MSIL (viz [soubory .netmodule jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md)). Pokud explicitně neurčíte **parametru/LTCG** při předání **/GL** nebo moduly jazyka MSIL do linkeru, linker nakonec to zjistí a restartuje propojení s použitím **parametru/LTCG**. Explicitně zadat **parametru/LTCG** při předání **/GL** a výkon sestavení jazyka MSIL moduly linkeru pro nejrychlejší možné.

Pro ještě rychlejší výkon použijte **parametru/LTCG: PŘÍRŮSTKOVÉ**. Tato možnost přikazuje linkeru, aby pouze znovu optimalizovat sadu souborů, které jsou ovlivněny změnu zdrojového souboru, namísto celého projektu. To může výrazně zkrátit čas odkaz vyžaduje. Nejedná se o stejné možnosti jako přírůstkové propojení.

**/ LTCG** není platná pro použití s [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md).

Když **parametru/LTCG** slouží k propojení modulech zkompilovaných pomocí [/og](../../build/reference/og-global-optimizations.md), [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), nebo [/Ox](../../build/reference/ox-full-optimization.md), jsou prováděny následující optimalizace:

- Vkládání napříč moduly

- Přidělení registru meziprocedurální (pouze 64bitové operační systémy)

- Vlastní konvence volání (pouze x86)

- Malé TLS posunutí (pouze x86)

- Zásobník double zarovnání (pouze x86)

- Odstraňování mnohoznačnosti paměti (lepší informace o rušení globální proměnné a vstupní parametry.)

> [!NOTE]
> Linker zjistí optimalizace, které se používaly pro každou funkci zkompilovat a platí stejné optimalizace v době spojení.

Pomocí **parametru/LTCG** a **/Ogt** způsobí, že optimalizace zarovnání double.

Pokud **parametru/LTCG** a **/Ogs** nejsou zadány, double zarovnání se neprovádí. Pokud se většina funkcí v aplikaci zkompiluje pro vyšší rychlost, s několika funkce zkompilované pro velikost (například pomocí [optimalizovat](../../preprocessor/optimize.md) – Direktiva pragma), kompilátor double – zarovná funkce, které jsou optimalizované pro velikost, pokud volání Funkce, které vyžadují dvojité zarovnání.

Pokud kompilátor může identifikovat všechny servery volání funkce, kompilátor ignoruje explicitní modifikátorů konvence volání funkce a pokusí se optimalizovat konvence volání funkce:

- předání parametrů do registrů

- Změna pořadí parametrů pro zarovnání

- odebrání nepoužitých parametrů

Pokud funkce je volána pomocí ukazatele na funkci nebo funkce je volána z mimo modul, který je zkompilován s použitím **/GL**, kompilátor nebude pokoušet o optimalizaci konvence volání funkce.

> [!NOTE]
> Pokud používáte **parametru/LTCG** a znovu definovat `mainCRTStartup`, vaše aplikace může mít nepředvídatelné chování, které se týkají uživatelský kód, který je spuštěn před globální objekty jsou inicializovány. Existují tři způsoby, jak tento problém vyřešit: atributy nemění `mainCRTStartup`, nejde zkompilovat soubor, který obsahuje `mainCRTStartup` pomocí **parametru/LTCG**, nebo staticky inicializovat globální proměnné a objekty.

### <a name="ltcg-and-msil-modules"></a>/ LTCG a jazyk MSIL moduly

Moduly, které jsou kompilovány pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) a [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) lze použít jako vstup do linkeru při **parametru/LTCG** určena.

- **/ LTCG** může přijmout nativní objekt soubory a soubory smíšené nativního/spravovaného objektu (zkompilován s použitím **/CLR**). **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

- **/LTCG:PGI** nepřijímá nativní moduly, které jsou kompilovány pomocí **/GL** a   **/CLR**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Zobrazit [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Obecné** stránku vlastností.

1. Upravit **optimalizace celého programu** vlastnost.

Můžete také použít **parametru/LTCG** konkrétní sestavení výběrem **sestavení** > **optimalizace na základě profilu** na řádku nabídek nebo výběrem jedné z profilu Na základě možnosti optimalizace na místní nabídku pro projekt.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.

## <a name="see-also"></a>Viz také:

- [Nastavení možností linkeru](../../build/reference/setting-linker-options.md)
- [Možnosti linkeru](../../build/reference/linker-options.md)
