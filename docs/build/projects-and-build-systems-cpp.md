---
title: Projekty C/C++ a systémy sestavení v sadě Visual Studio
ms.description: Use Visual Studio to compile and build C++ projects for Windows, ARM or Linux based on any project system.
ms.date: 12/08/2018
f1_keywords:
- vcbuilding
- buildingaprogramVC
helpviewer_keywords:
- builds [C++]
- Visual C++ projects, building
- projects [C++], building
- builds [C++], options
- Visual C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
ms.openlocfilehash: 0c4a74ce69f5c52eb6fc107ea477e5715e86ecd2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823034"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>Projekty C/C++ a systémy sestavení v sadě Visual Studio

Visual Studio 2017 můžete upravit, kompilace a sestavení jakékoli C++ kódovou základnu o plnou podporu technologie IntelliSense bez nutnosti k převedení tohoto kódu do projektu sady Visual Studio nebo proveďte kompilaci s sada nástrojů MSVC. Můžete třeba upravit – multiplatformního projektu CMake v sadě Visual Studio na počítači s Windows a pak kompilovat pro Linux s využitím g ++ na vzdáleném počítači s Linuxem.

## <a name="c-compilation"></a>Kompilace jazyka C++

K *sestavení* programu v jazyce C++ znamená, že ke kompilaci zdrojového kódu z jednoho nebo více souborů a propojit tyto soubory do spustitelného souboru (.exe), zatížení dynamické knihovny (DLL) nebo statická knihovna (.lib). 

Základní kompilace jazyka C++ zahrnuje tři hlavní kroky:

- Preprocesor jazyka C++ transformuje všechny #directives a makra definice v každý zdrojový soubor. Tím se vytvoří *jednotce překladu*.
- Kompilátor C++ kompiluje každou jednotku převodu do souborů objektů (.obj), použití jakékoli možnosti kompilátoru nebyly nastaveny.
- *Linkeru* sloučí objektových souborů jeden spustitelný soubor, použití možnosti linkeru, které jste nastavili. 

## <a name="the-msvc-toolset"></a>Sada nástrojů MSVC

Kompilátor C++ společnosti Microsoft, linker, standardní knihovny a související nástroje tvoří sada nástrojů kompilátoru MSCV (také nazývané sady nástrojů nebo "nástroje sestavení"). Tyto jsou zahrnuty v sadě Visual Studio. Můžete také stáhnout a použít sadu nástrojů jako samostatného balíčku zdarma z [umístění pro stahování Build Tools pro Visual Studio 2017](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017).

Vyvoláním a kompilátorem MSVC (cl.exe) přímo z příkazového řádku můžete vytvářet jednoduché programy. Následující příkaz přijímá jeden zdrojový soubor kódu a vyvolá cl.exe sestavit spustitelný soubor volá *hello.exe*: 

```cmd
cl /EHsc hello.cpp
```
Všimněte si, že tady kompilátoru (cl.exe) automaticky vyvolá preprocesor jazyka C++ a propojovací program vytvoří konečného výstupního souboru.  Další informace najdete v tématu [sestavení na příkazovém řádku](building-on-the-command-line.md).

## <a name="build-systems-and-projects"></a>Vytvářejte systémy a projekty

Většina programů reálného světa pomocí některých druh *sestavovací systém* ke správě složitosti kompilaci více zdrojových souborů pro více konfigurací (tj ladění a vydání), více platforem (x86, x64, ARM, a tak dále), vlastní sestavení kroky a ještě více spustitelné soubory, které musí být zkompilovány v určitém pořadí. Zkontrolujte nastavení v souborech konfigurace sestavení a sestavovací systém tento soubor přijímá jako vstup před volání kompilátoru. Je volána sadu souborů zdrojového kódu a sestavení konfigurační soubory potřebné k sestavení spustitelného souboru *projektu*. 

Následující seznam uvádí různé možnosti pro projekty aplikace Visual Studio – C++:

- Vytvořit projekt sady Visual Studio s použitím rozhraní IDE sady Visual Studio a konfigurovat pomocí stránky vlastností. Projekty aplikace Visual Studio vytvářet programy, které běží na Windows. Přehled najdete v tématu [kompilování a sestavování](/visualstudio/ide/compiling-and-building-in-visual-studio) v dokumentaci k sadě Visual Studio.

