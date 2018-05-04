---
title: Možnosti kompilátoru uvedené podle kategorie | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiler options, C++
ms.assetid: c4750dcf-dba0-4229-99b6-45cdecc11729
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fff661bf573ca30a5b0e7550c2e53b00a7ff3d8f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="compiler-options-listed-by-category"></a>Možnosti kompilátoru uvedené podle kategorie

Tento článek obsahuje seznam kategorií možností kompilátoru. Abecední seznam najdete v tématu [možnosti kompilátoru uvedené abecedně](compiler-options-listed-alphabetically.md).

### <a name="optimization"></a>Optimalizace

|Možnost|Účel|
|------------|-------------|
|[/ O1](o1-o2-minimize-size-maximize-speed.md)|Vytvoří malý kód.|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|Vytvoří rychlý kód.|
|[/Ob](ob-inline-function-expansion.md)|Vložené rozšíření ovládacích prvků.|
|[/Od](od-disable-debug.md)|Zakáže optimalizace.|
|[/Og](og-global-optimizations.md)|Zastaralé Využívá globální optimalizace.|
|[/OI](oi-generate-intrinsic-functions.md)|Generuje vnitřní funkce.|
|[/OS](os-ot-favor-small-code-favor-fast-code.md)|Upřednostňuje malý kód.|
|[/Ot](os-ot-favor-small-code-favor-fast-code.md)|Favors rychlý kód.|
|[/OX](ox-full-optimization.md)|Používá maximální optimalizace (nebo Ob2gity /Gs).|
|[/Oy](oy-frame-pointer-omission.md)|Vynechá ukazatel na rámec. (jenom x86)|
|[/ favor](favor-optimize-for-architecture-specifics.md)|Vytvoří kód, který je optimalizovaná pro zadaný architekturu nebo pro celou řadu architektur.|

### <a name="code-generation"></a>Generování kódu

