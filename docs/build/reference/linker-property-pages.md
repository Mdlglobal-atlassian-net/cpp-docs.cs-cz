---
title: Stránky vlastností linkeru
ms.date: 7/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 17880d50ae012b640cb83f3766883ab2b1bcbe73
ms.sourcegitcommit: 7b039b5f32f6c59be6c6bb1cffafd69c3bfadd35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68537599"
---
# <a name="linker-property-pages"></a>Stránky vlastností linkeru

Následující vlastnosti jsou nalezeny v části**vlastnosti** >  **projektu** > **vlastnosti** > konfigurace**linker**. Další informace o linkeru naleznete v tématu [CL vyvolá](cl-invokes-the-linker.md) Možnosti linkeru a [linkeru](linker-options.md).

## <a name="general-property-page"></a>Obecná stránka vlastností

### <a name="output-file"></a>Výstupní soubor

Možnost [/out](out-output-file-name.md) přepisuje výchozí název a umístění programu, který vytvoří linker.

### <a name="show-progress"></a>Zobrazit průběh

Vytiskne zprávy o průběhu linkeru.

**Vlastnit**

- Nenastaveno – bez podrobností
- **Zobrazit všechny zprávy o průběhu** – zobrazí všechny zprávy o průběhu. 
- **Pro prohledávané knihovny** – zobrazí zprávy o průběhu, které označují pouze prohledávané knihovny.
- **O skládání COMDAT během optimalizovaného propojování** – zobrazí informace o skládání COMDAT během optimalizovaného propojování.
- Informace o **odebraných datech během optimalizovaného propojování** – zobrazí informace o funkcích a datech odebraných během optimalizovaného propojování.
- **O modulech nekompatibilních s SEH** – zobrazí informace o modulech nekompatibilních s bezpečným zpracováním výjimek.
- **O aktivitě linkeru související se spravovaným kódem** – zobrazí informace o aktivitě linkeru související se spravovaným kódem.

### <a name="version"></a>Version

Možnost [/Version](version-version-information.md) dá linkeru pokyn, aby vložil číslo verze do hlavičky souboru. exe nebo. dll. Pomocí DUMPBIN/HEADERS můžete zobrazit pole verze obrázku VOLITELNÝch hodnot hlaviček, abyste viděli účinek **/Version**.

### <a name="enable-incremental-linking"></a>Povolit přírůstkové propojování

Povolí přírůstkové propojování. ([/INCREMENTAL](incremental-link-incrementally.md),/INCREMENTAL: NO)

### <a name="suppress-startup-banner"></a>Potlačit úvodní nápis

Možnost [/nologo](nologo-suppress-startup-banner-linker.md) zabraňuje zobrazení zprávy o autorských právech a čísla verze. 

### <a name="ignore-import-library"></a>Ignorovat knihovnu importu

Tato vlastnost oznamuje linkeru, že neodkazuje žádný z výstupů. lib vygenerovaných z tohoto sestavení do libovolného závislého projektu. To umožňuje systému projektu zpracovávat soubory. dll, které při sestavení nevytvářejí soubor. lib. Pokud projekt závisí na jiném projektu, který vytváří knihovnu DLL, systém projektu automaticky propojí soubor. lib vytvořený tímto podřízeným projektem. To nemusí být potřeba pro projekty, které vytvářejí knihovny COM DLL nebo knihovny DLL, které jsou jen pro prostředky; Tyto knihovny DLL nemají smysluplné exporty. Pokud knihovna DLL neobsahuje žádné exporty, linker negeneruje soubor. lib. Pokud na disku není k dispozici žádný soubor export. lib a systém projektu sdělí linkeru, aby provedl propojení s touto (chybějící) knihovnou DLL, odkaz se nezdařil. K vyřešení tohoto problému použijte vlastnost **Ignorovat knihovnu import** . Když je nastaveno na **Ano**, systém projektu ignoruje přítomnost nebo absence daného souboru. lib a způsobí, že každý projekt, který závisí na tomto projektu, nebude propojen s neexistujícím souborem. lib.

Chcete-li programově získat přístup k <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>této vlastnosti, přečtěte si téma.

### <a name="register-output"></a>Registrovat výstup

