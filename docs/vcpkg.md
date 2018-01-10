---
title: "vcpkg – Správce balíčků C++ pro Windows | Microsoft Docs"
description: "vcpkg je Správce balíčků příkazového řádku, který výrazně zjednodušuje získání a instalaci knihovny open-source C++ v systému Windows."
keywords: vcpkg
author: mikeblome
ms.author: mblome
ms.date: 05/30/2017
ms.technology: cpp-ide
ms.tgt_pltfrm: windows
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.topic: article
dev_langs: C++
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0728827cb2cd604ec4e7ff1ef58b68ed8fb64532
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="vcpkg-c-package-manager-for-windows"></a>vcpkg: Správce balíčků C++ pro Windows 
vcpkg je Správce balíčků příkazového řádku, který výrazně zjednodušuje získání a instalace knihoven třetích stran v systému Windows. Pokud projekt používá knihovny třetích stran, doporučujeme použít vcpkg k instalaci. vcpkg podporuje open source a vlastní knihovny. Všechny knihovny v katalogu veřejné vcpkg byly testovány z hlediska kompatibility s Visual Studio 2015 a Visual Studio 2017. Komunity C++ je přidání dalších knihoven průběžně od 2017 pravděpodobně neobsahuje více než 238 knihovny v katalogu.

## <a name="simple-yet-flexible"></a>Jednoduché, ale flexibilní
Pomocí jednoho příkazu můžete stáhnout zdroje a sestavení knihovny. vcpkg je sám open source projektu dostupná na Githubu. Můžete přizpůsobit vaší privátní clone(s) žádným způsobem, který se vám líbí, například zadáním různé knihovny, nebo jiné verze knihoven než co se nacházejí v katalogu veřejné. Může mít více klonech vcpkg na jednom počítači, každé z nich vytváření vlastní nastaví knihovny nebo přepínače kompilace atd. Každý klonování je zcela samostatné, kopírovatelná x prostředí se svou vlastní kopií z vcpkg.exe, funguje pouze na vlastní hierarchii. vcpkg není přidáno do proměnných prostředí a nemá žádné závislosti na registru systému Windows nebo Visual Studio.

## <a name="sources-not-binaries"></a>Zdroje není binární soubory
Pro knihovny v katalogu veřejné stáhne vcpkg zdroje místo binárních souborů [1]. Tyto zdroje pomocí Visual Studio 2017 nebo Visual Studio 2015, pokud není nainstalovaná 2017 kompilaci. V jazyce C++ je velmi důležité žádné knihovny, které používáte dodržení jsou stejné kompilátoru a verze kompilátoru jako odkazující na jeho kódu aplikace. Pomocí vcpkg eliminovat nebo alespoň výrazně předešli neodpovídající binární soubory a mohou způsobit problémy. Týmy, které jsou standardizované pro určitou verzi sady Visual C++ compiler slouží jeden člen seskupení vcpkg stáhnout zdroje a zkompilovat sadu binární soubory a pak použít příkaz export zip binární soubory a hlavičky pro ostatní členové týmu. Další informace najdete v tématu že export kompilovány binární soubory a hlavičky níže. 

Pokud vytvoříte klon vcpkg s privátní knihovny v kolekci porty, můžete přidat na port, který soubory ke stažení předem sestavené binární soubory a hlavičky a zápis do souboru portfile.cmake, který kopíruje jednoduše těchto souborů do požadovaného umístění.

[1] *Poznámka: některá vlastnické knihovny zdrojů nejsou k dispozici. Vcpkg stáhne kompatibilní předem sestavené binární soubory v těchto případech.*

## <a name="installation"></a>Instalace
Naklonujte úložiště vcpkg z Githubu: https://github.com/Microsoft/vcpkg. Můžete si stáhnout do libovolného umístění složky, kterému dáváte přednost.

Spustit zavaděč v kořenové složce: bootstrap vcpkg.bat.

## <a name="basic-tasks"></a>Základní úlohy
  
### <a name="search-the-list-of-available-libraries"></a>Hledat seznam dostupných knihoven
Balíčky, které jsou k dispozici, zadejte na příkazovém řádku:`vcpkg search`

Tento příkaz vytvoří výčet řídicích souborů v podsložkách vcpkg nebo porty. Zobrazí se v seznamu takto:

