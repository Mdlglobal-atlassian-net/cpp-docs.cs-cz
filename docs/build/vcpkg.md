---
title: 'vcpkg: správce C++ balíčků pro Windows, Linux a MacOS'
description: vcpkg je správce balíčků příkazového řádku, který významně zjednodušuje získávání a instalaci open-source C++ knihoven ve Windows, MacOS a Linux.
ms.date: 01/10/2020
ms.technology: cpp-ide
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.openlocfilehash: 7c3dddd62a66c746d92d2f931b97e354ee27d75f
ms.sourcegitcommit: ba129dc55dc3ff638f3af5ac0e87ec2ca1cb2674
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75869710"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg: správce C++ balíčků pro Windows, Linux a MacOS

vcpkg je správce balíčků příkazového řádku pro C++. Značně zjednodušuje získávání a instalaci knihoven třetích stran v systémech Windows, Linux a MacOS. Pokud váš projekt používá knihovny třetích stran, doporučujeme je nainstalovat pomocí vcpkg. vcpkg podporuje Open Source i proprietární knihovny. Všechny knihovny v katalogu Windows vcpkg byly testovány kvůli kompatibilitě se sadou Visual Studio 2015, Visual Studio 2017 a Visual Studio 2019. Vcpkg teď mezi katalogy Windows a Linux/MacOS podporuje víc než 1900 knihoven. C++ Komunita průběžně přidávají do obou katalogů další knihovny.

## <a name="simple-yet-flexible"></a>Jednoduché, zatím flexibilní

Jediným příkazem můžete stáhnout zdroje a vytvořit knihovnu. vcpkg je open source projekt, který je k dispozici na GitHubu. Vaše soukromé vcpkg klony je možné přizpůsobit jakýmkoli způsobem. Například zadejte různé knihovny nebo různé verze knihoven, než jaké jsou nalezeny ve veřejném katalogu. V jednom počítači můžete mít více klonů vcpkg. Každá z nich může být nastavena na vytvoření vlastní kolekce knihoven s upřednostňovanými přepínači kompilace. Každý klon je samostatné prostředí s vlastní kopií programu vcpkg. exe, která funguje pouze ve své vlastní hierarchii. vcpkg není přidán k žádným proměnným prostředí a nemá žádnou závislost na registru Windows nebo v aplikaci Visual Studio.

## <a name="sources-not-binaries"></a>Zdroje, nikoli binární soubory

