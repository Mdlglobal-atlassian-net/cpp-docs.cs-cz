---
title: Možnosti kompilátoru uvedené podle abecedy | Microsoft Docs
ms.custom: ''
ms.date: 02/22/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiler options, C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 259958d789ed189c38b75fe708034fb0d76fc35c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379624"
---
# <a name="compiler-options-listed-alphabetically"></a>Možnosti kompilátoru (abecední pořadí)

Následuje komplexní abecední seznam možností kompilátoru. Seznam kategorií, najdete v článku [kompilátoru možnosti uvedené podle kategorie](compiler-options-listed-by-category.md).

|Možnost|Účel|
|------------|-------------|
|[@](at-specify-a-compiler-response-file.md)|Určuje soubor odezvy.|
|[/?](help-compiler-command-line-help.md)|Zobrazí seznam možností kompilátoru.|
|[/AI](ai-specify-metadata-directories.md)|Určuje adresář, který chcete vyhledávat předaný odkazů na soubor [#using](../../preprocessor/hash-using-directive-cpp.md) – direktiva.|
|[/ analyze](analyze-code-analysis.md)|Povolte analýza kódu.|
|[/ arch](arch-minimum-cpu-architecture.md)|Určuje architekturu pro generování kódu.|
|[/ await](await-enable-coroutine-support.md)|Povolte rozšíření coroutines (odesílání funkce).|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|Zvyšuje počet adresovatelné oddílů v souboru .obj.|
|[/C](c-preserve-comments-during-preprocessing.md)|Zachovává komentáře při předběžném zpracování.|
|[/c](c-compile-without-linking.md)|Zkompiluje bez propojení.|
|[/ cgthreads](cgthreads-code-generation-threads.md)|Určuje počet vláken cl.exe pro optimalizace a generování kódu.|
|[/ CLR](clr-common-language-runtime-compilation.md)|Vytvoří výstupního souboru ke spuštění na modul common language runtime.|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Vyhodnocení constexpr ovládacího prvku v době kompilace.|
|[/D](d-preprocessor-definitions.md)|Definuje konstanty a makra.|
|[/Diagnostics](diagnostics-compiler-diagnostic-options.md)|Určuje formát diagnostické zprávy.|
|[/doc](doc-process-documentation-comments-c-cpp.md)|Proces dokumentační komentáře do souboru XML.|
|[/E](e-preprocess-to-stdout.md)|Výstup preprocesoru kopie standardním výstupu.|
|[/EH](eh-exception-handling-model.md)|Určuje model zpracování výjimek.|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Výstup preprocesoru kopie standardním výstupu.|
|[/ errorreport](errorreport-report-internal-compiler-errors.md)|Umožňuje zadat informace o chybě (LED) interní kompilátoru přímo do týmu Visual C++.|
|[/execution-charset](execution-charset-set-execution-character-set.md)|Znaková sada spuštění sady.|
|[/F](f-set-stack-size.md)|Nastaví zásobníku velikost.|
|[/ favor](favor-optimize-for-architecture-specifics.md)|Vytvoří kód, který je optimalizovaná pro konkrétní [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architektura nebo pro konkrétní architektur micro v AMD64 i rozšířené paměti 64 architektury Technology (EM64T).|
|[/FA](fa-fa-listing-file.md)|Vytvoří soubor seznamu.|
|[/Fa](fa-fa-listing-file.md)|Nastaví název souboru výpis.|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|Zobrazení úplná cesta předaný cl.exe v diagnostických textové soubory zdrojového kódu.|
|[/FD](fd-program-database-file-name.md)|Přejmenuje soubor databáze programu.|
|[/FE](fe-name-exe-file.md)|Přejmenuje spustitelný soubor.|
|[/FI](fi-name-forced-include-file.md)|Upraví zadaný soubor.|
|[/Fi](fi-preprocess-output-file-name.md)|Nastaví název předběžně zpracované výstupního souboru.|
|[/Fm](fm-name-mapfile.md)|Vytvoří souboru mapování.|
|[/FO](fo-object-file-name.md)|Vytvoří soubor objektu.|
|[/fp](fp-specify-floating-point-behavior.md)|Zadejte chování při s plovoucí desetinnou čárkou.|
|[/Fp](fp-name-dot-pch-file.md)|Určuje název souboru předkompilovaných hlaviček.|
|[/FR](fr-fr-create-dot-sbr-file.md)<br /><br /> [/FR](fr-fr-create-dot-sbr-file.md)|Generuje soubory prohlížeče. **/FR** je zastaralý.|
|[/FS](fs-force-synchronous-pdb-writes.md)|Vynutí zapisuje do souboru databáze (PDB) program k serializaci prostřednictvím MSPDBSRV. SOUBOR EXE.|
|[/FU](fu-name-forced-hash-using-file.md)|Vynutí použití názvu souboru, jako kdyby měl byla předána [#using](../../preprocessor/hash-using-directive-cpp.md) – direktiva.|
|[/Fx](fx-merge-injected-code.md)|Sloučení vloženého kódu se zdrojový soubor.|
|[/GA](ga-optimize-for-windows-application.md)|Optimalizuje kódu pro aplikaci systému Windows.|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|Používá `__cdecl` konvence (pouze x86) volání.|
|[/Ge](ge-enable-stack-probes.md)|Zastaralé Aktivuje sondy zásobníku.|
|[/GF](gf-eliminate-duplicate-strings.md)|Umožňuje sdružování řetězec.|
|[/GH](gh-enable-pexit-hook-function.md)|Funkce háku volání `_pexit`.|
|[/Gh](gh-enable-penter-hook-function.md)|Funkce háku volání `_penter`.|
|[/GL](gl-whole-program-optimization.md)|Umožňuje optimalizace celého programu.|
|[/Gm](gm-enable-minimal-rebuild.md)|Umožňuje minimální opětovné sestavení.|
|[/GR](gr-enable-run-time-type-information.md)|Umožňuje informace běhového typu (RTTI).|
|[GR](gd-gr-gv-gz-calling-convention.md)|Používá `__fastcall` konvence (pouze x86) volání.|
|[/GS](gs-buffer-security-check.md)|Kontrola zabezpečení vyrovnávací paměti.|
|[/Gs](gs-control-stack-checking-calls.md)|Sondy zásobníku ovládací prvky.|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|Podporuje zabezpečení fiber pro data přidělen s použitím statické úložiště thread-local.|
|[/Guard:CF](guard-enable-control-flow-guard.md)|Přidá kontroly zabezpečení ochrany toku řízení.|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|Používá `__vectorcall` konvence volání. (x86 a x64 pouze)|
|[/Gw](gw-optimize-global-data.md)|Umožňuje optimalizace celého programu globální data.|
|[/GX](gx-enable-exception-handling.md)|Zastaralé Umožňuje synchronní zpracování výjimek. Použití [/EH](eh-exception-handling-model.md) místo.|
|[/Gy](gy-enable-function-level-linking.md)|Povoluje funkce úrovni propojení.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Zastaralé Stejné jako [RTC1](rtc-run-time-error-checks.md).|
|[/Gz](gd-gr-gv-gz-calling-convention.md)|Používá `__stdcall` konvence (pouze x86) volání.|
|[/H](h-restrict-length-of-external-names.md)|Zastaralé Omezuje délku externích názvů (veřejné).|
|[/ HELP](help-compiler-command-line-help.md)|Zobrazí seznam možností kompilátoru.|
|[/ homeparams](homeparams-copy-register-parameters-to-stack.md)|Vynutí parametry předané zaregistruje k zápisu na jejich umístění v zásobníku při vstupu funkce. Tato možnost kompilátoru je pouze pro [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] kompilátory (nativní a multiplatformní kompilace).|
|[/ hotpatch](hotpatch-create-hotpatchable-image.md)|Vytvoří kopii opravitelnou za provozu.|
|[/I](i-additional-include-directories.md)|Vyhledá adresář pro zahrnout soubory.|
|[/J](j-default-char-type-is-unsigned.md)|Změní výchozí `char` typu.|
|[/kernel](kernel-create-kernel-mode-binary.md)|Kompilátoru a linkeru vytvoří binární soubor, který lze spustit v jádru systému Windows.|
|[/LD](md-mt-ld-use-run-time-library.md)|Vytvoří knihovnu DLL.|
|[/ LDd](md-mt-ld-use-run-time-library.md)|Vytvoří knihovnu DLL ladění.|
|[/link](link-pass-options-to-linker.md)|Předá Zadaná možnost propojení.|
|[/LN](ln-create-msil-module.md)|Vytvoří modul MSIL.|
|[/MD](md-mt-ld-use-run-time-library.md)|Vytvoří vícevláknové knihovny DLL pomocí MSVCRT.lib.|
|[/ MDd](md-mt-ld-use-run-time-library.md)|Vytvoří ladění vícevláknové knihovny DLL pomocí MSVCRTD.lib.|
|[/MP](mp-build-with-multiple-processes.md)|Zkompiluje víc zdrojových souborů pomocí několika procesů.|
|[/MT](md-mt-ld-use-run-time-library.md)|Vytvoří soubor s více vlákny spustitelný soubor pomocí LIBCMT.lib.|
|[/MTd](md-mt-ld-use-run-time-library.md)|Vytvoří ladění vícevláknové spustitelný soubor pomocí LIBCMTD.lib.|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|Potlačí zobrazení nápisu přihlášení.|
|[/ O1](o1-o2-minimize-size-maximize-speed.md)|Vytvoří malý kód.|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|Vytvoří rychlý kód.|
|[/Ob](ob-inline-function-expansion.md)|Vložené rozšíření ovládacích prvků.|
|[/Od](od-disable-debug.md)|Zakáže optimalizace.|
|[/Og](og-global-optimizations.md)|Zastaralé Využívá globální optimalizace.|
|[/OI](oi-generate-intrinsic-functions.md)|Generuje vnitřní funkce.|
|[/ OpenMP](openmp-enable-openmp-2-0-support.md)|Umožňuje [omp – #pragma](../../preprocessor/omp.md) ve zdrojovém kódu.|
|[/OS](os-ot-favor-small-code-favor-fast-code.md)|Upřednostňuje malý kód.|
|[/Ot](os-ot-favor-small-code-favor-fast-code.md)|Favors rychlý kód.|
|[/OX](ox-full-optimization.md)|Používá maximální optimalizace (nebo Ob2gity /Gs).|
|[/Oy](oy-frame-pointer-omission.md)|Vynechá ukazatel na rámec (pouze x86).|
|[/P](p-preprocess-to-a-file.md)|Výstup preprocesoru zapisuje do souboru.|
|[/ projektovou-](permissive-standards-conformance.md)|Nastavit režim standard shoda.|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|Generuje rychlé Transcendentní objekty.|
|[/ QIfist](qifist-suppress-ftol.md)|Zastaralé Potlačí `_ftol` Pokud převod z typu s plovoucí desetinnou čárkou integrální typ je požadovaná (pouze x86).|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Odebere `fwait` příkazy uvnitř `try` bloky.|
|[/Qpar (automatická paralelizace)](qpar-auto-parallelizer.md)|Umožňuje automatické paralelizace cykly, které jsou označené [#pragma loop()](../../preprocessor/loop.md) – direktiva.|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|Používá celé číslo přesunutí pokyny pro hodnoty s plovoucí desetinnou čárkou a zakáže určité plovoucí optimalizace zatížení bodu.|
|[/Qpar-report (úroveň generování sestav s automatickou vektorizací)](qvec-report-auto-vectorizer-reporting-level.md)|Umožňuje vytváření sestav úrovně pro automatické vectorization.|
|[/RTC](rtc-run-time-error-checks.md)|Umožňuje Kontrola chyb za běhu.|
|[/sdl](sdl-enable-additional-security-checks.md)|Povoluje další funkce zabezpečení a upozornění.|
|[/ showincludes vložených](showincludes-list-include-files.md)|Zobrazí seznam zahrnutí souborů během kompilace.|
|[/source-charset](source-charset-set-source-character-set.md)|Sada zdroj znakovou sadu.|
|[/std](std-specify-language-standard-version.md)|C++ standardní verzi kompatibility selektor.|
|[/Tc](tc-tp-tc-tp-specify-source-file-type.md)|Určuje zdrojový soubor C.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Určuje, že všechny zdrojové soubory jsou C.|
|[/Tp](tc-tp-tc-tp-specify-source-file-type.md)|Určuje zdrojový soubor C++.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Určuje, že všechny zdrojové soubory jsou C++.|
|[/U](u-u-undefine-symbols.md)|Odebere předdefinovaná makra.|
|[/u](u-u-undefine-symbols.md)|Odebere všechny předdefinovaná makra.|
|[/UTF-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Sada zdroje a provádění znakových sad, na UTF-8.|
|[/V](v-version-number.md)|Zastaralé Nastaví řetězec verze souboru .obj.|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|Ověřte soubory pouze kompatibilní znaky znakové sady UTF-8.|
|[/vd](vd-disable-construction-displacements.md)|Potlačí nebo umožňuje členům třídy vtordisp skrytá.|
|[/vmb](vmb-vmg-representation-method.md)|Používá nejlépe základní ukazatelé na členy.|
|[/vmg](vmb-vmg-representation-method.md)|Úplné obecné používá pro ukazatelé na členy.|
|[/vmm](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje vícenásobná dědičnost.|
|[/vms](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje jedna dědičnost.|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje virtuální dědičnost.|
|[/ volatile](volatile-volatile-keyword-interpretation.md)|Vybere, jak interpretovat volatile – klíčové slovo.|
|[/w](compiler-option-warning-level.md)|Zakáže všechna upozornění.|
|[/W0, /W1, /W2, /W3, /W4](compiler-option-warning-level.md)|Nastaví kterou úroveň upozornění na výstup.|
|[/w1, /w2, /w3, /w4](compiler-option-warning-level.md)|Nastaví úroveň pro upozornění pro zadaný upozornění.|
|[/ Wall](compiler-option-warning-level.md)|Umožňuje všech upozornění, včetně upozornění, která jsou ve výchozím nastavení zakázané.|
|[/WD](compiler-option-warning-level.md)|Zakáže zadaný upozornění.|
|[/we](compiler-option-warning-level.md)|Zadaný upozornění považuje za chybu.|
|[/WL](wl-enable-one-line-diagnostics.md)|Umožňuje diagnostiku pro chybové zprávy a upozornění při kompilování zdrojového kódu C++ v příkazovém řádku.|
|[/wo](compiler-option-warning-level.md)|Zobrazí se zadané upozornění pouze jednou.|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|Zastaralé. Zjistí problémy s 64bitovou přenositelností.|
|[/Wv](compiler-option-warning-level.md)|Zobrazí žádná varování vyšších zadaná verze kompilátoru.|
|[/WX](compiler-option-warning-level.md)|Zpracovává všechny upozornění jako chyby.|
|[/X](x-ignore-standard-include-paths.md)|Ignoruje standardní zahrnout adresář.|
|[/Y-](y-ignore-precompiled-header-options.md)|Ignoruje všechny ostatní možnosti kompilátoru předkompilovaných hlaviček v aktuální sestavení.|
|[/Yc](yc-create-precompiled-header-file.md)|Vytvoří soubor předkompilovaných hlaviček.|
|[/Yd](yd-place-debug-information-in-object-file.md)|Zastaralé Místech dokončit ladicí informace ve všech souborů objektu. Použití [/Zi](z7-zi-zi-debug-information-format.md) místo.|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|Vloží referenci PCH při vytváření knihovna ladění|
|[/YU](yu-use-precompiled-header-file.md)|Předkompilovaný hlavičkový soubor se používá během vytváření sestavení.|
|[/Z7](z7-zi-zi-debug-information-format.md)|Generuje C 7.0 kompatibilní ladicí informace.|
|[/Za](za-ze-disable-language-extensions.md)|Zakáže jazyková rozšíření.|
|[/Zc](zc-conformance.md)|Určuje standardní chování pod [/Ze](za-ze-disable-language-extensions.md).[ / Za, /Ze (zakázat jazyková rozšíření)](za-ze-disable-language-extensions.md)|
|[/Ze](za-ze-disable-language-extensions.md)|Zastaralé Umožňuje jazyková rozšíření.|
|[/Zf](zf.md)|Zlepšuje PDB čas generování v paralelní sestavení.|
|[/Zg](zg-generate-function-prototypes.md)|Odebrat ve Visual C++ 2015. Generuje prototypy funkcí.|
|[/ZI](z7-zi-zi-debug-information-format.md)|Obsahuje informace o ladění do databáze kompatibilní s upravit a pokračovat v programu.|
|[/Zi](z7-zi-zi-debug-information-format.md)|Generuje kompletní informace o ladění.|
|[/Zl](zl-omit-default-library-name.md)|Odebere názvu výchozí knihovny ze souboru .obj (pouze x86).|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|Určuje omezení přidělení paměti pro předkompilované hlavičky.|
|[/Zp](zp-struct-member-alignment.md)|Balíčky struktury členy.|
|[/ZS](zs-syntax-check-only.md)|Pouze kontrola syntaxe.|
|[/ZW](zw-windows-runtime-compilation.md)|Vytvoří soubor výstupu pro spouštění v prostředí Windows Runtime.|

## <a name="see-also"></a>Viz také
 [Odkaz sestavení C/C++](c-cpp-building-reference.md) [– možnosti kompilátoru](compiler-options.md) [nastavení možností kompilátoru](setting-compiler-options.md)