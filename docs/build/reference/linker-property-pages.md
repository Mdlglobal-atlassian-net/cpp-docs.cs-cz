---
title: Stránky vlastností linkeru
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 2f2068c6c51fc6bf4e4104213e946e243fc6df2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336590"
---
# <a name="linker-property-pages"></a>Stránky vlastností linkeru

Následující vlastnosti naleznete v části**Properties** > **Propojovací služba****Vlastnosti** > konfigurace **projektu** > . Další informace o propojovacím systému naleznete [v tématu CL vyvolá propojovací a](cl-invokes-the-linker.md) [linker možnosti](linker-options.md).

## <a name="general-property-page"></a>Stránka obecné vlastnosti

### <a name="output-file"></a>Výstupní soubor

Možnost [/OUT](out-output-file-name.md) přepíše výchozí název a umístění programu, který vytvoří propojovací program.

### <a name="show-progress"></a>Zobrazit průběh

Vytiskne zprávy o průběhu propojovacího programu

**Choices**

- **Není nastaveno** - žádná podrobnost.
- **Zobrazit všechny zprávy o průběhu** - Zobrazí všechny zprávy o průběhu.
- **Pro prohledávané knihovny** – zobrazí zprávy o průběhu označující pouze prohledávané knihovny.
- **O skládání comdat během optimalizovaného propojení** - Zobrazí informace o skládání COMDAT během optimalizovaného propojení.
- **Data odebraná během optimalizovaného propojení** – Zobrazí informace o funkcích a datech odebraných během optimalizovaného propojení.
- **Moduly nekompatibilní se sekcí SEH** – zobrazí informace o modulech nekompatibilních s bezpečným zpracováním výjimek.
- **Aktivita linkeru související se spravovaným kódem** – Zobrazí informace o aktivitě propojovacího programu související se spravovaným kódem.

### <a name="version"></a>Version

Možnost [/VERSION](version-version-information.md) informuje propojovací ho do záhlaví souboru EXE nebo DLL. Pomocí funkce DUMPBIN /HEADERS zobrazíte pole verze obrázku volitelných hodnot záhlaví, chcete-li zobrazit efekt **parametru /VERSION**.

### <a name="enable-incremental-linking"></a>Povolit přírůstkové propojení

Umožňuje přírůstkové propojení. ([/INCREMENTAL](incremental-link-incrementally.md), /INCREMENTAL:NE)

### <a name="suppress-startup-banner"></a>Potlačit spouštěcí banner

Možnost [/NOLOGO](nologo-suppress-startup-banner-linker.md) zabraňuje zobrazení zprávy o autorských právech a čísla verze.

### <a name="ignore-import-library"></a>Ignorovat knihovnu importu

Tato vlastnost říká propojovacího zařízení není propojení žádné .lib výstup generovaný z tohoto sestavení do všech závislých projektu. Umožňuje systému projektu zpracovávat soubory DLL, které při vytváření nevytvářejí soubor LIB. Pokud projekt závisí na jiném projektu, který vytváří dll, systém projektu automaticky propojí soubor LIB vytvořený tímto podřízeným projektem. Tato vlastnost může být zbytečné v projektech, které produkují knihovny DLL COM nebo knihovny DLL pouze pro prostředky, protože tyto knihovny DLL nemají žádné smysluplné exporty. Pokud dll nemá žádné exporty, propojovací systém negeneruje soubor LIB. Pokud není k dispozici žádný soubor exportu LIB a systém projektu oznámí propojovacímu programu propojení s chybějící dll, propojení se nezdaří. K vyřešení tohoto problému použijte vlastnost **Ignorovat knihovnu importu.** Pokud je nastavena na **ano**, systém projektu ignoruje přítomnost nebo nepřítomnost souboru LIB a způsobí, že jakýkoli projekt, který závisí na tomto projektu, nebude propojen s neexistujícím souborem LIB.

Chcete-li programově přistupovat <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>k této vlastnosti, naleznete v tématu .

### <a name="register-output"></a>Zaregistrovat výstup

