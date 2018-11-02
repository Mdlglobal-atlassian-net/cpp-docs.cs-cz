---
title: Možnosti linkeru
ms.date: 08/20/2018
f1_keywords:
- link
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
ms.openlocfilehash: 22ac88ede7cc015efd12f1a996ffdf361b43f041
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50510108"
---
# <a name="linker-options"></a>Možnosti linkeru

LINK.exe slouží k propojení objektových souborů Common Object File Format (COFF) a knihovny, které chcete vytvořit spustitelný soubor (.exe) nebo dynamická knihovna (DLL).

V následující tabulce jsou uvedeny možnosti LINK.exe. Další informace o knihovnách LINK naleznete v tématu:

- [Možnosti LINK řízené kompilátorem](../../build/reference/compiler-controlled-link-options.md)

- [Vstupní soubory LINK](../../build/reference/link-input-files.md)

- [LINK – výstup](../../build/reference/link-output.md)

- [Vyhrazená slova](../../build/reference/reserved-words.md)

Na příkazovém řádku možnosti propojovacího programu nerozlišují; například/base a propojovacího mají stejný význam. Podrobnosti o tom, jak každou možnost zadejte na příkazovém řádku nebo v sadě Visual Studio naleznete v dokumentaci k této možnosti.

Můžete použít [komentář](../../preprocessor/comment-c-cpp.md) – Direktiva pragma k zadání některých možností propojovacího programu.

