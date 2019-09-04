---
title: Možnosti kompilátoru uvedené podle kategorie
ms.date: 08/08/2019
helpviewer_keywords:
- compiler options, C++
ms.assetid: c4750dcf-dba0-4229-99b6-45cdecc11729
ms.openlocfilehash: bfc9bb17100a3ee5c662062963c71ee532487239
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273709"
---
# <a name="compiler-options-listed-by-category"></a>Možnosti kompilátoru uvedené podle kategorie

Tento článek obsahuje seznam kategorií možností kompilátoru. Abecední seznam naleznete v tématu [Možnosti kompilátoru seřazené podle abecedy](compiler-options-listed-alphabetically.md).

## <a name="optimization"></a>Optimalizace

|Možnost|Účel|
|------------|-------------|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|Vytvoří malý kód.|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|Vytvoří rychlý kód.|
|[/Ob](ob-inline-function-expansion.md)|Ovládá vložené rozšíření.|
|[/Od](od-disable-debug.md)|Zakáže optimalizaci.|
|[/OG](og-global-optimizations.md)|Zastaralé Používá globální optimalizace.|
|[/Oi](oi-generate-intrinsic-functions.md)|Generuje vnitřní funkce.|
|[/OS](os-ot-favor-small-code-favor-fast-code.md)|Upřednostňuje malý kód.|
|[/Ot](os-ot-favor-small-code-favor-fast-code.md)|Upřednostňuje rychlý kód.|
|[/Ox](ox-full-optimization.md)|Podmnožina/O2, která neobsahuje/GF nebo/Gy.|
|[/Oy](oy-frame-pointer-omission.md)|Vynechá ukazatel na rámec. (jenom x86)|
|[/Favor](favor-optimize-for-architecture-specifics.md)|Vytvoří kód, který je optimalizován pro zadanou architekturu, nebo pro rozsah architektur.|

## <a name="code-generation"></a>Generování kódu

|Možnost|Účel|
|------------|-------------|
|[/Arch](arch-x86.md)|Použití SSE nebo SSE2 instrukcí při generování kódu. (jenom x86)|
|[možností](clr-common-language-runtime-compilation.md)|Vytvoří výstupní soubor pro spuštění v modulu CLR (Common Language Runtime).|
|[/EH](eh-exception-handling-model.md)|Určuje model zpracování výjimek.|
|[/fp](fp-specify-floating-point-behavior.md)|Určuje chování s plovoucí desetinnou čárkou.|
|[/GA](ga-optimize-for-windows-application.md)|Optimalizuje aplikace pro Windows.|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|Používá konvenci `__cdecl` volání. (jenom x86)|
|[/GE](ge-enable-stack-probes.md)|Zastaralé Aktivuje sondy zásobníku.|
|[/GF](gf-eliminate-duplicate-strings.md)|Povolí sdružování řetězců.|
|[/Gh](gh-enable-penter-hook-function.md)|Funkce `_penter`zavěšení volání.|
|[/GH](gh-enable-pexit-hook-function.md)|Funkce `_pexit`zavěšení volání.|
|[/GL](gl-whole-program-optimization.md)|Povoluje optimalizaci celého programu.|
|[/Gm](gm-enable-minimal-rebuild.md)|Zastaralé Povoluje minimální opětovné sestavení.|
|[/GR](gr-enable-run-time-type-information.md)|Povoluje informace o typu běhu (RTTI).|
|[/Gr](gd-gr-gv-gz-calling-convention.md)|Používá konvenci `__fastcall` volání. (jenom x86)|
|[/GS](gs-buffer-security-check.md)|Kontroluje zabezpečení vyrovnávací paměti.|
|[/Gs](gs-control-stack-checking-calls.md)|Řídí sondy zásobníku.|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|Podporuje bezpečnost vlákna pro data přidělená pomocí statického úložiště místního vlákna.|
|[/Guard: CF](guard-enable-control-flow-guard.md)|Přidá kontrolu zabezpečení ochrany toku řízení.|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|Používá konvenci `__vectorcall` volání. (jenom x86 a x64)|
|[/Gw](gw-optimize-global-data.md)|Povolí globální optimalizaci dat celého programu.|
|[/GX](gx-enable-exception-handling.md)|Zastaralé Povoluje synchronní zpracování výjimek. Místo toho použijte [/eh](eh-exception-handling-model.md) .|
|[/Gy](gy-enable-function-level-linking.md)|Povolí propojení na úrovni funkcí.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Zastaralé Umožňuje rychlé kontroly. (Stejné jako [/RTC1](rtc-run-time-error-checks.md))|
|[/Gz](gd-gr-gv-gz-calling-convention.md)|Používá konvenci `__stdcall` volání. (jenom x86)|
|[/homeparams](homeparams-copy-register-parameters-to-stack.md)|Vynutí zapsání parametrů předaných v registrech do jejich umístění v zásobníku při zadání funkce. Tato možnost kompilátoru je určena pouze pro kompilátory x64 (nativní a příčná kompilace).|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|Vytvoří obrázek opravitelnou za provozu.|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|Generuje rychle transcendentní objekty.|
|[/QIfist](qifist-suppress-ftol.md)|Zastaralé Potlačí volání pomocné funkce `_ftol` , je-li vyžadován převod z typu s plovoucí desetinnou čárkou na integrální typ. (jenom x86)|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Odebere `fwait` příkazy uvnitř `try` bloků.|
|[/Qpar](qpar-auto-parallelizer.md)|Povoluje automatické paralelismuing smyček.|
|[/Qpar-report](qpar-report-auto-parallelizer-reporting-level.md)|Povoluje úrovně generování sestav pro automatické paralelismus.|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|Používá pro hodnoty s plovoucí desetinnou čárkou pokyny k přesunutí celého čísla a zakáže některé optimalizace načítání s plovoucí desetinnou čárkou.|
|[/Qspectre](qspectre.md)|Pro třídu útoků Spectre povolte omezení pro CVE 2017-5753.|
|[/Qvec-report](qvec-report-auto-vectorizer-reporting-level.md)|Povoluje generování úrovní pro automatické rozkládání.|
|[/RTC](rtc-run-time-error-checks.md)|Povoluje kontrolu chyb v době běhu.|
|[/volatile](volatile-volatile-keyword-interpretation.md)|Vybere způsob interpretace klíčového slova volatile.|

