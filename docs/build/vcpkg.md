---
title: vcpkg – Správce balíčků jazyka C++ A součásti pro Windows, Linux a MacOS
description: vcpkg je Správce balíčků příkazového řádku, který výrazně zjednodušuje pořízení a instalaci všech knihoven C++ open source na Windows.
author: mikeblome
ms.author: mblome
ms.date: 03/18/2019
ms.technology: cpp-ide
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.openlocfilehash: 2ca1b88f492d96f8a08d296cab7f35f3b72409c9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786663"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg: Správce balíčků jazyka C++ pro Windows, Linux a MacOS

vcpkg je Správce balíčků příkazového řádku, který výrazně zjednodušuje pořízení a instalaci knihovny třetích stran ve Windows, Linuxu a MacOS. Pokud váš projekt používá knihovny třetích stran, doporučujeme použít vcpkg jejich instalaci. vcpkg podporuje proprietární i open source knihoven. Všechny knihovny v katalogu Windows vcpkg byly testovány z hlediska kompatibility s Visual Studio 2015 a Visual Studio 2017. Od května 2018 se více než 900 knihovny v katalogu Windows a přes 350 v katalogu systému Linux nebo MacOS. Komunitou C++ přidává další knihovny se obě katalogů průběžně.

## <a name="simple-yet-flexible"></a>Jednoduché a přitom flexibilní

Pomocí jediného příkazu můžete stáhnout zdrojů a vytvoří knihovnu. vcpkg samotného je opensourcový projekt, k dispozici na Githubu. Můžete přizpůsobit, vašeho privátního clone(s) žádným způsobem, který vám vyhovuje. Můžete například zadat různé knihovny nebo různé verze knihoven, než jaké jsou součástí veřejného katalogu. Na jednom počítači může mít více klonech vcpkg, každý z nich vytváření vlastních sad knihovny a/nebo kompilaci přepínače atd. Každou duplicitu je samostatná prostředí s vlastní kopii vcpkg.exe, která funguje pouze na své vlastní hierarchie. vcpkg není přidán do proměnných prostředí a nemá žádné závislosti na registru Windows nebo Visual Studio.

## <a name="sources-not-binaries"></a>Zdroje není binární soubory

