---
title: Možnosti Linkeru MSVC
ms.date: 08/20/2018
f1_keywords:
- link
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
ms.openlocfilehash: 7ff8ecd6a607aac59fca6d32fa2784e7e3e4268f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817347"
---
# <a name="linker-options"></a>Možnosti linkeru

LINK.exe slouží k propojení objektových souborů Common Object File Format (COFF) a knihovny, které chcete vytvořit spustitelný soubor (.exe) nebo dynamická knihovna (DLL).

V následující tabulce jsou uvedeny možnosti LINK.exe. Další informace o knihovnách LINK naleznete v tématu:

- [Možnosti LINK řízené kompilátorem](compiler-controlled-link-options.md)

- [Vstupní soubory LINK](link-input-files.md)

- [LINK – výstup](link-output.md)

- [Vyhrazená slova](reserved-words.md)

Na příkazovém řádku možnosti propojovacího programu nerozlišují; například/base a propojovacího mají stejný význam. Podrobnosti o tom, jak každou možnost zadejte na příkazovém řádku nebo v sadě Visual Studio naleznete v dokumentaci k této možnosti.

Můžete použít [komentář](../../preprocessor/comment-c-cpp.md) – Direktiva pragma k zadání některých možností propojovacího programu.

|Možnost|Účel|
|------------|-------------|
|[@](at-specify-a-linker-response-file.md)|Určuje soubor odpovědí.|
|[/ ALIGN](align-section-alignment.md)|Určuje zarovnání jednotlivých oddílů.|
|[/ALLOWBIND](allowbind-prevent-dll-binding.md)|Určuje, že nemůže být svázaný s knihovnou DLL.|
|[/ALLOWISOLATION](allowisolation-manifest-lookup.md)|Určuje chování při vyhledávání manifestu.|
|[/APPCONTAINER](appcontainer-windows-store-app.md)|Určuje, zda je třeba aplikaci spustit v prostředí procesu appcontainer.|
|[/ ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)|Přidá <xref:System.Diagnostics.DebuggableAttribute> do spravované bitové kopie.|
|[/ ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)|Vytvoří odkaz na spravovaný prostředek.|
|[/ ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)|Určuje, že modul Microsoft intermediate language (MSIL) by měly být naimportovány do sestavení.|
|[/ ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)|Vloží spravovaný soubor prostředků v sestavení.|
|[/ BASE](base-base-address.md)|Nastaví základní adresu programu.|
|[/ CGTHREADS](cgthreads-compiler-threads.md)|Nastaví počet vláken cl.exe pro optimalizace a generování kódu při generování kódu při propojování určena.|
|[/ CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md)|Nastavuje typ bitové kopie modulu CLR (IJW, čistě nebo Bezpeční).|
|[/ CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|Zachová poslední chybový kód funkcí, které jsou volány prostřednictvím mechanismu P/Invoke.|
|[/ CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md)|Určuje atribut dělení na vlákna má použít pro vstupní bod programu CLR.|
|[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)|Určuje, zda linker použije atribut SuppressUnmanagedCodeSecurity linkerem generovaných zástupné procedury PInvoke, která volá ze spravovaného kódu do nativních knihoven DLL.|
|[/DEBUG](debug-generate-debug-info.md)|Vytvoří ladicí informace.|
|[/ DEBUGTYPE](debugtype-debug-info-options.md)|Určuje, jaká data mají být zahrnuty informace o ladění.|
|[/DEF](def-specify-module-definition-file.md)|Předá linkeru soubor definice modulu (.def).|
|[/ DEFAULTLIB](defaultlib-specify-default-library.md)|Prohledá zadanou knihovnu, když jsou překládány externí odkazy.|
|[/DELAY](delay-delay-load-import-settings.md)|Řídí opožděné načtení knihoven DLL.|
|[/DELAYLOAD](delayload-delay-load-import.md)|Způsobí opožděné načtení určené knihovny DLL.|
|[/ DELAYSIGN](delaysign-partially-sign-an-assembly.md)|Částečně podepíše sestavení.|
|[/DEPENDENTLOADFLAG](dependentloadflag.md)|Nastaví výchozí příznaky závislé načtení knihovny DLL.|
|[/DLL](dll-build-a-dll.md)|Sestavení knihovny DLL.|
|[/DRIVER](driver-windows-nt-kernel-mode-driver.md)|Vytvoří ovladač režimu jádra.|
|[/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)|Určuje, jestli se má generovat spustitelnou bitovou kopii, která lze náhodně změnit základ v okamžiku načtení pomocí funkce náhodného (technologie ASLR) adresu místo rozložení.|
|[/ ENTRY](entry-entry-point-symbol.md)|Nastaví počáteční adresu.|
|[/errorReport](errorreport-report-internal-linker-errors.md)|Společnosti Microsoft sestavy s interními chybami linkeru.|
|[/EXPORT](export-exports-a-function.md)|Exportuje funkci.|
|[/ FILEALIGN](filealign.md)|Zarovná oddíly v rámci výstupního souboru na násobky zadané hodnoty.|
|[/ FIXED](fixed-fixed-base-address.md)|Vytvoří program, který lze načíst pouze na jeho upřednostňované základní adrese.|
|[/ FORCE](force-force-file-output.md)|Vynutí odkaz dokončit i s nevyřešenými symboly nebo symboly definované více než jednou.|
|[/ FUNCTIONPADMIN](functionpadmin-create-hotpatchable-image.md)|Vytvoří bitovou kopii, která může být opraven za běhu.|
|[/ GENPROFILE, /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|Obě tyto možnosti určují generování souboru .pgd linkerem pro podporu profilováním řízené optimalizace (PGO). / GENPROFILE a /FASTGENPROFILE používají různé výchozí parametry.|
|[/GUARD](guard-enable-guard-checks.md)|Povolí ochranu toku provádění.|
|[/HEAP](heap-set-heap-size.md)|Nastaví velikost haldy v bajtech.|
|[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)|Určuje podporu pro náhodného generování rozložení prostoru adres 64-bit vysokou mírou entropie (technologie ASLR).|
|[/ IDLOUT](idlout-name-midl-output-files.md)|Určuje název souboru .idl a ostatních výstupních souborů MIDL.|
|[/ IGNORE](ignore-ignore-specific-warnings.md)|Potlačí výstup upozornění zadané linkeru.|
|[/ IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md)|Zabrání zpracování informací atributu v souboru IDL.|
|[/IMPLIB](implib-name-import-library.md)|Přepíše výchozí název knihovny importu.|
|[/ INCLUDE](include-force-symbol-references.md)|Vynutí odkazy na symbol.|
|[/INCREMENTAL](incremental-link-incrementally.md)|Řídí přírůstkové propojení.|
|[/INTEGRITYCHECK](integritycheck-require-signature-check.md)|Určuje, jestli modul vyžaduje v okamžiku načtení kontrolu podpisu.|
|[/ KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)|Určuje klíčový kontejner k podepsání sestavení.|
|[/ KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|Určuje klíč nebo dvojici klíčů k podepsání sestavení.|
|[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)|Instruuje kompilátor, že aplikace podporuje adresy větší než dva gigabajty|
|[/LIBPATH](libpath-additional-libpath.md)|Určuje cestu pro hledání před cestu ke knihovně prostředí.|
|[/LTCG](ltcg-link-time-code-generation.md)|Určuje generování kódu při propojování.|
|[/ MACHINE](machine-specify-target-platform.md)|Určuje cílovou platformu.|
|[/ VOLBA MANIFEST](manifest-create-side-by-side-assembly-manifest.md)|Vytvoří soubor manifestu vedle sebe a volitelně jej vloží do binárního souboru.|
|[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md)|Určuje \<dependentAssembly > v souboru manifestu.|
|[/MANIFESTFILE](manifestfile-name-manifest-file.md)|Mění název výchozího souboru manifestu.|
|[/ MANIFESTINPUT](manifestinput-specify-manifest-input.md)|Určuje vstupní soubor manifestu pro propojovací program pro zpracování a vložení do binárního souboru. Tuto možnost vícekrát můžete použít k určení více než jednoho vstupního souboru manifestu.|
|[/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)|Určuje, zda informace o řízení uživatelských účtů (UAC) je vloženy do manifestu.|
|[/MAP](map-generate-mapfile.md)|Vytvoří soubor mapfile.|
|[/MAPINFO](mapinfo-include-information-in-mapfile.md)|Obsahuje informace o zadaném v souboru mapfile.|
|[/MERGE](merge-combine-sections.md)|Kombinuje oddíly.|
|[/MIDL](midl-specify-midl-command-line-options.md)|Určuje možnosti příkazového řádku MIDL.|
|[/NATVIS](natvis-add-natvis-to-pdb.md)|Přidá do souboru PDB vizualizérů ladění ze souboru Natvis.|
|[/ NOASSEMBLY](noassembly-create-a-msil-module.md)|Potlačí vytváření sestavení rozhraní .NET Framework.|
|[/ NODEFAULTLIB](nodefaultlib-ignore-libraries.md)|Ignoruje všechny (nebo zadané) výchozí knihovny, když jsou překládány externí odkazy.|
|[/ NOENTRY](noentry-no-entry-point.md)|Vytvoří knihovnu DLL pouze prostředků.|
|[/NOLOGO](nologo-suppress-startup-banner-linker.md)|Potlačí úvodní nápis.|
|[/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)|Označí spustitelný soubor jako kompatibilního s funkcí Zabránění spuštění dat Windows.|
|[/ OPT](opt-optimizations.md)|Řídí optimalizace LINK.|
|[/ ORDER](order-put-functions-in-order.md)|Umístí prvky Comdat do bitové kopie v předurčeném pořadí.|
|[/ OUT](out-output-file-name.md)|Určuje název výstupního souboru.|
|[/PDB](pdb-use-program-database.md)|Vytvoří soubor databáze (PDB) programu.|
|[/PDBALTPATH](pdbaltpath-use-alternate-pdb-path.md)|Alternativní umístění používá k uložení souboru PDB.|
|[/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)|Vytvoří soubor databáze (PDB) programu, který nemá žádné soukromé symboly.|
|[/PGD](pgd-specify-database-for-profile-guided-optimizations.md)|Určuje soubor .pgd pro optimalizace řízenou profily.|
|[/POGOSAFEMODE](pogosafemode-linker-option.md)|**Zastaralé** vytváří sestavení instrumentováno PGO bezpečné pro vlákna.|
|[/ PROFILE](profile-performance-tools-profiler.md)|Vytvoří výstupní soubor, který lze použít s profilerem Performance Tools.|
|[/RELEASE](release-set-the-checksum.md)|Nastaví kontrolní součet v hlavičce .exe.|
|[/SAFESEH](safeseh-image-has-safe-exception-handlers.md)|Určuje, zda obrázek bude obsahovat tabulku bezpečných obslužných rutin výjimek.|
|[/ SECTION](section-specify-section-attributes.md)|Obejde atributy oddílu.|
|[/ SOURCELINK](sourcelink.md)|Určuje soubor SourceLink přidat do PDB.|
|[/STACK](stack-stack-allocations.md)|Nastaví velikost zásobníku v bajtech.|
|[/STUB](stub-ms-dos-stub-file-name.md)|Připojí se k programu Win32 zástupný program MS-DOS.|
|[/SUBSYSTEM](subsystem-specify-subsystem.md)|Říká operačnímu systému, jak spustit soubor .exe.|
|[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)|Říká operačním systém, chcete-li zkopírovat výstup linkeru do odkládacího souboru, před spuštěním.|
|[/TLBID](tlbid-specify-resource-id-for-typelib.md)|Určuje ID prostředku knihovny typů vygenerované linkerem.|
|[/TLBOUT](tlbout-name-dot-tlb-file.md)|Určuje název souboru .tlb a ostatních výstupních souborů MIDL.|
|[/TSAWARE](tsaware-create-terminal-server-aware-application.md)|Vytvoří aplikaci, která je specificky navržena pro spouštění v režimu terminálového serveru.|
|[/USEPROFILE](useprofile.md)|Použití na základě profilu – optimalizace trénovací data k vytvoření optimalizované bitové kopie.|
|[/ VERBOSE](verbose-print-progress-messages.md)|Vytiskne zprávy o průběhu linkeru.|
|[/VERSION](version-version-information.md)|Přiřadí číslo verze.|
|[/ WHOLEARCHIVE](wholearchive-include-all-library-object-files.md)|Obsahuje každý soubor objektu ze zadaného statických knihoven.|
|[/ WINMD](winmd-generate-windows-metadata.md)|Povolí generování souboru metadat Windows Runtime.|
|[/WINMDFILE](winmdfile-specify-winmd-file.md)|Určuje název souboru výstupního souboru Windows Runtime Metadata (winmd), který je generován [winmd](winmd-generate-windows-metadata.md) – možnost linkeru.|
|[/ WINMDFILE](winmdkeyfile-specify-winmd-key-file.md)|Určuje klíč nebo dvojici klíčů k podepsání souboru metadat Windows Runtime.|
|[/ WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md)|Určuje klíčový kontejner k podepsání souboru metadat Windows.|
|[/ WINMDDELAYSIGN SOUBORU](winmddelaysign-partially-sign-a-winmd.md)|Částečně podepíše soubor Windows Runtime Metadata (.winmd) tak, že umístí veřejný klíč v souboru winmd.|
|[/WX](wx-treat-linker-warnings-as-errors.md)|Zpracování propojení všech upozornění jako chyby.|

Další informace najdete v tématu [možnosti propojení Compiler-Controlled](compiler-controlled-link-options.md).

## <a name="see-also"></a>Viz také:

[Referenční zdroje k sestavení programu v jazyce C/C++](c-cpp-building-reference.md)<br/>
[Odkaz na MSVC linkeru](linking.md)