|Možnost|Účel|
|------------|-------------|
|[/ arch](arch-x86.md)|Použijte SSE nebo SSE2 pokyny v generování kódu. (jenom x86)|
|[/ CLR](clr-common-language-runtime-compilation.md)|Vytvoří výstupního souboru ke spuštění na modul common language runtime.|
|[/EH](eh-exception-handling-model.md)|Určuje model zpracování výjimek.|
|[/fp](fp-specify-floating-point-behavior.md)|Určuje chování s plovoucí desetinnou čárkou.|
|[/GA](ga-optimize-for-windows-application.md)|Optimalizovaný pro aplikace systému Windows.|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|Používá `__cdecl` konvence volání. (jenom x86)|
|[/Ge](ge-enable-stack-probes.md)|Zastaralé Aktivuje sondy zásobníku.|
|[/GF](gf-eliminate-duplicate-strings.md)|Umožňuje sdružování řetězec.|
|[/Gh](gh-enable-penter-hook-function.md)|Funkce háku volání `_penter`.|
|[/GH](gh-enable-pexit-hook-function.md)|Funkce háku volání `_pexit`.|
|[/GL](gl-whole-program-optimization.md)|Umožňuje optimalizace celého programu.|
|[/Gm](gm-enable-minimal-rebuild.md)|Umožňuje minimální opětovné sestavení.|
|[/GR](gr-enable-run-time-type-information.md)|Umožňuje informace běhového typu (RTTI).|
|[GR](gd-gr-gv-gz-calling-convention.md)|Používá `__fastcall` konvence volání. (jenom x86)|
|[/GS](gs-buffer-security-check.md)|Kontroly vyrovnávací paměti zabezpečení.|
|[/Gs](gs-control-stack-checking-calls.md)|Sondy zásobníku ovládací prvky.|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|Podporuje zabezpečení fiber pro data přidělené pomocí statické úložiště thread-local.|
|[/Guard:CF](guard-enable-control-flow-guard.md)|Přidá kontroly zabezpečení ochrany toku řízení.|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|Používá `__vectorcall` konvence volání. (x86 a x64 pouze)|
|[/Gw](gw-optimize-global-data.md)|Umožňuje optimalizace celého programu globální data.|
|[/GX](gx-enable-exception-handling.md)|Zastaralé Umožňuje synchronní zpracování výjimek. Použití [/EH](eh-exception-handling-model.md) místo.|
|[/Gy](gy-enable-function-level-linking.md)|Povoluje funkce úrovni propojení.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Zastaralé Umožňuje rychlé kontroly. (Stejné jako [RTC1](rtc-run-time-error-checks.md))|
|[/Gz](gd-gr-gv-gz-calling-convention.md)|Používá `__stdcall` konvence volání. (jenom x86)|
|[/ homeparams](homeparams-copy-register-parameters-to-stack.md)|Vynutí parametry předané zaregistruje k zápisu na jejich umístění v zásobníku při vstupu funkce. Tato možnost kompilátoru je pouze pro [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] kompilátory (nativní a multiplatformní kompilace).|
|[/ hotpatch](hotpatch-create-hotpatchable-image.md)|Vytvoří kopii opravitelnou za provozu.|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|Generuje rychlé Transcendentní objekty.|
|[QIfist](qifist-suppress-ftol.md)|Zastaralé Potlačí volání pomocné funkce `_ftol` po vyžaduje převod z typu s plovoucí desetinnou čárkou integrální typu. (jenom x86)|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Odebere `fwait` příkazy uvnitř `try` bloky.|
|[/ Qpar](qpar-auto-parallelizer.md)|Umožňuje automatické paralelizace smyčky.|
|[/Qpar-report](qpar-report-auto-parallelizer-reporting-level.md)|Umožňuje vytváření sestav úrovní Automatická paralelizace.|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|Používá celé číslo přesunutí pokyny pro hodnoty s plovoucí desetinnou čárkou a zakáže určité plovoucí optimalizace zatížení bodu.|
|[/Qspectre](qspectre.md)|Povolte jejich zmírnění pro CVE 2017-5753 pro třídu spektrum útoků.|
|[/ Qvec-report](qvec-report-auto-vectorizer-reporting-level.md)|Umožňuje vytváření sestav úrovně pro automatické vectorization.|
|[/RTC](rtc-run-time-error-checks.md)|Umožňuje Kontrola chyb za běhu.|
|[/ volatile](volatile-volatile-keyword-interpretation.md)|Vybere, jak interpretovat volatile – klíčové slovo.|

### <a name="output-files"></a>Výstupní soubory

|Možnost|Účel|
|------------|-------------|
|[/doc](doc-process-documentation-comments-c-cpp.md)|Zpracuje dokumentační komentáře do souboru XML.|
|[/FA](fa-fa-listing-file.md)|Nakonfiguruje výpis souboru sestavení.|
|[/Fa](fa-fa-listing-file.md)|Vytvoří seznam souboru sestavení.|
|[/FD](fd-program-database-file-name.md)|Přejmenuje soubor databáze programu.|
|[/FE](fe-name-exe-file.md)|Přejmenuje spustitelný soubor.|
|[/Fi](fi-preprocess-output-file-name.md)|Určuje název předběžně zpracované výstupního souboru.|
|[/Fm](fm-name-mapfile.md)|Vytvoří souboru mapování.|
|[/FO](fo-object-file-name.md)|Vytvoří soubor objektu.|
|[/Fp](fp-name-dot-pch-file.md)|Určuje název souboru předkompilovaných hlaviček.|
|[/ FR, /Fr](fr-fr-create-dot-sbr-file.md)|Název generované soubory .sbr prohlížeče.|

### <a name="preprocessor"></a>Preprocesor