```cmd
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. <https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

  Můžete filtrovat podle vzor, například `vcpkg search ta`:

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library

```

### <a name="install-a-library-on-your-local-machine"></a>Nainstalujte knihovnu na místním počítači
Po získání názvu knihovny pomocí `vcpkg search`, použijete `vcpkg install` stáhnout knihovny a jeho kompilace. vcpkg používá portfile knihovny v adresáři porty. Pokud není zadaný žádný trojdílná, vcpkg nainstaluje a kompilace pro x86 windows. Pokud portfile Určuje závislosti, bude vcpkg stáhněte a nainstalujte ty také. Po stažení, vcpkg sestavení knihovny pomocí ať sestavení systému, který používá knihovna. CMake a MSBuild projekty soubory jsou upřednostňované, ale je podporovaná ZKONTROLUJTE společně s všechny ostatní systémy sestavení. Pokud vcpkg nemůže najít zadaný sestavení systému v místním počítači, bude ji stáhněte a nainstalujte ho.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

### <a name="list-the-libraries-already-installed"></a>Vypisuje seznam knihoven již nainstalována
Po instalaci některé knihovny, můžete použít `vcpkg list` a zjistěte, co obsahuje:

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

### <a name="integrate-with-visual-studio"></a>Integrace se sadou Visual Studio
#### <a name="per-user"></a>Na uživatele
Spustit `vcpkg integrate install` konfigurace Visual Studio najít všechny soubory hlaviček vcpkg a binární soubory v jednotlivých uživatelů bez nutnosti ruční úpravy cesty adresáře VC ++. Pokud máte více klonech, klonování, ze které spouštíte tento příkaz změní výchozí umístění.

Teď můžete #include hlavičky jednoduše zadáním složky/záhlaví a bude automaticky dokončit vám pomůže. Žádné další kroky jsou vyžadovány pro propojení do knihovny nebo přidání odkazů projektu. Následující obrázek znázorňuje, jak Visual Studio vyhledá azure-storage-cpp hlavičky. vcpkg umístí jeho hlavičky v podsložce \installed rozdělena na oddíly podle cílové platformy. Následující diagram znázorňuje zahrnout soubory v seznamu `/was` podsložce knihovny:

 ![vcpkg Intellisense integrace](media/vcpkg-intellisense.png "vcpkg a Intellisense")  

#### <a name="per-project"></a>Každý projekt
Pokud budete muset použít konkrétní verzi knihovny, která je odlišná od verze v instanci active vcpkg, můžete vytvořit nový klon vcpkg, upravte portfile pro knihovnu verzi je třeba a poté spusťte `vcpkg install <library>`. Potom můžete použít `vcpkg integrate project` k vytvoření balíčku NuGet, který odkazuje na tuto knihovnu na jednotlivých projektů.

### <a name="export-compiled-binaries-and-headers"></a>Export kompilovány binární soubory a hlavičky
Vyžadování všichni členové týmu a stáhněte si a sestavte knihovny může být neefektivní. Jeden seskupení můžete dělat svou práci a pak použít `vcpkg export` vytvořte soubor zip binární soubory a hlaviček, které je možné snadno sdílet s dalšími členy týmu. 

### <a name="update-installed-libraries"></a>Knihovny nainstalována aktualizace
Veřejné katalogu je pořád aktuální a mají nejnovější verze knihoven. Chcete-li zjistit, které z vaší místní knihovny jsou zastaralé, použijte `vcpkg update`. Až budete připraveni k aktualizaci vaší kolekce porty na nejnovější verzi veřejné katalogu, právě provést vyžádanou operací git proti úložiště github, nebo vytvořte nový klon a ponechat ten starý, pokud je stále potřeba.