Spustí `regsvr32.exe /s $(TargetPath)` se na výstupu sestavení, který je platný pouze pro projekty .dll. U projektů EXE je tato vlastnost ignorována. Chcete-li zaregistrovat výstup .exe, nastavte událost postbuild v konfiguraci, abyste udělali vlastní registraci, která je vždy vyžadována pro registrované soubory EXE.

Chcete-li programově přistupovat <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>k této vlastnosti, naleznete v tématu .

### <a name="per-user-redirection"></a>Přesměrování na uživatele

Registrace v sadě Visual Studio se tradičně provádí v HKEY_CLASSES_ROOT (HKCR). V systému Windows Vista a novějších operačních systémech je nutné spustit visual studio ve zvýšeném režimu. Vývojáři ne vždy chtějí spustit ve zvýšeném režimu, ale stále musí pracovat s registrací. Přesměrování na uživatele umožňuje registraci bez nutnosti spouštět ve zvýšeném režimu.

Přesměrování na uživatele vynutí přesměrování zápisů do HKCR, které má být přesměrováno na HKEY\_CURRENT\_USER (HKCU). Pokud je přesměrování na uživatele vypnuto, může způsobit [chybu sestavení projektu PRJ0050,](../../error-messages/tool-errors/project-build-error-prj0050.md) když se program pokusí zapsat do HKCR.

### <a name="additional-library-directories"></a>Další adresáře knihovny

Umožňuje uživateli přepsat cestu knihovny prostředí. ([/LIBPATH](libpath-additional-libpath.md):složka)

### <a name="link-library-dependencies"></a>Závislosti knihovny propojení

Určuje, zda mají být soubory LIB vytvářeny závislými projekty. Obvykle chcete propojit v souborech LIB, ale nemusí tomu tak být u některých knihoven DLL.

Soubor OBJ můžete také zadat zadáním názvu souboru a relativní cesty, například ".. \\.. \MyLibProject\MyObjFile.obj". Pokud zdrojový kód souboru OBJ #includes předkompilované záhlaví, například pch.h, pak je soubor pch.obj umístěn ve stejné složce jako MyObjFile.obj. Je také nutné přidat pch.obj jako další závislost.

### <a name="use-library-dependency-inputs"></a>Použití vstupů závislostí knihovny

Určuje, zda mají být vstupy používány k knihovnickému nástroji, nikoli k samotnému souboru knihovny, při propojování výstupů knihovny závislostí projektu. Ve velkém projektu, když závislý projekt vytvoří soubor LIB, přírůstkové propojení je zakázáno. Pokud existuje mnoho závislých projektů, které vytvářejí soubory LIB, vytváření aplikace může trvat dlouhou dobu. Je-li tato vlastnost nastavena na **ano**, systém projektu propojí v souborech OBJ pro položky LIBProdukované závislými projekty a umožňuje přírůstkové propojení.

Informace o tom, jak získat přístup k stránce vlastností **obecného** propojovacího programu, naleznete [v tématu Nastavení kompilátoru jazyka C++ a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md).

### <a name="link-status"></a>Stav propojení

Určuje, zda má propojovací program zobrazit indikátor průběhu zobrazující procento propojení, které je dokončeno. Ve výchozím nastavení se tyto informace o stavu nezobrazují. ([/LTCG](ltcg-link-time-code-generation.md):STATUS| LTCG:NOSTATUS)

### <a name="prevent-dll-binding"></a>Zabránit vazbě dll

[/ALLOWBIND](allowbind-prevent-dll-binding.md): NO nastaví bit v záhlaví dll, který označuje Bind.exe, že obraz není povoleno být vázán. Pravděpodobně nebudete chtít, aby byla dll vázána, pokud byla digitálně podepsána (vazba zruší platnost podpisu).

### <a name="treat-linker-warning-as-errors"></a>Považovat upozornění propojovacího systému za chyby

[/WX](wx-treat-linker-warnings-as-errors.md) způsobí, že žádný výstupní soubor, který má být generován, pokud propojovací systém generuje upozornění.

### <a name="force-file-output"></a>Vynutit výstup souboru

Možnost [/FORCE](force-force-file-output.md) informuje propojovací systém k vytvoření souboru .exe nebo knihovny DLL, i když je symbol odkazován, ale není definován, nebo je definován. Může vytvořit neplatný soubor EXE.

