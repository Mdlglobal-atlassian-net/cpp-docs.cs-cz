---
title: 'vcpkg: správce balíčků Jazyka C++ pro Windows, Linux a MacOS'
description: vcpkg je správce balíčků příkazového řádku, který výrazně zjednodušuje pořízení a instalaci open-source knihoven C++ v systémech Windows, MacOS a Linux.
ms.date: 01/10/2020
ms.technology: cpp-ide
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.openlocfilehash: 9dbeba1f55164ace01fb8bb26155dd9319ba62db
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335399"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg: správce balíčků Jazyka C++ pro Windows, Linux a MacOS

vcpkg je správce balíčků příkazového řádku pro C++. To značně zjednodušuje pořízení a instalaci knihoven třetích stran na Windows, Linux a MacOS. Pokud váš projekt používá knihovny třetích stran, doporučujeme použít vcpkg k jejich instalaci. vcpkg podporuje jak open-source, tak proprietární knihovny. Všechny knihovny v katalogu vcpkg systému Windows byly testovány na kompatibilitu s Visual Studio 2015, Visual Studio 2017 a Visual Studio 2019. Mezi katalogy Windows a Linux/MacOS nyní vcpkg podporuje více než 1900 knihoven. Komunita C++ průběžně přidává do obou katalogů další knihovny.

## <a name="simple-yet-flexible"></a>Jednoduché, ale flexibilní

Pomocí jediného příkazu můžete stáhnout zdroje a vytvořit knihovnu. vcpkg je sám o sobě open source projekt, který je k dispozici na GitHubu. Je možné přizpůsobit své soukromé vcpkg klony jakýmkoli způsobem se vám líbí. Zadejte například různé knihovny nebo jiné verze knihoven, než jaké se nacházejí ve veřejném katalogu. Můžete mít více klonů vcpkg na jednom počítači. Každý z nich může být nastaven a vytváří vlastní kolekci knihoven s upřednostňovanými přepínači kompilace. Každý klon je samostatné prostředí s vlastní kopií vcpkg.exe, která pracuje pouze na vlastní hierarchii. vcpkg není přidán do žádné proměnné prostředí a nemá žádnou závislost na registru systému Windows nebo Visual Studio.

## <a name="sources-not-binaries"></a>Zdroje, nikoli binární soubory

