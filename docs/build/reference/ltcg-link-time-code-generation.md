---
title: /LTCG (vytváření kódu v době propojování)
ms.date: 05/16/2019
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
ms.openlocfilehash: a8f13c32593d1cfef690d63d506faf14490de02d
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837271"
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (vytváření kódu v době propojování)

Použití **parametru/LTCG** provádět optimalizaci celého programu, nebo k vytvoření instrumentace optimalizace na základě profilu (PGO), proveďte školení a vytvořit na základě profilu optimalizovat sestavení.

## <a name="syntax"></a>Syntaxe

> **/LTCG**[**:**{**INCREMENTAL**|**NOSTATUS**|**STATUS**|**OFF**}]<br/>

Tyto možnosti jsou zastaralé od verze Visual Studio 2015:

> **/ LTCG:**{**PGINSTRUMENT**|**PGOPTIMIZE**|**PGUPDATE**}<br/>

### <a name="arguments"></a>Arguments

**PŘÍRŮSTKOVÉ**<br/>
(Volitelné) Určuje, zda linker pouze vztahuje celého programu optimalizace nebo propojování generování kódu (LTCG) do sady souborů, které jsou ovlivněny editací namísto celého projektu. Ve výchozím nastavení, není tento příznak nastaven při **parametru/LTCG** není zadán, a celý projekt je spojen s použitím optimalizace celého programu.

**NOSTATUS** &AMP;#124; **STAV**<br/>
(Volitelné) Určuje, zda linker zobrazí indikátor průběhu, který ukazuje, jaké je procento odkazu je dokončena. Ve výchozím nastavení nezobrazí tato informace o stavu.

**OFF**<br/>
(Volitelné) Zakáže generování kódu při propojování. Toto chování je stejné jako při **parametru/LTCG** není zadán v příkazovém řádku.

**PGINSTRUMENT**<br/>
(Volitelné) Tato možnost je zastaralé od verze Visual Studio 2015. Místo toho použijte **parametru/LTCG** a [/genprofile nebo /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) ke generování instrumentované sestavení pro optimalizace na základě profilu. Data, která se shromažďují ze spuštění instrumentované slouží k vytvoření optimalizované bitové kopie. Další informace najdete v tématu [Profile-Guided optimalizace](../profile-guided-optimizations.md). Je zkratka pro tuto možnost **/LTCG:PGI**.

**PGOPTIMIZE**<br/>
(Volitelné) Tato možnost je zastaralé od verze Visual Studio 2015. Místo toho použijte **parametru/LTCG** a [/useprofile](useprofile.md) k vytvoření optimalizované bitové kopie. Další informace najdete v tématu [Profile-Guided optimalizace](../profile-guided-optimizations.md). Je zkratka pro tuto možnost **/LTCG:PGO**.

**PGUPDATE**<br/>
(Volitelné) Tato možnost je zastaralé od verze Visual Studio 2015. Místo toho použijte **parametru/LTCG** a **/useprofile** optimalizovanou bitovou kopii znovu sestavit. Další informace najdete v tématu [Profile-Guided optimalizace](../profile-guided-optimizations.md). Je zkratka pro tuto možnost **/LTCG:PGU**.

## <a name="remarks"></a>Poznámky

**Parametru/LTCG** přikazuje linkeru, volání kompilátoru a provádět optimalizaci celého programu. Můžete také provést profilově řízené optimalizace. Další informace najdete v tématu [Profile-Guided optimalizace](../profile-guided-optimizations.md).

S následujícími výjimkami, nelze přidat možnosti linkeru pro PGO kombinací **parametru/LTCG** a **/useprofile** , který není zadané v předchozím PGO inicializace kombinace  **/ LTCG** a **/genprofile** možnosti:

- [/ BASE](base-base-address.md)

- [/ FIXED](fixed-fixed-base-address.md)

- **/LTCG**

- [/MAP](map-generate-mapfile.md)

- [/MAPINFO](mapinfo-include-information-in-mapfile.md)

- [/NOLOGO](nologo-suppress-startup-banner-linker.md)

- [/ OUT](out-output-file-name.md)

- [/PGD](pgd-specify-database-for-profile-guided-optimizations.md)

- [/PDB](pdb-use-program-database.md)

- [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)

- [/STUB](stub-ms-dos-stub-file-name.md)

- [/ VERBOSE](verbose-print-progress-messages.md)

Všechny možnosti linkeru, které jsou zadány společně s **parametru/LTCG** a **/genprofile** není potřeba zadat při sestavení s použitím možnosti, jak inicializovat PGO **parametru/LTCG** a **/Useprofile**; jsou implicitní.

Zbývající část tohoto článku popisuje **parametru/LTCG** z hlediska generování kódu při propojování.

**/ LTCG** je vyjádřena pomocí [/GL](gl-whole-program-optimization.md).

Linker vyvolá generování kódu při propojování, je-li předán modulu, který byl zkompilován pomocí **/GL** nebo modul MSIL (viz [soubory .netmodule jako vstup Linkeru](netmodule-files-as-linker-input.md)). Pokud explicitně neurčíte **parametru/LTCG** při předání **/GL** nebo moduly jazyka MSIL do linkeru, linker nakonec to zjistí a restartuje propojení s použitím **parametru/LTCG**. Explicitně zadat **parametru/LTCG** při předání **/GL** a výkon sestavení jazyka MSIL moduly linkeru pro nejrychlejší možné.

Pro ještě rychlejší výkon použijte **parametru/LTCG: PŘÍRŮSTKOVÉ**. Tato možnost přikazuje linkeru, aby pouze znovu optimalizovat sadu souborů, které jsou ovlivněny změnu zdrojového souboru, namísto celého projektu. To může výrazně zkrátit čas odkaz vyžaduje. Nejedná se o stejné možnosti jako přírůstkové propojení.

**/ LTCG** není platná pro použití s [/INCREMENTAL](incremental-link-incrementally.md).

Když **parametru/LTCG** slouží k propojení modulech zkompilovaných pomocí [/og](og-global-optimizations.md), [/O1](o1-o2-minimize-size-maximize-speed.md), [/O2](o1-o2-minimize-size-maximize-speed.md), nebo [/Ox](ox-full-optimization.md), jsou prováděny následující optimalizace:

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

Moduly, které jsou kompilovány pomocí [/GL](gl-whole-program-optimization.md) a [/CLR](clr-common-language-runtime-compilation.md) lze použít jako vstup do linkeru při **parametru/LTCG** určena.

- **/ LTCG** může přijmout nativní objekt soubory a soubory smíšené nativního/spravovaného objektu (zkompilován s použitím **/CLR**). **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v sadě Visual Studio 2017 a novější.

- **/LTCG:PGI** nepřijímá nativní moduly, které jsou kompilovány pomocí **/GL** a   **/CLR**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Zobrazit [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Obecné** stránku vlastností.

1. Upravit **optimalizace celého programu** vlastnost.

Můžete také použít **parametru/LTCG** konkrétní sestavení výběrem **sestavení** > **optimalizace na základě profilu** na řádku nabídek nebo výběrem jedné z profilu Na základě možnosti optimalizace na místní nabídku pro projekt.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.

## <a name="see-also"></a>Viz také:

- [Referenční zdroje k linkeru MSVC](linking.md)
- [Možnosti linkeru MSVC](linker-options.md)