**Choices**

- **Povoleno** - /FORCE bez argumentů znamená více a nevyřešené.
- **Vynásobte pouze definovaný symbol** – k vytvoření výstupního souboru použijte parametr /FORCE:MULTIPLE, i když odkaz najde více než jednu definici symbolu.
- **Pouze nedefinovaný symbol** - K vytvoření výstupního souboru použijte parametr /FORCE:UNRESOLVED bez ohledu na to, zda odkaz najde nedefinovaný symbol. /FORCE:UNRESOLVED je ignorována, pokud symbol vstupního bodu není vyřešen.

### <a name="create-hot-patchable-image"></a>Vytvořit funkční opravitelný obraz

Připraví obraz pro hotpatching.

**Choices**

- **Povoleno** – Připraví bitovou kopii pro hotpatching.
- **X86 Pouze obrázek** - Připraví obraz X86 pro hotpatching.
- **Pouze obrázek X64** - Připraví obraz X64 pro hotpatching.
- **Pouze obraz Itanium** - Připraví obraz Itanium pro hotpatching.

### <a name="specify-section-attributes"></a>Určení atributů oddílu

Možnost [/SECTION](section-specify-section-attributes.md) změní atributy oddílu a přepíše atributy nastavené při kompilaci souboru OBJ pro oddíl.

## <a name="input-property-page"></a>Stránka vstupních vlastností

### <a name="additional-dependencies"></a>Další závislosti

Určuje další položky, které mají být přidejte do příkazového řádku odkazu, například *kernel32.lib*.

### <a name="ignore-all-default-libraries"></a>Ignorovat všechny výchozí knihovny

Možnost [/NODEFAULTLIB](nodefaultlib-ignore-libraries.md) informuje propojovací ho, aby odebral jednu nebo více výchozích knihoven ze seznamu knihoven, které hledá při řešení externích odkazů.

### <a name="ignore-specific-default-libraries"></a>Ignorovat konkrétní výchozí knihovny

Určuje jeden nebo více názvů výchozích knihoven, které chcete ignorovat. Oddělte více knihoven středníky. (/NODEFAULTLIB:[jméno, jméno, ...])

### <a name="module-definition-file"></a>Soubor definice modulu

Možnost [/DEF](def-specify-module-definition-file.md) předá soubor definice modulu (.def) linkeru. Link lze zadat pouze jeden soubor .def.

### <a name="add-module-to-assembly"></a>Přidat modul do sestavy

Možnost [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md) umožňuje přidat odkaz na modul do sestavení. Informace o typu v modulu nebudou k dispozici pro program sestavení, který přidal odkaz na modul. Informace o typu v modulu však budou k dispozici všem programům, které odkazují na sestavení.

### <a name="embed-managed-resource-file"></a>Vložit soubor spravovaného prostředku

[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) vloží soubor prostředků do výstupního souboru.

### <a name="force-symbol-references"></a>Odkazy na symboly síly

Volba [/INCLUDE](include-force-symbol-references.md) sděluje propojovacímu zařízení, aby do tabulky symbolů přidal zadaný symbol.

### <a name="delay-loaded-dlls"></a>Zpožděné načtené knihovny DLL

Možnost [/DELAYLOAD](delayload-delay-load-import.md) způsobí zpožděné načítání knihoven DLL. Název dll určuje dll zpoždění zatížení.

### <a name="assembly-link-resource"></a>Zdroj propojení sestavení

Možnost [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md) vytvoří odkaz na prostředek rozhraní .NET Framework ve výstupním souboru. soubor prostředků není umístěn do výstupního souboru.

## <a name="manifest-file-property-page"></a>Stránka vlastností souboru manifestu

### <a name="generate-manifest"></a>Generovat manifest

[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md) určuje, že propojovací program by měl vytvořit soubor manifestu vedle sebe.

### <a name="manifest-file"></a>Soubor manifestu

[/MANIFESTFILE](manifestfile-name-manifest-file.md) umožňuje změnit výchozí název souboru manifestu. Výchozí název souboru manifestu je název souboru s připojeným manifestem .

### <a name="additional-manifest-dependencies"></a>Další závislosti manifestu

