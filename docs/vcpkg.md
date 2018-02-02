---
title: "vcpkg – Správce balíčků C++ pro Windows | Microsoft Docs"
description: "vcpkg je Správce balíčků příkazového řádku, který výrazně zjednodušuje získání a instalaci knihovny open-source C++ v systému Windows."
keywords: vcpkg
author: mikeblome
ms.author: mblome
ms.date: 01/21/2018
ms.technology:
- cpp-ide
ms.tgt_pltfrm: windows
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.topic: article
dev_langs:
- C++
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7980297dd7068022cd2765b8ac9d8d5679af9e64
ms.sourcegitcommit: 1e367a5f5c5a6fd0b6018f4fb5edcdf2f1a8085c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="vcpkg-c-package-manager-for-windows"></a>vcpkg: Správce balíčků C++ pro Windows 
vcpkg je Správce balíčků příkazového řádku, který výrazně zjednodušuje získání a instalace knihoven třetích stran v systému Windows. Pokud projekt používá knihovny třetích stran, doporučujeme použít vcpkg k instalaci. vcpkg podporuje open source a vlastní knihovny. Všechny knihovny v katalogu veřejné vcpkg byly testovány z hlediska kompatibility s Visual Studio 2015 a Visual Studio 2017. Komunita C++ je přidání dalších knihoven průběžně od ledna 2018 neobsahuje více než 600 knihovny v katalogu.

## <a name="simple-yet-flexible"></a>Jednoduché, ale flexibilní
Pomocí jednoho příkazu můžete stáhnout zdroje a sestavení knihovny. vcpkg je sám open source projektu dostupná na Githubu. Můžete přizpůsobit vaší privátní clone(s) žádným způsobem, který chcete. Například můžete zadat různé knihovny, nebo jiné verze knihoven než co se nacházejí v katalogu veřejné. Může mít více klonech vcpkg na jednom počítači, každé z nich vytváření vlastní nastaví knihovny nebo přepínače kompilace atd. Každý klonování je samostatná, kopírovatelná x prostředí se svou vlastní kopií z vcpkg.exe, funguje pouze na vlastní hierarchii. vcpkg není přidáno do proměnných prostředí a nemá žádné závislosti na registru systému Windows nebo Visual Studio.

## <a name="sources-not-binaries"></a>Zdroje není binární soubory
Pro knihovny v katalogu veřejné stáhne vcpkg zdroje místo binárních souborů [1]. Tyto zdroje pomocí Visual Studio 2017 nebo Visual Studio 2015, pokud není nainstalovaná 2017 kompilaci. V jazyce C++ je velmi důležité žádné knihovny, které používáte dodržení jsou stejné kompilátoru a verze kompilátoru jako odkazující na jeho kódu aplikace. Pomocí vcpkg eliminovat nebo alespoň výrazně předešli neodpovídající binární soubory a mohou způsobit problémy. Týmy, které jsou standardizované pro určitou verzi sady Visual C++ compiler slouží jeden člen seskupení vcpkg stáhnout zdroje a zkompilovat sadu binární soubory a pak použít příkaz export zip binární soubory a hlavičky pro ostatní členové týmu. Další informace najdete v tématu že export kompilovány binární soubory a hlavičky níže. 

Pokud vytvoříte klon vcpkg s privátní knihovny v kolekci porty, můžete přidat na port, který soubory ke stažení předem sestavené binární soubory a hlavičky a zápis do souboru portfile.cmake, který kopíruje jednoduše těchto souborů do požadovaného umístění.

[1] *Poznámka: některá vlastnické knihovny zdrojů nejsou k dispozici. Vcpkg stáhne kompatibilní předem sestavené binární soubory v těchto případech.*

## <a name="installation"></a>Instalace
Naklonujte úložiště vcpkg z Githubu: https://github.com/Microsoft/vcpkg. Můžete si stáhnout do libovolného umístění složky, kterému dáváte přednost.

Spustit zavaděč v kořenové složce: bootstrap vcpkg.bat.

## <a name="search-the-list-of-available-libraries"></a>Hledat seznam dostupných knihoven
Balíčky, které jsou k dispozici, zadejte na příkazovém řádku: **vcpkg vyhledávání**

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

  Můžete filtrovat podle vzor, například **vcpkg vyhledávání dat**:

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library