V případě knihoven v katalogu Windows vcpkg stáhne zdroje místo binárních souborů<sup>1</sup>. Zkompiluje tyto zdroje pomocí nejnovější verze sady Visual Studio, kterou může najít. V C++nástroji je důležité, aby byl kód aplikace i všechny knihovny, které používáte, kompilovány stejným kompilátorem a verzí kompilátoru. Pomocí vcpkg Eliminujte nebo alespoň významně snížíte riziko neodpovídajících binárních souborů a problémy, které mohou způsobovat. V týmech, které jsou standardizovány na konkrétní verzi kompilátoru, může jeden člen týmu použít vcpkg ke stažení zdrojů a zkompilování sady binárních souborů. Pak mohou pomocí příkazu Exportovat zazálohovat binární soubory a hlavičky pro ostatní členy týmu. Další informace najdete v tématu [Export kompilovaných binárních souborů a hlaviček](#export_binaries_per_project) níže.

Můžete také vytvořit klon vcpkg, který má v kolekci portů soukromé knihovny. Přidejte port, který stáhne předem připravené binární soubory a hlavičky. Pak napíšete soubor Portfile. CMAK, který jednoduše zkopíruje tyto soubory do upřednostňovaného umístění.

<sup>1</sup> *Poznámka: zdroje nejsou pro některé proprietární knihovny k dispozici. V těchto případech vcpkg stáhne kompatibilní předem připravené binární soubory.*

## <a name="installation"></a>Instalace služby

Naklonujte úložiště vcpkg z GitHubu: [https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg). Můžete si stáhnout do libovolného umístění složky, které dáváte přednost.

Spusťte zaváděcí nástroj v kořenové složce:

- **bootstrap-vcpkg.bat** (Windows)
- **./bootstrap-vcpkg.sh** (Linux, MacOS)

## <a name="search-the-list-of-available-libraries"></a>Hledat v seznamu dostupných knihoven

Pokud chcete zjistit, jaké balíčky jsou k dispozici, zadejte na příkazovém řádku: **vcpkg Search** .

Tento příkaz vytvoří výčet řídicích souborů v podsložkách vcpkg/ports. Zobrazí se seznam podobný tomuto:

```cmd
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. \<https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

Můžete filtrovat podle vzoru, například **vcpkg Search**:

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-local-machine"></a>Instalace knihovny na místním počítači

Po získání názvu knihovny pomocí **vyhledávání vcpkg**použijte **instalaci vcpkg** ke stažení knihovny a její kompilaci. vcpkg používá Portfile knihovny v adresáři portů. Pokud není zadaný žádný s trojicí, vcpkg se nainstaluje a zkompiluje pro výchozí s trojicí pro cílovou platformu: x86-Windows, x64-Linux. cmake nebo x64-OSX. cmake.

Pro knihovny Linux vcpkg závisí na instalaci RSZ na místním počítači. V MacOS používá vcpkg Clang.

Pokud Portfile určuje závislosti, vcpkg ho stáhne a nainstaluje. Po stažení vcpkg vytvoří knihovnu pomocí stejného systému sestavení, který knihovna používá. Projekty nástroje MSBuild pro CMake a (v systému Windows) jsou upřednostňovány, ale podporují se spolu s jakýmkoli jiným systémem sestavení. Pokud vcpkg nemůže najít zadaný systém sestavení v místním počítači, stáhne a nainstaluje ho.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

V případě projektů CMAKe použijte CMAKE_TOOLCHAIN_FILE k zpřístupnění knihoven s `find_package()`. Příklad:

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake (Linux/MacOS)
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake (Windows)
```

## <a name="list-the-libraries-already-installed"></a>Vypíše knihovny, které jsou už nainstalované.

Po instalaci některých knihoven můžete použít **seznam vcpkg** , abyste viděli, co máte:

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

## <a name="integrate-with-visual-studio-windows"></a>Integrace se sadou Visual Studio (Windows)

### <a name="per-user"></a>Podle uživatele

Spusťte **integraci vcpkg Integration** pro konfiguraci sady Visual Studio tak, aby vyhledala všechny soubory hlaviček vcpkg a binární soubory na jednotlivých uživatelích. Není potřeba provádět ruční úpravy cest k adresářům VC + +. Pokud máte více klonů, klon, ze kterého spouštíte tento příkaz, se stal novým výchozím umístěním.

Nyní můžete #include záhlaví jednoduše zadáním složky nebo záhlaví a automatické dokončování vám pomůže. Pro propojení s knihovny nebo přidávání odkazů na projekt nejsou vyžadovány žádné další kroky. Následující ilustrace znázorňuje, jak Visual Studio nalezne hlavičky Azure-Storage-cpp. vcpkg umístí své hlavičky do podsložky **/Installed** , která je rozdělená na cílovou platformu. Následující diagram zobrazuje seznam vložených souborů v podsložce **/was** knihovny:

![vcpkg a IntelliSense](media/vcpkg-intellisense.png "vcpkg a IntelliSense")

### <a name="per-project"></a>Na projekt

Pokud potřebujete použít konkrétní verzi knihovny, která se liší od verze v aktivní instanci vcpkg, postupujte takto:

1. Vytvoření nového klonu pro vcpkg
1. Upravte Portfile pro knihovnu, abyste získali potřebnou verzi.
1. Spusťte **\<> knihovny pro instalaci vcpkg**.
1. Použijte **vcpkg Integration Project** k vytvoření balíčku NuGet, který odkazuje na tuto knihovnu na základě jednotlivých projektů.

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>Integrace s Visual Studio Code (Linux/MacOS)

Spusťte **vcpkg Integration Install** a nakonfigurujte Visual Studio Code v systému Linux/MacOS. Tento příkaz nastaví umístění zařazení vcpkg a povolí technologii IntelliSense ve zdrojových souborech.

## <a name="target-linux-from-windows-via-wsl"></a>Cílová platforma Linux od Windows přes WSL

Binární soubory pro Linux můžete vytvořit na počítači s Windows pomocí subsystému Windows pro Linux nebo WSL. Podle pokynů [nastavte WSL ve Windows 10](/windows/wsl/install-win10)a nakonfigurujte ji pomocí [rozšíření sady Visual Studio pro Linux](https://blogs.msdn.microsoft.com/vcblog/2017/02/08/targeting-windows-subsystem-for-linux-from-visual-studio/). Všechny vaše sestavené knihovny pro Windows a Linux je možné vložit do stejné složky. Jsou přístupné z Windows i WSL.

## <a name="export_binaries_per_project"></a>Exportovat zkompilované binární soubory a hlavičky

Je neefektivní zajistit, aby všichni členové týmu stáhli a vytvořili společné knihovny. Jeden člen týmu může použít příkaz **vcpkg export** k vytvoření společného souboru ZIP binárních souborů a hlaviček nebo balíčku NuGet. Pak je můžete snadno sdílet s ostatními členy týmu.

## <a name="updateupgrade-installed-libraries"></a>Aktualizace a upgrade nainstalovaných knihoven

Veřejný katalog je udržován v aktuálním stavu pomocí nejnovějších verzí knihoven. Pokud chcete zjistit, které z místních knihoven jsou zastaralé, použijte **vcpkg Update**. Až budete připraveni aktualizovat kolekci portů na nejnovější verzi veřejného katalogu, spusťte příkaz **vcpkg upgrade** . Automaticky stáhne a znovu sestaví všechny nainstalované knihovny, které nejsou aktuální.

Ve výchozím nastavení příkaz pro **upgrade** obsahuje jenom knihovny, které jsou zastaralé; neupgraduje je. Chcete-li skutečně upgradovat knihovny, použijte možnost **--No-suchého běhu** .

```cmd
  vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>Možnosti upgradu

- **--No-suchý-běh**  Proveďte upgrade. Pokud není zadán, příkaz zobrazí pouze zastaralé balíčky.
- **--zachování**  Pokračovat v instalaci balíčků i v případě, že jedna dojde k chybě
- **--s trojicí \<t >**  Nastavte výchozí s trojicí pro nekvalifikované balíčky.
- **--vcpkg-root \<cesta >**  Zadejte adresář vcpkg, který se má použít místo aktuálního adresáře nebo nástroje.

### <a name="upgrade-example"></a>Příklad upgradu

Následující příklad ukazuje, jak upgradovat pouze zadané knihovny. vcpkg v případě potřeby automaticky vyžádá závislosti.

```cmd
c:\users\satyan\vcpkg> vcpkg upgrade tiny-dnn:x86-windows zlib
The following packages are up-to-date:
   tiny-dnn:x86-windows

The following packages will be rebuilt:
    * libpng[core]:x86-windows
    * tiff[core]:x86-windows
      zlib[core]:x86-windows
Additional packages (*) will be modified to complete this operation.
If you are sure you want to rebuild the above packages, run this command with the --no-dry-run option.
```

## <a name="contribute-new-libraries"></a>Přispět k novým knihovnám

Do kolekce privátních portů můžete zahrnout všechny knihovny, které chcete. Pokud chcete navrhnout novou knihovnu pro veřejný katalog, otevřete problém na [stránce problém Vcpkg GitHubu](https://github.com/Microsoft/vcpkg/issues).

## <a name="remove-a-library"></a>Odebrání knihovny

Pro odebrání nainstalované knihovny zadejte **vcpkg Remove** . Pokud na něm závisí jiné knihovny, budete vyzváni k opětovnému spuštění příkazu pomocí příkazu **--rekurze**, který způsobí odebrání všech podřízených knihoven.

## <a name="customize-vcpkg"></a>Přizpůsobení vcpkg

Klonování vcpkg můžete upravit jakýmkoli způsobem. Můžete dokonce vytvořit několik klonů vcpkg a pak upravit portfiles v každém z nich. To je jednoduchý způsob, jak získat konkrétní verze knihoven, nebo zadat konkrétní parametry příkazového řádku. Například v podniku mohou jednotlivé skupiny vývojářů fungovat na softwaru, který má sadu závislostí specifickou pro skupinu. Řešením je nastavit klon vcpkg pro každý tým. Pak upravte duplicity a Stáhněte si verze knihovny a nastavte přepínače kompilace, které každý tým potřebuje.

## <a name="uninstall-vcpkg"></a>Odinstalace vcpkg

Stačí odstranit adresář vcpkg. Když se tento adresář odstraní, odinstaluje se distribuce vcpkg a všechny knihovny, které vcpkg nainstaloval.

## <a name="send-feedback-about-vcpkg"></a>Poslat názor na vcpkg

Pomocí příkazu **vcpkg Contact--Survey** můžete odeslat zpětnou vazbu Microsoftu o vcpkg, včetně sestav chyb a návrhů pro funkce.

## <a name="the-vcpkg-folder-hierarchy"></a>Hierarchie složky vcpkg

Všechny funkce a data vcpkg jsou samostatně obsaženy v jedné hierarchii adresáře, která se nazývá "instance". Neexistují žádná nastavení registru ani proměnné prostředí. V počítači můžete mít libovolný počet instancí vcpkg a nedojde k jejich vzájemnému narušování.

Obsah instance vcpkg je:

- buildtrees – obsahuje podsložky zdrojů, ze kterých je každá knihovna sestavena.
- dokumentace a příklady
- soubory ke stažení – kopie všech stažených nástrojů nebo zdrojů uložených v mezipaměti. vcpkg vyhledá nejprve při spuštění instalačního příkazu.
- nainstalováno – obsahuje hlavičky a binární soubory pro každou nainstalovanou knihovnu. Když provádíte integraci se sadou Visual Studio, budete v podstatě sdělit, že tuto složku přidá do svých vyhledávacích cest.
- balíčky – interní složka pro přípravu mezi instalacemi.
- porty – soubory, které popisují každou knihovnu v katalogu, její verzi a kde se mají stáhnout. V případě potřeby můžete přidat vlastní porty.
- skripty – skripty (cmake, PowerShell) používané v vcpkg.
- toolsrc – C++ zdrojový kód pro vcpkg a související součásti
- Triplets – obsahuje nastavení pro každou podporovanou cílovou platformu (například x86-Windows nebo x64 – UWP).

## <a name="command-line-reference"></a>Referenční dokumentace k příkazovému řádku

|Příkaz|Popis|
|---------|---------|
|**vcpkg Search \[Pat]**|Vyhledat balíčky dostupné k instalaci|
|**vcpkg \<pkg instalace >...**|Instalace balíčku|
|**vcpkg odebrat > \<pkg...**|Odinstalace balíčku|
|**vcpkg odebrat – zastaralé**|Odinstalace všech zastaralých balíčků|
|**seznam vcpkg**|Výpis nainstalovaných balíčků|
|**vcpkg aktualizace**|Zobrazit seznam balíčků pro aktualizaci|
|**upgrade vcpkg**|Znovu sestavit všechny zastaralé balíčky|
|**vcpkg hash \<soubor > \[ALG]**|Vyhodnotit soubor podle konkrétního algoritmu, výchozí SHA512|
|**vcpkg Integration Install**|Zpřístupněte nainstalované balíčky na úrovni uživatele. Při prvním použití vyžaduje oprávnění správce.|
|**vcpkg Integration Remove**|Odebrat integraci na úrovni uživatele|
|**vcpkg Integration Project**|Vygenerujte odkaz na balíček NuGet pro individuální použití projektu VS.|
|**vcpkg export \<pkg >... \[opt]...**|Export balíčku|
|**vcpkg edit \<pkg>**|Otevřete port pro úpravy (používá% EDITOR%, výchozí kód).|
|**vcpkg Create \<pkg > \<URL > \[Archive]**|Vytvořit nový balíček|
|**vcpkg cache**|Vypsat zkompilované balíčky v mezipaměti|
|**verze vcpkg**|Zobrazit informace o verzi|
|**vcpkg kontakt – průzkum**|Zobrazí kontaktní informace pro odeslání zpětné vazby.|

### <a name="options"></a>Možnosti

|Možnost|Popis|
|---------|---------|
|**--s trojicí \<t >**|Zadejte cílovou architekturu s trojicí. (výchozí: `%VCPKG_DEFAULT_TRIPLET%`, viz také **vcpkg Help s trojicí**)|
|**--vcpkg-root \<path>**|Zadejte kořenový adresář vcpkg (výchozí: `%VCPKG_ROOT%`).|