[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) umožňuje zadat atributy, které budou umístěny v části závislosti souboru manifestu.

### <a name="allow-isolation"></a>Povolit izolaci

Určuje chování pro vyhledávání manifestu. ([/ALLOWIZOLACE](allowisolation-manifest-lookup.md):NE)

### <a name="enable-user-account-control-uac"></a>Povolit řízení uživatelských účtů (UAC)

Určuje, zda je povolen a)If Account Control is enabled.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md), /MANIFESTUAC:NE)

### <a name="uac-execution-level"></a>Úroveň provádění příkazu Řízení řízení o řízení jako v OV

Určuje požadovanou úroveň spuštění aplikace při spuštění s řízením uživatelských účtů.  (/MANIFESTUAC:level=[hodnota])

**Choices**

- **asInvoker** - Úroveň spuštění uac: jako vyvolávač.
- **highestAvailable** - Úroveň spuštění příkazu UAC: nejvyšší dostupná.
- **requireAdministrator** - Úroveň spuštění systému Řízení přístupu: vyžadovat správce.

### <a name="uac-bypass-ui-protection"></a>Ochrana před uzemnatem ui.

Určuje, zda se mají obejít úrovně ochrany uživatelského rozhraní pro jiná okna na ploše.  Nastavte tuto vlastnost na "Ano" pouze pro aplikace pro usnadnění přístupu.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md):uiAccess=[true | false])

## <a name="debugging-property-page"></a>Stránka vlastností ladění

### <a name="generate-debug-info"></a>Generovat informace o ladění

Tato možnost umožňuje vytvoření ladicích informací pro soubor EXE nebo dll.

**Choices**

- **Ne** - Nevytvoří žádné informace o ladění.
- **Generovat informace o ladění** – vytvořte kompletní databázi programů (PDB) ideální pro distribuci na server symbolů společnosti Microsoft.
- **Generovat informace o ladění optimalizované pro rychlejší odkazy** – vytvoří programovou databázi (PDB) ideální pro cyklus edit-link-ladění.
- **Generovat informace o ladění optimalizované pro sdílení a publikování** - Vytvoří programdatabáze (PDB) ideální pro edit-link-ladění cyklu.

### <a name="generate-program-database-file"></a>Generovat soubor databáze programů

Ve výchozím nastavení při [/DEBUG](debug-generate-debug-info.md) je zadán, propojovací program vytvoří databázi programu (PDB), který obsahuje informace o ladění. Výchozí název souboru pro PDB má základní název programu a příponu .pdb.

### <a name="strip-private-symbols"></a>Strip soukromé symboly

Možnost [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md) vytvoří soubor druhé databáze programu (PDB) při vytváření bitové kopie programu s některou z možností kompilátoru nebo propojovacího programu, které generují soubor PDB (/DEBUG, /Z7, /Zd nebo /Zi).

### <a name="generate-map-file"></a>Generovat mapový soubor

[Možnost /MAP](map-generate-mapfile.md) sděluje propojovacímu systému vytvoření souboru mapy.

### <a name="map-file-name"></a>Název mapového souboru

Uživatelem zadaný název souboru map. Nahradí výchozí název.

### <a name="map-exports"></a>Mapovat exporty

Možnost [/MAPINFO](mapinfo-include-information-in-mapfile.md) informuje propojovací zařízení, aby zadal zadané informace do souboru mapy, který je vytvořen, pokud zadáte možnost /MAP. Export říká propojovacíprogram zahrnout exportované funkce.

### <a name="debuggable-assembly"></a>Laditelné sestavení

[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md) vydává atribut Ladicí atribut se sledováním ladicích informací a zakáže optimalizace JIT.

## <a name="system-property-page"></a>Stránka vlastností systému

### <a name="subsystem"></a>Subsystému

Možnost [/SUBSYSTEM](subsystem-specify-subsystem.md) informuje operační systém o spuštění souboru EXE. Volba subsystému ovlivňuje symbol vstupního bodu (nebo funkci vstupního bodu), kterou propojovací program zvolí.

**Choices**

