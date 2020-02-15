---
title: Možnosti linkeru MSVC
description: Seznam možností podporovaných linkerem odkazů společnosti Microsoft.
ms.date: 02/09/2020
f1_keywords:
- link
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
ms.openlocfilehash: 12710aff1cf833e277e48ab2f13abc702c7d6c14
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257543"
---
# <a name="linker-options"></a>Možnosti linkeru

LINK. exe spojuje soubory objektů a knihovny Common Object File Format (COFF) a vytváří spustitelný soubor (. exe) nebo dynamickou knihovnu (DLL).

V následující tabulce jsou uvedeny možnosti pro soubor LINK. exe. Další informace o propojení najdete v tématech:

- [Možnosti LINK řízené kompilátorem](compiler-controlled-link-options.md)

- [Vstupní soubory LINK](link-input-files.md)

- [LINK – výstup](link-output.md)

- [Vyhrazená slova](reserved-words.md)

V příkazovém řádku Možnosti linkeru nerozlišují velká a malá písmena; například `/base` a `/BASE` znamenají stejnou věc. Podrobnosti o tom, jak zadat jednotlivé možnosti na příkazovém řádku nebo v sadě Visual Studio, najdete v dokumentaci k této možnosti.

K určení některých možností linkeru můžete použít direktivu pragma [Komentáře](../../preprocessor/comment-c-cpp.md) .

## <a name="linker-options-listed-alphabetically"></a>Možnosti linkeru seřazené abecedně