```

## <a name="install-a-library-on-your-local-machine"></a>Nainstalujte knihovnu na místním počítači
Po získání názvu knihovny pomocí **vcpkg vyhledávání**, použijete **vcpkg nainstalovat** stáhnout knihovny a jeho kompilace. vcpkg používá portfile knihovny v adresáři porty. Pokud není zadaný žádný trojdílná, vcpkg nainstaluje a kompilace pro x86 windows. Pokud portfile Určuje závislosti, vcpkg stáhne a nainstaluje ty také. Po stažení, vcpkg sestavení knihovny pomocí ať sestavení systému, který používá knihovna. CMake a MSBuild projekty soubory jsou upřednostňované, ale je podporovaná ZKONTROLUJTE společně s všechny ostatní systémy sestavení. Pokud vcpkg nemůže najít zadaný sestavení systému v místním počítači, stáhne a nainstaluje se.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

## <a name="list-the-libraries-already-installed"></a>Vypisuje seznam knihoven již nainstalována
Po instalaci některé knihovny, můžete použít **vcpkg seznamu** co máte:

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

## <a name="integrate-with-visual-studio"></a>Integrace se sadou Visual Studio
### <a name="per-user"></a>Na uživatele
Spustit **vcpkg integrovat instalace** konfigurace Visual Studio najít všechny soubory hlaviček vcpkg a binární soubory v jednotlivých uživatelů bez nutnosti ruční úpravy cesty adresáře VC ++. Pokud máte více klonech, klonování, ze které spouštíte tento příkaz změní výchozí umístění.

Teď můžete #include hlavičky jednoduše zadáním složky/záhlaví a automatické dokončování pomáhá. Žádné další kroky jsou vyžadovány pro propojení do knihovny nebo přidání odkazů projektu. Následující obrázek znázorňuje, jak Visual Studio vyhledá azure-storage-cpp hlavičky. vcpkg umístí jeho hlavičky v podsložce \installed rozdělena na oddíly podle cílové platformy. Následující diagram znázorňuje zahrnout soubory v seznamu `/was` podsložce knihovny:

 ![vcpkg Intellisense integrace](media/vcpkg-intellisense.png "vcpkg a Intellisense")  

### <a name="per-project"></a>Každý projekt
Pokud potřebujete použít konkrétní verzi knihovny, která je odlišná od verze v instanci active vcpkg, postupujte takto:

1. Ujistěte se, nový klon vcpkg 
1. Upravit portfile pro knihovnu verzi, které potřebujete
1. Spustit **vcpkg nainstalovat \<Knihovna >**.
1. Použití **vcpkg integrovat projekt** k vytvoření balíčku NuGet, který odkazuje na tuto knihovnu na jednotlivých projektů.


## <a name="export-compiled-binaries-and-headers"></a>Export kompilovány binární soubory a hlavičky
Vyžadování všichni členové týmu a stáhněte si a sestavte knihovny může být neefektivní. Jeden seskupení můžete dělat svou práci a pak použít **vcpkg export** vytvořte soubor zip binární soubory a hlaviček, které je možné snadno sdílet s dalšími členy týmu. 

## <a name="updateupgrade-installed-libraries"></a>Aktualizovat nebo upgradovat nainstalované knihovny
Veřejné katalogu je pořád aktuální a mají nejnovější verze knihoven. Chcete-li zjistit, které z vaší místní knihovny jsou zastaralé, použijte **vcpkg aktualizace**. Až budete připraveni k aktualizaci vaší kolekce porty na nejnovější verzi veřejné katalogu, spusťte **vcpkg upgrade** příkaz, který automaticky stáhnout a znovu sestavte některého nebo všech vaší nainstalované knihovny, které jsou zastaralé.

Ve výchozím nastavení **upgrade** příkazu jsou uvedeny pouze knihovny, které jsou zastaralé; nemá upgradovat, je. Chcete-li provést upgrade, použijte **– ne test** možnost. 

```cmd
  vcpkg upgrade --no-dry-run 