- **Není nastaveno** - Není nastavenžádný subsystém.
- **Konzole** - Win32 znak-režim aplikace. Konzolové aplikace jsou uvedeny konzole operačním systémem. Pokud je definována hodnota main nebo wmain, je výchozím nastavením konzola CONSOLE.
- **Windows** - Aplikace nevyžaduje konzolu, pravděpodobně proto, že vytvoří vlastní okna pro interakci s uživatelem. Pokud je definována hodnota WinMain nebo wWinMain, je výchozí systém WINDOWS.
- **Nativní** – ovladače zařízení pro systém Windows NT. Pokud /DRIVER:WDM je zadán, NATIVE je výchozí.
- **Aplikace EFI** - aplikace EFI.
- **Ovladač zaváděcí služby EFI** - ovladač spouštěcí služby EFI.
- **EFI ROM** - EFI ROM.
- **Doba provozu EFI** – doba provozu EFI.
- **POSIX** - Aplikace, která běží s podsystémem POSIX v systému Windows NT.

### <a name="minimum-required-version"></a>Minimální požadovaná verze

Zadejte minimální požadovanou verzi subsystému. Argumenty jsou desetinná čísla v rozsahu 0 až 65 535.

### <a name="heap-reserve-size"></a>Velikost rezervhaldy

Určuje celkovou velikost přidělení haldy ve virtuální paměti. Výchozí hodnota je 1 MB.    ([/HEAP](heap-set-heap-size.md):rezerva)

### <a name="heap-commit-size"></a>Velikost potvrzení haldy

Určuje celkovou velikost přidělení haldy ve fyzické paměti. Výchozí hodnota je 4 KB.    ([/HEAP](heap-set-heap-size.md):rezerva,potvrzení)

### <a name="stack-reserve-size"></a>Velikost rezervace zásobníku

Určuje celkovou velikost přidělení zásobníku ve virtuální paměti. Výchozí hodnota je 1 MB.     ([/STACK](stack-stack-allocations.md):rezerva)

### <a name="stack-commit-size"></a>Velikost potvrzení zásobníku

Určuje celkovou velikost přidělení zásobníku ve fyzické paměti. Výchozí hodnota je 4 KB.     ([/STACK](stack-stack-allocations.md):rezerva,potvrzení)

### <a name="enable-large-addresses"></a>Povolit velké adresy

Možnost [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md) říká propojovacímu modulu, že aplikace může zpracovávat adresy větší než 2 gigabajty. Ve výchozím nastavení /LARGEADDRESSAWARE:NO je povolena, pokud /LARGEADDRESSAWARE není jinak zadán na linkerřádku.

### <a name="terminal-server"></a>Terminálový server

Možnost [/TSAWARE](tsaware-create-terminal-server-aware-application.md) nastaví příznak v poli IMAGE_OPTIONAL_HEADER DllCharacteristics ve volitelném záhlaví bitové kopie programu. Je-li tento příznak nastaven, terminálový server neprovede určité změny v aplikaci.

### <a name="swap-run-from-cd"></a>Zaměnit spuštění z disku CD

[Možnost /SWAPRUN](swaprun-load-linker-output-to-swap-file.md) říká operačnímu systému nejprve zkopírovat výstup propojovacího programu do odkládacího souboru a potom spustit bitovou kopii odtud. Tato možnost je funkcí systému Windows NT 4.0 (a novější). Je-li zadán disk CD,zkopíruje operační systém bitovou kopii na vyměnitelný disk do stránkovacího souboru a poté ji načte. **CD**

### <a name="swap-run-from-network"></a>Zaměnit spuštění ze sítě

[Možnost /SWAPRUN](swaprun-load-linker-output-to-swap-file.md) říká operačnímu systému nejprve zkopírovat výstup propojovacího programu do odkládacího souboru a potom spustit bitovou kopii odtud. Tato možnost je funkcí systému Windows NT 4.0 (a novější). Pokud **NET** net je zadán, operační systém nejprve zkopíruje binární bitovou kopii ze sítě do odkládacího souboru a načíst jej odtud. Tato možnost je užitečná pro spouštění aplikací v síti.

### <a name="driver"></a>Ovladač

Pomocí možnosti propojovacího programu [/DRIVER](driver-windows-nt-kernel-mode-driver.md) vytvořte ovladač režimu jádra systému Windows NT.

