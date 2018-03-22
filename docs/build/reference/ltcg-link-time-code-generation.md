---
title: / LTCG (vytváření kódu v době propojování) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: article
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fd40617afecd0c9be03e3676ebe5f2fb8058312a
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (vytváření kódu v době propojování)

Použití **/ltgc** k provedení optimalizace celého programu, nebo k vytvoření instrumentace optimalizace na základě profilu (PGO), proveďte školení a vytvořit na základě profilu optimalizované sestavení.

## <a name="syntax"></a>Syntaxe

> **/ LTCG**[**:**{**PŘÍRŮSTKOVÉ**|**NOSTATUS**|**STAV** | **OFF**}]<br/>

Tyto možnosti jsou zastaralé od verze sady Visual Studio 2015:

> **/LTCG:**{**PGINSTRUMENT**|**PGOPTIMIZE**|**PGUPDATE**}<br/>

### <a name="arguments"></a>Arguments

**PŘÍRŮSTKOVÉ** (volitelné)<br/>
Určuje, že linkeru do sady souborů, které jsou ovlivněné upravíte, nikoli celý projekt aplikuje jenom celého programu optimalizace nebo propojování generování kódu (LTCG). Ve výchozím nastavení, není tento příznak nastaven při **/ltgc** není zadaný, a celý projekt je propojený s použitím optimalizace celého programu.

**NOSTATUS** &#124; **stav** (volitelné)<br/>
Určuje, zda linkeru zobrazuje indikátor průběhu, který ukazuje, jaké procento odkaz je kompletní. Ve výchozím nastavení není tato informace o stavu zobrazí.

**VYPNOUT** (volitelné)<br/>
Znemožňuje generování kódu v době propojování. Toto chování je stejné jako při/ltgc není zadán v příkazovém řádku.

**PGINSTRUMENT** (volitelné)<br/>
Tato možnost je zastaralý, spouštění v sadě Visual Studio 2015. Místo toho použijte **/ltgc** a [/GENPROFILE nebo /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) ke generování instrumentovaného sestavení pro optimalizace na základě profilu. Data, která se shromažďují ze instrumentovaného spustí slouží k vytvoření image optimalizované. Další informace najdete v tématu [optimalizace na základě profilu](profile-guided-optimizations.md). Je zkratka pro tuto možnost **/LTCG:PGI**.

**PGOPTIMIZE** (volitelné)<br/>
Tato možnost je zastaralý, spouštění v sadě Visual Studio 2015. Místo toho použijte **/ltgc** a [/USEPROFILE](useprofile.md) vytvářet optimalizované bitové kopie. Další informace najdete v tématu [optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md). Je zkratka pro tuto možnost **/LTCG:PGO**.

**PGUPDATE** (volitelné)<br/>
Tato možnost je zastaralý, spouštění v sadě Visual Studio 2015. Místo toho použijte **/ltgc** a **/USEPROFILE** znovu sestavit optimalizované bitové kopie. Další informace najdete v tématu [optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md). Je zkratka pro tuto možnost **/LTCG:PGU**.

## <a name="remarks"></a>Poznámky

**/Ltgc** informuje – možnost linkeru volání do kompilátoru a provedení optimalizace celého programu. Můžete také provést optimalizace na základě profilu. Další informace najdete v tématu [optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md).

S následujícími výjimkami, nemůžete přidat možnosti linkeru kombinace PGO **/ltgc** a **/USEPROFILE** , nebyly zadány v předchozí PGO inicializace kombinace  **/ LTCG** a **/GENPROFILE** možnosti:

- [/BASE](../../build/reference/base-base-address.md)

- [/ FIXED](../../build/reference/fixed-fixed-base-address.md)

- **/LTCG**

- [/MAP](../../build/reference/map-generate-mapfile.md)

- [/ MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)

- [/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)

- [/OUT](../../build/reference/out-output-file-name.md)

- [/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)

- [/PDB](../../build/reference/pdb-use-program-database.md)

- [/PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)

- [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md)

Všechny možnosti linkeru, které jsou určené společně s **/ltgc** a **/GENPROFILE** není nutné je třeba zadat při vytváření s použitím možnosti k chybě při inicializaci PGO **/ltgc** a **/USEPROFILE**; jejich implicitní.

Zbývající část tohoto článku popisuje **/ltgc** z hlediska generování kódu v době propojování.

