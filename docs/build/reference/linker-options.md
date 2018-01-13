---
title: "Možnosti linkeru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: link
dev_langs: C++
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
caps.latest.revision: "37"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f64f9bb94f6809ecfa189cd012dd0494506a3ca4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-options"></a>Možnosti linkeru

LINK.exe propojí běžné objekt souboru formátu (COFF) objekt souborů a knihoven vytvořit soubor spustitelný soubor (.exe) nebo dynamická knihovna (DLL).

Následující tabulka uvádí možnosti LINK.exe. Další informace o propojení najdete v tématu:

- [Možnosti LINK řízené kompilátorem](../../build/reference/compiler-controlled-link-options.md)

- [Vstupní soubory LINK](../../build/reference/link-input-files.md)

- [LINK – výstup](../../build/reference/link-output.md)

- [Vyhrazená slova](../../build/reference/reserved-words.md)

Na příkazovém řádku nejsou možnosti linkeru malá a velká písmena; například/základní a /BASE mají stejný význam. Podrobnosti o tom, jak zadat jednotlivé možnosti, na příkazovém řádku nebo v sadě Visual Studio najdete v dokumentaci pro tuto možnost.

Můžete použít [komentář](../../preprocessor/comment-c-cpp.md) – Direktiva pragma chcete zadat některé možnosti linkeru.