### <a name="contribute-new-libraries"></a>Přispívat nové knihovny
Můžete zahrnout všechny knihovny, které chcete v kolekci privátní porty. Navrhovat nová knihovna pro veřejné katalogu, otevřete na problém [GitHub vcpkg problém stránce](https://github.com/Microsoft/vcpkg/issues).

### <a name="remove-a-library"></a>Odebrání knihovny
Typ `vcpkg remove` k odebrání nainstalované knihovny. Pokud jsou na ní závislé další knihovny, zobrazí se výzva k znovu spusťte příkaz s `--recurse`, což způsobí, že všechny podřízené knihovny odebrat.

### <a name="customize-vcpkg"></a>Přizpůsobení vcpkg
Vaše klon vcpkg žádným způsobem, který chcete, můžete upravit. Můžete vytvořit více klonech vcpkg a upravit portfiles v každé z nich pro získání konkrétních verzí knihovny, nebo zadejte parametry příkazového řádku. Například v podniku, jedna skupina vývojářů může pracovat na softwaru, který má jednu sadu závislosti a jiné skupiny může mít jinou sadu. Můžete nastavit dva klony vcpkg a upravit každé z nich ke stažení verze knihovny a kompilace přepínače a podobně, podle svých potřeb. 

### <a name="uninstall-vcpkg"></a>Odinstalace vcpkg
Odstraňte adresář. 

## <a name="the-vcpkg-folder-hierarchy"></a>Hierarchie složky vcpkg
Všechna data a funkce vcpkg je zcela samostatné v hierarchii jednoho adresářového; tomu se říká "instance". Neexistují žádné nastavení registru nebo proměnné prostředí. Může mít libovolný počet instancí vcpkg na počítači, a nebude do mezi sebou. 

Obsah instance vcpkg jsou: 
- buildtrees – obsahuje podsložky zdrojů, ze kterých vychází jednotlivých knihoven
- dokumentace – dokumentace a příklady
- stáhne – kopie v mezipaměti všechny stažené nástroje nebo zdroje. vcpkg prohledá zde nejprve při spuštění příkazu instalace.
- nainstalovat – obsahuje záhlaví a binární soubory pro každou nainstalovanou knihovny. Při integraci se sadou VIsual Studio v podstatě oznamujete ho tuto složku přidat do jeho cesty pro hledání.
- balíčky – vnitřní složku pro pracovní mezi nainstaluje.
- porty – soubory, které popisují každou knihovny v katalogu, jeho verzi a kde se stáhne. V případě potřeby můžete přidat vlastní porty.
- skripty – skripty (cmake, prostředí powershell) používané vcpkg.
- toolsrc – zdrojového kódu C++ pro vcpkg a související součásti
- trojice – obsahuje nastavení pro každou platformu podporovaný cíl (např. x86 windows nebo x64 uwp).

## <a name="command-line-reference"></a>Odkaz na příkazový řádek
- hledání vcpkg [Jan] vyhledávání pro balíčky, které jsou k dispozici má být sestaven.
- Nainstalujte vcpkg <pkg>...    Instalovat balíček
- odebrat vcpkg <pkg>...  Odinstalace balíčku
- odebrat vcpkg – zastaralých odinstalovat všechny zastaralé balíčky
- vcpkg seznam výpis nainstalovaných balíčků
- vcpkg aktualizovat zobrazení seznamu balíčků pro aktualizaci
- Hodnota hash vcpkg <file> [alg] konkrétní algoritmem Hash souboru, výchozí SHA512
- vcpkg integrovat instalace zkontrolujte nainstalována balíčky k dispozici uživatelské úrovni. Vyžaduje oprávnění správce na první použití
- vcpkg integrovat integrace odebrat celou odebrat uživatele
- vcpkg integrovat projekt generování odkazující balíček nuget pro jednotlivé použití projektu VS
- vcpkg export <pkg>... [opt]...    Exportuje balíčku
- Upravit vcpkg <pkg> otevřete port pro úpravy (používá EDITOR %, výchozí kód)
- vcpkg import <pkg> importujte předem připravený knihovny
- Vytvoření vcpkg <pkg> <url> [archivename] vytvořit nový balíček
- vlastní vcpkg <pat> vyhledávání souborů v nainstalované balíčky
- vcpkg mezipaměti seznamu kompilované balíčky uložené v mezipaměti.
- verze vcpkg zobrazení informací o verzi
- Obraťte se na vcpkg zobrazení informací o váš názor

### <a name="options"></a>Možnosti:
  **`--triplet <t>`**Zadejte trojdílná architektura cíl. (výchozí: `%VCPKG_DEFAULT_TRIPLET%`, viz také `vcpkg help triplet`)

  **`--vcpkg-root <path>`**Zadejte kořenový adresář vcpkg (výchozí: `%VCPKG_ROOT%`)