**Choices**

- **Není nastaveno** – výchozí nastavení ovladače.
- **Řidič** - Řidič
- **Pouze UP** - /DRIVER:UPONLY způsobí, že propojovací zařízení přidat IMAGE_FILE_UP_SYSTEM_ONLY bit u vlastností ve výstupní hlavičce určit, že se jedná o ovladač jednoprocesor (UP). Operační systém odmítne načíst ovladač UP do víceprocesorového (MP) systému.
- **WDM** - /DRIVER:WDM způsobí, že propojovací zařízení nastavit IMAGE_DLLCHARACTERISTICS_WDM_DRIVER bit v poli DllCharacteristics volitelné hlavičky.

## <a name="optimization-property-page"></a>Stránka vlastností optimalizace

### <a name="references"></a>Odkazy

[/OPT](opt-optimizations.md): REF eliminuje funkce a/nebo data, na která se nikdy neodkazuje, zatímco /OPT:NOREF uchovává funkce a/nebo data, na která se nikdy neodkazuje.

### <a name="enable-comdat-folding"></a>Povolit skládání sekvencí COMDAT

Pomocí [parametru /OPT](opt-optimizations.md):ICF\[=iterací] proveďte identické skládání COMDAT.

### <a name="function-order"></a>Pořadí funkcí

Možnost [/ORDER](order-put-functions-in-order.md)říká LINK pro optimalizaci programu umístěním určitých COMDATs do obrazu v předem určeném pořadí. LINK umístí funkce v zadaném pořadí v rámci každé části v obraze.

### <a name="profile-guided-database"></a>Databáze s asistencí profilu

Zadejte soubor .pgd pro optimalizaci s asistencí profilu. ([/PGD](pgd-specify-database-for-profile-guided-optimizations.md))

### <a name="link-time-code-generation"></a>Generování kódu času propojení

Určuje generování kódu v době propojení. ([/LTCG](ltcg-link-time-code-generation.md))

**Choices**

- **Výchozí** – výchozí nastavení LTCG.
- **Použití rychlého generování kódu času propojení** - použijte generování kódu času propojení s [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md).
- **Použití generování kódu času propojení** – použijte generování kódu času [propojení](ltcg-link-time-code-generation.md).
- **Optimalizace s asistencí profilu - Nástroj** - Použijte [optimalizaci s asistencí profilu](../profile-guided-optimizations.md) s :PGINSTRUMENT.
- **Optimalizace s asistencí profilu - Optimalizace** - Určuje, že propojovací program by měl použít data profilu vytvořená po spuštění instrumentovaného binárního souboru k vytvoření optimalizovaného obrazu.
- **Optimalizace s asistencí profilu - Aktualizace** - Umožňuje a sleduje seznam vstupních souborů, které mají být přidány nebo změněny z toho, co bylo zadáno ve fázi :PGINSTRUMENT.

## <a name="embedded-idl-property-page"></a>Stránka vlastností Vložené IDL

### <a name="midl-commands"></a>Příkazy MIDL

Určete možnosti příkazového řádku MIDL. ([/MIDL](midl-specify-midl-command-line-options.md):@responsefile)

### <a name="ignore-embedded-idl"></a>Ignorovat vložené IDL

Možnost [/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md) určuje, že žádné atributy IDL ve zdrojovém kódu by neměly být zpracovány do souboru .idl.

### <a name="merged-idl-base-file-name"></a>Sloučený název základního souboru IDL

Možnost [/IDLOUT](idlout-name-midl-output-files.md) určuje název a příponu souboru .idl.

### <a name="type-library"></a>Knihovna typů

Možnost [/TLBOUT](tlbout-name-dot-tlb-file.md) určuje název a příponu souboru TLB.

### <a name="typelib-resource-id"></a>ID prostředku TypeLib

Umožňuje zadat ID prostředku knihovny typů generovaných linkerem. ([/TLBID](tlbid-specify-resource-id-for-typelib.md):id)

## <a name="windows-metadata-property-page"></a>Stránka vlastností metadat systému Windows

### <a name="generate-windows-metadata"></a>Generování metadat systému Windows

Povolí nebo zakáže generování metadat systému Windows.