Spouští `regsvr32.exe /s $(TargetPath)` se ve výstupu sestavení, který je platný pouze pro projekty. dll. Pro projekty. exe je tato vlastnost ignorována. Chcete-li zaregistrovat výstup. exe, nastavte událost postbuild v konfiguraci tak, aby vlastní registraci, která je vždy vyžadována pro registrované soubory. exe.

Chcete-li programově získat přístup k <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>této vlastnosti, přečtěte si téma.

### <a name="per-user-redirection"></a>Přesměrování podle uživatele

Registrace v aplikaci Visual Studio se tradičně provedla v registru HKEY_CLASSES_ROOT (HKCR). V případě systému Windows Vista a novějších operačních systémů je pro přístup k HKCR nutné spustit aplikaci Visual Studio v režimu zvýšeného oprávnění. Vývojáři nechtějí vždy spouštět v režimu zvýšené úrovně, ale stále musí fungovat s registrací. Přesměrování vázané na uživatele umožňuje registraci bez nutnosti spuštění v tomto režimu.

Přesměrování dle uživatele vynutí přesměrování zápisu do HKCR na HKEY\_aktuálního\_uživatele (HKCU). Pokud je přesměrování pro jednotlivé uživatele vypnuté, může způsobit [chybu sestavení projektu PRJ0050](../../error-messages/tool-errors/project-build-error-prj0050.md) , když se program pokusí zapisovat do HKCR.

### <a name="additional-library-directories"></a>Další adresáře knihoven

Umožňuje uživateli přepsat cestu ke knihovně prostředí. ([/LIBPATH](libpath-additional-libpath.md): složka)

### <a name="link-library-dependencies"></a>Propojit závislosti knihoven

Určuje, zda se mají propojit soubory. lib, které jsou vytvářeny závislými projekty. Obvykle je vhodné propojit soubory. lib, ale nemusí se jednat o případ některých knihoven DLL.

Můžete také zadat soubor. obj zadáním názvu souboru a relativní cesty, například. \\. \MyLibProject\MyObjFile.obj". Pokud zdrojový kód pro soubor. obj #includes předkompilovanou hlavičku, například PCH. h, pak je soubor PCH. obj umístěný ve stejné složce jako MyObjFile. obj a Vy musíte také přidat soubor PCH. obj jako další závislost.

### <a name="use-library-dependency-inputs"></a>Použít vstupy závislosti knihoven

Určuje, zda se při propojování výstupů knihoven závislostí projektu použijí vstupy nástroje Librarian spíše než samotný soubor knihovny. Ve velkém projektu, když závislý projekt vytvoří soubor. lib, je přírůstkové propojení zakázáno. Pokud existuje mnoho závislých projektů, které vytvářejí soubory. lib, sestavení aplikace může trvat dlouhou dobu. Pokud je tato vlastnost nastavena na **hodnotu Ano**, projektový systém odkazuje v souborech. obj pro. knihovny vytvořených závislými projekty, čímž umožňuje přírůstkové propojení.

Informace o tom, jak získat přístup k stránce vlastností **obecného** linkeru, naleznete v tématu [Nastavení vlastností kompilátoru a sestavení v sadě C++ Visual Studio](../working-with-project-properties.md).

### <a name="link-status"></a>Stav propojení

Určuje, zda má linker zobrazit ukazatel průběhu ukazující, jaké procento propojení je dokončeno. Ve výchozím nastavení se tyto informace o stavu nezobrazují. ([/LTCG](ltcg-link-time-code-generation.md): STATUS | LTCG: INSTATUS)

### <a name="prevent-dll-binding"></a>Zabránit vazbě knihoven DLL

[/ALLOWBIND](allowbind-prevent-dll-binding.md): v záhlaví knihovny DLL nejsou nastaveny žádné bity, které označují, že se k souboru BIND. exe nepovoluje svázat. Je možné, že nebudete mít vazbu na knihovnu DLL, pokud byla digitálně podepsaná (vazba zruší platnost podpisu).

### <a name="treat-linker-warning-as-errors"></a>Zpracovávat upozornění linkeru jako chyby

[/WX](wx-treat-linker-warnings-as-errors.md) způsobí vygenerování žádného výstupního souboru, pokud linker vygeneruje upozornění.