- Otevřete složku, která obsahuje soubor CMakeLists.txt. Podpora CMake je integrované do sady Visual Studio. Integrované vývojové prostředí můžete upravit, testování a ladění beze změny CMake soubory žádným způsobem. To umožňuje pracovat ve stejném projektu CMake jako ostatní, kdo může používat různými editory. CMake je doporučený postup pro vývoj pro různé platformy. Další informace najdete v tématu [projekty CMake](cmake-projects-in-visual-studio.md).
 
- Otevřete složku dojde ke ztrátě zdrojových souborů s žádný soubor projektu. Visual Studio použije heuristiku k sestavení souborů. Toto je snadný způsob, jak kompilovat a spouštět malé konzolové aplikace. Další informace najdete v tématu [projekty otevřít složku](open-folder-projects-cpp.md).

- Otevřete složku, která obsahuje soubor pravidel nebo jakýkoli jiný soubor konfigurace sestavení systému. Můžete nakonfigurovat k vyvolání všechny příkazy libovolného sestavení tak, že přidáte soubory JSON do složky Visual Studio. Další informace najdete v tématu [projekty otevřít složku](open-folder-projects-cpp.md).
 
- Otevřete soubor pravidel Windows v sadě Visual Studio. Další informace najdete v tématu [NMake – odkaz](reference/nmake-reference.md).

## <a name="msbuild-from-the-command-line"></a>Nástroj MSBuild z příkazového řádku 

MSBuild vyvoláte z příkazového řádku s předáním souboru .vcxproj spolu s možností příkazového řádku. Tento přístup vyžaduje dostatečné povědomí o MSBuild a doporučuje se pouze v případě, že je nezbytně nutné. Další informace najdete v tématu [MSBuild](msbuild-visual-cpp.md).

## <a name="in-this-section"></a>V tomto oddílu

[Projekty aplikace Visual Studio](creating-and-managing-visual-cpp-projects.md) jak vytvářet, konfigurovat a sestavovat C++ projekty v sadě Visual Studio pomocí jeho nativní sestavovací systém (MSBuild).

[Projekty CMake](cmake-projects-in-visual-studio.md) kódu, sestavení a nasazení projektů CMake v sadě Visual Studio.

[Otevřete složku projekty](open-folder-projects-cpp.md) tom, jak pomocí sady Visual Studio code, sestavování a nasazování projektů v jazyce C++ založené na libovolný systém libovolné sestavení nebo žádný systém sestavení. Vůbec. 

[Sestavení pro vydání](release-builds.md) jak vytvořit a řešení potíží s optimalizovanou verzi sestavení pro nasazení pro koncové uživatele.

[Použití nástrojů MSVC z příkazového řádku](building-on-the-command-line.md)<br/>
Popisuje, jak použít kompilátor jazyka C/C++ a vytváření buildů přímo z příkazového řádku, nikoli pomocí integrovaného vývojového prostředí sady Visual Studio.

[Vytváření knihovny DLL v sadě Visual Studio](dlls-in-visual-cpp.md) tom, jak vytvářet, ladit a nasazovat knihovny DLL jazyka C/C++ (sdílené knihovny) v sadě Visual Studio.

[Sestavení izolovaných aplikací C/C++ a sestavení vedle sebe](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md) popisuje model nasazení pro aplikace Windows Desktop, založené na představu o izolovaných aplikací a sestavení vedle sebe.

[Konfigurace projektů C++ pro 64bitové, x64 cíle](configuring-programs-for-64-bit-visual-cpp.md) jak k cíli 64-bit x64 hardware s MSVC nástroje sestavení.

[Konfigurace projektů C++ pro procesory ARM](configuring-programs-for-arm-processors-visual-cpp.md) způsob použití nástroje sestavení MSVC cílit na ARM hardwaru.

[Optimalizace kódu](optimizing-your-code.md) k optimalizaci kódu různými způsoby, včetně optimalizace programu s asistencí.

[Konfigurace programů pro Windows XP](configuring-programs-for-windows-xp.md) jak na cíl Windows XP s MSVC nástroje sestavení.

[Referenční zdroje k sestavení programu v jazyce C/C++](reference/c-cpp-building-reference.md)<br/>
Poskytuje odkazy na články, referenční informace o programu sestavení v jazyce C++, možnosti kompilátoru a propojovacího programu a různé nástroje pro vytváření.