## <a name="output-files"></a>Výstupní soubory

|Možnost|Účel|
|------------|-------------|
|[/doc](doc-process-documentation-comments-c-cpp.md)|Zpracuje komentáře dokumentace do souboru XML.|
|[/FA](fa-fa-listing-file.md)|Nakonfiguruje soubor výpisu sestavení.|
|[/Fa](fa-fa-listing-file.md)|Vytvoří soubor výpisu sestavení.|
|[/Fd](fd-program-database-file-name.md)|Přejmenuje soubor databáze programu.|
|[/FE](fe-name-exe-file.md)|Přejmenuje spustitelný soubor.|
|[/Fi](fi-preprocess-output-file-name.md)|Určuje název předzpracovaného výstupního souboru.|
|[/Fm](fm-name-mapfile.md)|Vytvoří souboru mapování.|
|[/Fo](fo-object-file-name.md)|Vytvoří soubor objektu.|
|[/Fp](fp-name-dot-pch-file.md)|Určuje název souboru předkompilované hlavičky.|
|[/FR, /Fr](fr-fr-create-dot-sbr-file.md)|Název byl vygenerován. SBR soubory prohlížeče.|

## <a name="preprocessor"></a>Preprocesor

|Možnost|Účel|
|------------|-------------|
|[/AI](ai-specify-metadata-directories.md)|Určuje adresář, ve kterém se mají hledat odkazy na soubory předané direktivě [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/C](c-preserve-comments-during-preprocessing.md)|Zachovává komentáře během předběžného zpracování.|
|[/D](d-preprocessor-definitions.md)|Definuje konstanty a makra.|
|[/E](e-preprocess-to-stdout.md)|Zkopíruje výstup preprocesoru do standardního výstupu.|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Zkopíruje výstup preprocesoru do standardního výstupu.|
|[/FI](fi-name-forced-include-file.md)|Předzpracovává zadaný soubor k zahrnutí.|
|[/FU](fu-name-forced-hash-using-file.md)|Vynutí použití názvu souboru, jako kdyby byl předán direktivě [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/Fx](fx-merge-injected-code.md)|Sloučí vložený kód se zdrojovým souborem.|
|[/I](i-additional-include-directories.md)|Vyhledá v adresáři soubory k zahrnutí.|
|[/P](p-preprocess-to-a-file.md)|Zapisuje výstup preprocesoru do souboru.|
|[/U](u-u-undefine-symbols.md)|Odebere předdefinované makro.|
|[/u](u-u-undefine-symbols.md)|Odebere všechna Předdefinovaná makra.|
|[/X](x-ignore-standard-include-paths.md)|Ignoruje standardní adresář include.|