### <a name="force-file-output"></a>Vynutit výstup souboru

Možnost [/Force](force-force-file-output.md) přikáže linkeru, aby vytvořil soubor. exe nebo knihovnu DLL i v případě, že se na symbol odkazuje, ale není definován nebo je definován násobek. Může vytvořit neplatný soubor. exe.

**Vlastnit**

- **Enabled** –/Force bez argumentů předpokládá vícenásobné i nevyřešené.
- **Vynásobit definovaný symbol pouze** pomocí parametru/Force: Multiple k vytvoření výstupního souboru, bez ohledu na to, zda propojení nalezne více než jednu definici pro symbol.
- **Pouze nedefinovaný symbol** – k vytvoření výstupního souboru, bez ohledu na to, zda odkaz najde nedefinovaný symbol, použijte příkaz/Force: unresolveed. /FORCE: nevyřešeno je ignorováno, pokud je symbol vstupního bodu nevyřešený.

### <a name="create-hot-patchable-image"></a>Vytvořit bitovou kopii s aktivní opravou

Připraví bitovou kopii na technologii HotPatching.

**Vlastnit**

- **Enabled** – připraví bitovou kopii na technologii HotPatching.
- **Pouze image x86** – připraví bitovou kopii x86 pro technologii HotPatching.
- **Image x64** – připraví bitovou kopii x64 pro technologii HotPatching.
- **Pouze image Itanium** – připraví bitovou kopii Itanium pro technologii HotPatching.

### <a name="specify-section-attributes"></a>Zadat atributy oddílu

Možnost [/Section](section-specify-section-attributes.md) změní atributy oddílu a přepíše přitom atributy nastavené při kompilaci souboru. obj pro oddíl.

## <a name="input-property-page"></a>Vstupní stránka vlastností

### <a name="additional-dependencies"></a>Další závislosti

Určuje další položky, které se mají přidat do příkazového řádku propojení, například *Kernel32. lib*.

### <a name="ignore-all-default-libraries"></a>Ignorovat všechny výchozí knihovny

Možnost [/NODEFAULTLIB](nodefaultlib-ignore-libraries.md) přikáže linkeru, aby odebral jednu nebo více výchozích knihoven ze seznamu knihoven, které vyhledává při překladu externích odkazů. 

### <a name="ignore-specific-default-libraries"></a>Ignorovat specifické výchozí knihovny

Určuje jeden nebo více názvů výchozích knihoven, které se mají ignorovat. více knihoven oddělte středníkem. (/NODEFAULTLIB: [název; název;...])

### <a name="module-definition-file"></a>Soubor definice modulu

Parametr [/def](def-specify-module-definition-file.md) předá linkeru soubor definice modulu (. def). Pro propojení lze zadat pouze jeden soubor. def. 

### <a name="add-module-to-assembly"></a>Přidat modul do sestavení

Možnost [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md) umožňuje přidat odkaz na modul do sestavení. Informace o typu v modulu nebudou k dispozici programu sestavení, který přidal odkaz na modul. Nicméně informace o typech v modulu budou k dispozici pro všechny programy, které odkazují na sestavení.

### <a name="embed-managed-resource-file"></a>Vložit spravovaný soubor prostředků

[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) vloží soubor prostředků do výstupního souboru.

### <a name="force-symbol-references"></a>Vynutit odkazy na symboly

Možnost [/include](include-force-symbol-references.md) dá linkeru pokyn, aby přidal zadaný symbol do tabulky symbolů.

### <a name="delay-loaded-dlls"></a>Odložené načtené knihovny DLL

Možnost [/DELAYLOAD](delayload-delay-load-import.md) způsobuje zpožděné načítání knihoven DLL. Název knihovny DLL určuje knihovnu DLL pro odložené načtení. 

### <a name="assembly-link-resource"></a>Prostředek odkazu na sestavení

Možnost [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md) vytvoří odkaz na prostředek .NET Framework ve výstupním souboru; zdrojový soubor není umístěný do výstupního souboru.

## <a name="manifest-file-property-page"></a>Stránka vlastností souboru manifestu

### <a name="generate-manifest"></a>Generovat manifest