```

### <a name="upgrade-options"></a>Možnosti upgradu

- **– Ne test** provést upgrade, není-li zadána, příkaz je uveden pouze zastaralé balíčky. 
- **--zachovat probíhající** pokračovat v instalaci balíčků i v případě, že jeden server selže. 
- **--Trojdílná \<t >** nastavit výchozí trojdílná nekvalifikované balíčků. 
- **--vcpkg-root \<cesta >** zadejte vcpkg adresář, který chcete použít místo aktuální adresář nebo nástroj adresář. 

### <a name="upgrade-example"></a>Příklad upgradu

Následující příklad ukazuje, jak upgradovat pouze zadané knihovny. Všimněte si, že vcpgk se automaticky vrátí v závislosti podle potřeby.

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
Můžete zahrnout všechny knihovny, které chcete v kolekci privátní porty. Navrhovat nová knihovna pro veřejné katalogu, otevřete na problém [GitHub vcpkg problém stránce](https://github.com/Microsoft/vcpkg/issues).

## <a name="remove-a-library"></a>Odebrání knihovny
Typ **vcpkg odebrat** k odebrání nainstalované knihovny. Pokud jsou na ní závislé další knihovny, jste vyzváni k spusťte znovu příkaz s **--recurse**, což způsobí, že všechny podřízené knihovny odebrat.

## <a name="customize-vcpkg"></a>Přizpůsobení vcpkg
Vaše klon vcpkg žádným způsobem, který chcete, můžete upravit. Můžete vytvořit více klonech vcpkg a upravit portfiles v každé z nich pro získání konkrétních verzí knihovny, nebo zadejte parametry příkazového řádku. Například v podniku, jedna skupina vývojářů může pracovat na softwaru, který má jednu sadu závislosti a jiné skupiny může mít jinou sadu. Můžete nastavit dva klony vcpkg a upravit každé z nich ke stažení verze knihovny a kompilace přepínače a podobně, podle svých potřeb. 

## <a name="uninstall-vcpkg"></a>Odinstalace vcpkg
Odstraňte adresář. 

## <a name="send-feedback-about-vcpkg"></a>Pošlete svůj názor vcpkg
Použití **– průzkum** příkaz k odeslání zpětné vazby společnosti Microsoft o vcpkg, včetně sestav chyb a návrhy na funkce.

## <a name="the-vcpkg-folder-hierarchy"></a>Hierarchie složky vcpkg
Všechna data a funkce vcpkg je samostatný v hierarchii, jeden adresář, nazývá "instance". Neexistují žádné nastavení registru nebo proměnné prostředí. Může mít libovolný počet instancí vcpkg na počítači, a tedy nekolidují mezi sebou. 

Obsah instance vcpkg jsou: 

- buildtrees – obsahuje podsložky zdrojů, ze kterých vychází jednotlivých knihoven
- dokumentace – dokumentace a příklady
- stáhne – kopie v mezipaměti všechny stažené nástroje nebo zdroje. vcpkg prohledá zde nejprve při spuštění příkazu instalace.
- nainstalovat – obsahuje záhlaví a binární soubory pro každou nainstalovanou knihovny. Při integraci se sadou Visual Studio v podstatě oznamujete ho tuto složku přidat do jeho cesty pro hledání.
- balíčky – vnitřní složku pro pracovní mezi nainstaluje.
- porty – soubory, které popisují každou knihovny v katalogu, jeho verzi a kde se stáhne. V případě potřeby můžete přidat vlastní porty.
- skripty – skripty (cmake, prostředí powershell) používané vcpkg.
- toolsrc – zdrojového kódu C++ pro vcpkg a související součásti
- trojice – obsahuje nastavení pro každou platformu podporovaný cíl (například x86 windows nebo x64 uwp).

## <a name="command-line-reference"></a>Referenční dokumentace k příkazovému řádku

|Příkaz|Popis|
|---------|---------|
|**hledání vcpkg [Jan]**|Vyhledejte balíčky, které jsou k dispozici pro instalaci|
|**Nainstalujte vcpkg \<pkg >...**|Instalovat balíček|
|**odebrat vcpkg \<pkg >...**|Odinstalace balíčku|
|**vcpkg remove --outdated**|Odinstalujte všechny balíčky zastaralé|
|**vcpkg list**|Výpis nainstalovaných balíčků|
|**vcpkg update**|Zobrazení seznamu balíčků pro aktualizaci|
|**vcpkg upgrade**|Znovu vytvořit všechny zastaralé balíčky|
|**Hodnota hash vcpkg \<soubor > [alg]**|Konkrétní algoritmem hash souboru, výchozí SHA512|
|**vcpkg integrovat instalace**|Zkontrolujte nainstalována balíčky k dispozici úrovni uživatele. Vyžaduje oprávnění správce na první použití|
|**vcpkg integrovat odebrat**|Odebrat uživatele celou integrace|
|**vcpkg integrovat projektu**|Generovat odkazující balíček NuGet pro jednotlivé použití projektu VS|
|**vcpkg export \<pkg >... [opt]...**|Exportovat balíček|
|**vcpkg edit \<pkg>**|Otevřete port pro úpravy (používá EDITOR %, výchozí kód)|
|**vcpkg import \<pkg >**|Importujte předem připravený knihovny|
|**Vytvoření vcpkg \<pkg > \<url > [archivename]**|Vytvořit nový balíček|
|**vcpkg owns \<pat>**|Vyhledávání souborů v nainstalované balíčky|
|**vcpkg cache**|Seznam mezipaměti zkompilovat balíčky|
|**vcpkg version**|Zobrazit informace o verzi|
|**vcpkg contact**|Zobrazení informací o váš názor|


### <a name="options"></a>Možnosti:
|Možnost|Popis|
|---------|---------|
|**--Trojdílná \<t >**|Zadejte trojdílná architektura cíl. (výchozí: `%VCPKG_DEFAULT_TRIPLET%`, viz také **vcpkg nápovědy trojdílná**)|
|**--vcpkg-root \<path>**|Zadejte kořenový adresář vcpkg (výchozí: `%VCPKG_ROOT%`)|