|Možnost|Účel|
|------------|-------------|
|[@](at-specify-a-linker-response-file.md)|Určuje soubor odpovědí.|
|[/ALIGN](align-section-alignment.md)|Určuje zarovnání jednotlivých oddílů.|
|[/ALLOWBIND](allowbind-prevent-dll-binding.md)|Určuje, že knihovna DLL nemůže být vázaná.|
|[/ALLOWISOLATION](allowisolation-manifest-lookup.md)|Určuje chování při vyhledávání manifestu.|
|[/APPCONTAINER](appcontainer-windows-store-app.md)|Určuje, jestli aplikace musí běžet v prostředí procesu kontejneru AppContainer.|
|[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)|Přidá <xref:System.Diagnostics.DebuggableAttribute> do spravované image.|
|[/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)|Vytvoří odkaz na spravovaný prostředek.|
|[/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)|Určuje, že modul jazyka MSIL (Microsoft Intermediate Language) by měl být importován do sestavení.|
|[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)|Vloží spravovaný soubor prostředků do sestavení.|
|[/BASE](base-base-address.md)|Nastaví základní adresu programu.|
|[/CGTHREADS](cgthreads-compiler-threads.md)|Nastaví počet vláken CL. exe, který se má použít pro optimalizaci a generování kódu, když je zadané generování kódu při propojování.|
|[/CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md)|Nastaví typ (IJW, Pure nebo Safe) image CLR.|
|[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|Zachová poslední chybový kód funkcí, které jsou volány prostřednictvím mechanismu volání nespravovaného kódu.|
|[/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md)|Určuje atribut vláken, který má být použit pro vstupní bod programu CLR.|
|[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)|Určuje, zda linker použije atribut SuppressUnmanagedCodeSecurity na linkerem generované procedury PInvoke, které volají ze spravovaného kódu do nativních knihoven DLL.|
|[/DEBUG](debug-generate-debug-info.md)|Vytvoří ladicí informace.|
|[/DEBUGTYPE](debugtype-debug-info-options.md)|Určuje, která data se mají zahrnout do informací o ladění.|
|[/DEF](def-specify-module-definition-file.md)|Předá linkeru soubor definice modulu (. def).|
|[/DEFAULTLIB](defaultlib-specify-default-library.md)|Vyhledá zadanou knihovnu, když se vyřeší externí odkazy.|
|[/DELAY](delay-delay-load-import-settings.md)|Řídí opožděné načítání knihoven DLL.|
|[/DELAYLOAD](delayload-delay-load-import.md)|Způsobí opožděné načtení zadané knihovny DLL.|
|[/DELAYSIGN](delaysign-partially-sign-an-assembly.md)|Částečně podepíše sestavení.|
|[/DEPENDENTLOADFLAG](dependentloadflag.md)|Nastaví výchozí příznaky při načtení závislých knihoven DLL.|
|[/DLL](dll-build-a-dll.md)|Vytvoří knihovnu DLL.|
|[/DRIVER](driver-windows-nt-kernel-mode-driver.md)|Vytvoří ovladač režimu jádra.|
|[/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)|Určuje, zda se má generovat spustitelná bitová kopie, která je založena na čase načítání pomocí funkce náhodnosti rozložení adresního prostoru (ASLR).|
|[/ENTRY](entry-entry-point-symbol.md)|Nastaví počáteční adresu.|
|[/ERRORREPORT](errorreport-report-internal-linker-errors.md)| Zastaralé Zasílání zpráv o chybách se řídí nastavením [zasílání zpráv o chybách systému Windows (WER)](/windows/win32/wer/windows-error-reporting) . |
|[/EXPORT](export-exports-a-function.md)|Vyexportuje funkci.|
|[/FILEALIGN](filealign.md)|Zarovná oddíly v rámci výstupního souboru na násobcích zadané hodnoty.|
|[/FIXED](fixed-fixed-base-address.md)|Vytvoří program, který se dá načíst jenom na upřednostňovanou základní adresu.|
|[/Force.](force-force-file-output.md)|Vynutí odkaz na dokončení, a to i s nevyřešenými symboly nebo symboly, které jsou definovány více než jednou.|
|[/FUNCTIONPADMIN](functionpadmin-create-hotpatchable-image.md)|Vytvoří Image, která může být Hot patchovaná.|
|[/GENPROFILE,/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|Obě tyto možnosti specifikují generování *`.pgd`* souboru linkerem pro podporu optimalizace na základě profilu (PGO). /GENPROFILE a/FASTGENPROFILE používají jiné výchozí parametry.|
|[/GUARD](guard-enable-guard-checks.md)|Povolí ochranu před ochranou toku řízení.|
|[/HEAP](heap-set-heap-size.md)|Nastaví velikost haldy (v bajtech).|
|[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)|Určuje podporu náhodnosti rozložení adresního prostoru s vysokou entropií 64 (ASLR).|
|[/IDLOUT](idlout-name-midl-output-files.md)|Určuje název souboru *`.idl`* a dalších výstupních souborů MIDL.|
|[/IGNORE](ignore-ignore-specific-warnings.md)|Potlačí výstup zadaného upozornění linkeru.|
|[/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md)|Zabraňuje zpracování informací o atributu do souboru *`.idl`* .|
|[/IMPLIB](implib-name-import-library.md)|Přepíše výchozí název knihovny importu.|
|[/INCLUDE](include-force-symbol-references.md)|Vynutí odkazy na symboly.|
|[/INCREMENTAL](incremental-link-incrementally.md)|Řídí přírůstkové propojování.|
|[/INTEGRITYCHECK](integritycheck-require-signature-check.md)|Určuje, že modul vyžaduje kontrolu podpisu v době načítání.|
|[/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)|Určuje kontejner klíčů pro podepsání sestavení.|
|[/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|Určuje klíč nebo dvojici klíčů pro podepsání sestavení.|
|[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)|Instruuje kompilátor, že aplikace podporuje adresy větší než 2 gigabajty.|
|[/LIBPATH](libpath-additional-libpath.md)|Určuje cestu, která se má hledat před cestou ke knihovně prostředí.|
|[/LINKREPRO](linkrepro.md)|Určuje cestu k vygenerování artefaktů reprodukci propojení v.|
|[/LINKREPROTARGET](linkreprotarget.md)|Vygeneruje propojení reprodukci pouze při vytváření zadaného cíle. <sup>16,1</sup>|
|[/LTCG](ltcg-link-time-code-generation.md)|Určuje generování kódu při propojování.|
|[/MACHINE](machine-specify-target-platform.md)|Určuje cílovou platformu.|
|[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md)|Vytvoří soubor souběžného manifestu a volitelně ho vloží do binárního souboru.|
|[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md)|Určuje > oddílu \<dependentAssembly v souboru manifestu.|
|[/MANIFESTFILE](manifestfile-name-manifest-file.md)|Změní výchozí název souboru manifestu.|
|[/MANIFESTINPUT](manifestinput-specify-manifest-input.md)|Určuje vstupní soubor manifestu pro linker, který bude zpracovávat a vkládat v binárním souboru. Tuto možnost můžete použít několikrát, chcete-li zadat více než jeden vstupní soubor manifestu.|
|[/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)|Určuje, zda jsou v manifestu programu vloženy informace řízení uživatelských účtů (UAC).|
|[/MAP](map-generate-mapfile.md)|Vytvoří souboru mapování.|
|[/MAPINFO](mapinfo-include-information-in-mapfile.md)|Zahrnuje zadané informace v souboru mapování.|
|[/MERGE](merge-combine-sections.md)|Kombinuje oddíly.|
|[/MIDL](midl-specify-midl-command-line-options.md)|Určuje možnosti příkazového řádku MIDL.|
|[/NATVIS](natvis-add-natvis-to-pdb.md)|Přidá vizualizace ladicího programu ze souboru Natvis do databáze programu (PDB).|
|[/NOASSEMBLY](noassembly-create-a-msil-module.md)|Potlačí vytváření sestavení .NET Framework.|
|[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)|Při vyřešení externích odkazů ignoruje všechny (nebo zadané) výchozí knihovny.|
|[/NOENTRY](noentry-no-entry-point.md)|Vytvoří knihovnu DLL, která je jen pro prostředky.|
|[/NOLOGO](nologo-suppress-startup-banner-linker.md)|Potlačí úvodní nápis.|
|[/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)|Označí spustitelný soubor jako ověřený, aby byl kompatibilní s funkcí Zabránění spuštění dat systému Windows.|
|[/OPT](opt-optimizations.md)|Ovládá optimalizace odkazů.|
|[/ORDER](order-put-functions-in-order.md)|Umístí sekvence COMDAT do obrázku v předem určeném pořadí.|
|[/OUT](out-output-file-name.md)|Určuje název výstupního souboru.|
|[/PDB](pdb-use-program-database.md)|Vytvoří soubor PDB.|
|[/PDBALTPATH](pdbaltpath-use-alternate-pdb-path.md)|Používá alternativní umístění k uložení souboru PDB.|
|[/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)|Vytvoří soubor PDB, který nemá žádné soukromé symboly.|
|[/PGD](pgd-specify-database-for-profile-guided-optimizations.md)|Určuje *`.pgd`* soubor pro optimalizace na základě profilu.|
|[/POGOSAFEMODE](pogosafemode-linker-option.md)|**Zastaralé** Vytvoří instrumentované sestavení PGO bezpečné pro přístup z více vláken.|
|[/PROFILE](profile-performance-tools-profiler.md)|Vytvoří výstupní soubor, který se dá použít s profilerem Performance Tools.|
|[/RELEASE](release-set-the-checksum.md)|Nastaví kontrolní součet v hlavičce *`.exe`* .|
|[/SAFESEH](safeseh-image-has-safe-exception-handlers.md)|Určuje, že bitová kopie bude obsahovat tabulku bezpečných obslužných rutin výjimek.|
|[/SECTION](section-specify-section-attributes.md)|Přepisuje atributy oddílu.|
|[PŘEPÍNAČ/SOURCELINK](sourcelink.md)|Určuje soubor SourceLink, který se má přidat do souboru PDB.|
|[/STACK](stack-stack-allocations.md)|Nastaví velikost zásobníku v bajtech.|
|[/STUB](stub-ms-dos-stub-file-name.md)|Připojí k programu Win32 programový zástupný program v režimu MS-DOS.|
|[/SUBSYSTEM](subsystem-specify-subsystem.md)|Oznamuje operačnímu systému, jak spustit soubor *`.exe`* .|
|[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)|Oznamuje operačnímu systému, aby před spuštěním zkopíroval výstup linkeru do odkládacího souboru.|
|[/TLBID](tlbid-specify-resource-id-for-typelib.md)|Určuje ID prostředku knihovny typů generované linkerem.|
|[/TLBOUT](tlbout-name-dot-tlb-file.md)|Určuje název souboru *`.tlb`* a dalších výstupních souborů MIDL.|
|[/TSAWARE](tsaware-create-terminal-server-aware-application.md)|Vytvoří aplikaci, která je navržená speciálně pro spouštění v rámci terminálového serveru.|
|[/USEPROFILE](useprofile.md)|Používá školicí data optimalizace na základě profilu k vytvoření optimalizované bitové kopie.|
|[/VERBOSE](verbose-print-progress-messages.md)|Zobrazí zprávy o průběhu linkeru.|
|[/VERSION](version-version-information.md)|Přiřadí číslo verze.|
|[/WHOLEARCHIVE](wholearchive-include-all-library-object-files.md)|Zahrnuje všechny soubory objektů ze zadaných statických knihoven.|
|[/WINMD](winmd-generate-windows-metadata.md)|Povoluje generování souboru metadat prostředí Windows Runtime.|
|[/WINMDFILE](winmdfile-specify-winmd-file.md)|Určuje název souboru výstupu prostředí Windows Runtime metadat (WinMD), který je generován možností linkeru [/winmd](winmd-generate-windows-metadata.md) .|
|[/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md)|Určuje klíč nebo dvojici klíčů k podepsání prostředí Windows Runtime souboru metadat.|
|[/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md)|Určuje kontejner klíčů pro podepsání souboru metadat Windows.|
|[/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md)|Částečně podepíše soubor metadat prostředí Windows Runtime (. winmd) umístěním veřejného klíče do souboru winmd.|
|[/WX](wx-treat-linker-warnings-as-errors.md)|Zpracovává upozornění linkeru jako chyby.|

<sup>16,1</sup> Tato možnost je k dispozici počínaje verzí Visual Studio 2019 16,1.

## <a name="see-also"></a>Viz také

[C/C++ sestavit\ odkazu](c-cpp-building-reference.md)
[Referenční zdroje k linkeru MSVC](linking.md)