|Možnost|Účel|
|------------|-------------|
|[/AI](ai-specify-metadata-directories.md)|Určuje adresář, který chcete vyhledávat předaný odkazů na soubor [#using](../../preprocessor/hash-using-directive-cpp.md) – direktiva.|
|[/C](c-preserve-comments-during-preprocessing.md)|Zachovává komentáře při předběžném zpracování.|
|[/D](d-preprocessor-definitions.md)|Definuje konstanty a makra.|
|[/E](e-preprocess-to-stdout.md)|Výstup preprocesoru kopie standardním výstupu.|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Výstup preprocesoru kopie standardním výstupu.|
|[/FI](fi-name-forced-include-file.md)|Upraví zadaný soubor.|
|[/FU](fu-name-forced-hash-using-file.md)|Vynutí použití název souboru, jako kdyby měl byla předána [#using](../../preprocessor/hash-using-directive-cpp.md) – direktiva.|
|[/Fx](fx-merge-injected-code.md)|Sloučení vloženého kódu se zdrojový soubor.|
|[/I](i-additional-include-directories.md)|Vyhledá adresář pro zahrnout soubory.|
|[/P](p-preprocess-to-a-file.md)|Výstup preprocesoru zapisuje do souboru.|
|[/U](u-u-undefine-symbols.md)|Odebere předdefinovaná makra.|
|[/u](u-u-undefine-symbols.md)|Odebere všechny předdefinovaná makra.|
|[/X](x-ignore-standard-include-paths.md)|Ignoruje standardní zahrnout adresář.|

### <a name="language"></a>Jazyk

|Možnost|Účel|
|------------|-------------|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Vyhodnocení constexpr ovládacího prvku v době kompilace.|
|[/ OpenMP](openmp-enable-openmp-2-0-support.md)|Umožňuje [omp – #pragma](../../preprocessor/omp.md) ve zdrojovém kódu.|
|[/vd](vd-disable-construction-displacements.md)|Potlačí nebo umožňuje Skrytá `vtordisp` třídy členy.|
|[/vmb](vmb-vmg-representation-method.md)|Používá nejlépe základní ukazatelé na členy.|
|[/vmg](vmb-vmg-representation-method.md)|Úplné obecné používá pro ukazatelé na členy.|
|[/vmm](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje vícenásobná dědičnost.|
|[/vms](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje jedna dědičnost.|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje virtuální dědičnost.|
|[/Z7](z7-zi-zi-debug-information-format.md)|Generuje C 7.0 kompatibilní ladicí informace.|
|[/Za](za-ze-disable-language-extensions.md)|Zakáže jazyková rozšíření.|
|[/Zc](zc-conformance.md)|Určuje standardní chování pod [/Ze](za-ze-disable-language-extensions.md).|
|[/Ze](za-ze-disable-language-extensions.md)|Zastaralé Umožňuje jazyková rozšíření.|
|[/Zf](zf.md)|Zlepšuje PDB čas generování v paralelní sestavení.|
|[/ZI](z7-zi-zi-debug-information-format.md)|Obsahuje informace o ladění do databáze kompatibilní s upravit a pokračovat v programu. (jenom x86)|
|[/Zi](z7-zi-zi-debug-information-format.md)|Generuje kompletní informace o ladění.|
|[/Zl](zl-omit-default-library-name.md)|Odebere ze souboru .obj názvu výchozí knihovny.|
|[/Zp](zp-struct-member-alignment.md) *n*|Balíčky struktury členy.|
|[/ZS](zs-syntax-check-only.md)|Pouze kontrola syntaxe.|
|[/ZW](zw-windows-runtime-compilation.md)|Vytvoří soubor výstupu pro spouštění v prostředí Windows Runtime.|

### <a name="linking"></a>Propojení

|Možnost|Účel|
|------------|-------------|
|[/F](f-set-stack-size.md)|Nastaví zásobníku velikost.|
|[/LD](md-mt-ld-use-run-time-library.md)|Vytvoří knihovnu DLL.|
|[/ LDd](md-mt-ld-use-run-time-library.md)|Vytvoří knihovnu DLL ladění.|
|[/link](link-pass-options-to-linker.md)|Předá Zadaná možnost propojení.|
|[/LN](ln-create-msil-module.md)|Vytvoří modul MSIL.|
|[/MD](md-mt-ld-use-run-time-library.md)|Zkompiluje k vytvoření vícevláknové knihovny DLL pomocí MSVCRT.lib.|
|[/ MDd](md-mt-ld-use-run-time-library.md)|Zkompiluje k vytvoření ladění vícevláknové knihovny DLL pomocí MSVCRTD.lib.|
|[/MT](md-mt-ld-use-run-time-library.md)|Zkompiluje k vytvoření s více vlákny spustitelný soubor, pomocí LIBCMT.lib.|
|[/MTd](md-mt-ld-use-run-time-library.md)|Zkompiluje k vytvoření ladění vícevláknové spustitelný soubor pomocí LIBCMTD.lib.|

### <a name="miscellaneous"></a>Různé

|Možnost|Účel|
|------------|-------------|
|[/?](help-compiler-command-line-help.md)|Zobrazí seznam možností kompilátoru.|
|[@](at-specify-a-compiler-response-file.md)|Určuje soubor odezvy.|
|[/ analyze](analyze-code-analysis.md)|Analýza kódu umožňuje.|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|Zvyšuje počet adresovatelné oddílů v souboru .obj.|
|[/c](c-compile-without-linking.md)|Zkompiluje bez propojení.|
|[/ cgthreads](cgthreads-code-generation-threads.md)|Určuje počet vláken cl.exe pro optimalizace a generování kódu.|
|[/ errorreport](errorreport-report-internal-compiler-errors.md)|Umožňuje zadat informace o chybě (LED) interní kompilátoru přímo do týmu Visual C++.|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|Zobrazí úplnou cestu předaný cl.exe v diagnostických textové soubory zdrojového kódu.|
|[/FS](fs-force-synchronous-pdb-writes.md)|Vynutí zapisuje do souboru databáze (PDB) program k serializaci prostřednictvím MSPDBSRV. SOUBOR EXE.|
|[/H](h-restrict-length-of-external-names.md)|Zastaralé Omezuje délku externích názvů (veřejné).|
|[/ HELP](help-compiler-command-line-help.md)|Zobrazí seznam možností kompilátoru.|
|[/J](j-default-char-type-is-unsigned.md)|Změní výchozí `char` typu.|
|[/kernel](kernel-create-kernel-mode-binary.md)|Kompilátoru a linkeru vytvoří binární soubor, který lze spustit v jádru systému Windows.|
|[/MP](mp-build-with-multiple-processes.md)|Sestaví víc souborů současně.|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|Potlačí zobrazení nápisu přihlášení.|
|[/sdl](sdl-enable-additional-security-checks.md)|Povoluje další funkce zabezpečení a upozornění.|
|[/ showincludes vložených](showincludes-list-include-files.md)|Zobrazí seznam všech zahrnují souborů během kompilace.|
|[/Tc](tc-tp-tc-tp-specify-source-file-type.md)|Určuje zdrojový soubor C.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Určuje, že všechny zdrojové soubory jsou C.|
|[/Tp](tc-tp-tc-tp-specify-source-file-type.md)|Určuje zdrojový soubor C++.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Určuje, že všechny zdrojové soubory jsou C++.|
|[/V](v-version-number.md)|Zastaralé Nastaví řetězec verze.|
|[/w](compiler-option-warning-level.md)|Zakáže všechna upozornění.|
|[/W0, /W1, /W2, /W3, /W4](compiler-option-warning-level.md)|Nastaví výstup úroveň pro upozornění.|
|[/w1, /w2, /w3, /w4](compiler-option-warning-level.md)|Nastaví úroveň pro upozornění na zadaný varování.|
|[/ Wall](compiler-option-warning-level.md)|Umožňuje všech upozornění, včetně upozornění, která jsou ve výchozím nastavení zakázané.|
|[/WD](compiler-option-warning-level.md)|Zakáže zadaný upozornění.|
|[/we](compiler-option-warning-level.md)|Zadaný upozornění považuje za chybu.|
|[/WL](wl-enable-one-line-diagnostics.md)|Umožňuje diagnostiku pro chybové zprávy a upozornění při kompilování zdrojového kódu C++ v příkazovém řádku.|
|[/wo](compiler-option-warning-level.md)|Zobrazí se zadané upozornění pouze jednou.|
|[/Wv](compiler-option-warning-level.md)|Zakáže upozornění zavedených v novějších verzích kompilátoru.|
|[/WX](compiler-option-warning-level.md)|Zpracovává upozornění jako chyby.|
|[/Yc](yc-create-precompiled-header-file.md)|Vytvořte. PCH soubor.|
|[/Yd](yd-place-debug-information-in-object-file.md)|Zastaralé Místech dokončit ladicí informace ve všech souborů objektu. Použití [/Zi](z7-zi-zi-debug-information-format.md) místo.|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|Vloží referenci PCH při vytváření ladicí knihovny.|
|[/YU](yu-use-precompiled-header-file.md)|Předkompilovaný hlavičkový soubor se používá během vytváření sestavení.|
|[/Y-](y-ignore-precompiled-header-options.md)|Ignoruje všechny ostatní možnosti kompilátoru předkompilovaných hlaviček v aktuální sestavení.|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|Určuje omezení přidělení paměti pro předkompilované hlavičky.|
|[/ await](await-enable-coroutine-support.md)|Povolte rozšíření coroutines (odesílání funkce).|
|[/source-charset](source-charset-set-source-character-set.md)|Sada zdroj znakovou sadu.|
|[/execution-charset](execution-charset-set-execution-character-set.md)|Znaková sada spuštění sady.|
|[/UTF-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Sada zdroje a provádění znakových sad, na UTF-8.|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|Ověřte soubory pouze kompatibilní znaky znakové sady UTF-8.|
|[/Diagnostics](diagnostics-compiler-diagnostic-options.md)|Určuje formát diagnostické zprávy.|
|[/ projektovou-](permissive-standards-conformance.md)|Nastavit režim standard shoda.|
|[/std](std-specify-language-standard-version.md)|C++ standardní verzi kompatibility selektor.|

### <a name="deprecated-and-removed-compiler-options"></a>Možnosti kompilátoru zastaralé a odebrání

|Možnost|Účel|
|------------|-------------|
|[/CLR:noAssembly](clr-common-language-runtime-compilation.md)|Zastaralé Použití [/LN (vytvořit modul MSIL)](ln-create-msil-module.md) místo.|
|[/FR](fr-fr-create-dot-sbr-file.md)|Zastaralé Vytvoří soubor s informacemi o procházení bez místní proměnné.|
|[/Ge](ge-enable-stack-probes.md)|Zastaralé Aktivuje sondy zásobníku. Na ve výchozím nastavení.|
|[/GX](gx-enable-exception-handling.md)|Zastaralé Umožňuje synchronní zpracování výjimek. Použití [/EH](eh-exception-handling-model.md) místo.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Zastaralé Umožňuje rychlé kontroly. Použití [RTC1](rtc-run-time-error-checks.md) místo.|
|[/H](h-restrict-length-of-external-names.md)|Zastaralé Omezuje délku externích názvů (veřejné).|
|[/Og](og-global-optimizations.md)|Zastaralé Využívá globální optimalizace.|
|[QIfist](qifist-suppress-ftol.md)|Zastaralé Jednou umožňuje zadat, jak převést na typ integrální z typu s plovoucí desetinnou čárkou.|
|[/V](v-version-number.md)|Zastaralé Nastaví řetězec verze souboru .obj.|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|Zastaralé. Zjistí problémy s 64bitovou přenositelností.|
|[/Yd](yd-place-debug-information-in-object-file.md)|Zastaralé Místech dokončit ladicí informace ve všech souborů objektu. Použití [/Zi](z7-zi-zi-debug-information-format.md) místo.|
|[/Zc:forScope-](zc-forscope-force-conformance-in-for-loop-scope.md)|Zastaralé Zakáže shoda v pro obor cyklu for.|
|[/Ze](za-ze-disable-language-extensions.md)|Zastaralé Umožňuje jazyková rozšíření.|
|[/Zg](zg-generate-function-prototypes.md)|Odebrat ve Visual C++ 2015. Generuje prototypy funkcí.|

## <a name="see-also"></a>Viz také

[Referenční zdroje k sestavení programu v jazyce C/C++](c-cpp-building-reference.md)<br/>
[Možnosti kompilátoru](compiler-options.md)<br/>
[Nastavení možností kompilátoru](setting-compiler-options.md)<br/>