[/Manifest](manifest-create-side-by-side-assembly-manifest.md) určuje, že linker by měl vytvořit souběžně umístěný soubor manifestu.

### <a name="manifest-file"></a>Soubor manifestu

[/MANIFESTFILE](manifestfile-name-manifest-file.md) umožňuje změnit výchozí název souboru manifestu. Výchozím názvem souboru manifestu je název souboru s příponou. manifest byl připojen.

### <a name="additional-manifest-dependencies"></a>Další závislosti manifestu

[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) umožňuje zadat atributy, které budou umístěny v části závislosti souboru manifestu.

### <a name="allow-isolation"></a>Povoluje izolaci

Určuje chování při vyhledávání manifestu. ([/ALLOWISOLATION](allowisolation-manifest-lookup.md): NO)

### <a name="enable-user-account-control-uac"></a>Povolit řízení uživatelských účtů (UAC)

Určuje, jestli je povolený řízení uživatelských účtů.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md),/MANIFESTUAC: NO)

### <a name="uac-execution-level"></a>Úroveň spuštění nástroje řízení uživatelských účtů

Určuje požadovanou úroveň spuštění aplikace při spuštění pomocí nástroje řízení uživatelských účtů.  (/MANIFESTUAC: Level = [hodnota])

**Vlastnit**

- **podle volajícího** -UAC – úroveň spuštění: jako původce.
- **nejvyšší dostupná** -UAC – úroveň spuštění: nejvyšší dostupný.
- **vyžadovat správce** -UAC – úroveň spuštění: vyžadovat správce.

### <a name="uac-bypass-ui-protection"></a>Řízení uživatelských účtů – obejít ochranu uživatelského rozhraní

Určuje, jestli se mají obejít úrovně ochrany uživatelského rozhraní pro jiná okna na ploše.  Nastavte tuto vlastnost na Yes jenom pro aplikace usnadnění.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md): UIAccess = [true | false])

## <a name="debugging-property-page"></a>Stránka vlastností ladění

### <a name="generate-debug-info"></a>Generovat informace o ladění

Tato možnost umožňuje vytvoření informací o ladění pro soubor. exe nebo knihovnu DLL.

**Vlastnit**

- **Ne** – nevytváří žádné ladicí informace.
- **Vygenerovat informace o ladění** – vytvoří kompletní programovou databázi (PDB), která je ideální pro distribuci na server symbolů Microsoft.
- **Generovat ladicí informace optimalizované pro rychlejší odkazy** – vytvoří programovou databázi (PDB) ideální pro cyklus úpravy-propojení-ladění. 
- **Vygenerovat informace o ladění optimalizované pro sdílení a publikování** – vytvoří databázi programu (PDB) ideální pro cyklus úpravy-propojení-ladění. 

### <a name="generate-program-database-file"></a>Generovat soubor databáze programu

Ve výchozím nastavení, když je zadán parametr [/Debug](debug-generate-debug-info.md) , linker vytvoří databázi programu (PDB), která obsahuje ladicí informace. Výchozí název souboru PDB má základní název programu a příponu. pdb.

### <a name="strip-private-symbols"></a>Odstranit privátní symboly

Možnost [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md) vytvoří druhý soubor programové databáze (PDB) při sestavování image programu pomocí kterékoli z možností kompilátoru nebo linkeru, které GENERUJÍ soubor PDB (/Debug,/Z7,/zd nebo/Zi).

### <a name="generate-map-file"></a>Generovat soubor mapy

Možnost [/map](map-generate-mapfile.md) dá linkeru pokyn, aby vytvořil souboru mapování.

### <a name="map-file-name"></a>Název souboru mapy

Uživatelem zadaný název pro souboru mapování. Nahradí výchozí název.

### <a name="map-exports"></a>Exporty map

Možnost [/MapInfo](mapinfo-include-information-in-mapfile.md) dá linkeru pokyn, aby zahrnul zadané informace do souboru mapování, které se vytvoří, pokud zadáte možnost/map. Export dává linkeru pokyn, aby zahrnoval exportované funkce.

### <a name="debuggable-assembly"></a>Laditelné sestavení

[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md) emituje atribut DebuggableAttribute pomocí sledování informací o ladění a ZAKÁŽE optimalizace JIT.

## <a name="system-property-page"></a>Stránka vlastností systému