## <a name="language"></a>Jazyk

|Možnost|Účel|
|------------|-------------|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Řídí vyhodnocení constexpr v době kompilace.|
|[/OpenMP](openmp-enable-openmp-2-0-support.md)|Povolí [#pragma omp](../../preprocessor/omp.md) ve zdrojovém kódu.|
|[/vd](vd-disable-construction-displacements.md)|Potlačí nebo povolí skryté `vtordisp` členy třídy.|
|[/vmb](vmb-vmg-representation-method.md)|Používá nejlepší základ pro ukazatele na členy.|
|[/vmg](vmb-vmg-representation-method.md)|Používá úplný obec pro ukazatele na členy.|
|[/vmm](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje vícenásobnou dědičnost.|
|[/vms](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje jednoduchou dědičnost.|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje virtuální dědění.|
|[/Z7](z7-zi-zi-debug-information-format.md)|Generuje ladicí informace kompatibilní s C 7,0.|
|[/Za](za-ze-disable-language-extensions.md)|Zakáže jazyková rozšíření c89.|
|[/Zc](zc-conformance.md)|Určuje standardní chování v rámci [/ze](za-ze-disable-language-extensions.md).|
|[/Ze](za-ze-disable-language-extensions.md)|Zastaralé Povolí c89 jazyková rozšíření.|
|[/Zf](zf.md)|Vylepšuje čas generování PDB v paralelních sestaveních.|
|[/ZI](z7-zi-zi-debug-information-format.md)|Obsahuje informace o ladění v databázi programu kompatibilní s úpravou a pokračováním. (jenom x86)|
|[/Zi](z7-zi-zi-debug-information-format.md)|Vygeneruje úplné ladicí informace.|
|[/Zl](zl-omit-default-library-name.md)|Odstraní výchozí název knihovny ze souboru. obj.|
|[/Zp](zp-struct-member-alignment.md) *n*|Balíčky členů struktury.|
|[/Zs](zs-syntax-check-only.md)|Kontroluje pouze syntaxi.|
|[/ZW](zw-windows-runtime-compilation.md)|Vytvoří výstupní soubor pro spuštění na prostředí Windows Runtime.|

## <a name="linking"></a>Propojení

|Možnost|Účel|
|------------|-------------|
|[/F](f-set-stack-size.md)|Nastaví velikost zásobníku.|
|[/LD](md-mt-ld-use-run-time-library.md)|Vytvoří dynamickou knihovnu.|
|[/LDd](md-mt-ld-use-run-time-library.md)|Vytvoří dynamickou knihovnu pro ladění.|
|[/link](link-pass-options-to-linker.md)|Předá zadanou možnost propojení.|
|[/LN](ln-create-msil-module.md)|Vytvoří modul MSIL.|
|[/MD](md-mt-ld-use-run-time-library.md)|Zkompiluje pro vytvoření vícevláknové knihovny DLL pomocí MSVCRT. lib.|
|[/MDd](md-mt-ld-use-run-time-library.md)|Zkompiluje pro vytvoření vícevláknové knihovny DLL ladění pomocí MSVCRTD. lib.|
|[/MT](md-mt-ld-use-run-time-library.md)|Zkompiluje pro vytvoření vícevláknového spustitelného souboru pomocí LIBCMT. lib.|
|[/MTd](md-mt-ld-use-run-time-library.md)|Zkompiluje pro vytvoření vícevláknového spustitelného souboru ladění pomocí LIBCMTD. lib.|

## <a name="miscellaneous"></a>Různé

|Možnost|Účel|
|------------|-------------|
|[/?](help-compiler-command-line-help.md)|Zobrazí seznam možností kompilátoru.|
|[@](at-specify-a-compiler-response-file.md)|Určuje soubor odpovědí.|
|[/Analyze](analyze-code-analysis.md)|Povolí analýzu kódu.|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|Zvýší počet adresovatelných oddílů v souboru. obj.|
|[/c](c-compile-without-linking.md)|Zkompiluje bez propojení.|
|[/cgthreads](cgthreads-code-generation-threads.md)|Určuje počet vláken CL. exe, který se má použít pro optimalizaci a generování kódu.|
|[/errorReport](errorreport-report-internal-compiler-errors.md)|Umožňuje poskytnout informace o vnitřní chybě kompilátoru (ICE) přímo týmu společnosti Microsoft C++ .|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|Zobrazí úplnou cestu souborů se zdrojovým kódem předaných do cl. exe v diagnostickém textu.|
|[/FS](fs-force-synchronous-pdb-writes.md)|Vynutí zápisy do souboru databáze programu (PDB) k serializaci pomocí MSPDBSRV. Programu.|
|[/H](h-restrict-length-of-external-names.md)|Zastaralé Omezuje délku externích (veřejných) názvů.|
|[/HELP](help-compiler-command-line-help.md)|Zobrazí seznam možností kompilátoru.|
|[/J](j-default-char-type-is-unsigned.md)|Změní výchozí `char` typ.|
|[/JMC](jmc.md)|Podporuje ladění C++ nativního pouze můj kód.|
|[/kernel](kernel-create-kernel-mode-binary.md)|Kompilátor a linker vytvoří binární soubor, který bude možné spustit v jádru systému Windows.|
|[/MP](mp-build-with-multiple-processes.md)|Souběžně sestaví více zdrojových souborů.|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|Potlačí zobrazení nápisu přihlášení.|
|[/sdl](sdl-enable-additional-security-checks.md)|Povolí další funkce zabezpečení a upozornění.|
|[/showIncludes](showincludes-list-include-files.md)|Zobrazí seznam všech vložených souborů během kompilace.|
|[/Tc](tc-tp-tc-tp-specify-source-file-type.md)|Určuje zdrojový soubor jazyka C.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Určuje, že všechny zdrojové soubory jsou C.|
|[/Tp](tc-tp-tc-tp-specify-source-file-type.md)|Určuje C++ zdrojový soubor.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Určuje všechny zdrojové soubory C++.|
|[/V](v-version-number.md)|Zastaralé Nastaví řetězec verze.|
|[/w](compiler-option-warning-level.md)|Zakáže všechna upozornění.|
|[/W0, /W1, /W2, /W3, /W4](compiler-option-warning-level.md)|Nastaví úroveň upozornění na výstup.|
|[/w1, /w2, /w3, /w4](compiler-option-warning-level.md)|Nastaví úroveň upozornění pro zadané upozornění.|
|[/Wall](compiler-option-warning-level.md)|Povolí všechna upozornění, včetně upozornění, která jsou ve výchozím nastavení zakázaná.|
|[/wd](compiler-option-warning-level.md)|Zakáže zadané upozornění.|
|[/We](compiler-option-warning-level.md)|Zpracuje zadané upozornění jako chybu.|
|[/WL](wl-enable-one-line-diagnostics.md)|Povoluje jednořádkový diagnostiku pro chybové zprávy a upozornění při kompilování C++ zdrojového kódu z příkazového řádku.|
|[/wo](compiler-option-warning-level.md)|Zobrazí zadané upozornění pouze jednou.|
|[/Wv](compiler-option-warning-level.md)|Zakáže upozornění zavedená novějšími verzemi kompilátoru.|
|[/WX](compiler-option-warning-level.md)|Zpracovává upozornění jako chyby.|
|[/Yc](yc-create-precompiled-header-file.md)|Vytvořeny. Soubor PCH.|
|[/Yd](yd-place-debug-information-in-object-file.md)|Zastaralé Umístí úplné informace o ladění do všech objektových souborů. Místo toho použijte [/Zi](z7-zi-zi-debug-information-format.md) .|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|Vloží odkaz PCH při vytváření knihovny ladění.|
|[/Yu](yu-use-precompiled-header-file.md)|Při sestavování používá předkompilovaný hlavičkový soubor.|
|[/Y-](y-ignore-precompiled-header-options.md)|Ignoruje všechny ostatní možnosti kompilátoru předkompilované hlavičky v aktuálním sestavení.|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|Určuje limit přidělení paměti předkompilovaných hlaviček.|
|[/await](await-enable-coroutine-support.md)|Povolte rozšíření korutiny (obnovitelné funkce).|
|[/source-charset](source-charset-set-source-character-set.md)|Nastavte zdrojovou znakovou sadu.|
|[/execution-charset](execution-charset-set-execution-character-set.md)|Nastavit znakovou sadu spuštění.|
|[/utf-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Nastavte zdrojové a spouštěcí znakové sady na UTF-8.|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|Ověří soubory UTF-8 pouze pro kompatibilní znaky.|
|[/Diagnostics](diagnostics-compiler-diagnostic-options.md)|Určuje formát diagnostických zpráv.|
|[/Permissive-](permissive-standards-conformance.md)|Nastavte režim pro shodu Standard.|
|[/STD](std-specify-language-standard-version.md)|C++Výběr kompatibility standardní verze|

## <a name="experimental-options"></a>Experimentální možnosti

Experimentální možnosti mohou být podporovány pouze některými verzemi kompilátoru a mohou se chovat odlišně v různých verzích kompilátoru. Nejlepší nebo pouze dokumentace pro experimentální možnosti je často na [blogu týmu společnosti Microsoft C++ ](https://devblogs.microsoft.com/cppblog/).

|Možnost|Účel|
|------------|-------------|
|[/Experimental: modul](experimental-module.md)|Povolí experimentální podporu modulu.|
|[/Experimental: preprocesor](experimental-preprocessor.md)|Povoluje experimentální vyhovující s podporou preprocesoru.|

## <a name="deprecated-and-removed-compiler-options"></a>Zastaralé a odebrané možnosti kompilátoru

|Možnost|Účel|
|------------|-------------|
|[/CLR: sestavení](clr-common-language-runtime-compilation.md)|Zastaralé Místo toho použijte [/ln (vytvořit modul MSIL)](ln-create-msil-module.md) .|
|[/Fr](fr-fr-create-dot-sbr-file.md)|Zastaralé Vytvoří soubor s informacemi o procházení bez místních proměnných.|
|[/GE](ge-enable-stack-probes.md)|Zastaralé Aktivuje sondy zásobníku. Ve výchozím nastavení zapnuto.|
|[/Gm](gm-enable-minimal-rebuild.md)|Zastaralé Povoluje minimální opětovné sestavení.|
|[/GX](gx-enable-exception-handling.md)|Zastaralé Povoluje synchronní zpracování výjimek. Místo toho použijte [/eh](eh-exception-handling-model.md) .|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Zastaralé Umožňuje rychlé kontroly. Místo toho použijte [/RTC1](rtc-run-time-error-checks.md) .|
|[/H](h-restrict-length-of-external-names.md)|Zastaralé Omezuje délku externích (veřejných) názvů.|
|[/OG](og-global-optimizations.md)|Zastaralé Používá globální optimalizace.|
|[/QIfist](qifist-suppress-ftol.md)|Zastaralé Slouží k určení způsobu převodu z typu s plovoucí desetinnou čárkou na celočíselný typ.|
|[/V](v-version-number.md)|Zastaralé Nastaví řetězec verze souboru. obj.|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|Zastaralé. Detekuje problémy s přenositelností 64 bitů.|
|[/Yd](yd-place-debug-information-in-object-file.md)|Zastaralé Umístí úplné informace o ladění do všech objektových souborů. Místo toho použijte [/Zi](z7-zi-zi-debug-information-format.md) .|
|[/Zc:forScope-](zc-forscope-force-conformance-in-for-loop-scope.md)|Zastaralé Zakáže shodu v oboru for Loop.|
|[/Ze](za-ze-disable-language-extensions.md)|Zastaralé Povolí jazykové rozšíření.|
|[/Zg](zg-generate-function-prototypes.md)|Odebráno v aplikaci Visual Studio 2015. Generuje prototypy funkcí.|

## <a name="see-also"></a>Viz také:

[Referenční zdroje k sestavení programu v jazyce C/C++](c-cpp-building-reference.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