**Choices**

- **Ano** – Povolte generování souborů metadat systému Windows.
- **Ne** - Zakažte generování souborů metadat systému Windows.

### <a name="windows-metadata-file"></a>Soubor metadat systému Windows

Přepínač možností [/WINMDFILE.](winmdfile-specify-winmd-file.md)

### <a name="windows-metadata-key-file"></a>Soubor klíče metadat systému Windows

Zadejte klíč nebo dvojici klíčů pro podepsání metadat systému Windows. ([/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md):název_souboru)

### <a name="windows-metadata-key-container"></a>Kontejner klíčů metadat systému Windows

Zadejte kontejner klíčů pro podepsání metadat systému Windows. ([/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md):název)

### <a name="windows-metadata-delay-sign"></a>Znacení zpoždění metadat systému Windows

Částečně podepište metadata systému Windows. [Parametr /WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md) použijte, pokud chcete umístit veřejný klíč pouze do metadat systému Windows. Výchozí hodnota je /WINMDDELAYSIGN:NO.

## <a name="advanced-property-page"></a>Stránka rozšířené vlastnosti

### <a name="entry-point"></a>Vstupní bod

Možnost [/ENTRY](entry-entry-point-symbol.md) určuje funkci vstupního bodu jako počáteční adresu pro soubor EXE nebo dll.

### <a name="no-entry-point"></a>Žádný vstupní bod

Možnost [/NOENTRY](noentry-no-entry-point.md)je vyžadována pro vytvoření dll pouze pro prostředky. Tuto možnost použijte, chcete-li `_main` zabránit propojení odkazu s odkazem na dll.

### <a name="set-checksum"></a>Nastavit kontrolní součet

Možnost [/RELEASE](release-set-the-checksum.md) nastaví kontrolní součet v záhlaví souboru EXE.

### <a name="base-address"></a>Základní adresa

Nastaví základní adresu programu. ([/BASE](base-base-address.md):{adresa\[, velikost] | @filename,klíč})

### <a name="randomized-base-address"></a>Randomizovaná základní adresa

Randomizovaná základní adresa. ([/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)\[:NE])

### <a name="fixed-base-address"></a>Pevná základní adresa

Vytvoří program, který lze načíst pouze na jeho upřednostňovanou základní adresu. ([/OPRAVENO](fixed-fixed-base-address.md)\[:NE])

### <a name="data-execution-prevention-dep"></a>Zabránění spuštění dat (DEP)

Označí spustitelný soubor jako testovaný tak, aby byl kompatibilní s funkcí Zabránění spuštění dat systému Windows. ([/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)\[:NE])

### <a name="turn-off-assembly-generation"></a>Vypnout generování sestavy

Možnost [/NOASSEMBLY](noassembly-create-a-msil-module.md) informuje propojovací program k vytvoření bitové kopie pro aktuální výstupní soubor bez sestavení rozhraní .NET Framework.

### <a name="unload-delay-loaded-dll"></a>Uvolnit zpoždění načtené dll

Kvalifikátor **UNLOAD** informuje pomocnou funkci zpoždění a zatížení pro podporu explicitního uvolnění dll. ([/DELAY](delay-delay-load-import-settings.md):UNLOAD)

### <a name="nobind-delay-loaded-dll"></a>Nobind zpoždění načtené DLL

Kvalifikátor **NOBIND** říká propojovacímu zařízení, aby do konečného obrázku nezahrnul vyvažovatelný IAT. Výchozí hodnota je vytvořit vypovatelné IAT pro zpožděné knihovny DLL. ([/DELAY](delay-delay-load-import-settings.md):NOBIND)

### <a name="import-library"></a>Importovat knihovnu

Přepíše výchozí název knihovny importu. ([/IMPLIB](implib-name-import-library.md):název souboru)

### <a name="merge-sections"></a>Sloučit oddíly

Možnost [/MERGE](merge-combine-sections.md) kombinuje první část (od) s druhou částí (do) pojmenováním výsledného oddílu. Například /merge:.rdata=.text.

### <a name="target-machine"></a>Cílový stroj

Možnost [/MACHINE](machine-specify-target-platform.md) určuje cílovou platformu pro program.