### <a name="subsystem"></a>Provozuschopn

Možnost [/Subsystem](subsystem-specify-subsystem.md) oznamuje operačnímu systému, jak spustit soubor. exe. Volba subsystému ovlivní symbol vstupního bodu (nebo funkci vstupního bodu), kterou bude linker volit.

**Vlastnit**

- Nenastaveno-není nastaven žádný subsystém.
- **Konzola** – aplikace v režimu znaků Win32 Konzolové aplikace jsou v operačním systému přiděleny konzolou. Je-li definována Main nebo wmain, je konzola výchozím nastavením.
- **Systém Windows** -aplikace nevyžaduje konzolu, pravděpodobně proto, že vytváří vlastní okna pro interakci s uživatelem. Je-li definována hodnota WinMain nebo wWinMain, je výchozím systémem systém WINDOWS.
- Ovladače nativního zařízení pro systém Windows NT. Pokud je zadáno/DRIVER: WDM, NATIVNÍ je výchozí hodnota.
- Aplikace **rozhraní EFI** – aplikace EFI.
- Ovladač **spouštěcí služby EFI** – ovladač spouštěcí služby EFI
- **EFI ROM** – EFI ROM
- **Modul runtime EFI** – modul runtime EFI.
- **POSIX** – aplikace, která běží v subsystému POSIX v systému Windows NT.

### <a name="minimum-required-version"></a>Minimální požadovaná verze

Zadejte minimální požadovanou verzi subsystému. Argumenty jsou desítková čísla v rozsahu 0 až 65 535.

### <a name="heap-reserve-size"></a>Velikost rezervace haldy

Určuje celkovou velikost alokace haldy ve virtuální paměti. Výchozí hodnota je 1 MB.    ([/Heap](heap-set-heap-size.md): Reserve)

### <a name="heap-commit-size"></a>Velikost potvrzení haldy

Určuje celkovou velikost paměti haldy ve fyzické paměti. Výchozí hodnota je 4 KB.    ([/Heap](heap-set-heap-size.md): Reserve, Commit)

### <a name="stack-reserve-size"></a>Velikost rezervace zásobníku

Určuje celkovou velikost alokačního zásobníku ve virtuální paměti. Výchozí hodnota je 1 MB.     ([/Stack](stack-stack-allocations.md): Reserve)

### <a name="stack-commit-size"></a>Velikost potvrzení zásobníku

Určuje celkovou velikost zásobníku přidělenou ve fyzické paměti. Výchozí hodnota je 4 KB.     ([/Stack](stack-stack-allocations.md): Reserve, Commit)

### <a name="enable-large-addresses"></a>Povolit velké adresy

Možnost [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md) instruuje linkeru, že aplikace může zpracovávat adresy větší než 2 gigabajty. Ve výchozím nastavení je/LARGEADDRESSAWARE: NO povolena, pokud/LARGEADDRESSAWARE není jinak zadáno na řádku linkeru.

### <a name="terminal-server"></a>Terminálový server

Možnost [/TSAWARE](tsaware-create-terminal-server-aware-application.md) nastaví příznak v poli IMAGE_OPTIONAL_HEADER DllCharacteristics v volitelné hlavičce obrázku programu. Pokud je tento příznak nastaven, terminálový server neprovede určité změny aplikace.

### <a name="swap-run-from-cd"></a>Prohodit běh z CD

Možnost [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) určuje, že operační systém nejprve zkopíruje výstup linkeru do odkládacího souboru a pak z něj spustí bitovou kopii. Toto je funkce systému Windows NT 4,0 (a novější). Když zadáte **CD** , operační systém zkopíruje image na vyměnitelném disku do stránkovacího souboru a načte ho.

### <a name="swap-run-from-network"></a>Prohození spouštění ze sítě

Možnost [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) určuje, že operační systém nejprve zkopíruje výstup linkeru do odkládacího souboru a pak z něj spustí bitovou kopii. Toto je funkce systému Windows NT 4,0 (a novější). Je-li zadán parametr **net** , bude operační systém nejprve kopírovat binární obrázek ze sítě do odkládacího souboru a načíst jej z něj. Tato možnost je užitečná pro spuštěné aplikace v síti.