Pro knihovny v katalogu systému Windows stahuje vcpkg zdroje namísto binárních souborů<sup>1</sup>. Zkompiluje tyto zdroje pomocí nejnovější verze sady Visual Studio, které lze najít. V jazyce C++ je důležité, aby kód aplikace i všechny knihovny, které používáte, byly kompilovány stejným kompilátorem a verzí kompilátoru. Pomocí vcpkg eliminujete nebo alespoň výrazně snížíte potenciál pro neodpovídající binární soubory a problémy, které mohou způsobit. V týmech, které jsou standardizovány na konkrétní verzi kompilátoru, jeden člen týmu můžete použít vcpkg ke stažení zdrojů a kompilaci sadu binárních souborů. Potom mohou použít příkaz export u zip u binárních souborů a záhlaví pro ostatní členy týmu. Další informace naleznete v [tématu Export kompilovaných binárních souborů a záhlaví](#export_binaries_per_project) níže.

Můžete také vytvořit klon vcpkg, který má soukromé knihovny v kolekci portů. Přidejte port, který stáhne předem sestavené binární soubory a záhlaví. Potom napište soubor portfile.cmake, který tyto soubory jednoduše zkopíruje do upřednostňovaného umístění.

<sup>1</sup> *Poznámka: zdroje nejsou k dispozici pro některé proprietární knihovny. V těchto případech vcpkg stáhne kompatibilní předdefinované binární soubory.*

## <a name="installation"></a>Instalace

Klonovat úložiště vcpkg z GitHubu: [https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg). Můžete si stáhnout do libovolného umístění složky, které upřednostňujete.

Spusťte zaváděcí nástroj v kořenové složce:

- **bootstrap-vcpkg.bat** (Windows)
- **./bootstrap-vcpkg.sh** (Linux, MacOS)

## <a name="search-the-list-of-available-libraries"></a>Hledání v seznamu dostupných knihoven

Chcete-li zjistit, jaké balíčky jsou k dispozici, na příkazovém řádku: **vcpkg hledání**

Tento příkaz vytvoří výčet řídicích souborů v podsložkách vcpkg/ports. Zobrazí se výpis, jako je tento:

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

Můžete filtrovat na vzor, například **vcpkg vyhledávání ta**:

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-local-machine"></a>Instalace knihovny v místním počítači

Po získání názvu knihovny pomocí **vyhledávání vcpkg**použijete k stažení knihovny a kompilaci **použít instalaci vcpkg.** vcpkg používá portfile knihovny v adresáři portů. Pokud není zadán žádný trojčata, vcpkg nainstaluje a zkompiluje pro výchozí trojčata pro cílovou platformu: x86-windows, x64-linux.cmake nebo x64-osx.cmake.

U linuxových knihoven závisí vcpkg na gcc, které jsou instalovány v místním počítači. V MacOS používá vcpkg Clang.

Když portfile určuje závislosti, vcpkg stáhne a nainstaluje je také. Po stažení vytvoří vcpkg knihovnu pomocí stejného systému sestavení, který knihovna používá. CMake a (v systému Windows) MSBuild projekty jsou upřednostňovány, ale MAKE je podporována, spolu s jiným systémem sestavení. Pokud vcpkg nemůže najít zadaný systém sestavení v místním počítači, stáhne a nainstaluje jej.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

Pro projekty CMAKE použijte CMAKE_TOOLCHAIN_FILE zpřístupnit `find_package()`knihovny pomocí aplikace . Příklad:

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake (Linux/MacOS)
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake (Windows)
```

## <a name="list-the-libraries-already-installed"></a>Seznam již nainstalovaných knihoven

Po instalaci některých knihoven můžete pomocí **seznamu vcpkg** zjistit, co máte:

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

## <a name="integrate-with-visual-studio-windows"></a>Integrace s Visual Studio (Windows)

### <a name="per-user"></a>Na uživatele

Spusťte **integrujte vcpkg instalaci** a nakonfigurujte Visual Studio tak, aby vyhledávala všechny soubory hlaviček vcpkg a binární soubory pro jednotlivé uživatele. Není třeba provádět ruční úpravy cest adresářů VC++. Pokud máte více klonů, klon, ze kterých tento příkaz spustíte, se stane novým výchozím umístěním.

Nyní můžete #include záhlaví jednoduše zadáním složky / záhlaví a automatické dokončování vám pomůže. Pro propojení s libs nebo přidávání odkazů na projekt nejsou nutné žádné další kroky. Následující obrázek ukazuje, jak Visual Studio najde záhlaví azure-storage-cpp. vcpkg umístí své hlavičky do podsložky **/installed,** rozdělené podle cílové platformy. Následující diagram znázorňuje seznam zahrnutí souborů v podsložce **/was** pro knihovnu:

![vcpkg a Technologie IntelliSense](media/vcpkg-intellisense.png "vcpkg a Technologie IntelliSense")

### <a name="per-project"></a>Na projekt

Pokud potřebujete použít určitou verzi knihovny, která se liší od verze v aktivní instanci vcpkg, postupujte takto:

1. Vytvořit nový klon vcpkg
1. Upravte soubor portfile pro knihovnu získat verzi, kterou potřebujete
1. Spusťte **knihovnu \<vcpkg,>. **
1. Pomocí **projektu integrace vcpkg vytvořte** balíček NuGet, který odkazuje na tuto knihovnu na základě projektu.

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>Integrace s visual studio kód (Linux/MacOS)

Spusťte **vcpkg integrujte instalaci** a nakonfigurujte kód Visual Studia na Linuxu/MacOS. Tento příkaz nastaví umístění zařazení vcpkg a povolí intelliSense ve zdrojových souborech.

## <a name="target-linux-from-windows-via-wsl"></a>Cíl linux z Windows přes WSL

Binární soubory Linuxu můžete vytvářet na počítači se systémem Windows pomocí podsystému Windows pro Linux nebo WSL. Podle pokynů [nastavte wsl ve Windows 10](/windows/wsl/install-win10)a nakonfigurujte ho pomocí [rozšíření Visual Studio pro Linux](https://blogs.msdn.microsoft.com/vcblog/2017/02/08/targeting-windows-subsystem-for-linux-from-visual-studio/). Je v pořádku umístit všechny vytvořené knihovny pro Windows a Linux do stejné složky. Jsou přístupné z windows i wsl.

## <a name="export-compiled-binaries-and-headers"></a><a name="export_binaries_per_project"></a>Export zkompilovaných binárních souborů a záhlaví

Je neefektivní, aby všichni v týmu stahovat a vytvářet společné knihovny. Jeden člen týmu můžete použít **příkaz export vcpkg** k vytvoření společného souboru zip binárních souborů a záhlaví nebo balíčku NuGet. Pak je snadné sdílet s ostatními členy týmu.

## <a name="updateupgrade-installed-libraries"></a>Aktualizace nebo upgrade nainstalovaných knihoven

Veřejný katalog je průběžně aktualizován s nejnovějšími verzemi knihoven. Chcete-li zjistit, které z místních knihoven jsou zastaralé, použijte **aktualizaci vcpkg**. Až budete připraveni aktualizovat kolekci portů na nejnovější verzi veřejného katalogu, spusťte příkaz **upgradu vcpkg.** Automaticky stáhne a znovu vytvoří některé nebo všechny nainstalované knihovny, které jsou zastaralé.

Ve výchozím nastavení je v příkazu **pro upgrade** uvedenpouze knihovny, které jsou zastaralé. neupgraduje je. Chcete-li skutečně upgradovat knihovny, použijte **možnost --no-dry-run.**

```cmd
  vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>Možnosti upgradu

- **--ne-suchý běh**  Proveďte upgrade; pokud není zadán, příkaz obsahuje pouze zastaralé balíčky.
- **--keep-going**  Pokračujte v instalaci balíčků, i když se jeden nezdaří.
- ** \<--trojčata t>**  Nastavte výchozí trojčata pro neúplné balíčky.
- **--vcpkg-root \<>cesty**  Zadejte adresář vcpkg, který se má použít místo aktuálního adresáře nebo adresáře nástrojů.

### <a name="upgrade-example"></a>Příklad upgradu

Následující příklad ukazuje, jak inovovat pouze zadané knihovny. vcpkg automaticky táhne závislosti podle potřeby.

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

## <a name="contribute-new-libraries"></a>Přispívat novými knihovnami

Do kolekce soukromých portů můžete zahrnout všechny knihovny, které se vám líbí. Chcete-li navrhnout novou knihovnu pro veřejný katalog, otevřete problém na [stránce githubu vcpkg](https://github.com/Microsoft/vcpkg/issues).

## <a name="remove-a-library"></a>Odebrání knihovny

Zadejte **příkaz vcpkg odebrat,** chcete-li odebrat nainstalovanou knihovnu. Pokud na něm závisí jiné knihovny, budete vyzváni k opětovnému spuštění příkazu s **--recurse**, což způsobí odebrání všech podřízených knihoven.

## <a name="customize-vcpkg"></a>Přizpůsobení vcpkg

Můžete upravit klon vcpkg jakýmkoli způsobem se vám líbí. Můžete dokonce vytvořit více klonů vcpkg a pak upravit portfiles v každém z nich. To je jednoduchý způsob, jak získat konkrétní verze knihovny nebo určit konkrétní parametry příkazového řádku. Například v rozlehlé síti mohou jednotlivé skupiny vývojářů pracovat na softwaru, který má sadu závislostí specifických pro jejich skupinu. Řešením je nastavit klon vcpkg pro každý tým. Potom upravte klony ke stažení verze knihovny a nastavte přepínače kompilace, které každý tým potřebuje.

## <a name="uninstall-vcpkg"></a>Odinstalovat vcpkg

Stačí odstranit adresář vcpkg. Odstraněním tohoto adresáře odinstalujete distribuci vcpkg a nainstalují všechny knihovny, které má vcpkg.

## <a name="send-feedback-about-vcpkg"></a>Odeslat zpětnou vazbu o vcpkg

Pomocí příkazu **vcpkg contact --survey** odepřete společnosti Microsoft zpětnou vazbu o vcpkg, včetně hlášení chyb a návrhů funkcí.

## <a name="the-vcpkg-folder-hierarchy"></a>Hierarchie složek vcpkg

Všechny funkce vcpkg a data jsou samostatné v jedné hierarchii adresářů, nazývané "instance". Neexistují žádná nastavení registru nebo proměnné prostředí. Můžete mít libovolný počet instancí vcpkg v počítači a nebudou vzájemně zasahovat.

Obsah instance vcpkg jsou:

- buildtrees -- obsahuje podsložky zdrojů, ze kterých je každá knihovna vytvořena
- dokumenty -- dokumentace a příklady
- ke stažení -- kopie všech stažených nástrojů nebo zdrojů uložených v mezipaměti. vcpkg hledá zde první při spuštění příkazu install.
- nainstalována-- Obsahuje záhlaví a binární soubory pro každou nainstalovanou knihovnu. Při integraci s Visual Studio, jste v podstatě říká, že přidat tuto složku do svých vyhledávacích cest.
- packages -- Interní složka pro přípravu mezi instalacemi.
- ports -- Soubory, které popisují každou knihovnu v katalogu, jeho verzi a kde ji stáhnout. V případě potřeby můžete přidat vlastní porty.
- skripty -- Skripty (cmake, powershell) používané vcpkg.
- toolsrc -- Zdrojový kód Jazyka C++ pro vcpkg a související komponenty
- trojčata -- Obsahuje nastavení pro každou podporovanou cílovou platformu (například x86-windows nebo x64-uwp).

## <a name="command-line-reference"></a>Referenční dokumentace k příkazovému řádku

|Příkaz|Popis|
|---------|---------|
|**vcpkg \[hledání pat]**|Hledat balíčky, které jsou k dispozici k instalaci|
|**vcpkg \<instalace pkg>...**|Instalace balíčku|
|**vcpkg \<odstranit pkg>...**|Odinstalace balíčku|
|**vcpkg odebrat --zastaralé**|Odinstalace všech zastaralých balíčků|
|**seznam vcpkg**|Seznam nainstalovaných balíčků|
|**aktualizace vcpkg**|Zobrazit seznam balíčků pro aktualizaci|
|**upgrade vcpkg**|Znovu sestavit všechny zastaralé balíčky|
|**soubor hash \<vcpkg> \[alg]**|Hash soubor podle konkrétního algoritmu, výchozí SHA512|
|**vcpkg integrovat instalaci**|Zpřístupnit nainstalované balíčky pro celou uživatele. Vyžaduje oprávnění správce při prvním použití.|
|**vcpkg integrovat odebrat**|Odebrání integrace pro celý uživatel|
|**vcpkg integrovat projekt**|Generovat odkazující balíček NuGet pro použití jednotlivých projektů VS|
|**vcpkg \<export pkg>... \[opt]...**|Export balíčku|
|**vcpkg \<upravit pkg>**|Otevření portu pro úpravy (používá %EDITOR%, výchozí 'kód')|
|**vcpkg \<vytvořit pkg \< \[> url> archivename]**|Vytvoření nového balíčku|
|**mezipaměť vcpkg**|Seznam sestavených balíčků v mezipaměti|
|**verze vcpkg**|Zobrazit informace o verzi|
|**kontakt vcpkg --průzkum**|Zobrazí kontaktní informace pro odeslání zpětné vazby.|

### <a name="options"></a>Možnosti

|Možnost|Popis|
|---------|---------|
|**--trojčata \<t>**|Zadejte trojčata cílové architektury. (výchozí: `%VCPKG_DEFAULT_TRIPLET%`, viz také **vcpkg pomoci trojčata**)|
|**--vcpkg-root \<>cesty**|Zadejte kořenový adresář vcpkg (výchozí: `%VCPKG_ROOT%`)|