|Možnost|Účel|
|------------|-------------|
|[@](../../build/reference/at-specify-a-linker-response-file.md)|Určuje soubor odezvy.|
|[/ ALIGN](../../build/reference/align-section-alignment.md)|Určuje zarovnání každého oddílu.|
|[/ ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md)|Určuje, že nemůže být vázán knihovny DLL.|
|[/ ALLOWISOLATION](../../build/reference/allowisolation-manifest-lookup.md)|Určuje chování pro vyhledání manifestu.|
|[/ APPCONTAINER](../../build/reference/appcontainer-windows-store-app.md)|Určuje, zda aplikace musíte spustit v prostředí appcontainer procesu.|
|[/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)|Přidá <xref:System.Diagnostics.DebuggableAttribute> do spravovaných bitové kopie.|
|[/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)|Vytvoří odkaz na spravovaných prostředků.|
|[/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)|Určuje, že modul (MSIL intermediate language) Microsoft by měly být naimportovány do sestavení.|
|[/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)|Vloží soubor spravovaných prostředků v sestavení.|
|[/ BASE](../../build/reference/base-base-address.md)|Nastaví základní adresu programu.|
|[/ CGTHREADS](../../build/reference/cgthreads-compiler-threads.md)|Nastaví počet vláken cl.exe pro optimalizaci a generování kódu pokud je zadán parametr generování kódu v době propojování.|
|[/ CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md)|Nastaví typ obrázku CLR (IJW, čistý nebo bezpečné).|
|[/ CLRSUPPORTLASTERROR](../../build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|Zachovává kód poslední chyby funkcí, které se nazývají přes mechanismus P/Invoke.|
|[/ CLRTHREADATTRIBUTE](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md)|Určuje vláken atribut, který chcete použít pro vstupní bod aplikace CLR.|
|[/ CLRUNMANAGEDCODECHECK](../../build/reference/clrunmanagedcodecheck-add-supressunmanagedcodesecurityattribute.md)|Určuje, zda linkeru uplatní atributem suppressunmanagedcodesecurity na zástupných PInvoke generované linkeru procedur, které volají do nativních knihoven DLL ze spravovaného kódu.|
|[/ DEBUG](../../build/reference/debug-generate-debug-info.md)|Vytvoří ladicí informace.|
|[/ DEBUGTYPE](../../build/reference/debugtype-debug-info-options.md)|Určuje, která data chcete zahrnout do informace pro ladění.|
|[/ DEF](../../build/reference/def-specify-module-definition-file.md)|Soubor definice modulu (.def) předá linkeru.|
|[/ DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md)|Když jsou vyřešeny externí odkazy, vyhledá uvedené knihovny.|
|[/ DELAY](../../build/reference/delay-delay-load-import-settings.md)|Ovládací prvky zpožděné načítání knihovny DLL.|
|[/ DELAYLOAD](../../build/reference/delayload-delay-load-import.md)|Způsobí, že zpožděné načítání určené knihovny DLL.|
|[/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)|Částečně podepisuje sestavení.|
|[/ DLL](../../build/reference/dll-build-a-dll.md)|Sestavení knihovny DLL.|
|[/ DRIVER](../../build/reference/driver-windows-nt-kernel-mode-driver.md)|Vytvoří ovladač režimu jádra.|
|[/ DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md)|Určuje, jestli se má generovat spustitelné bitové kopie, který může být náhodně rebased při načítání, pomocí funkce adresního prostoru rozložení náhodného přeskupování (technologie ASLR).|
|[/ ENTRY](../../build/reference/entry-entry-point-symbol.md)|Nastaví počáteční adresa.|
|[/ errorreport](../../build/reference/errorreport-report-internal-linker-errors.md)|Sestava s interními chybami linkeru společnosti Microsoft.|
|[/ EXPORT](../../build/reference/export-exports-a-function.md)|Export funkce.|
|[/ FILEALIGN](../../build/reference/filealign.md)|Zarovnává částí v souboru výstup na násobky zadanou hodnotou.|
|[/ FIXED](../../build/reference/fixed-fixed-base-address.md)|Vytvoří program, který je možné načíst pouze v jeho upřednostňovaná základní adresa.|
|[/ FORCE](../../build/reference/force-force-file-output.md)|Vynutí odkazu na dokončení i s nevyřešenými symboly nebo symboly definován více než jednou.|
|[/ FUNCTIONPADMIN](../../build/reference/functionpadmin-create-hotpatchable-image.md)|Vytvoří bitovou kopii, která se dá za opravit.|
|[/ GENPROFILE, /FASTGENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|Obě tyto možnosti určují generování souboru .pgd podle linkeru pro podporu optimalizace na základě profilu (PGO). / GENPROFILE a /FASTGENPROFILE používají různé výchozí parametry.|
|[/ GUARD](../../build/reference/guard-enable-guard-checks.md)|Umožňuje řízení toku ochrana ochrany.|
|[/ HEAP](../../build/reference/heap-set-heap-size.md)|Nastaví velikost haldy, v bajtech.|
|[/ HIGHENTROPYVA](../../build/reference/highentropyva-support-64-bit-aslr.md)|Určuje podporu pro vysokou entropií 64-bit adresu místa rozložení náhodné (technologie ASLR).|
|[/ IDLOUT](../../build/reference/idlout-name-midl-output-files.md)|Určuje název souboru IDL a ostatní výstupní soubory MIDL.|
|[/ IGNORE](../../build/reference/ignore-ignore-specific-warnings.md)|Potlačí výstup linkeru zadaný upozornění.|
|[/ IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)|Zabraňuje zpracování informace o atributu do souboru IDL.|
|[/ IMPLIB](../../build/reference/implib-name-import-library.md)|Přepíše výchozí název knihovny importu.|
|[/ INCLUDE](../../build/reference/include-force-symbol-references.md)|Vynutí symbolů odkazy.|
|[/ INCREMENTAL](../../build/reference/incremental-link-incrementally.md)|Ovládací prvky přírůstkové propojování.|
|[/ INTEGRITYCHECK](../../build/reference/integritycheck-require-signature-check.md)|Určuje, že modul vyžaduje Kontrola podpisu v okamžiku načtení.|
|[/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)|Určuje kontejner klíčů pro podepsání sestavení.|
|[/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|Určuje klíč nebo pár klíčů pro podepsání sestavení.|
|[/ LARGEADDRESSAWARE](../../build/reference/largeaddressaware-handle-large-addresses.md)|Říká kompilátoru, že aplikace podporuje větší než dva gigabajty adresy|
|[/ LIBPATH](../../build/reference/libpath-additional-libpath.md)|Určuje cestu k vyhledání před cestu prostředí knihovny.|
|[/ LTCG](../../build/reference/ltcg-link-time-code-generation.md)|Určuje generování kódu v době propojování.|
|[/ MACHINE](../../build/reference/machine-specify-target-platform.md)|Určuje cílovou platformu.|
|[/ MANIFEST](../../build/reference/manifest-create-side-by-side-assembly-manifest.md)|Vytvoří soubor manifestu vedle sebe a volitelně se vloží do binárního souboru.|
|[/ MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md)|Určuje \<dependentAssembly > oddíl v souboru manifestu.|
|[/ MANIFESTFILE](../../build/reference/manifestfile-name-manifest-file.md)|Změní výchozí název souboru manifestu.|
|[/ MANIFESTINPUT](../../build/reference/manifestinput-specify-manifest-input.md)|Určuje vstupní soubor manifestu pro linkeru pro zpracování a vložit do binárního souboru. Tato možnost více než jednou. můžete zadat více než jeden vstupní soubor manifestu.|
|[/ MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md)|Určuje, zda je v manifestu program vložených informace řízení uživatelských účtů (UAC).|
|[/ MAP](../../build/reference/map-generate-mapfile.md)|Vytvoří souboru mapování.|
|[/ MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)|Obsahuje informace o zadaném v souboru mapování.|
|[/ MERGE](../../build/reference/merge-combine-sections.md)|Kombinuje části.|
|[/ MIDL](../../build/reference/midl-specify-midl-command-line-options.md)|Určuje možnosti příkazového řádku MIDL.|
|[/ NATVIS](../../build/reference/natvis-add-natvis-to-pdb.md)|Přidá ladicí program vizualizérech ze souboru Natvis PDB.|
|[/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)|Potlačí vytvoření sestavení rozhraní .NET Framework.|
|[/ NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)|Ignoruje všechny (nebo zadaný) výchozí knihovny, když jsou vyřešeny externí odkazy.|
|[/ NOENTRY](../../build/reference/noentry-no-entry-point.md)|Vytvoří prostředek knihovny DLL.|
|[/ NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)|Potlačí úvodní nápis při spouštění.|
|[/ NXCOMPAT](../../build/reference/nxcompat-compatible-with-data-execution-prevention.md)|Označí spustitelného souboru jako kompatibilní s funkcí Zabránění spuštění dat systému Windows.|
|[/ OPT](../../build/reference/opt-optimizations.md)|Ovládací prvky odkaz optimalizace.|
|[/ ORDER](../../build/reference/order-put-functions-in-order.md)|COMDATs umístí do bitové kopie v předurčeném pořadí.|
|[/ OUT](../../build/reference/out-output-file-name.md)|Určuje název výstupního souboru.|
|[/ PDB](../../build/reference/pdb-use-program-database.md)|Vytvoří soubor programu databáze (PDB).|
|[/ PDBALTPATH](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)|Uloží do souboru PDB pomocí alternativního umístění.|
|[/ PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)|Vytvoří soubor databáze (PDB) program, který nemá žádný privátní symboly.|
|[/ PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)|Určuje soubor .pgd pro optimalizace na základě profilu.|
|[NEBO PROFIL](../../build/reference/profile-performance-tools-profiler.md)|Vytvoří výstupního souboru, který lze použít s profileru nástroje pro sledování výkonu.|
|[A VERZE](../../build/reference/release-set-the-checksum.md)|Nastaví kontrolního součtu v hlavičce .exe.|
|[/ SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)|Určuje, zda obrázek bude obsahovat tabulku obslužné rutiny výjimek bezpečné.|
|[/ SECTION](../../build/reference/section-specify-section-attributes.md)|Přepíše atributy oddílu.|
|[/ STACK](../../build/reference/stack-stack-allocations.md)|Nastaví velikost zásobníku v bajtech.|
|[/ STUB](../../build/reference/stub-ms-dos-stub-file-name.md)|Připojí programu zástupného kódu MS-DOS Win32 programu.|
|[/ SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)|Popis operačního systému způsobu spusťte soubor .exe.|
|[/ SWAPRUN](../../build/reference/swaprun-load-linker-output-to-swap-file.md)|Informuje zkopírujte výstup linkeru do souboru odkládacího souboru, než je spuštěn operační systém.|
|[/ TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md)|Určuje ID prostředku knihovny typů generované linkeru.|
|[/ TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)|Určuje název souboru .tlb a ostatní výstupní soubory MIDL.|
|[/ TSAWARE](../../build/reference/tsaware-create-terminal-server-aware-application.md)|Vytvoří aplikaci, která je určená speciálně ke spuštění v režimu terminálového serveru.|
|[/ VERBOSE](../../build/reference/verbose-print-progress-messages.md)|Vytiskne hlášení průběhu linkeru.|
|[/ VERZE](../../build/reference/version-version-information.md)|Přiřadí číslo verze.|
|[/ WHOLEARCHIVE](../../build/reference/wholearchive-include-all-library-object-files.md)|Zahrnuje každý soubor objekt ze zadané statické knihovny.|
|[/ WINMD](../../build/reference/winmd-generate-windows-metadata.md)|Umožňuje generování metadat Windows Runtime souboru.|
|[/ WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md)|Určuje název souboru pro výstupní soubor metadat Windows Runtime (winmd), který je generovaný [/WINMD](../../build/reference/winmd-generate-windows-metadata.md) – možnost linkeru.|
|[/ WINMDFILE](../../build/reference/winmdkeyfile-specify-winmd-key-file.md)|Určuje klíč nebo pár klíčů k podepsání souboru metadat modulu Runtime Windows.|
|[/ WINMDKEYCONTAINER](../../build/reference/winmdkeycontainer-specify-key-container.md)|Určuje kontejner klíčů pro podepsání souboru metadat Windows.|
|[/ WINMDDELAYSIGN](../../build/reference/winmddelaysign-partially-sign-a-winmd.md)|Částečně podepíše soubor metadat Windows Runtime (.winmd) tím, že veřejný klíč v souboru winmd.|
|[/WX](../../build/reference/wx-treat-linker-warnings-as-errors.md)|Zpracovává upozornění linkeru jako chyby.|

Další informace najdete v tématu [možnosti odkazů Compiler-Controlled](../../build/reference/compiler-controlled-link-options.md).

## <a name="see-also"></a>Viz také

[Referenční zdroje k sestavení programu v jazyce C/C++](../../build/reference/c-cpp-building-reference.md)  
[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)  