### <a name="driver"></a>Faktorů

Pomocí možnosti linkeru [/Driver](driver-windows-nt-kernel-mode-driver.md) můžete vytvořit ovladač režimu jádra systému Windows NT.

**Vlastnit**

- Nenastaveno-výchozí nastavení ovladače.
- Ovladač **ovladače**
- **Pouze** /Driver: v linkeru způsobí, že LINKER přidá IMAGE_FILE_UP_SYSTEM_ONLY bit do vlastností ve výstupní hlavičce a určí, že se jedná o ovladač JEDNOPROCESOROVÉHO (up). Operační systém odmítne načíst ovladač do systému s více procesory (MP).
- **WDM** -/Driver: WDM způsobí, že LINKER nastaví použití parametru bit v poli DLLCHARACTERISTICS volitelného záhlaví.

## <a name="optimization-property-page"></a>Stránka vlastností optimalizace

### <a name="references"></a>Odkazy

[/Opt](opt-optimizations.md): ref eliminuje funkce nebo data, která nejsou nikdy odkazována v době, kdy/OPT: NOREF udržuje funkce nebo data, která nejsou nikdy odkazována. 

### <a name="enable-comdat-folding"></a>Povolit skládání sekvencí COMDAT

Pomocí [/opt](opt-optimizations.md): ICF\[= iterace] proveďte identické skládání COMDAT. 

### <a name="function-order"></a>Pořadí funkcí

Možnost [/Order](order-put-functions-in-order.md)určuje odkaz na optimalizaci programu tím, že na něj umístíte určité sekvence comdaty v předem určeném pořadí. ODKAZ umístí funkce v zadaném pořadí v rámci jednotlivých oddílů v imagi.

### <a name="profile-guided-database"></a>Databáze s průvodcem profilace

Zadejte soubor. pgd pro optimalizace na základě profilu. ([/PGD](pgd-specify-database-for-profile-guided-optimizations.md))

### <a name="link-time-code-generation"></a>Generování kódu při propojování

Určuje generování kódu při propojování. ([/LTCG](ltcg-link-time-code-generation.md))

**Vlastnit**

- **Výchozí** nastavení – výchozí LTCG
- **Použít rychlé generování kódu při propojování** – použijte generování kódu při propojování s [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md).
- **Použít generování kódu při propojování** – použijte [generování kódu při propojování](ltcg-link-time-code-generation.md).
- **Optimalizace na základě profilu – instrumentace** – použijte optimalizaci na základě [profilu](../profile-guided-optimizations.md) s:P ginstrument.
- **Optimalizace na základě profilu – optimalizace** – určuje, že linker má použít data profilu vytvořená po spuštění instrumentované binárního souboru k vytvoření optimalizované bitové kopie.
- **Optimalizace na základě profilu – aktualizace** – povolí a sleduje seznam vstupních souborů, které mají být přidány nebo změněny z toho, co bylo zadáno ve fázi:P ginstrument.

## <a name="embedded-idl-property-page"></a>Stránka vlastností vloženého IDL

### <a name="midl-commands"></a>Příkazy MIDL

Zadejte parametry příkazového řádku MIDL. ([/MIDL](midl-specify-midl-command-line-options.md):@responsefile)

### <a name="ignore-embedded-idl"></a>Ignorovat vložený IDL

Možnost [/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md) určuje, že žádné atributy IDL ve zdrojovém kódu by neměly být zpracovány do souboru. idl.

### <a name="merged-idl-base-file-name"></a>Název základního souboru sloučeného IDL

Možnost [/IDLOUT](idlout-name-midl-output-files.md) Určuje název a příponu souboru. idl.

### <a name="type-library"></a>Knihovna typů

Možnost [/TLBOUT](tlbout-name-dot-tlb-file.md) Určuje název a příponu souboru. tlb.

### <a name="typelib-resource-id"></a>ID prostředku TypeLib

Umožňuje zadat ID prostředku knihovny typů generované linkerem. ([/TLBID](tlbid-specify-resource-id-for-typelib.md): ID)

## <a name="windows-metadata-property-page"></a>Stránka vlastností metadat Windows

### <a name="generate-windows-metadata"></a>Generovat metadata Windows