|Možnost|Účel|
|------------|-------------|
|[@](../../build/reference/at-specify-a-linker-response-file.md)|Určuje soubor odpovědí.|
|[/ ALIGN](../../build/reference/align-section-alignment.md)|Určuje zarovnání jednotlivých oddílů.|
|[/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md)|Určuje, že nemůže být svázaný s knihovnou DLL.|
|[/ALLOWISOLATION](../../build/reference/allowisolation-manifest-lookup.md)|Určuje chování při vyhledávání manifestu.|
|[/APPCONTAINER](../../build/reference/appcontainer-windows-store-app.md)|Určuje, zda je třeba aplikaci spustit v prostředí procesu appcontainer.|
|[/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)|Přidá <xref:System.Diagnostics.DebuggableAttribute> do spravované bitové kopie.|
|[/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)|Vytvoří odkaz na spravovaný prostředek.|
|[/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)|Určuje, že modul Microsoft intermediate language (MSIL) by měly být naimportovány do sestavení.|
|[/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)|Vloží spravovaný soubor prostředků v sestavení.|
|[/ BASE](../../build/reference/base-base-address.md)|Nastaví základní adresu programu.|
|[/ CGTHREADS](../../build/reference/cgthreads-compiler-threads.md)|Nastaví počet vláken cl.exe pro optimalizace a generování kódu při generování kódu při propojování určena.|
|[/ CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md)|Nastavuje typ bitové kopie modulu CLR (IJW, čistě nebo Bezpeční).|
|[/ CLRSUPPORTLASTERROR](../../build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|Zachová poslední chybový kód funkcí, které jsou volány prostřednictvím mechanismu P/Invoke.|
|[/ CLRTHREADATTRIBUTE](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md)|Určuje atribut dělení na vlákna má použít pro vstupní bod programu CLR.|
|[/ CLRUNMANAGEDCODECHECK](../../build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)|Určuje, zda linker použije atribut SuppressUnmanagedCodeSecurity linkerem generovaných zástupné procedury PInvoke, která volá ze spravovaného kódu do nativních knihoven DLL.|
|[/ DEBUG](../../build/reference/debug-generate-debug-info.md)|Vytvoří ladicí informace.|
|[/ DEBUGTYPE](../../build/reference/debugtype-debug-info-options.md)|Určuje, jaká data mají být zahrnuty informace o ladění.|
|[/ DEF](../../build/reference/def-specify-module-definition-file.md)|Předá linkeru soubor definice modulu (.def).|
|[/ DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md)|Prohledá zadanou knihovnu, když jsou překládány externí odkazy.|
|[/ DELAY](../../build/reference/delay-delay-load-import-settings.md)|Řídí opožděné načtení knihoven DLL.|
|[/ DELAYLOAD](../../build/reference/delayload-delay-load-import.md)|Způsobí opožděné načtení určené knihovny DLL.|
|[/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)|Částečně podepíše sestavení.|
|[/ DEPENDENTLOADFLAG](dependentloadflag.md)|Nastaví výchozí příznaky závislé načtení knihovny DLL.|
|[/ DLL](../../build/reference/dll-build-a-dll.md)|Sestavení knihovny DLL.|
|[/ DRIVER](../../build/reference/driver-windows-nt-kernel-mode-driver.md)|Vytvoří ovladač režimu jádra.|
|[/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md)|Určuje, jestli se má generovat spustitelnou bitovou kopii, která lze náhodně změnit základ v okamžiku načtení pomocí funkce náhodného (technologie ASLR) adresu místo rozložení.|
|[/ ENTRY](../../build/reference/entry-entry-point-symbol.md)|Nastaví počáteční adresu.|
|[/ errorreport](../../build/reference/errorreport-report-internal-linker-errors.md)|Společnosti Microsoft sestavy s interními chybami linkeru.|
|[/EXPORT](../../build/reference/export-exports-a-function.md)|Exportuje funkci.|
|[/ FILEALIGN](../../build/reference/filealign.md)|Zarovná oddíly v rámci výstupního souboru na násobky zadané hodnoty.|
|[/ FIXED](../../build/reference/fixed-fixed-base-address.md)|Vytvoří program, který lze načíst pouze na jeho upřednostňované základní adrese.|
|[/ FORCE](../../build/reference/force-force-file-output.md)|Vynutí odkaz dokončit i s nevyřešenými symboly nebo symboly definované více než jednou.|
|[/ FUNCTIONPADMIN](../../build/reference/functionpadmin-create-hotpatchable-image.md)|Vytvoří bitovou kopii, která může být opraven za běhu.|
|[/ GENPROFILE, /FASTGENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|Obě tyto možnosti určují generování souboru .pgd linkerem pro podporu profilováním řízené optimalizace (PGO). / GENPROFILE a /FASTGENPROFILE používají různé výchozí parametry.|
|[/ GUARD](../../build/reference/guard-enable-guard-checks.md)|Povolí ochranu toku provádění.|
|[/HEAP](../../build/reference/heap-set-heap-size.md)|Nastaví velikost haldy v bajtech.|
|[/HIGHENTROPYVA](../../build/reference/highentropyva-support-64-bit-aslr.md)|Určuje podporu pro náhodného generování rozložení prostoru adres 64-bit vysokou mírou entropie (technologie ASLR).|
|[/ IDLOUT](../../build/reference/idlout-name-midl-output-files.md)|Určuje název souboru .idl a ostatních výstupních souborů MIDL.|
|[/ IGNORE](../../build/reference/ignore-ignore-specific-warnings.md)|Potlačí výstup upozornění zadané linkeru.|
|[/ IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)|Zabrání zpracování informací atributu v souboru IDL.|
|[/ IMPLIB](../../build/reference/implib-name-import-library.md)|Přepíše výchozí název knihovny importu.|
|[/ INCLUDE](../../build/reference/include-force-symbol-references.md)|Vynutí odkazy na symbol.|
|[/ INCREMENTAL](../../build/reference/incremental-link-incrementally.md)|Řídí přírůstkové propojení.|
|[/INTEGRITYCHECK](../../build/reference/integritycheck-require-signature-check.md)|Určuje, jestli modul vyžaduje v okamžiku načtení kontrolu podpisu.|
|[/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)|Určuje klíčový kontejner k podepsání sestavení.|
|[/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|Určuje klíč nebo dvojici klíčů k podepsání sestavení.|
|[/LARGEADDRESSAWARE](../../build/reference/largeaddressaware-handle-large-addresses.md)|Instruuje kompilátor, že aplikace podporuje adresy větší než dva gigabajty|
|[/ LIBPATH](../../build/reference/libpath-additional-libpath.md)|Určuje cestu pro hledání před cestu ke knihovně prostředí.|
|[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)|Určuje generování kódu při propojování.|
|[/ MACHINE](../../build/reference/machine-specify-target-platform.md)|Určuje cílovou platformu.|
|[/ VOLBA MANIFEST](../../build/reference/manifest-create-side-by-side-assembly-manifest.md)|Vytvoří soubor manifestu vedle sebe a volitelně jej vloží do binárního souboru.|
|[/ MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md)|Určuje \<dependentAssembly > v souboru manifestu.|
|[/ MANIFESTFILE](../../build/reference/manifestfile-name-manifest-file.md)|Mění název výchozího souboru manifestu.|
|[/ MANIFESTINPUT](../../build/reference/manifestinput-specify-manifest-input.md)|Určuje vstupní soubor manifestu pro propojovací program pro zpracování a vložení do binárního souboru. Tuto možnost vícekrát můžete použít k určení více než jednoho vstupního souboru manifestu.|
|[/ MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md)|Určuje, zda informace o řízení uživatelských účtů (UAC) je vloženy do manifestu.|
|[/MAP](../../build/reference/map-generate-mapfile.md)|Vytvoří soubor mapfile.|
|[/ MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)|Obsahuje informace o zadaném v souboru mapfile.|
|[/MERGE](../../build/reference/merge-combine-sections.md)|Kombinuje oddíly.|
|[/ MIDL](../../build/reference/midl-specify-midl-command-line-options.md)|Určuje možnosti příkazového řádku MIDL.|
|[/ NATVIS](../../build/reference/natvis-add-natvis-to-pdb.md)|Přidá do souboru PDB vizualizérů ladění ze souboru Natvis.|
|[/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)|Potlačí vytváření sestavení rozhraní .NET Framework.|
|[/ NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)|Ignoruje všechny (nebo zadané) výchozí knihovny, když jsou překládány externí odkazy.|
|[/ NOENTRY](../../build/reference/noentry-no-entry-point.md)|Vytvoří knihovnu DLL pouze prostředků.|
|[/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)|Potlačí úvodní nápis.|
|[/NXCOMPAT](../../build/reference/nxcompat-compatible-with-data-execution-prevention.md)|Označí spustitelný soubor jako kompatibilního s funkcí Zabránění spuštění dat Windows.|
|[/ OPT](../../build/reference/opt-optimizations.md)|Řídí optimalizace LINK.|
|[/ ORDER](../../build/reference/order-put-functions-in-order.md)|Umístí prvky Comdat do bitové kopie v předurčeném pořadí.|
|[/ OUT](../../build/reference/out-output-file-name.md)|Určuje název výstupního souboru.|
|[/PDB](../../build/reference/pdb-use-program-database.md)|Vytvoří soubor databáze (PDB) programu.|
|[/ PDBALTPATH](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)|Alternativní umístění používá k uložení souboru PDB.|
|[/ PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)|Vytvoří soubor databáze (PDB) programu, který nemá žádné soukromé symboly.|
|[/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)|Určuje soubor .pgd pro optimalizace řízenou profily.|
|[/POGOSAFEMODE](../../build/reference/pogosafemode-linker-option.md)|**Zastaralé** vytváří sestavení instrumentováno PGO bezpečné pro vlákna.|
|[/ PROFILE](../../build/reference/profile-performance-tools-profiler.md)|Vytvoří výstupní soubor, který lze použít s profilerem Performance Tools.|
|[/RELEASE](../../build/reference/release-set-the-checksum.md)|Nastaví kontrolní součet v hlavičce .exe.|
|[/ SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)|Určuje, zda obrázek bude obsahovat tabulku bezpečných obslužných rutin výjimek.|
|[/ SECTION](../../build/reference/section-specify-section-attributes.md)|Obejde atributy oddílu.|
|[/ SOURCELINK](../../build/reference/sourcelink.md)|Určuje soubor SourceLink přidat do PDB.|
|[/STACK](../../build/reference/stack-stack-allocations.md)|Nastaví velikost zásobníku v bajtech.|
|[/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)|Připojí se k programu Win32 zástupný program MS-DOS.|
|[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)|Říká operačnímu systému, jak spustit soubor .exe.|
|[/SWAPRUN](../../build/reference/swaprun-load-linker-output-to-swap-file.md)|Říká operačním systém, chcete-li zkopírovat výstup linkeru do odkládacího souboru, před spuštěním.|
|[/ TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md)|Určuje ID prostředku knihovny typů vygenerované linkerem.|
|[/ TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)|Určuje název souboru .tlb a ostatních výstupních souborů MIDL.|
|[/TSAWARE](../../build/reference/tsaware-create-terminal-server-aware-application.md)|Vytvoří aplikaci, která je specificky navržena pro spouštění v režimu terminálového serveru.|
|[/USEPROFILE](../../build/reference/useprofile.md)|Použití na základě profilu – optimalizace trénovací data k vytvoření optimalizované bitové kopie.|
|[/ VERBOSE](../../build/reference/verbose-print-progress-messages.md)|Vytiskne zprávy o průběhu linkeru.|
|[/VERSION](../../build/reference/version-version-information.md)|Přiřadí číslo verze.|
|[/ WHOLEARCHIVE](../../build/reference/wholearchive-include-all-library-object-files.md)|Obsahuje každý soubor objektu ze zadaného statických knihoven.|
|[/ WINMD](../../build/reference/winmd-generate-windows-metadata.md)|Povolí generování souboru metadat Windows Runtime.|
|[/ WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md)|Určuje název souboru výstupního souboru Windows Runtime Metadata (winmd), který je generován [winmd](../../build/reference/winmd-generate-windows-metadata.md) – možnost linkeru.|
|[/ WINMDFILE](../../build/reference/winmdkeyfile-specify-winmd-key-file.md)|Určuje klíč nebo dvojici klíčů k podepsání souboru metadat Windows Runtime.|
|[/ WINMDKEYCONTAINER](../../build/reference/winmdkeycontainer-specify-key-container.md)|Určuje klíčový kontejner k podepsání souboru metadat Windows.|
|[/ WINMDDELAYSIGN SOUBORU](../../build/reference/winmddelaysign-partially-sign-a-winmd.md)|Částečně podepíše soubor Windows Runtime Metadata (.winmd) tak, že umístí veřejný klíč v souboru winmd.|
|[/WX](../../build/reference/wx-treat-linker-warnings-as-errors.md)|Zpracování propojení všech upozornění jako chyby.|

Další informace najdete v tématu [možnosti propojení Compiler-Controlled](../../build/reference/compiler-controlled-link-options.md).

## <a name="see-also"></a>Viz také

[Referenční zdroje k sestavení programu v jazyce C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)