**/ LTCG** je implicitní s [/GL](../../build/reference/gl-whole-program-optimization.md).

Linkeru vyvolá generování kódu v době propojování, je-li předán modul, který byl kompilován s použitím **/GL** nebo modul MSIL (viz [.netmodule soubory jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md)). Pokud nezadáte explicitně **/ltgc** při předání **/GL** nebo moduly MSIL linkeru, nakonec linkeru to zjistí a restartuje odkaz pomocí **/ltgc**. Explicitně zadáte **/ltgc** při předání **/GL** a moduly MSIL linkeru pro nejrychlejší možné sestavit výkonu.

I rychlejší průběh, použijte **/ltgc: PŘÍRŮSTKOVÉ**. Tato možnost umožňuje linkeru pouze znovu optimalizace sadu souborů, která jsou ovlivněná změnu zdrojového souboru, místo celý projekt. To může výrazně snížit odkaz čas potřebný. Toto není stejná možnost jako přírůstkové propojování.

**/ LTCG** není platná pro použití s [/PŘÍRŮSTKOVÉ](../../build/reference/incremental-link-incrementally.md).

Když **/ltgc** slouží k propojení s použitím Kompilované moduly [/Og](../../build/reference/og-global-optimizations.md), [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), nebo [/Ox](../../build/reference/ox-full-optimization.md), jsou prováděny následující optimalizace:

- Vložené cross-module

- Přidělení interprocedural registru (pouze 64bitové operační systémy)

- Vlastní konvence volání (pouze x86)

- Malé přestavění TLS (pouze x86)

- Dvojité zarovnání zásobníku (pouze x86)

- Vylepšené paměti rozlišení více tras (lepší narušení informace pro vstupní parametry a globální proměnné)

> [!NOTE]
> Linkeru Určuje, které optimalizace se používá ke kompilaci jednotlivé funkce a platí stejné optimalizace v době spojení.

Pomocí **/ltgc** a **/Ogt** způsobí, že optimalizace zarovnání dvojitou hodnotu.

Pokud **/ltgc** a **/Ogs** jsou nastaveny, neprovádí se dvojité zarovnání. Pokud se většina funkcí v aplikaci kompilovat pro rychlost, s několika funkce zkompilovaném pro velikost (například pomocí [optimalizovat](../../preprocessor/optimize.md) – Direktiva pragma), kompilátor zarovná dvojitou funkce, které jsou optimalizované pro velikost, pokud volání Funkce, které vyžadují dvojité zarovnání.

Pokud kompilátor můžete identifikovat všechny weby volání funkce, kompilátor ignoruje explicitní modifikátory konvence volání na funkci a pokusí se konvence volání funkce na optimalizovat:

- předat parametry v registrech

- Změna pořadí parametrů pro zarovnání

- odebrat nepoužité parametry

Pokud funkce, se nazývá prostřednictvím ukazatel na funkci, nebo pokud funkce je volána z mimo modul, který se zkompiluje pomocí **/GL**, kompilátor nebude pokoušet o konvence volání funkce na optimalizovat.

> [!NOTE]
> Pokud používáte **/ltgc** a znovu definovat `mainCRTStartup`, vaše aplikace může mít nepředvídatelné chování, která má vztah k uživatelského kódu, které provádí předtím, než se inicializují globální objekty. Existují tři způsoby, jak tento problém vyřešit: není znovu definovat `mainCRTStartup`, nejde kompilovat soubor, který obsahuje `mainCRTStartup` pomocí **/ltgc**, nebo inicializovat staticky globální proměnné a objekty.

### <a name="ltcg-and-msil-modules"></a>/ LTCG a moduly MSIL

Moduly, které jsou kompilovaná pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) a [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) lze použít jako vstup linkeru při **/ltgc** je zadán.

- **/ LTCG** může přijmout soubory nativní objektů a smíšený nativní nebo spravovaný objekt soubory (zkompilovat pomocí **/CLR**). **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.

- **/LTCG:PGI** nepřijímá nativní moduly zkompilovat pomocí **/GL** a   **/CLR**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. V tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Obecné** stránku vlastností.

1. Změnit **optimalizace celého programu** vlastnost.

Můžete taky použít **/ltgc** na konkrétní sestavení tak, že zvolíte **sestavení** > **optimalizace na základě profilu** v řádku nabídek nebo výběrem jedné z profilu Na základě možnosti optimalizace v místní nabídce pro projekt.

#### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
