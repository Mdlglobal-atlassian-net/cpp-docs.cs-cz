---
title: Možnosti kompilátoru (abecední pořadí)
ms.date: 01/08/2020
helpviewer_keywords:
- compiler options, C++
ms.openlocfilehash: d64a41802c18627cf8e07f0d83b53fa5a4555f5b
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2020
ms.locfileid: "77034594"
---
# <a name="compiler-options-listed-alphabetically"></a>Možnosti kompilátoru (abecední pořadí)

Následuje úplný Abecední seznam možností kompilátoru. Seznam kategorií naleznete v tématu [Možnosti kompilátoru uvedené podle kategorie](compiler-options-listed-by-category.md).

|Možnost|Účel|
|------------|-------------|
|[@](at-specify-a-compiler-response-file.md)|Určuje soubor odpovědí.|
|[/?](help-compiler-command-line-help.md)|Zobrazí seznam možností kompilátoru.|
|[/AI](ai-specify-metadata-directories.md)|Určuje adresář, ve kterém se mají hledat odkazy na soubory předané direktivě [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/Analyze](analyze-code-analysis.md)|Povolit analýzu kódu.|
|[/Arch](arch-minimum-cpu-architecture.md)|Určuje architekturu pro generování kódu.|
|[/await](await-enable-coroutine-support.md)|Povolte rozšíření korutiny (obnovitelné funkce).|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|Zvýší počet adresovatelných oddílů v souboru. obj.|
|[/C](c-preserve-comments-during-preprocessing.md)|Zachovává komentáře během předběžného zpracování.|
|[/c](c-compile-without-linking.md)|Zkompiluje bez propojení.|
|[/cgthreads](cgthreads-code-generation-threads.md)|Určuje počet vláken CL. exe, který se má použít pro optimalizaci a generování kódu.|
|[možností](clr-common-language-runtime-compilation.md)|Vytvoří výstupní soubor pro spuštění v modulu CLR (Common Language Runtime).|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Řídí vyhodnocení constexpr v době kompilace.|
|[Parametr](d-preprocessor-definitions.md)|Definuje konstanty a makra.|
|[/Diagnostics](diagnostics-compiler-diagnostic-options.md)|Určuje formát diagnostických zpráv.|
|[/doc](doc-process-documentation-comments-c-cpp.md)|Zpracuje komentáře dokumentace do souboru XML.|
|[/E](e-preprocess-to-stdout.md)|Zkopíruje výstup preprocesoru do standardního výstupu.|
|[/EH](eh-exception-handling-model.md)|Určuje model zpracování výjimek.|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Zkopíruje výstup preprocesoru do standardního výstupu.|
|[/errorReport](errorreport-report-internal-compiler-errors.md)|Umožňuje poskytnout informace o vnitřní chybě kompilátoru (ICE) přímo týmu společnosti Microsoft C++ .|
|[/Execution-charset](execution-charset-set-execution-character-set.md)|Nastavit znakovou sadu spuštění.|
|[/Experimental: modul](experimental-module.md)|Povolí experimentální podporu modulu.|
|[/Experimental: preprocesor](experimental-preprocessor.md)|Povoluje experimentální vyhovující s podporou preprocesoru.|
|[Přepínač](f-set-stack-size.md)|Nastaví velikost zásobníku.|
|[/Favor](favor-optimize-for-architecture-specifics.md)|Vytvoří kód, který je optimalizován pro konkrétní architekturu x64 nebo pro konkrétní mikroarchitektury v architektuře AMD64 a rozšířené paměti 64 technologie (EM64T).|
|[/FA](fa-fa-listing-file.md)|Vytvoří soubor výpisu.|
|[/FA](fa-fa-listing-file.md)|Nastaví název souboru výpisu.|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|Zobrazí úplnou cestu souborů se zdrojovým kódem předaných do cl. exe v diagnostickém textu.|
|[/FD](fd-program-database-file-name.md)|Přejmenuje soubor databáze programu.|
|[/FE](fe-name-exe-file.md)|Přejmenuje spustitelný soubor.|
|[/FI](fi-name-forced-include-file.md)|Předzpracovává zadaný soubor k zahrnutí.|
|[/Fi](fi-preprocess-output-file-name.md)|Nastaví název předzpracovaného výstupního souboru.|
|[/FM](fm-name-mapfile.md)|Vytvoří soubor mapy.|
|[/FO](fo-object-file-name.md)|Vytvoří soubor objektu.|
|[/FP](fp-specify-floating-point-behavior.md)|Určuje chování s plovoucí desetinnou čárkou.|
|[/FP](fp-name-dot-pch-file.md)|Určuje název souboru předkompilované hlavičky.|
|[/FR](fr-fr-create-dot-sbr-file.md)<br /><br /> [/FR](fr-fr-create-dot-sbr-file.md)|Generuje soubory prohlížeče. **/Fr** je zastaralá.|
|[/FS](fs-force-synchronous-pdb-writes.md)|Vynutí zápisy do souboru databáze programu (PDB) k serializaci pomocí MSPDBSRV. Programu.|
|[/FU](fu-name-forced-hash-using-file.md)|Vynutí použití názvu souboru, jako kdyby byl předán direktivě [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/FX](fx-merge-injected-code.md)|Sloučí vložený kód se zdrojovým souborem.|
|[/GA](ga-optimize-for-windows-application.md)|Optimalizuje kód pro aplikaci pro Windows.|
|[/GD](gd-gr-gv-gz-calling-convention.md)|Používá konvenci volání `__cdecl` (pouze x86).|
|[/GE](ge-enable-stack-probes.md)|Zastaralé Aktivuje sondy zásobníku.|
|[/GF](gf-eliminate-duplicate-strings.md)|Povolí sdružování řetězců.|
|[/GH](gh-enable-pexit-hook-function.md)|`_pexit`funkce vidlice volání.|
|[/GH](gh-enable-penter-hook-function.md)|`_penter`funkce vidlice volání.|
|[/GL](gl-whole-program-optimization.md)|Povoluje optimalizaci celého programu.|
|[/GM](gm-enable-minimal-rebuild.md)|Zastaralé Povoluje minimální opětovné sestavení.|
|[/GR](gr-enable-run-time-type-information.md)|Povoluje informace o typu běhu (RTTI).|
|[/GR](gd-gr-gv-gz-calling-convention.md)|Používá konvenci volání `__fastcall` (pouze x86).|
|[/GS](gs-buffer-security-check.md)|Uloží kontrolu zabezpečení do vyrovnávací paměti.|
|[/GS](gs-control-stack-checking-calls.md)|Řídí sondy zásobníku.|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|Podporuje bezpečnost vlákna pro data přidělená pomocí statického úložiště místního vlákna.|
|[/Guard: CF](guard-enable-control-flow-guard.md)|Přidá kontrolu zabezpečení ochrany toku řízení.|
|[/GV](gd-gr-gv-gz-calling-convention.md)|Používá konvenci volání `__vectorcall`. (jenom x86 a x64)|
|[/GW](gw-optimize-global-data.md)|Povolí globální optimalizaci dat celého programu.|
|[/GX](gx-enable-exception-handling.md)|Zastaralé Povoluje synchronní zpracování výjimek. Místo toho použijte [/eh](eh-exception-handling-model.md) .|
|[/Gy](gy-enable-function-level-linking.md)|Povolí propojení na úrovni funkcí.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Zastaralé Stejné jako [/RTC1](rtc-run-time-error-checks.md).|
|[/GZ](gd-gr-gv-gz-calling-convention.md)|Používá konvenci volání `__stdcall` (pouze x86).|
|[/H](h-restrict-length-of-external-names.md)|Zastaralé Omezuje délku externích (veřejných) názvů.|
|[/HELP](help-compiler-command-line-help.md)|Zobrazí seznam možností kompilátoru.|
|[/homeparams](homeparams-copy-register-parameters-to-stack.md)|Vynutí zapsání parametrů předaných v registrech do jejich umístění v zásobníku při zadání funkce. Tato možnost kompilátoru je určena pouze pro kompilátory x64 (nativní a příčná kompilace).|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|Vytvoří bitovou kopii s aktivní opravou.|
|[Parametr](i-additional-include-directories.md)|Vyhledá v adresáři soubory k zahrnutí.|
|[/J](j-default-char-type-is-unsigned.md)|Změní výchozí typ `char`.|
|[/JMC](jmc.md)|Podporuje ladění C++ nativního pouze můj kód.|
|[/kernel](kernel-create-kernel-mode-binary.md)|Kompilátor a linker vytvoří binární soubor, který bude možné spustit v jádru systému Windows.|
|[/LD](md-mt-ld-use-run-time-library.md)|Vytvoří dynamickou knihovnu.|
|[/LDd](md-mt-ld-use-run-time-library.md)|Vytvoří dynamickou knihovnu pro ladění.|
|[/link](link-pass-options-to-linker.md)|Předá zadanou možnost propojení.|
|[/LN](ln-create-msil-module.md)|Vytvoří modul MSIL.|
|[/MD](md-mt-ld-use-run-time-library.md)|Vytvoří vícevláknovou knihovnu DLL pomocí knihovny MSVCRT. lib.|
|[/MDd](md-mt-ld-use-run-time-library.md)|Vytvoří vícevláknovou knihovnu DLL pro ladění pomocí MSVCRTD. lib.|
|[/MP](mp-build-with-multiple-processes.md)|Zkompiluje více zdrojových souborů pomocí více procesů.|
|[/MT](md-mt-ld-use-run-time-library.md)|Vytvoří vícevláknový spustitelný soubor s použitím LIBCMT. lib.|
|[/MTd](md-mt-ld-use-run-time-library.md)|Vytvoří vícevláknový spustitelný soubor ladění pomocí LIBCMTD. lib.|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|Potlačí zobrazení nápisu přihlášení.|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|Vytvoří malý kód.|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|Vytvoří rychlý kód.|
|[/Ob](ob-inline-function-expansion.md)|Ovládá vložené rozšíření.|
|[/Od](od-disable-debug.md)|Zakáže optimalizaci.|
|[/OG](og-global-optimizations.md)|Zastaralé Používá globální optimalizace.|
|[/Oi](oi-generate-intrinsic-functions.md)|Generuje vnitřní funkce.|
|[/OpenMP](openmp-enable-openmp-2-0-support.md)|Povoluje direktivu [`#pragma omp`](../../preprocessor/omp.md) ve zdrojovém kódu.|
|[/OS](os-ot-favor-small-code-favor-fast-code.md)|Upřednostňuje malý kód.|
|[/Ot](os-ot-favor-small-code-favor-fast-code.md)|Upřednostňuje rychlý kód.|
|[/Ox](ox-full-optimization.md)|Podmnožina/O2, která neobsahuje/GF nebo/Gy.|
|[/Oy](oy-frame-pointer-omission.md)|Vynechá ukazatel na rámec (jenom x86).|
|[/P](p-preprocess-to-a-file.md)|Zapisuje výstup preprocesoru do souboru.|
|[/Permissive-](permissive-standards-conformance.md)|Nastavte režim pro shodu Standard.|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|Generuje rychle transcendentní objekty.|
|[/QIfist](qifist-suppress-ftol.md)|Zastaralé Potlačí `_ftol`, je-li vyžadován převod z typu s plovoucí desetinnou čárkou na integrální typ (pouze x86).|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Odebere příkazy `fwait` uvnitř bloků `try`.|
|[/QIntel-jcc-erratum](qintel-jcc-erratum.md)|Snižuje dopad na výkon aktualizace Intel JCC kontrola vyžádal povolení mikrokódu.|
|[/Qpar (automatická paralelizace)](qpar-auto-parallelizer.md)|Povoluje automatické paralelismuing smyček, které jsou označeny direktivou [#pragma Loop ()](../../preprocessor/loop.md) .|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|Používá pro hodnoty s plovoucí desetinnou čárkou pokyny k přesunutí celého čísla a zakáže některé optimalizace načítání s plovoucí desetinnou čárkou.|
|[/Qspectre](qspectre.md)|Určuje generování kompilátoru s pokyny pro zmírnění některých ohrožení zabezpečení Spectre varianty 1 – 1.|
|[/Qspectre-load](qspectre-load.md)|Určuje generování kompilátoru pro vytváření serializace instrukcí pro zmírnění ohrožení zabezpečení Spectre v závislosti na pokynech k načtení.|
|[/Qspectre-load-cf](qspectre-load-cf.md)|Určuje generování kompilátoru pro serializaci instrukcí pro zmírnění ohrožení zabezpečení Spectre v závislosti na pokynech toku ovládacích prvků, které načítají paměť.|
|[/Qpar-report (úroveň generování sestav s automatickou vektorizací)](qvec-report-auto-vectorizer-reporting-level.md)|Povoluje generování úrovní pro automatické rozkládání.|
|[/RTC](rtc-run-time-error-checks.md)|Povoluje kontrolu chyb v době běhu.|
|[/SDL](sdl-enable-additional-security-checks.md)|Povolí další funkce zabezpečení a upozornění.|
|[/showIncludes](showincludes-list-include-files.md)|Zobrazí seznam vložených souborů během kompilace.|
|[/Source-charset](source-charset-set-source-character-set.md)|Nastavte zdrojovou znakovou sadu.|
|[/STD](std-specify-language-standard-version.md)|C++Výběr kompatibility standardní verze|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Určuje zdrojový soubor jazyka C.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Určuje, že všechny zdrojové soubory jsou C.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Určuje C++ zdrojový soubor.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Určuje všechny zdrojové soubory C++.|
|[Přepínač](u-u-undefine-symbols.md)|Odebere předdefinované makro.|
|[přepínač](u-u-undefine-symbols.md)|Odebere všechna Předdefinovaná makra.|
|[/UTF-8.](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Nastavte zdrojové a spouštěcí znakové sady na UTF-8.|
|[/V](v-version-number.md)|Zastaralé Nastaví řetězec verze souboru. obj.|
|[/Validate-charset](validate-charset-validate-for-compatible-characters.md)|Ověří soubory UTF-8 pouze pro kompatibilní znaky.|
|[/VD](vd-disable-construction-displacements.md)|Potlačí nebo povolí skryté členy třídy vtordisp.|
|[/VMB](vmb-vmg-representation-method.md)|Používá nejlepší základ pro ukazatele na členy.|
|[/VMG](vmb-vmg-representation-method.md)|Používá úplný obec pro ukazatele na členy.|
|[/VMM](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje vícenásobnou dědičnost.|
|[/VMS](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje jednoduchou dědičnost.|
|[/VMV](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje virtuální dědění.|
|[/volatile](volatile-volatile-keyword-interpretation.md)|Vybere způsob interpretace klíčového slova volatile.|
|[přepínače](compiler-option-warning-level.md)|Zakáže všechna upozornění.|
|[/W0,/W1,/W2,/W3,/W4](compiler-option-warning-level.md)|Nastaví úroveň upozornění na výstup.|
|[/W1,/W2,/W3,/W4](compiler-option-warning-level.md)|Nastaví úroveň upozornění pro zadané upozornění.|
|[/Wall](compiler-option-warning-level.md)|Povolí všechna upozornění, včetně upozornění, která jsou ve výchozím nastavení zakázaná.|
|[/WD](compiler-option-warning-level.md)|Zakáže zadané upozornění.|
|[/We](compiler-option-warning-level.md)|Zpracuje zadané upozornění jako chybu.|
|[/WL](wl-enable-one-line-diagnostics.md)|Povoluje jednořádkový diagnostiku pro chybové zprávy a upozornění při kompilování C++ zdrojového kódu z příkazového řádku.|
|[/WO](compiler-option-warning-level.md)|Zobrazí zadané upozornění pouze jednou.|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|Zastaralé. Detekuje problémy s přenositelností 64 bitů.|
|[/WV](compiler-option-warning-level.md)|Nezobrazí žádná upozornění zavedená po zadané verzi kompilátoru.|
|[/WX](compiler-option-warning-level.md)|Zpracovává všechna upozornění jako chyby.|
|[/X](x-ignore-standard-include-paths.md)|Ignoruje standardní adresář include.|
|[/Y-](y-ignore-precompiled-header-options.md)|Ignoruje všechny ostatní možnosti kompilátoru předkompilované hlavičky v aktuálním sestavení.|
|[/YC](yc-create-precompiled-header-file.md)|Vytvoří předkompilovaný hlavičkový soubor.|
|[/Yd](yd-place-debug-information-in-object-file.md)|Zastaralé Umístí úplné informace o ladění do všech objektových souborů. Místo toho použijte [/Zi](z7-zi-zi-debug-information-format.md) .|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|Vloží odkaz PCH při vytváření knihovny ladění.|
|[/Yu](yu-use-precompiled-header-file.md)|Při sestavování používá předkompilovaný hlavičkový soubor.|
|[/Z7](z7-zi-zi-debug-information-format.md)|Generuje ladicí informace kompatibilní s C 7,0.|
|[/Za](za-ze-disable-language-extensions.md)|Zakáže jazyková rozšíření.|
|[Parametr](zc-conformance.md)|Určuje standardní chování v rámci [/ze](za-ze-disable-language-extensions.md). [/Za,/ze (zakázat jazyková rozšíření)](za-ze-disable-language-extensions.md)|
|[/Ze](za-ze-disable-language-extensions.md)|Zastaralé Povolí jazykové rozšíření.|
|[/ZF](zf.md)|Vylepšuje čas generování PDB v paralelních sestaveních.|
|[/ZG](zg-generate-function-prototypes.md)|Odebráno v aplikaci Visual Studio 2015. Generuje prototypy funkcí.|
|[/ZH](zh.md)|Určuje MD5, SHA-1 nebo SHA-256 pro kontrolní součty v informacích o ladění.|
|[/ZI](z7-zi-zi-debug-information-format.md)|Obsahuje informace o ladění v databázi programu kompatibilní s úpravou a pokračováním.|
|[/Zi](z7-zi-zi-debug-information-format.md)|Vygeneruje úplné ladicí informace.|
|[/Zl](zl-omit-default-library-name.md)|Odstraní výchozí název knihovny ze souboru. obj (jenom x86).|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|Určuje limit přidělení paměti předkompilovaných hlaviček.|
|[/Zo](zo-enhance-optimized-debugging.md)|Generuje rozšířené ladicí informace pro optimalizovaný kód.|
|[/Zp](zp-struct-member-alignment.md)|Balíčky členů struktury.|
|[/ZS](zs-syntax-check-only.md)|Kontroluje pouze syntaxi.|
|[/ZW](zw-windows-runtime-compilation.md)|Vytvoří výstupní soubor pro spuštění na prostředí Windows Runtime.|

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