Povolí nebo zakáže generování metadat Windows.

**Vlastnit**

- **Ano** – povolí generování souborů metadat Windows.
- **Ne** – zakáže generování souborů metadat Windows.

### <a name="windows-metadata-file"></a>Soubor metadat Windows

Přepínač možnosti [/WINMDFILE](winmdfile-specify-winmd-file.md)

### <a name="windows-metadata-key-file"></a>Soubor klíče metadat Windows

Zadejte klíč nebo dvojici klíčů k podepsání metadat systému Windows. ([/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md): filename)

### <a name="windows-metadata-key-container"></a>Kontejner klíčů metadat Windows

Zadejte kontejner klíčů pro podepsání metadat systému Windows. ([/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md): název)

### <a name="windows-metadata-delay-sign"></a>Znaménko zpoždění metadat systému Windows

Částečně podepisuje metadata Windows. [/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md) použijte, pokud chcete umístit pouze veřejný klíč do metadat Windows. Výchozí hodnota je/WINMDDELAYSIGN: NO.

## <a name="advanced-property-page"></a>Upřesnit stránku vlastností

### <a name="entry-point"></a>Vstupní bod

Možnost [/entry](entry-entry-point-symbol.md) Určuje funkci vstupního bodu jako počáteční adresu souboru exe nebo knihovny DLL.

### <a name="no-entry-point"></a>Žádný vstupní bod

Možnost [/NOENTRY](noentry-no-entry-point.md)je vyžadována pro vytvoření knihovny DLL, která je jen pro prostředky. Tuto možnost použijte, pokud nechcete, aby propojení propojuje odkaz na `_main` do knihovny DLL.

### <a name="set-checksum"></a>Nastavit kontrolní součet

Možnost [/release](release-set-the-checksum.md) nastavuje kontrolní součet v hlavičce souboru exe.

### <a name="base-address"></a>Základní adresa

Nastaví základní adresu programu. ([/Base](base-base-address.md): {Address\[; size] | @filename, klíč})

### <a name="randomized-base-address"></a>Náhodná základní adresa

Náhodná základní adresa. ([/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)\[: NO])

### <a name="fixed-base-address"></a>Pevná základní adresa

Vytvoří program, který se dá načíst jenom na upřednostňovanou základní adresu. ([/FIXED](fixed-fixed-base-address.md)\[: NO])

### <a name="data-execution-prevention-dep"></a>Zabránění spuštění dat (DEP)

Označí spustitelný soubor jako testovaný, aby byl kompatibilní s funkcí Zabránění spuštění dat systému Windows. ([/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)\[: NO])

### <a name="turn-off-assembly-generation"></a>Vypnout generování sestavení

Možnost [/NOASSEMBLY](noassembly-create-a-msil-module.md) dá linkeru pokyn, aby vytvořil obrázek pro aktuální výstupní soubor bez sestavení .NET Framework.

### <a name="unload-delay-loaded-dll"></a>Uvolnit odložené načtení knihovny DLL

Kvalifikátor **Unload** oznamuje funkci opožděného načítání, aby podporovala explicitní uvolnění knihovny DLL. ([/DELAY](delay-delay-load-import-settings.md): UNLOAD)

### <a name="nobind-delay-loaded-dll"></a>Knihovna DLL pro odložené načtení zpoždění vazby

Kvalifikátor **IAT** přikáže linkeru, aby NEzahrnoval s možností vazby v konečné imagi. Výchozím nastavením je vytvoření IAT s možností vazby pro odložené načítání knihoven DLL. ([/DELAY](delay-delay-load-import-settings.md): NENÍ VÁZÁNO)

### <a name="import-library"></a>Importovat knihovnu

Přepíše výchozí název knihovny importu. ([/IMPLIB](implib-name-import-library.md): filename)

### <a name="merge-sections"></a>Sloučit oddíly

Parametr [/Merge](merge-combine-sections.md) kombinuje první oddíl (od) s druhou sekcí (do) a pojmenuje výsledný oddíl na. Například/Merge:. rdata =. text.

### <a name="target-machine"></a>Cílový počítač

Možnost [/Machine](machine-specify-target-platform.md) určuje cílovou platformu pro program.

**Vlastnit**

