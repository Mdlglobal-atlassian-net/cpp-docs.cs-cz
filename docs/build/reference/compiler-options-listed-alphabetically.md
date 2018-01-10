---
title: "Možnosti kompilátoru uvedené podle abecedy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: compiler options, C++
ms.assetid: 98375dad-c9c6-4796-aaa6-fd573269d4ae
caps.latest.revision: "66"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ee6062b04c1f406fe3286f6035eba1cda65ef1fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-options-listed-alphabetically"></a>Možnosti kompilátoru (abecední pořadí)
Následuje komplexní abecední seznam možností kompilátoru. Seznam kategorií, najdete v článku [kompilátoru možnosti uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
|Možnost|Účel|  
|------------|-------------|  
|[@](../../build/reference/at-specify-a-compiler-response-file.md)|Určuje soubor odezvy.|  
|[/?](../../build/reference/help-compiler-command-line-help.md)|Zobrazí seznam možností kompilátoru.|  
|[/AI](../../build/reference/ai-specify-metadata-directories.md)|Určuje adresář, který chcete vyhledávat předaný odkazů na soubor [#using](../../preprocessor/hash-using-directive-cpp.md) – direktiva.|  
|[/ analyze](../../build/reference/analyze-code-analysis.md)|Povolte analýza kódu.|  
|[/ arch](../../build/reference/arch-minimum-cpu-architecture.md)|Určuje architekturu pro generování kódu.|  
|[/ await](await-enable-coroutine-support.md)|Povolte rozšíření coroutines (odesílání funkce).|  
|[/ bigobj](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md)|Zvyšuje počet adresovatelné oddílů v souboru .obj.|  
|[/C](../../build/reference/c-preserve-comments-during-preprocessing.md)|Zachovává komentáře při předběžném zpracování.|  
|[/c](../../build/reference/c-compile-without-linking.md)|Zkompiluje bez propojení.|  
|[/ cgthreads](../../build/reference/cgthreads-code-generation-threads.md)|Určuje počet vláken cl.exe pro optimalizace a generování kódu.|  
|[/ CLR](../../build/reference/clr-common-language-runtime-compilation.md)|Vytvoří výstupního souboru ke spuštění na modul common language runtime.|  
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Vyhodnocení constexpr ovládacího prvku v době kompilace.|  
|[/D](../../build/reference/d-preprocessor-definitions.md)|Definuje konstanty a makra.|  
|[/Diagnostics](diagnostics-compiler-diagnostic-options.md)|Určuje formát diagnostické zprávy.|  
|[/doc](../../build/reference/doc-process-documentation-comments-c-cpp.md)|Proces dokumentační komentáře do souboru XML.|  
|[/E](../../build/reference/e-preprocess-to-stdout.md)|Výstup preprocesoru kopie standardním výstupu.|  
|[/EH](../../build/reference/eh-exception-handling-model.md)|Určuje model zpracování výjimek.|  
|[/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)|Výstup preprocesoru kopie standardním výstupu.|  
|[/ errorreport](../../build/reference/errorreport-report-internal-compiler-errors.md)|Umožňuje zadat informace o chybě (LED) interní kompilátoru přímo do týmu Visual C++.|  
|[/Execution-Charset](execution-charset-set-execution-character-set.md)|Znaková sada spuštění sady.|  
|[/F](../../build/reference/f-set-stack-size.md)|Nastaví zásobníku velikost.|  
|[/ favor](../../build/reference/favor-optimize-for-architecture-specifics.md)|Vytvoří kód, který je optimalizovaná pro konkrétní [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architektura nebo pro konkrétní architektur micro v AMD64 i rozšířené paměti 64 architektury Technology (EM64T).|  
|[/FA](../../build/reference/fa-fa-listing-file.md)|Vytvoří soubor seznamu.|  
|[/Fa](../../build/reference/fa-fa-listing-file.md)|Nastaví název souboru výpis.|  
|[/FC](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)|Zobrazení úplná cesta předaný cl.exe v diagnostických textové soubory zdrojového kódu.|  
|[/FD](../../build/reference/fd-program-database-file-name.md)|Přejmenuje soubor databáze programu.|  
|[/FE](../../build/reference/fe-name-exe-file.md)|Přejmenuje spustitelný soubor.|  
|[/FI](../../build/reference/fi-name-forced-include-file.md)|Upraví zadaný soubor.|  
|[/Fi](../../build/reference/fi-preprocess-output-file-name.md)|Nastaví název předběžně zpracované výstupního souboru.|  
|[/FM](../../build/reference/fm-name-mapfile.md)|Vytvoří souboru mapování.|  
|[/FO](../../build/reference/fo-object-file-name.md)|Vytvoří soubor objektu.|  
|[/fp](../../build/reference/fp-specify-floating-point-behavior.md)|Zadejte chování při s plovoucí desetinnou čárkou.|  
|[/Fp](../../build/reference/fp-name-dot-pch-file.md)|Určuje název souboru předkompilovaných hlaviček.|  
|[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)<br /><br /> [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)|Generuje soubory prohlížeče. **/FR** je zastaralý.|  
|[/FS](../../build/reference/fs-force-synchronous-pdb-writes.md)|Vynutí zapisuje do souboru databáze (PDB) program k serializaci prostřednictvím MSPDBSRV. SOUBOR EXE.|  
|[/FU](../../build/reference/fu-name-forced-hash-using-file.md)|Vynutí použití názvu souboru, jako kdyby měl byla předána [#using](../../preprocessor/hash-using-directive-cpp.md) – direktiva.|  
|[/FX](../../build/reference/fx-merge-injected-code.md)|Sloučení vloženého kódu se zdrojový soubor.|  
|[/GA](../../build/reference/ga-optimize-for-windows-application.md)|Optimalizuje kódu pro aplikaci systému Windows.|  
|[/GD](../../build/reference/gd-gr-gv-gz-calling-convention.md)|Používá `__cdecl` konvence (pouze x86) volání.|  
|[/Ge](../../build/reference/ge-enable-stack-probes.md)|Zastaralé Aktivuje sondy zásobníku.|  
|[/GF](../../build/reference/gf-eliminate-duplicate-strings.md)|Umožňuje sdružování řetězec.|  
|[/GH](../../build/reference/gh-enable-pexit-hook-function.md)|Funkce háku volání `_pexit`.|  
|[/GH](../../build/reference/gh-enable-penter-hook-function.md)|Funkce háku volání `_penter`.|  
|[/GL](../../build/reference/gl-whole-program-optimization.md)|Umožňuje optimalizace celého programu.|  
|[/GM](../../build/reference/gm-enable-minimal-rebuild.md)|Umožňuje minimální opětovné sestavení.|  
|[GR](../../build/reference/gr-enable-run-time-type-information.md)|Umožňuje informace běhového typu (RTTI).|  
|[GR](../../build/reference/gd-gr-gv-gz-calling-convention.md)|Používá `__fastcall` konvence (pouze x86) volání.|  
|[/GS](../../build/reference/gs-buffer-security-check.md)|Kontrola zabezpečení vyrovnávací paměti.|  
|[/GS](../../build/reference/gs-control-stack-checking-calls.md)|Sondy zásobníku ovládací prvky.|  
|[/GT OPTICKÉHO](../../build/reference/gt-support-fiber-safe-thread-local-storage.md)|Podporuje zabezpečení fiber pro data přidělen s použitím statické úložiště thread-local.|  
|[/Guard:CF](../../build/reference/guard-enable-control-flow-guard.md)|Přidá kontroly zabezpečení ochrany toku řízení.|  
|[/ Gv](../../build/reference/gd-gr-gv-gz-calling-convention.md)|Používá `__vectorcall` konvence volání. (x86 a x64 pouze)|  
|[/GW](../../build/reference/gw-optimize-global-data.md)|Umožňuje optimalizace celého programu globální data.|  
|[/GX](../../build/reference/gx-enable-exception-handling.md)|Zastaralé Umožňuje synchronní zpracování výjimek. Použití [/EH](../../build/reference/eh-exception-handling-model.md) místo.|  
|[/Gy](../../build/reference/gy-enable-function-level-linking.md)|Povoluje funkce úrovni propojení.|  
|[/GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md)|Zastaralé Stejné jako [RTC1](../../build/reference/rtc-run-time-error-checks.md).|  
|[/GZ](../../build/reference/gd-gr-gv-gz-calling-convention.md)|Používá `__stdcall` konvence (pouze x86) volání.|  
|[/H](../../build/reference/h-restrict-length-of-external-names.md)|Zastaralé Omezuje délku externích názvů (veřejné).|  
|[/ HELP](../../build/reference/help-compiler-command-line-help.md)|Zobrazí seznam možností kompilátoru.|  
|[/ homeparams](../../build/reference/homeparams-copy-register-parameters-to-stack.md)|Vynutí parametry předané zaregistruje k zápisu na jejich umístění v zásobníku při vstupu funkce. Tato možnost kompilátoru je pouze pro [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] kompilátory (nativní a multiplatformní kompilace).|  
|[/ hotpatch](../../build/reference/hotpatch-create-hotpatchable-image.md)|Vytvoří kopii opravitelnou za provozu.|  
|[/I](../../build/reference/i-additional-include-directories.md)|Vyhledá adresář pro zahrnout soubory.|  
|[/J](../../build/reference/j-default-char-type-is-unsigned.md)|Změní výchozí `char` typu.|  
|[/ Kernel](../../build/reference/kernel-create-kernel-mode-binary.md)|Kompilátoru a linkeru vytvoří binární soubor, který lze spustit v jádru systému Windows.|  
|[/LD](../../build/reference/md-mt-ld-use-run-time-library.md)|Vytvoří knihovnu DLL.|  
|[/ LDd](../../build/reference/md-mt-ld-use-run-time-library.md)|Vytvoří knihovnu DLL ladění.|  
|[/link](../../build/reference/link-pass-options-to-linker.md)|Předá Zadaná možnost propojení.|  
|[/LN](../../build/reference/ln-create-msil-module.md)|Vytvoří modul MSIL.|  
|[/MD](../../build/reference/md-mt-ld-use-run-time-library.md)|Vytvoří vícevláknové knihovny DLL pomocí MSVCRT.lib.|  
|[/ MDd](../../build/reference/md-mt-ld-use-run-time-library.md)|Vytvoří ladění vícevláknové knihovny DLL pomocí MSVCRTD.lib.|  
|[/ MP](../../build/reference/mp-build-with-multiple-processes.md)|Zkompiluje víc zdrojových souborů pomocí několika procesů.|  
|[/ MT](../../build/reference/md-mt-ld-use-run-time-library.md)|Vytvoří soubor s více vlákny spustitelný soubor pomocí LIBCMT.lib.|  
|[/ MTd](../../build/reference/md-mt-ld-use-run-time-library.md)|Vytvoří ladění vícevláknové spustitelný soubor pomocí LIBCMTD.lib.|  
|[/nologo](../../build/reference/nologo-suppress-startup-banner-c-cpp.md)|Potlačí zobrazení nápisu přihlášení.|  
|[/ O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)|Vytvoří malý kód.|  
|[/ O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)|Vytvoří rychlý kód.|  
|[/Ob](../../build/reference/ob-inline-function-expansion.md)|Vložené rozšíření ovládacích prvků.|  
|[/Od](../../build/reference/od-disable-debug.md)|Zakáže optimalizace.|  
|[/Og](../../build/reference/og-global-optimizations.md)|Zastaralé Využívá globální optimalizace.|  
|[/OI](../../build/reference/oi-generate-intrinsic-functions.md)|Generuje vnitřní funkce.|  
|[/ OpenMP](../../build/reference/openmp-enable-openmp-2-0-support.md)|Umožňuje [omp – #pragma](../../preprocessor/omp.md) ve zdrojovém kódu.|  
|[/OS](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)|Upřednostňuje malý kód.|  
|[/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)|Favors rychlý kód.|  
|[/OX](../../build/reference/ox-full-optimization.md)|Používá maximální optimalizace (nebo Ob2gity /Gs).|  
|[/Oy](../../build/reference/oy-frame-pointer-omission.md)|Vynechá ukazatel na rámec (pouze x86).|  
|[/P](../../build/reference/p-preprocess-to-a-file.md)|Výstup preprocesoru zapisuje do souboru.|  
|[/ projektovou-](permissive-standards-conformance.md)|Nastavit režim standard shoda.|  
|[/ Qfast_transcendentals](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md)|Generuje rychlé Transcendentní objekty.|  
|[/ QIfist](../../build/reference/qifist-suppress-ftol.md)|Zastaralé Potlačí `_ftol` Pokud převod z typu s plovoucí desetinnou čárkou integrální typ je požadovaná (pouze x86).|  
|[/ Qimprecise_fwaits](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Odebere `fwait` příkazy uvnitř `try` bloky.|  
|[/ Qpar (automatickou vektorizací)](../../build/reference/qpar-auto-parallelizer.md)|Umožňuje automatické paralelizace cykly, které jsou označené [#pragma loop()](../../preprocessor/loop.md) – direktiva.|  
|[/ Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md)|Používá celé číslo přesunutí pokyny pro hodnoty s plovoucí desetinnou čárkou a zakáže určité plovoucí optimalizace zatížení bodu.|  
|[/ Qvec-report (úroveň sestav automatickou vektorizací)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md)|Umožňuje vytváření sestav úrovně pro automatické vectorization.|  
|[/ RTC](../../build/reference/rtc-run-time-error-checks.md)|Umožňuje Kontrola chyb za běhu.|  
|[SDL](../../build/reference/sdl-enable-additional-security-checks.md)|Povoluje další funkce zabezpečení a upozornění.|  
|[/ showincludes vložených](../../build/reference/showincludes-list-include-files.md)|Zobrazí seznam zahrnutí souborů během kompilace.|  
|[/Source-Charset](source-charset-set-source-character-set.md)|Sada zdroj znakovou sadu.|  
|[/std](std-specify-language-standard-version.md)|C++ standardní verzi kompatibility selektor.|  
|[/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)|Určuje zdrojový soubor C.|  
|[/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)|Určuje, že všechny zdrojové soubory jsou C.|  
|[/TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)|Určuje zdrojový soubor C++.|  
|[/TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)|Určuje, že všechny zdrojové soubory jsou C++.|  
|[/U](../../build/reference/u-u-undefine-symbols.md)|Odebere předdefinovaná makra.|  
|[/u](../../build/reference/u-u-undefine-symbols.md)|Odebere všechny předdefinovaná makra.|  
|[/UTF-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Sada zdroje a provádění znakových sad, na UTF-8.|  
|[/V](../../build/reference/v-version-number.md)|Zastaralé Nastaví řetězec verze souboru .obj.|  
|[/Validate-Charset](validate-charset-validate-for-compatible-characters.md)|Ověřte soubory pouze kompatibilní znaky znakové sady UTF-8.|  
|[/VD](../../build/reference/vd-disable-construction-displacements.md)|Potlačí nebo umožňuje členům třídy vtordisp skrytá.|  
|[/ vmb](../../build/reference/vmb-vmg-representation-method.md)|Používá nejlépe základní ukazatelé na členy.|  
|[/ vmg](../../build/reference/vmb-vmg-representation-method.md)|Úplné obecné používá pro ukazatelé na členy.|  
|[/ VMM](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)|Deklaruje vícenásobná dědičnost.|  
|[/ VMS](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)|Deklaruje jedna dědičnost.|  
|[/ vmv](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)|Deklaruje virtuální dědičnost.|  
|[/ volatile](../../build/reference/volatile-volatile-keyword-interpretation.md)|Vybere, jak interpretovat volatile – klíčové slovo.|  
|[/w](../../build/reference/compiler-option-warning-level.md)|Zakáže všechna upozornění.|  
|[/ W0, /W1, /W2, /W3, /W4](../../build/reference/compiler-option-warning-level.md)|Nastaví kterou úroveň upozornění na výstup.|  
|[/W1, /w2, /w3, /w4](../../build/reference/compiler-option-warning-level.md)|Nastaví úroveň pro upozornění pro zadaný upozornění.|  
|[/ Wall](../../build/reference/compiler-option-warning-level.md)|Umožňuje všech upozornění, včetně upozornění, která jsou ve výchozím nastavení zakázané.|  
|[/WD](../../build/reference/compiler-option-warning-level.md)|Zakáže zadaný upozornění.|  
|[/we](../../build/reference/compiler-option-warning-level.md)|Zadaný upozornění považuje za chybu.|  
|[/WL ONLINE](../../build/reference/wl-enable-one-line-diagnostics.md)|Umožňuje diagnostiku pro chybové zprávy a upozornění při kompilování zdrojového kódu C++ v příkazovém řádku.|  
|[/wo](../../build/reference/compiler-option-warning-level.md)|Zobrazí se zadané upozornění pouze jednou.|  
|[/ Wp64](../../build/reference/wp64-detect-64-bit-portability-issues.md)|Zastaralé. Zjistí problémy s 64bitovou přenositelností.|  
|[/WV](../../build/reference/compiler-option-warning-level.md)|Zobrazí žádná varování vyšších zadaná verze kompilátoru.|  
|[/WX](../../build/reference/compiler-option-warning-level.md)|Zpracovává všechny upozornění jako chyby.|  
|[/X](../../build/reference/x-ignore-standard-include-paths.md)|Ignoruje standardní zahrnout adresář.|  
|[/Y-](../../build/reference/y-ignore-precompiled-header-options.md)|Ignoruje všechny ostatní možnosti kompilátoru předkompilovaných hlaviček v aktuální sestavení.|  
|[/Yc](../../build/reference/yc-create-precompiled-header-file.md)|Vytvoří soubor předkompilovaných hlaviček.|  
|[/Yd](../../build/reference/yd-place-debug-information-in-object-file.md)|Zastaralé Místech dokončit ladicí informace ve všech souborů objektu. Použití [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) místo.|  
|[/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md)|Vloží referenci PCH při vytváření knihovna ladění|  
|[/YU](../../build/reference/yu-use-precompiled-header-file.md)|Předkompilovaný hlavičkový soubor se používá během vytváření sestavení.|  
|[/ Z7](../../build/reference/z7-zi-zi-debug-information-format.md)|Generuje C 7.0 kompatibilní ladicí informace.|  
|[/Za](../../build/reference/za-ze-disable-language-extensions.md)|Zakáže jazyková rozšíření.|  
|[/Zc](../../build/reference/zc-conformance.md)|Určuje standardní chování pod [/Ze](../../build/reference/za-ze-disable-language-extensions.md).[ / Za, /Ze (zakázat jazyková rozšíření)](../../build/reference/za-ze-disable-language-extensions.md)|  
|[/Ze](../../build/reference/za-ze-disable-language-extensions.md)|Zastaralé Umožňuje jazyková rozšíření.|  
|[/Zg](../../build/reference/zg-generate-function-prototypes.md)|Odebrat ve Visual C++ 2015. Generuje prototypy funkcí.|  
|[/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)|Obsahuje informace o ladění do databáze kompatibilní s upravit a pokračovat v programu.|  
|[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)|Generuje kompletní informace o ladění.|  
|[/Zl](../../build/reference/zl-omit-default-library-name.md)|Odebere názvu výchozí knihovny ze souboru .obj (pouze x86).|  
|[/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)|Určuje omezení přidělení paměti pro předkompilované hlavičky.|  
|[/Zp](../../build/reference/zp-struct-member-alignment.md)|Balíčky struktury členy.|  
|[/ZS](../../build/reference/zs-syntax-check-only.md)|Pouze kontrola syntaxe.|  
|[/ZW](../../build/reference/zw-windows-runtime-compilation.md)|Vytvoří soubor výstupu pro spouštění v prostředí Windows Runtime.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz sestavení C/C++](../../build/reference/c-cpp-building-reference.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)