**Choices**

- **Nenastaveno**
- **MachineARM**
- **StrojARM64**
- **MachineEBC**
- **StrojIA64**
- **MachineMIPS**
- **StrojMIPS16**
- **MachineMIPSFPU**
- **StrojMIPSFPU16**
- **StrojSH4**
- **MachineTHUMB**
- **StrojX64**
- **StrojX86**

### <a name="profile"></a>Profil

Vytvoří výstupní soubor, který lze použít s profilerem Nástroje výkonu. Vyžaduje generateDebugInformation (/[/DEBUG](debug-generate-debug-info.md)) nastavit. ([/PROFIL](profile-performance-tools-profiler.md))

### <a name="clr-thread-attribute"></a>Atribut vlákna CLR

Explicitně zadejte atribut zřetězení pro vstupní bod programu CLR.

**Choices**

- **Atribut zřetězení MTA** - Použije atribut MTAThreadAttribute na vstupní bod programu.
- **Sta threading atribut** - Použije STAThreadAttribute atribut vstupní bod programu.
- **Výchozí atribut zřetězení** – stejné jako nezadání [/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md). Umožňuje clr (Common Language Runtime) nastavit výchozí atribut zřetězení.

### <a name="clr-image-type"></a>Typ obrázku CLR

Nastaví typ (IJW, čistý nebo bezpečný) obrazu CLR.

**Choices**

- **Vynutit IJW obrázek**
- **Vynutit čistý obraz IL**
- **Vynutit bezpečný il obraz**
- **Výchozí typ obrázku**

### <a name="key-file"></a>Soubor klíče

Zadejte klíč nebo dvojici klíčů pro podepsání sestavení. ([/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md):název souboru)

### <a name="key-container"></a>Kontejner klíčů

Zadejte kontejner klíčů pro podepsání sestavení. ([/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md):název)

### <a name="delay-sign"></a>Znaménko zpoždění

Částečně podepsat sestavení. Použijte [/DELAYSIGN,](delaysign-partially-sign-an-assembly.md) pokud chcete umístit pouze veřejný klíč v sestavení. Výchozí hodnota je /DELAYSIGN:NO.

### <a name="clr-unmanaged-code-check"></a>Kontrola nespravovaného kódu CLR

[/CLRUNMANAGEDCODECHECK určuje,](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md) zda propojovací program použije suppressUnmanagedCodeSecurityAttribute pro volání PInvoke generovaný linkerem ze spravovaného kódu do nativních knihoven DLL.

### <a name="error-reporting"></a>Hlášení chyb

Umožňuje poskytnout informace o vnitřní chybě kompilátoru (ICE) přímo týmu Visual C++.

**Choices**

- **PromptImmediately** - Okamžitě se dotázat.
- **Fronta pro další přihlášení** – fronta pro další přihlášení.
- **Odeslat zprávu o chybě** – Odeslat zprávu o chybě.
- **Žádná zpráva o chybě** – žádná zpráva o chybách.

### <a name="sectionalignment"></a>SectionAlignment

Volba [/ALIGN](align-section-alignment.md) určuje zarovnání jednotlivých oddílů v lineárním adresním prostoru programu. Argument číslo je v bajtů a musí být mocninu dvou.

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>Zachovat poslední kód chyby pro volání PInvoke

[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md), který je ve výchozím nastavení zapnutý, zachová poslední kód chyby funkcí volaných prostřednictvím mechanismu P/Invoke, který umožňuje volat nativní funkce v DLLS z kódu kompilovaného pomocí /clr.

**Choices**

- **Povoleno** – povolit clrSupportlasterror.
- **Zakázáno** - Zakázat CLRSupportLastError.
- **Pouze systémové dll -** Povolit CLRSupportLastError pouze pro systémové dll.

### <a name="image-has-safe-exception-handlers"></a>Obrázek má obslužné rutiny bezpečných výjimek

Pokud [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) je zadán, propojovací aplikace vytvoří pouze bitovou kopii, pokud může také vytvořit tabulku obslužné rutiny bezpečné výjimky obrázku. Tato tabulka určuje, které obslužné rutiny výjimek jsou v operačním systému pro bitovou kopii platné.