- **Nenastaveno**
- **MachineARM**
- **Počítač arm64**
- **MachineEBC**
- **MachineIA64**
- **MachineMIPS**
- **MachineMIPS16**
- **MachineMIPSFPU**
- **MachineMIPSFPU16**
- **MachineSH4**
- **MachineTHUMB**
- **MachineX64**
- **MachineX86**

### <a name="profile"></a>Profil

Vytvoří výstupní soubor, který se dá použít s profilerem Performance Tools. Vyžaduje nastavení GenerateDebugInformation (/[/Debug](debug-generate-debug-info.md)). ([/PROFILE](profile-performance-tools-profiler.md))

### <a name="clr-thread-attribute"></a>Atribut vlákna CLR

Explicitně zadejte atribut pro dělení na vlákna pro vstupní bod programu CLR.

**Vlastnit**

- **Atribut vlákna MTA** – aplikuje atribut MTAThreadAttribute na vstupní bod programu.
- **Atribut vláken sta** – aplikuje atribut STAThreadAttribute na vstupní bod programu.
- **Výchozí atribut vlákna** je stejný jako nespecifikuje [/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md). Umožňuje, aby modul CLR (Common Language Runtime) nastavil výchozí atribut pro dělení na vlákna.

### <a name="clr-image-type"></a>Typ bitové kopie CLR

Nastaví typ (IJW, Pure nebo Safe) image CLR.

**Vlastnit**

- **Vynutit bitovou kopii IJW**
- **Vynutit čistou bitovou kopii IL**
- **Vynutit bezpečnou bitovou kopii IL**
- **Výchozí typ obrázku**

### <a name="key-file"></a>Soubor klíče

Zadejte klíč nebo dvojici klíčů pro podepsání sestavení. ([/Keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md): filename)

### <a name="key-container"></a>Kontejner klíčů

Zadejte kontejner klíčů pro podepsání sestavení. ([/Keycontainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md): název)

### <a name="delay-sign"></a>Odložit podpis

Částečně podepíše sestavení. Použijte [/delaysign](delaysign-partially-sign-an-assembly.md) , pokud chcete umístit pouze veřejný klíč do sestavení. Výchozí hodnota je/DELAYSIGN: NO.

### <a name="clr-unmanaged-code-check"></a>Kontrolu nespravovaného kódu CLR

[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md) určuje, zda bude linker použít SuppressUnmanagedCodeSecurityAttribute na volání PInvoke generovaná linkerem ze spravovaného kódu do nativních knihoven DLL.

### <a name="error-reporting"></a>Hlášení chyb

Umožňuje poskytnout informace o vnitřní chybě kompilátoru (ICE) přímo vizuálu C++ týmu.

**Vlastnit**

- **Vyzvat okamžitě** -Prompt hned.
- **Zařadit do fronty pro** další přihlášení – fronta pro další přihlášení
- **Odeslat zprávu o chybách** – odeslat zprávu o chybách
- **Žádná zpráva o chybách** – žádná zpráva o chybách.

### <a name="sectionalignment"></a>Zarovnání oddílu

Možnost [/align](align-section-alignment.md) určuje zarovnání jednotlivých oddílů v rámci lineárního adresního prostoru programu. Argument Number je v bajtech a musí být mocninou dvou.

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>Zachovat kód poslední chyby pro volání PInvoke

[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md), který je ve výchozím nastavení zapnutý, zachovává poslední chybový kód funkcí volaných pomocí mechanismu volání nespravovaného kódu, který umožňuje volat nativní funkce v knihovnách DLL z kódu kompilovaného pomocí parametrem/CLR.

**Vlastnit**

- **Povoleno** – povolit CLRSupportLastError.
- **Disabled** – zakáže CLRSupportLastError.
- **Jenom systémové knihovny DLL** – povolte CLRSupportLastError jenom pro systémové knihovny DLL.

### <a name="image-has-safe-exception-handlers"></a>Image má bezpečné obslužné rutiny výjimek

Když je zadán parametr [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) , linker vytvoří pouze obrázek, pokud může také vytvořit tabulku bezpečných obslužných rutin výjimek pro obrázek. Tato tabulka určuje, které obslužné rutiny výjimek jsou v operačním systému pro bitovou kopii platné.