Pro knihovny v katalogu Windows stáhne vcpkg zdroje místo binární soubory [1]. Kompiluje tyto zdroje pomocí sady Visual Studio 2017 nebo Visual Studio 2015, pokud není nainstalované 2017. V jazyce C++ je velmi důležité, všech knihoven, které používáte dodržování stejnému kompilátoru a verze kompilátoru, jak aplikace kód, který odkazuje na ni. Pomocí vcpkg eliminovat nebo alespoň výrazně snížit riziko neodpovídající binární soubory a může způsobit problémy. V týmech, které jsou standardizované pro konkrétní verzi kompilátoru můžete použít jeden člen seskupení vcpkg ke stažení zdrojů a zkompilujte sadu binární soubory a pak použijte příkaz export se komprimovat binární soubory a záhlaví pro ostatní členy týmu. Další informace najdete v tématu [Export kompilaci binárních souborů a záhlaví](#export_binaries_per_project) níže.

Pokud jste vytvořili klon vcpkg privátní knihovny v kolekci porty, můžete přidat port, který stáhne předem připravených binární soubory a záhlaví a zápis do souboru portfile.cmake, který jednoduše zkopíruje soubory do požadovaného umístění.

[1] *Poznámka: některé knihovny proprietární zdroje nejsou k dispozici. Vcpkg stáhne kompatibilní předem připravených binárních souborů v těchto případech.*

## <a name="installation"></a>Instalace

Naklonujte úložiště vcpkg z Githubu: [ https://github.com/Microsoft/vcpkg ](https://github.com/Microsoft/vcpkg). Můžete stáhnout do jakéhokoli umístění složky, kterému dáváte přednost.

Zaváděcí nástroj spusťte v kořenové složce:

- **bootstrap-vcpkg.bat** (Windows)
- **./bootstrap-vcpkg.sh** (Linux, MacOS)

## <a name="search-the-list-of-available-libraries"></a>Prohledejte seznam dostupných knihoven

Chcete-li zobrazit balíčky, které jsou k dispozici, zadejte na příkazovém řádku: **vcpkg vyhledávání**

Tento příkaz zobrazí ovládací prvek soubory v podsložkách vcpkg/porty. Zobrazí se seznam takto:

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

Můžete filtrovat podle vzoru, například **vcpkg hledání ta**:

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-local-machine"></a>Nainstalovat knihovnu na místním počítači

Po získání názvu knihovny pomocí **vcpkg hledání**, použijete **vcpkg nainstalovat** stažení knihovny a jeho kompilace. vcpkg používá portfile knihovny v adresáři porty. Pokud není zadána žádná trojici, vcpkg nainstaluje a kompilace pro výchozí trojici pro cílovou platformu: x86 windows, x64 linux.cmake nebo x64 osx.cmake.

Pro Linuxové knihovny vcpkg závisí na gcc instaluje na místním počítači. V systému MacOS používá vcpkg Clang.

Pokud portfile Určuje závislosti, vcpkg stáhne a nainstaluje ty také. Po stažení si vcpkg sestavení knihovny pomocí cokoli, co sestavovací systém, který používá knihovnu. CMake a (Windows) projekty MSBuild jsou upřednostňované, ale UJISTĚTE se podporuje spolu s jakýmkoliv systémem sestavení. Pokud vcpkg nemůže najít zadaný sestavovací systém v místním počítači, stáhne a nainstaluje ho.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

Pro projekty CMAKE, využívat k zpřístupňování knihovny s CMAKE_TOOLCHAIN_FILE `find_package()`. Příklad:

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake (Linux/MacOS)
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake (Windows)
```

## <a name="list-the-libraries-already-installed"></a>Seznam knihoven už nainstalovaný

Po instalaci některé knihovny, můžete použít **vcpkg seznamu** abyste zjistili, co jsou:

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

### <a name="per-user"></a>Za uživatele

Spustit **vcpkg integrovat instalace** konfigurovat Visual Studio k vyhledání všech vcpkg hlavičkové soubory a binární soubory na základě jednotlivých uživatelů bez nutnosti ručních úprav cesty adresáře VC ++. Pokud máte více klonech klonu, ze které spouštíte tento příkaz změní výchozí umístění.

Nyní můžete #include záhlaví jednoduše tak, že zadáte složky nebo hlaviček a automatické dokončování vám pomůže. Žádné další kroky jsou požadovány pro odkazování na knihovny nebo přidávání odkazů na projekty. Následující obrázek znázorňuje, jak sada Visual Studio najde azure-storage-cpp záhlaví. vcpkg umístí jeho záhlaví v **/ nainstalované** podsložku, rozdělené podle cílové platformy. Následující diagram znázorňuje seznam vložených souborů v **/ was** podsložce knihovny:

![vcpkg integrace technologie IntelliSense](media/vcpkg-intellisense.png "vcpkg a technologie IntelliSense")

### <a name="per-project"></a>Na projekt

Pokud budete muset použít konkrétní verzi knihovny, která se liší od verze v instanci active vcpkg, postupujte podle těchto kroků:

1. Vytvořit nový klon vcpkg
1. Upravit portfile knihovny, která se získat verzi, které potřebujete
1. Spustit **vcpkg nainstalovat \<knihovny >**.
1. Použití **vcpkg integrovat projekt** k vytvoření balíčku NuGet, který odkazuje na tuto knihovnu na základě jednotlivých projektů.

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>Integrace s Visual Studio Code (Linux/MacOS)

Spustit **vcpkg integrovat instalace** ke konfiguraci Visual Studio Code v systému Linux nebo MacOS s umístěním vcpkg enlistement a povolení funkce IntelliSense ve zdrojových souborech.

## <a name="target-linux-from-windows-via-wsl"></a>Cíl Linux z Windows prostřednictvím WSL

Linux binární soubory z počítače s Windows můžete vytvářet pomocí subsystém Windows pro Linux (WSL). Postupujte podle pokynů a [nastavení WSL ve Windows 10](/windows/wsl/install-win10)a nakonfigurujte ho [rozšíření sady Visual Studio pro Linux](https://blogs.msdn.microsoft.com/vcblog/2017/02/08/targeting-windows-subsystem-for-linux-from-visual-studio/). Můžete vložit všechny sestavené knihovny pro Windows i Linuxem do stejné složky a k němu přístup z Windows a WSL.

## <a name="export_binaries_per_project"></a> Export kompilované binární soubory a hlavičky

Vyžadování všichni členové týmu ke stažení a sestavení knihovny může být neefektivní. Můžete provést tuto práci členovi týmu a potom pomocí **vcpkg export** vytvořit soubor zip se binární soubory a záhlaví nebo balíčku NuGet (různé formátování k dispozici), které můžete snadno sdílet s ostatními členy týmu.

## <a name="updateupgrade-installed-libraries"></a>Aktualizovat nebo upgradovat, které jsou nainstalované knihovny

Veřejné katalogu je pořád aktuální pomocí nejnovější verze knihoven. Chcete-li zjistit, které místní knihovny jsou zastaralé, použijte **vcpkg aktualizace**. Až budete připravení aktualizace kolekce portů na nejnovější verzi z veřejného katalogu, spusťte **vcpkg upgrade** příkaz, který automaticky stáhnout a znovu sestavte některých nebo všech nainstalovaných knihoven, které jsou zastaralé.

Ve výchozím nastavení **upgradovat** příkaz vypíše pouze knihoven, které jsou zastaralé; není upgraduje je. Chcete-li provést upgrade, použijte **--no test** možnost.

```cmd
  vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>Možnosti upgradu

- **--no test** provést upgrade, pokud není zadán, příkaz vypíše pouze zastaralé balíčky.
- **--zachovat probíhající** pokračovat v instalaci balíčků i v případě, že jeden server selže.
- **--trojici \<t >** nastavit výchozí trojici nekvalifikované balíčků.
- **--vcpkg kořenové \<cesta >** zadejte vcpkg adresář, který chcete použít místo aktuální adresář nebo adresář nástrojů.

### <a name="upgrade-example"></a>Příklad upgradu

Následující příklad ukazuje, jak upgradovat jenom zadané knihovny. Všimněte si, že tento vcpgk automaticky si vyžádá závislostí podle potřeby.

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

## <a name="contribute-new-libraries"></a>Přispívat nové knihovny

Můžete zahrnout všechny knihovny, který rádi používáte ve vaší kolekci privátních portů. Chcete-li navrhnout novou knihovnu pro veřejné katalog, otevřete problém na [stránce problém Githubu vcpkg](https://github.com/Microsoft/vcpkg/issues).

## <a name="remove-a-library"></a>Odebrání knihovny

Typ **odebrat vcpkg** odebrání knihovny nainstalované. Pokud jsou na ní závislé další knihovny, zobrazí se výzva k příkaz s **--recurse**, což způsobí, že všechny podřízené knihovny odebrat.

## <a name="customize-vcpkg"></a>Přizpůsobení vcpkg

Váš klonovací vcpkg žádným způsobem, který rádi používáte, můžete upravit. Můžete vytvořit více klonech vcpkg a upravit portfiles v každém z nich k získání konkrétní verze knihovny nebo zadat parametry příkazového řádku. Například v podniku, jedna skupina vývojářů může fungovat na software, který má jednu sadu závislostí a jiná skupina může mít jinou sadu. Můžete nastavit dvěma klony vcpkg a upravit každé z nich do verze knihoven a kompilaci přepínače a další, si můžete stáhnout podle vašich potřeb.

## <a name="uninstall-vcpkg"></a>Odinstalujte vcpkg

Odstraňte adresář.

## <a name="send-feedback-about-vcpkg"></a>Odeslat zpětnou vazbu o vcpkg

Použití **vcpkg kontakt – zjišťování** příkaz odeslat zpětnou vazbu společnosti Microsoft o vcpkg, včetně zpráv o chybách a návrhy na funkce.

## <a name="the-vcpkg-folder-hierarchy"></a>Vcpkg hierarchii složek

Všechna data a funkce vcpkg je samostatný v hierarchii, jeden adresář, nazývá "instance". Neexistují žádné nastavení registru nebo proměnné prostředí. Na počítači můžete mít libovolný počet instancí vcpkg a že není konfliktu mezi sebou.

Obsah instance vcpkg jsou:

- buildtrees – obsahuje podsložky zdrojů, ze kterých je postavená každou knihovnu
- dokumentace – dokumentaci a příklady
- soubory ke stažení – kopie v mezipaměti všechny stažené nástroje nebo zdroje. vcpkg prohledá tady nejprve při spuštění příkazu instalace.
- nainstalovat – obsahuje hlavičkové soubory a binární soubory pro každou nainstalovanou knihovnu. Při integraci s Visual Studio, které jsou v podstatě tím rozdílem, že tuto složku přidat do cesty pro hledání.
- balíčky--vnitřní složky pro pracovní mezi nainstaluje.
- porty – soubory, které popisují každou knihovnu v katalogu, jeho verze a kde ho můžete stáhnout. V případě potřeby můžete přidat vlastní porty.
- skripty – skripty (cmake, prostředí powershell) používá vcpkg.
- toolsrc – zdrojový kód C++ vcpkg a související součásti
- trojice – obsahuje nastavení pro jednotlivé podporované cílové platformy (například x86 windows nebo x64 UPW).

## <a name="command-line-reference"></a>Referenční dokumentace k příkazovému řádku

|Příkaz|Popis|
|---------|---------|
|**vcpkg hledání [cesta]**|Vyhledat balíčky, které jsou k dispozici pro instalaci|
|**vcpkg nainstalovat \<pkg >...**|Instalace balíčku|
|**vcpkg remove \<pkg>...**|Odinstalovat balíček|
|**odebrat vcpkg – zastaralé**|Odinstalujte všechny zastaralé balíčky|
|**vcpkg list**|Výpis nainstalovaných balíčků|
|**vcpkg update**|Zobrazit seznam balíčků pro aktualizaci|
|**vcpkg upgradu**|Znovu sestavit všechny zastaralé balíčky|
|**Hodnota hash vcpkg \<soubor > [alg]**|Konkrétní algoritmem hash souboru, výchozí SHA512|
|**vcpkg integrovat instalace**|Zkontrolujte nainstalované balíčky k dispozici uživatelské úrovni. Vyžaduje oprávnění správce při prvním použití|
|**vcpkg integrovat odebrat**|Odebrat uživatele celou integraci|
|**vcpkg integrovat projekt**|Generování referenčního balíčku NuGet pro individuální použití projektu VS|
|**vcpkg export \<pkg >... [optimalizované]...**|Exportovat balíček|
|**vcpkg edit \<pkg>**|Otevřete port pro úpravy (použití EDITORU %, výchozí "kód")|
|**Vytvoření vcpkg \<pkg > \<url > [archivename]**|Vytvoření nového balíčku|
|**vcpkg cache**|Seznam s mezipamětí zkompilován balíčky|
|**vcpkg verze**|Zobrazit informace o verzi|
|**vcpkg kontakt – průzkum**|Zobrazení informací o váš názor.|

### <a name="options"></a>Možnosti

|Možnost|Popis|
|---------|---------|
|**--trojici \<t >**|Zadejte trojici cílové architektury. (výchozí: `%VCPKG_DEFAULT_TRIPLET%`, viz také **vcpkg nápovědy trojici**)|
|**--vcpkg-root \<path>**|Zadat kořenový adresář vcpkg (výchozí: `%VCPKG_ROOT%`)|
