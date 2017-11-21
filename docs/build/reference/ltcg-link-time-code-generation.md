---
title: "-LTCG (vytváření kódu v době propojování) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
dev_langs: C++
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0932ba85a6570e83be655bb3f8f71bdf9726e88e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (vytváření kódu v době propojování)
```  
/LTCG[:INCREMENTAL|:NOSTATUS|:STATUS|:OFF|:PGINSTRUMENT|:PGOPTIMIZE|:PGUPDATE]  
```  
  
## <a name="remarks"></a>Poznámky  
 : PŘÍRŮSTKOVÉ (volitelné)  
 Určuje, že linkeru do sady souborů, které jsou ovlivněné upravíte, nikoli celý projekt aplikuje jenom celého programu optimalizace nebo propojování generování kódu (LTCG). Ve výchozím nastavení tento příznak není nastavená, pokud je zadán/ltgc a celý projekt je propojena s použitím optimalizace celého programu.  
  
 : NOSTATUS &#124; : Stav (volitelné)  
 Určuje, zda linkeru zobrazuje indikátor průběhu, který ukazuje, jaké procento odkaz je kompletní. Ve výchozím nastavení není tato informace o stavu zobrazí.  
  
 : OFF (volitelné)  
 Znemožňuje generování kódu v době propojování. Toto chování je stejné jako při/ltgc není zadán v příkazovém řádku.  
  
 : PGINSTRUMENT (volitelné)  
 Tato možnost je zastaralý. Místo toho použijte **/ltgc** a **/GENPROFILE** nebo **/FASTGENPROFILE** ke generování instrumentovaného sestavení pro optimalizace na základě profilu.  
  
 Data, která se shromažďují ze instrumentovaného spustí slouží k vytvoření image optimalizované. Další informace najdete v tématu [optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md). Zkratka pro tuto možnost je /LTCG:PGI.  
  
 : PGOPTIMIZE (volitelné)  
 Tato možnost je zastaralý. Místo toho použijte **/ltgc** a **/USEPROFILE** vytvářet optimalizované bitové kopie. Další informace najdete v tématu [optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md). Zkratka pro tuto možnost je /LTCG:PGO.  
  
 : PGUPDATE (volitelné)  
 Tato možnost je zastaralý. Místo toho použijte **/ltgc** a **/USEPROFILE** vytvářet optimalizované bitové kopie. Další informace najdete v tématu [optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md). Zkratka pro tuto možnost je /LTCG:PGU.  
  
 Možnost/ltgc informuje linkeru volání do kompilátoru a provedení optimalizace celého programu. Můžete také provést optimalizace na základě profilu. Další informace najdete v tématu [optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md).  
  
 S následujícími výjimkami nemůžete přidat možnosti linkeru PGO kombinace/ltgc a /USEPROFILE, které nebyly zadány v předchozí kombinace inicializace PGO/ltgc a /GENPROFILE možnosti:  
  
-   [/ BASE](../../build/reference/base-base-address.md)  
  
-   [/ FIXED](../../build/reference/fixed-fixed-base-address.md)  
  
-   / LTCG  
  
-   [/ MAP](../../build/reference/map-generate-mapfile.md)  
  
-   [/ MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)  
  
-   [/ NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)  
  
-   [/ OUT](../../build/reference/out-output-file-name.md)  
  
-   [/ PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)  
  
-   [/ PDB](../../build/reference/pdb-use-program-database.md)  
  
-   [/ PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)  
  
-   [/ STUB](../../build/reference/stub-ms-dos-stub-file-name.md)  
  
-   [/ VERBOSE](../../build/reference/verbose-print-progress-messages.md)  
  
 Všechny možnosti linkeru, které jsou zadány společně s / ltgc a možnosti /GENPROFILE k chybě při inicializaci PGO není potřeba zadat při vytváření pomocí/ltgc a /USEPROFILE; že jsou implicitní.  
  
 Zbývající část tohoto tématu popisuje/ltgc z hlediska generování kódu v době propojování.  
  
 / LTCG je implicitní s [/GL](../../build/reference/gl-whole-program-optimization.md).  
  
 Linkeru vyvolá generování kódu v době propojování, je-li předán modul, který byl kompilován s použitím **/GL** nebo modul MSIL (viz [.netmodule soubory jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md)). Pokud nezadáte explicitně **/ltgc** při předání **/GL** nebo moduly MSIL linkeru, nakonec linkeru to zjistí a restartuje odkaz pomocí **/ltgc**. Explicitně zadáte **/ltgc** při předání **/GL** a moduly MSIL linkeru pro nejrychlejší možné sestavit výkonu.  
  
 I rychlejší průběh, použijte **/ltgc: PŘÍRŮSTKOVÉ**. Tato možnost umožňuje linkeru pouze znovu optimalizace sadu souborů, která jsou ovlivněná změnu zdrojového souboru, místo celý projekt. To může výrazně snížit odkaz čas potřebný. Toto není stejná možnost jako přírůstkové propojování.  
  
 **/ LTCG** není platná pro použití s [/PŘÍRŮSTKOVÉ](../../build/reference/incremental-link-incrementally.md).  
  
 Když **/ltgc** slouží k propojení s použitím Kompilované moduly [/Og](../../build/reference/og-global-optimizations.md), [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), nebo [/Ox](../../build/reference/ox-full-optimization.md), jsou prováděny následující optimalizace:  
  
