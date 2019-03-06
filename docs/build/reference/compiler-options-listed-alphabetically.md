---
title: Možnosti kompilátoru (abecední pořadí)
ms.date: 08/20/2018
helpviewer_keywords:
- compiler options, C++
ms.openlocfilehash: 73236485026b82895426a2651b48a83fc35ce8b7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415874"
---
# <a name="compiler-options-listed-alphabetically"></a>Možnosti kompilátoru (abecední pořadí)

Následuje úplný abecední seznam – možnosti kompilátoru. Seznam kategorií naleznete v tématu [možnosti kompilátoru seřazené podle kategorie](compiler-options-listed-by-category.md).

|Možnost|Účel|
|------------|-------------|
|[@](at-specify-a-compiler-response-file.md)|Určuje soubor odpovědí.|
|[/?](help-compiler-command-line-help.md)|Vypíše nastavení kompilátoru.|
|[/AI](ai-specify-metadata-directories.md)|Určuje adresář pro vyhledávání pro přeložení referencí souboru předaných [#using](../../preprocessor/hash-using-directive-cpp.md) směrnice.|
|[/ analyze](analyze-code-analysis.md)|Povolte analýzu kódu.|
|[/ arch](arch-minimum-cpu-architecture.md)|Určuje architekturu pro generování kódu.|
|[/ await](await-enable-coroutine-support.md)|Povolte rozšíření korutin (funkcí resumable).|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|Zvýší počet adresovatelných sekcí v souboru .obj.|
|[/C](c-preserve-comments-during-preprocessing.md)|Zachová komentáře při předzpracování.|
|[/c](c-compile-without-linking.md)|Zkompiluje bez propojení.|
|[/cgthreads](cgthreads-code-generation-threads.md)|Určuje počet vláken cl.exe pro optimalizace a generování kódu.|
|[/ CLR](clr-common-language-runtime-compilation.md)|Vytvoří výstupní soubor pro spuštění na modulu common language runtime.|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Kontrolní vyhodnocení constexpr v době kompilace.|
|[/D](d-preprocessor-definitions.md)|Definuje konstanty a makra.|
|[/ Diagnostics](diagnostics-compiler-diagnostic-options.md)|Určuje formát diagnostických zpráv.|
|[/doc](doc-process-documentation-comments-c-cpp.md)|Zpracuje komentáře dokumentace do souboru XML.|
|[/E](e-preprocess-to-stdout.md)|Zkopíruje výstup předzpracování do standardního výstupu.|
|[/EH](eh-exception-handling-model.md)|Určuje model zpracování výjimek.|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Zkopíruje výstup předzpracování do standardního výstupu.|
|[/errorReport](errorreport-report-internal-compiler-errors.md)|Umožňuje poskytnout kompilátoru informace o chybě (ICE) přímo do týmu Visual C++.|
|[/execution-charset](execution-charset-set-execution-character-set.md)|Nastavení znakové sady spuštění.|
|[/F](f-set-stack-size.md)|Nastaví velikost zásobníku.|
|[/ favor](favor-optimize-for-architecture-specifics.md)|Vytvoří kód, který je optimalizovaný pro konkrétní x64 architekturu nebo pro konkrétní micro architektury v AMD64, tak i Extended Memory 64 (EM64T) technologie architektury.|
|[/FA](fa-fa-listing-file.md)|Vytvoří soubor výpisu.|
|[/Fa](fa-fa-listing-file.md)|Nastaví název souboru výpisu.|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|Úplná cesta zobrazení souborů zdrojového kódu předaných do cl.exe v rámci diagnostického textu.|
|[/Fd](fd-program-database-file-name.md)|Přejmenuje soubor databáze programu.|
|[/FE](fe-name-exe-file.md)|Přejmenuje spustitelný soubor.|
|[/FI](fi-name-forced-include-file.md)|Předzpracuje určeného zahrnutého souboru.|
|[/Fi](fi-preprocess-output-file-name.md)|Nastaví název předzpracovaného výstupního souboru.|
|[/Fm](fm-name-mapfile.md)|Vytvoří soubor mapfile.|
|[/Fo](fo-object-file-name.md)|Vytvoří objektový soubor.|
|[/fp](fp-specify-floating-point-behavior.md)|Zadejte chování plovoucí desetinné čárky.|
|[/Fp](fp-name-dot-pch-file.md)|Určuje název souboru předkompilované hlavičky.|
|[/FR](fr-fr-create-dot-sbr-file.md)<br /><br /> [/Fr](fr-fr-create-dot-sbr-file.md)|Vytvoří soubory prohlížeče. **/FR** je zastaralý.|
|[/FS](fs-force-synchronous-pdb-writes.md)|Vynutí zápisy do souboru databáze (PDB) programu k serializaci pomocí MSPDBSRV. SOUBOR EXE.|
|[/FU](fu-name-forced-hash-using-file.md)|Vynutí použití názvu souboru, jako kdyby byl předán [#using](../../preprocessor/hash-using-directive-cpp.md) směrnice.|
|[/Fx](fx-merge-injected-code.md)|Sloučí vložený kód se zdrojovým souborem.|
|[/GA](ga-optimize-for-windows-application.md)|Optimalizuje kód pro aplikace Windows.|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|Používá `__cdecl` (pouze x86) konvence volání.|
|[/Ge](ge-enable-stack-probes.md)|Zastaralé Aktivuje sondy zásobníku.|
|[/GF](gf-eliminate-duplicate-strings.md)|Umožňuje sdružování řetězců.|
|[/GH](gh-enable-pexit-hook-function.md)|Zavolá funkci připojení `_pexit`.|
|[/Gh](gh-enable-penter-hook-function.md)|Zavolá funkci připojení `_penter`.|
|[/GL](gl-whole-program-optimization.md)|Povolí optimalizaci celého programu.|
|[/Gm](gm-enable-minimal-rebuild.md)|Povolí minimální opětovné sestavení.|
|[/GR](gr-enable-run-time-type-information.md)|Povolí informace běhového typu (RTTI).|
|[/Gr](gd-gr-gv-gz-calling-convention.md)|Používá `__fastcall` (pouze x86) konvence volání.|
|[/GS](gs-buffer-security-check.md)|Kontrola zabezpečení vyrovnávací paměti.|
|[/Gs](gs-control-stack-checking-calls.md)|Řídí sondu zásobníku.|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|Podporuje bezpečnost vlákna pro data Alokovaná pomocí statického úložiště lokálního vlákna.|
|[/guard:cf](guard-enable-control-flow-guard.md)|Přidá kontroly zabezpečení ochrany toku řízení.|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|Používá `__vectorcall` konvence volání. (x86 a pouze x64)|
|[/Gw](gw-optimize-global-data.md)|Povolí optimalizaci globálních dat celého programu.|
|[/GX](gx-enable-exception-handling.md)|Zastaralé Povolí synchronní zpracování výjimek. Použití [/EH](eh-exception-handling-model.md) místo.|
|[/Gy](gy-enable-function-level-linking.md)|Povolí funkci propojení na úrovni.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Zastaralé Stejné jako [RTC1](rtc-run-time-error-checks.md).|
|[/Gz](gd-gr-gv-gz-calling-convention.md)|Používá `__stdcall` (pouze x86) konvence volání.|
|[/H](h-restrict-length-of-external-names.md)|Zastaralé Omezí délku externích (veřejných) názvů.|
|[/HELP](help-compiler-command-line-help.md)|Vypíše nastavení kompilátoru.|
|[/ homeparams](homeparams-copy-register-parameters-to-stack.md)|Přinutí parametry předané do registrů k zápisu do jejich umístění v zásobníku při vstupu funkce. Tato možnost kompilátoru je pouze pro x64 kompilátory (nativní a křížové kompilování).|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|Vytvoří bitovou kopii opravitelnou za provozu.|
|[/I](i-additional-include-directories.md)|Vyhledá v adresáři vkládané soubory.|
|[/J](j-default-char-type-is-unsigned.md)|Změní výchozí `char` typu.|
|[/JMC](jmc.md)|Podporuje nativní ladění pouze můj kód C++.|
|[/kernel](kernel-create-kernel-mode-binary.md)|Kompilátor a propojovací program vytvoří binární soubor, který lze spustit v jádru Windows.|
|[/LD](md-mt-ld-use-run-time-library.md)|Vytvoří dynamickou knihovnu.|
|[/LDd](md-mt-ld-use-run-time-library.md)|Vytvoří dynamickou knihovnu ladění.|
|[/link](link-pass-options-to-linker.md)|Předá zadané nastavení do LINK.|
|[/LN](ln-create-msil-module.md)|Vytvoří modul MSIL.|
|[/MD](md-mt-ld-use-run-time-library.md)|Vytvoří vícevláknovou knihovnu DLL pomocí MSVCRT.lib.|
|[/MDd](md-mt-ld-use-run-time-library.md)|Vytvoří ladicí vícevláknovou knihovnu DLL pomocí MSVCRTD.lib.|
|[/MP](mp-build-with-multiple-processes.md)|Kompiluje několik zdrojových souborů pomocí více procesů.|
|[/MT](md-mt-ld-use-run-time-library.md)|Vytvoří vícevláknový spustitelný soubor pomocí LIBCMT.lib.|
|[/MTd](md-mt-ld-use-run-time-library.md)|Vytvoří vícevláknového spustitelného souboru ladění pomocí LIBCMTD.lib.|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|Potlačí zobrazení nápisu.|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|Vytvoří malý kód.|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|Vytvoří rychlý kód.|
|[/Ob](ob-inline-function-expansion.md)|Řídí vložené rozšíření.|
|[/Od](od-disable-debug.md)|Zakáže optimalizaci.|
|[/Og](og-global-optimizations.md)|Zastaralé Používá globální optimalizace.|
|[/Oi](oi-generate-intrinsic-functions.md)|Vytváří vnitřní funkce.|
|[/ OpenMP](openmp-enable-openmp-2-0-support.md)|Umožňuje [#pragma omp](../../preprocessor/omp.md) ve zdrojovém kódu.|
|[/ OS](os-ot-favor-small-code-favor-fast-code.md)|Upřednostní malý kód.|
|[/Ot](os-ot-favor-small-code-favor-fast-code.md)|Upřednostní rychlý kód.|
|[/OX](ox-full-optimization.md)|Použije maximální optimalizaci (/ Ob2gity /Gs).|
|[/Oy](oy-frame-pointer-omission.md)|Vynechá rámcový ukazatel (pouze x86).|
|[/P](p-preprocess-to-a-file.md)|Zapíše výstup předprocesoru do souboru.|
|[/permissive-](permissive-standards-conformance.md)|Nastavit režim přizpůsobení standard.|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|Vytvoří rychlé transcendentals.|
|[/ QIfist](qifist-suppress-ftol.md)|Zastaralé Potlačí `_ftol` při převodu z typu s plovoucí desetinnou čárkou na celočíselný typ je povinné (jenom x86).|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Odebere `fwait` příkazy uvnitř `try` bloky.|
|[/Qpar (automatická paralelizace)](qpar-auto-parallelizer.md)|Povolí automatickou paralelizaci smyček, které jsou označeny [#pragma loop()](../../preprocessor/loop.md) směrnice.|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|Použije instrukce přesunu celého čísla pro hodnoty s plovoucí desetinnou čárkou a zakáže některé optimalizace zátěže bod s plovoucí čárkou.|
|[/Qpar-report (úroveň generování sestav s automatickou vektorizací)](qvec-report-auto-vectorizer-reporting-level.md)|Povolí protokolování úrovní pro automatickou vektorizaci.|
|[/RTC](rtc-run-time-error-checks.md)|Povolí kontrolu chyb za běhu.|
|[/sdl](sdl-enable-additional-security-checks.md)|Povolí další funkce zabezpečení a upozornění.|
|[/showIncludes](showincludes-list-include-files.md)|Zobrazí seznam vložených souborů během kompilace.|
|[/source-charset](source-charset-set-source-character-set.md)|Nastavení zdrojové znakové sady.|
|[/std](std-specify-language-standard-version.md)|Selektor kompatibility standardní verze C++.|
|[/Tc](tc-tp-tc-tp-specify-source-file-type.md)|Určí zdrojový soubor C.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Určuje, že jsou všechny zdrojové soubory C.|
|[/Tp](tc-tp-tc-tp-specify-source-file-type.md)|Určuje zdrojový soubor jazyka C++.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Určuje, že jsou všechny zdrojové soubory C++.|
|[/U](u-u-undefine-symbols.md)|Odstraní předdefinované makro.|
|[/u](u-u-undefine-symbols.md)|Odstraní všechna předdefinovaná makra.|
|[/utf-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Sady zdrojů i znak provedení nastaví na UTF-8.|
|[/V](v-version-number.md)|Zastaralé Nastaví řetězec verze souboru .obj.|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|Ověří soubory ve formátu UTF-8 jenom kompatibilních znaků.|
|[/vd](vd-disable-construction-displacements.md)|Potlačí nebo povolí skryté členy třídy vtordisp.|
|[/vmb](vmb-vmg-representation-method.md)|Použije nejlepší základ pro ukazatele na členy.|
|[/vmg](vmb-vmg-representation-method.md)|Použije úplnou všeobecnost pro ukazatele na členy.|
|[/vmm](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje vícenásobnou dědičnost.|
|[/vms](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje jednoduchou dědičnost.|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje virtuální dědičnost.|
|[/ volatile](volatile-volatile-keyword-interpretation.md)|Vybere, způsob interpretace klíčového slova volatile.|
|[/w](compiler-option-warning-level.md)|Zakáže všechna upozornění.|
|[/W0, /W1, /W2, /W3, /W4](compiler-option-warning-level.md)|Nastaví jaké úroveň pro upozornění do výstupu.|
|[/w1, /w2, /w3, /w4](compiler-option-warning-level.md)|Nastaví úroveň upozornění pro zadané upozornění.|
|[/ Wall](compiler-option-warning-level.md)|Povolí všechna upozornění včetně upozornění, která jsou ve výchozím nastavení zakázané.|
|[/wd](compiler-option-warning-level.md)|Zakáže zadaný upozornění.|
|[/we](compiler-option-warning-level.md)|Zadané upozornění se považuje za chybu.|
|[/WL](wl-enable-one-line-diagnostics.md)|Umožňuje jednořádkové diagnostiky pro chybové zprávy a upozornění při kompilaci zdrojového kódu jazyka C++ z příkazového řádku.|
|[/wo](compiler-option-warning-level.md)|Zobrazí zadaným upozornění pouze jednou.|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|Zastaralé. Zjistí problémy s 64bitovou přenositelností.|
|[/Wv](compiler-option-warning-level.md)|Zobrazí bez upozornění zavedená po zadanou verzi kompilátoru.|
|[/WX](compiler-option-warning-level.md)|Zpracuje všechna upozornění jako chyby.|
|[/X](x-ignore-standard-include-paths.md)|Ignoruje standardní adresář include.|
|[/Y-](y-ignore-precompiled-header-options.md)|Ignoruje všechny ostatní možnosti předkompilované hlavičky v aktuálním sestavení.|
|[/Yc](yc-create-precompiled-header-file.md)|Vytvoří soubor předkompilované hlavičky.|
|[/Yd](yd-place-debug-information-in-object-file.md)|Zastaralé Umístí úplnou informaci o ladění do všech objektových souborů. Použití [/zi](z7-zi-zi-debug-information-format.md) místo.|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|Při vytvoření knihovny ladění vloží referenci PCH|
|[/Yu](yu-use-precompiled-header-file.md)|Používá předkompilovaného hlavičkového souboru během sestavování.|
|[/Z7](z7-zi-zi-debug-information-format.md)|Generuje kompatibilní s C 7.0 ladicí informace.|
|[/Za](za-ze-disable-language-extensions.md)|Zakáže jazyková rozšíření.|
|[/Zc](zc-conformance.md)|Určí obvyklé chování pod [/Ze](za-ze-disable-language-extensions.md).[ / Za, /Ze (zakázání jazykových rozšíření)](za-ze-disable-language-extensions.md)|
|[/Ze](za-ze-disable-language-extensions.md)|Zastaralé Povolí jazyková rozšíření.|
|[/Zf](zf.md)|Zlepšuje PDB generování dobu v paralelních sestaveních.|
|[/Zg](zg-generate-function-prototypes.md)|Odebrat v sadě Visual C++ 2015. Vytvoří prototypy funkcí.|
|[/ZI](z7-zi-zi-debug-information-format.md)|Obsahuje informace o ladění v databázi programu, který je kompatibilní s upravit a pokračovat.|
|[/Zi](z7-zi-zi-debug-information-format.md)|Generuje úplné ladicí informace.|
|[/Zl](zl-omit-default-library-name.md)|Odstraní výchozí název knihovny ze souboru .obj (pouze x86).|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|Určuje omezení přidělení paměti pro předkompilované hlavičky.|
|[/Zp](zp-struct-member-alignment.md)|Zabalí členy struktury.|
|[/Zs](zs-syntax-check-only.md)|Zkontroluje pouze syntaxi.|
|[/ZW](zw-windows-runtime-compilation.md)|Vytvoří výstupní soubor pro spuštění v modulu Windows Runtime.|

## <a name="see-also"></a>Viz také:

[Referenční zdroje k sestavení programu v jazyce C/C++](c-cpp-building-reference.md)<br/>
[Možnosti kompilátoru](compiler-options.md)<br/>
[Nastavení možností kompilátoru](setting-compiler-options.md)