-   Vložené cross-module  
  
-   Přidělení interprocedural registru (pouze 64bitové operační systémy)  
  
-   Vlastní konvence volání (pouze x86)  
  
-   Malé přestavění TLS (pouze x86)  
  
-   Dvojité zarovnání zásobníku (pouze x86)  
  
-   Vylepšené paměti rozlišení více tras (lepší narušení informace pro vstupní parametry a globální proměnné)  
  
> [!NOTE]
>  Linkeru Určuje, které optimalizace se používá ke kompilaci jednotlivé funkce a platí stejné optimalizace v době spojení.  
  
 Pomocí **/ltgc** a **/Ogt** způsobí, že optimalizace zarovnání dvojitou hodnotu.  
  
 Pokud **/ltgc** a **/Ogs** jsou nastaveny, neprovádí se dvojité zarovnání. Pokud se většina funkcí v aplikaci kompilovat pro rychlost, s několika funkce zkompilovaném pro velikost (například pomocí [optimalizovat](../../preprocessor/optimize.md) – Direktiva pragma), kompilátor zarovná dvojitou funkce, které jsou optimalizované pro velikost, pokud volání Funkce, které vyžadují dvojité zarovnání.  
  
 Pokud kompilátor můžete identifikovat všechny weby volání funkce, kompilátor ignoruje explicitní modifikátory konvence volání na funkci a pokusí se konvence volání funkce na optimalizovat:  
  
-   předat parametry v registrech  
  
-   Změna pořadí parametrů pro zarovnání  
  
-   odebrat nepoužité parametry  
  
 Pokud funkce, se nazývá prostřednictvím ukazatel na funkci, nebo pokud funkce je volána z mimo modul, který se zkompiluje pomocí **/GL**, kompilátor nebude pokoušet o konvence volání funkce na optimalizovat.  
  
> [!NOTE]
>  Pokud používáte **/ltgc** a znovu definovat mainCRTStartup, vaše aplikace může mít nepředvídatelné chování, která má vztah k uživatelského kódu, které provádí předtím, než se inicializují globální objekty.  Existují tři způsoby, jak tento problém vyřešit: není znovu definovat mainCRTStartup, nejde kompilovat soubor, který obsahuje mainCRTStartup pomocí **/ltgc**, nebo inicializovat staticky globální proměnné a objekty.  
  
## <a name="ltcg-and-msil-modules"></a>/ LTCG a moduly MSIL  
 Moduly, které jsou kompilovaná pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) a [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) lze použít jako vstup linkeru při **/ltgc** je zadán.  
  
-   **/ LTCG** může přijmout nativní objekt soubory, soubory nativní nebo spravovaný objektů ve smíšeném (zkompilovat pomocí **/CLR**) a soubory čistý objektů (zkompilovat pomocí **/CLR: pure**), a bezpečné objekt soubory ( zkompilovat pomocí **/CLR: safe**). **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
-   **/ LTCG** může přijmout bezpečné .netmodules, který lze vytvořit pomocí **/CLR: safe /LN** v jazyce Visual C++ a **/target: Module** v žádné sadě Visual Studio .NET kompilátoru. . Netmodules vytvořeného pomocí **/CLR** nebo **/CLR: pure** nejsou přijímány **/ltgc**.  
  
-   /LTCG:PGI nepřijímá nativní moduly zkompilovat pomocí **/GL** a **/CLR**, nebo čisté moduly (vytvořeného pomocí **/CLR: pure**)  
  
#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno. V tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **vlastnosti konfigurace** složky.  
  
3.  Vyberte **Obecné** stránku vlastností.  
  
4.  Změnit **optimalizace celého programu** vlastnost.  
  
 Můžete taky použít **/ltgc** na konkrétní sestavení tak, že zvolíte **sestavení**, **optimalizace na základě profilu** v řádku nabídek nebo výběrem jedné z optimalizace na základě profilu Možnosti v místní nabídce pro projekt.  
  
#### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)