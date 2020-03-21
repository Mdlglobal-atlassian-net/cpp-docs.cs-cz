---
title: Nástroje a funkce C++ v různých edicích sady Visual Studio
ms.date: 05/21/2019
helpviewer_keywords:
- tools and platforms [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: 03a28c87bd0a122229a7e93b7077b1d6e3fea53f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079253"
---
# <a name="c-tools-and-features-in-visual-studio-editions"></a>Nástroje a funkce C++ v různých edicích sady Visual Studio

::: moniker range=">=vs-2019"

V aplikaci C++ Visual Studio 2019 jsou k dispozici následující funkce. Pokud není uvedeno jinak, všechny funkce jsou k dispozici ve všech edicích: Visual Studio Community, Visual Studio Professional a Visual Studio Enterprise. Některé funkce vyžadují konkrétní úlohy nebo volitelné součásti, které můžete nainstalovat pomocí Instalační program pro Visual Studio.

## <a name="platforms"></a>Platformy

- Windows Desktop
- Univerzální platforma Windows (tablet, PC, Xbox, IoT a HoloLens))
- Linux
- Android
- iOS

## <a name="compilers"></a>Kompilátory

- MSVC 32 – 32bitový kompilátor pro procesory x86, x64, ARM a ARM64
- MSVC 64 – 32bitový kompilátor pro procesory x86, x64, ARM a ARM64
- Křížové kompilátory RSZ pro ARM
- Clang/LLVM
  - Ve Windows, Clang/LLVM 7,0, cílící na x86 nebo x64 (pouze podpora CMake). Jiné verze Clang mohou fungovat, ale nejsou oficiálně podporovány.
  - V systému Linux všechny instalace Clang/LLVM podporované rozhraním distribuce.

## <a name="c-workloads"></a>C++Úlohy

Visual Studio obsahuje následující úlohy pro C++ vývoj. Můžete nainstalovat libovolné nebo všechny tyto součásti, spolu s dalšími úlohami, jako je vývoj desktopových aplikací pro .NET, vývoj v jazyce Python, vývoj pro Azure, vývoj rozšíření sady Visual Studio a další.

### <a name="desktop-development-with-c"></a>Vývoj desktopových aplikací pomocí C++

Obsaženy
- C++základní desktopové funkce

Volitelné součásti:
- Nástroje MSVC V142-VS C++ 2019 x64/x86 Build Tools (v 14.21)
- Windows 10 SDK (10.0.17763.0)
- Just-In-Time debugger
- Nástroje pro profilaci v C++
- C++Nástroje CMake pro Windows
- C++ATL pro nástroje V142 Build (x86 & x64)
- Testovací adaptér pro Boost.Test
- Testovací adaptér pro Google Test
- Live Share
- IntelliCode
- IntelliTrace (jenom Enterprise)
- C++MFC pro nástroje V142 Build (x86 & x64)
- C++Podpora/CLI pro nástroje V142 Build (14,21)
- C++Moduly pro V142 Build Tools (x64/x86 – experimentální)
- Kompilátor Clang pro Windows
- IncrediBuild – urychlení sestavení
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- Nástroje MSVC v141-VS C++ 2017 x64/x86 Build Tools (v 14.16)
- MSVC v140-VS 2015 C++ Build Tools (v 14.00)

### <a name="linux-development-with-c"></a>Vývoj linuxových aplikací v jazyce C++

Obsaženy
- C++základní funkce
- Windows Universal C Runtime
- C++pro vývoj pro Linux

Volitelné součásti:
- C++Nástroje CMake pro Linux
- Nástroje pro vývoj integrovaných a IoT

### <a name="universal-windows-platform-development"></a>Vývoj pro Univerzální platformu Windows

Obsaženy
- Blend for Visual Studio
- .NET native a .NET Standard
- Správce balíčků NuGet
- Nástroje pro univerzální platformu Windows
- Windows 10 SDK (10.0.17763.0)

Volitelné součásti:
- IntelliCode
- IntelliTrace (jenom Enterprise)
- Připojení zařízení USB
- C++(v142) Nástroje Univerzální platforma Windows
- C++v141 Nástroje Univerzální platforma Windows
- Ladicí program grafiky a profiler GPU pro DirectX
- Windows 10 SDK (10.0.18362.0)
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- Architektury a analytické nástroje

### <a name="c-game-development"></a>C++Vývoj her

Obsaženy
- C++základní funkce
- Windows Universal C Runtime
- C++2019 Distribuovatelný aktualizace
- Nástroje MSVC V142-VS C++ 2019 x64/x86 Build Tools (v 14.21)

Volitelné součásti:
- Nástroje pro profilaci v C++
- Windows 10 SDK (10.0.17763.0)
- IntelliCode
- IntelliTrace (jenom Enterprise)
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- IncrediBuild – urychlení sestavení
- Cocos
- Instalační program Unreal Engine
- Podpora prostředí Android IDE pro modul Unreal

### <a name="mobile-development-with-c"></a>Vývoj mobilních aplikací v jazyce C++

Obsaženy
- C++základní funkce
- Instalace Android SDK (úroveň rozhraní API 25) (místní instalace pro vývoj pro C++mobilní zařízení pomocí)

Volitelné součásti:
- Android NDK (R16B)
- Apache Ant (1.9.3)
- Vývojové nástroje C++ pro Android
- IntelliCode
- Google Android Emulator (rozhraní API úrovně 25) (místní instalace)
- Intel Hardware Accelerated provádění Manager (HAXM) (místní instalace)
- Android NDK (R16B) (32 bitů)
- Nástroje pro vývoj iOS C++
- IncrediBuild – urychlení sestavení

## <a name="individual-components"></a>Jednotlivé komponenty

Tyto součásti můžete nainstalovat nezávisle na jakémkoli zatížení.

- Diagnostika jazyka JavaScript
- Live Share
- C++Modul runtime Univerzální platforma Windows pro nástroje V142 Build
- Publikování ClickOnce
- Projekty instalační služby Microsoft Visual Studio

## <a name="libraries-and-headers"></a>Knihovny a hlavičky

- Hlavičky a knihovny Windows
- Windows Universal C runtime (CRT)
- Standardní knihovna C++
- ATL
- MFC
- .NET Framework – knihovna tříd
- C++Podpora knihovny pro .NET
- OpenMP 2,0
- Více než 900 Open-Source knihoven prostřednictvím katalogu vcpkg

## <a name="build-and-project-systems"></a>Systémy sestavení a projektů

- CMake
- Libovolný systém sestavení prostřednictvím otevřené složky
- Sestavení příkazového řádku (MSBuild. exe)
- Nativní cílení na více platforem
- Spravované cílení na více platforem
- Paralelní sestavení
- Přizpůsobení sestavení
- Rozšíření stránek vlastností

## <a name="project-templates"></a>Šablony projektů

Následující šablony projektu jsou k dispozici v závislosti na tom, jaké úlohy jste nainstalovali.

Plocha Windows:
- Prázdný projekt
- Konzolová aplikace
- Průvodce desktopem systému Windows
- Desktopová aplikace pro Windows
- Projekt sdílených položek
- Aplikace MFC
- Knihovna dynamického propojení
- Prázdný projekt CLR
- Konzolová aplikace CLR
- Statická knihovna
- Projekt CMake
- ATL – projekt
- Knihovna MFC DLL
- Knihovna tříd CLR
- Projekt makefile (Windows)
- ActiveXControl knihovny MFC
- Nativní projekt testu jednotek
- Google Test

Univerzální platforma Windows (C++/CX):
- Prázdná aplikace
- Aplikace DirectX 11 a XAML
- Aplikace DirectX 11
- Aplikace DirectX 12
- Aplikace pro testování částí
- DLL
- Součást prostředí Windows Runtime
- Statická knihovna
- Projekt pro balení aplikace pro systém Windows

Linux:
- Konzolová aplikace (Linux)
- Prázdný projekt (Linux)
- Bliknutí ve Maline PI
- Projekt makefile (Linux)

## <a name="tools"></a>Nástroje

- Přírůstkový Linker (Link. exe)
- Microsoft makefile Utility (NMAKE. exe)
- Lib Generator (lib. exe)
- Kompilátor prostředků Windows (RC. exe)
- Převaděč prostředků Windows do objektů (CvtRes. exe)
- Nástroj pro údržbu informací o procházení (BscMake. exe)
- C++Název Undecorator (UNDNAME. exe)
- COFF/PE tlumič (DUMPBIN. exe)
- Editor COFF/PE (nástroje Editbin. exe)
- MASM (ml. exe)
- Spy++
- ErrLook
- AtlTrace
- Odvozená pravidla
- Optimalizace na základě profilu

## <a name="debugging-features"></a>Funkce ladění

- Nativní ladění
- Natvis (vizualizace nativního typu)
- Ladění grafiky
- Spravované ladění
- Využití GPU
- Využití paměti
- Vzdálené ladění
- Ladění SQL
- Analýza statického kódu

## <a name="designers-and-editors"></a>Návrháři a editory

- Návrhář XAML
- Návrhář/Editor stylu CSS
- Návrhář nebo editor HTML
- Editor XML
- Editor zdrojového kódu
- Funkce pro produktivitu: refaktoring, modul EDG C++ IntelliSense, formátování kódu
- Návrhář formulářů Windows
- Návrhář dat
- Nativní editor prostředků (soubory. RC)
- Editory prostředků
- Editor modelů
- Návrhář shaderů
- Ověřování závislostí v reálném čase (jenom Enterprise)
- Diagramy vrstev architektury (jenom Enterprise)
- Ověření architektury (jenom Enterprise)
- Klon kódu (jenom Enterprise)

## <a name="data-features"></a>Datové funkce

- Návrhář dat
- Datové objekty
- Webové služby
- Průzkumník serveru

## <a name="automation-and-extensibility"></a>Automatizace a rozšiřitelnost

- Rozšiřitelné objektové modely
- Model kódu
- Model projektu
- Model editoru prostředků
- Model průvodce
- Model objektu ladicího programu

## <a name="application-lifecycle-management-tools"></a>Nástroje pro správu životního cyklu aplikací

- Testování částí (Microsoft Native C++, zvyšování. Test, Google test, CTest)
- Mapa kódu a grafy závislostí (Professional a Enterprise)
- Pokrytí kódu (jenom Enterprise)
- Manuální testování (jenom Enterprise)
- Průzkumné testování (jenom Enterprise)
- Správa testovacích případů (jenom Enterprise)
- Integrace ladicího programu mapy kódu (jenom Enterprise)
- Live Unit Testing (jenom Enterprise)
- IntelliTrace (jenom Enterprise)
- IntelliTest (jenom Enterprise)
- Napodobeniny Microsoftu (jenom Enterprise test Unit) (jenom Enterprise)
- Pokrytí kódu (jenom Enterprise)

## <a name="see-also"></a>Viz také

[Instalace sady Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Co je nového v aplikaci Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[C++typy projektů v aplikaci Visual Studio](../build/reference/visual-cpp-project-types.md)

::: moniker-end

::: moniker range="<=vs-2017"

V následujících tabulkách jsou uvedeny C++ vizuální funkce, které jsou k dispozici v aplikaci visual Studio 2017. X v buňce označuje, že funkce je k dispozici; prázdná buňka označuje, že funkce není k dispozici. Poznámky v závorkách označují, že funkce je k dispozici, ale je omezená.

## <a name="platforms"></a>Platformy

||||||
|-|-|-|-|-|
|Platforma|Visual Studio Express pro Windows 10|Visual Studio Express pro desktopovou plochu Windows|Visual Studio Community/Professional|Visual Studio Enterprise|
|Windows Desktop||×|×|×|
|Univerzální platforma Windows ((telefon, tablet, PC, Xbox, IoT a HoloLens))|×||×|×|
|Linux|×|×|
|Microsoft Store 8,1|||×|×|
|Windows Phone 8,0|||×|×|
|Android|||×|×|
|iOS|||×|×|

## <a name="compilers"></a>Kompilátory

|Přepínač|Visual Studio Express pro Windows|Visual Studio Express pro desktopovou plochu Windows|Visual Studio Professional/komunita|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|MSVC 32 – 32bitový kompilátor x86|×|×|×|×|
|X86_arm mezi kompilátorem|×||×|×|
|64 MSVC – 32bitový kompilátor x64|||×|×|
|X86_ x64 cross-compiler|×|×|×|×|

## <a name="libraries-and-headers"></a>Knihovny a hlavičky

|Knihovna nebo hlavička|Visual Studio Express pro Windows|Visual Studio Express pro desktopovou plochu Windows|Visual Studio Professional/komunita|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Hlavičky a knihovny systému Windows a Knihovna CRT|(X)|×|×|×|
|Standardní knihovna C++|×|×|×|×|
|ATL|||×|×|
|MFC|||×|×|
|.NET Framework – knihovna tříd||×|×|×|
|C++Podpora knihovny pro .NET||×|×|×|
|OpenMP 2,0|×|×|×|×|

## <a name="project-templates"></a>Šablony projektů

|Šablona|Visual Studio Express pro Windows|Visual Studio Express pro desktopovou plochu Windows|Visual Studio Professional/komunita|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Šablony XAML pro UWP, Windows 8.1 Windows Phone 8,0|×||×|×|
|Aplikace Direct3D|×||×|×|
|DLL (univerzální pro Windows)|×||×|×|
|Statická knihovna (univerzální pro Windows)|×||×|×|
|Součást prostředí Windows Runtime|×||×|×|
|Aplikace pro testování jednotek (univerzální pro Windows)|×||×|×|
|ATL – projekt|||×|×|
|Knihovna tříd (CLR)||×|×|×|
|Konzolová aplikace CLR||×|×|×|
|Prázdný projekt CLR||×|×|×|
|Vlastní průvodce|||×|×|
|Prázdný projekt||×|×|×|
|Projekt makefile||×|×|×|
|MFC – ovládací prvek ActiveX|||×|×|
|Aplikace MFC|||×|×|
|MFC DLL|||×|×|
|Projekt testů|×|×|×|×|
|Konzolová aplikace Win32||×|×|×|
|Projekt Win32||×|×|×|

## <a name="tools"></a>Nástroje

|Nástroj|Visual Studio Express pro Windows|Visual Studio Express pro desktopovou plochu Windows|Visual Studio Professional/komunita|Visual Studio Enterprise|
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Přírůstkový Linker (Link. exe)|×|×|×|×|
|Nástroj Údržba programu (NMAKE. exe)||×|×|×|
|Lib Generator (lib. exe)|×|×|×|×|
|Kompilátor prostředků Windows (RC. exe)|×|×|×|×|
|Převaděč prostředků Windows do objektů (CvtRes. exe)||×|×|×|
|Nástroj pro údržbu informací o procházení (BscMake. exe)|×|×|×|×|
|C++Název Undecorator (UNDNAME. exe)|×|×|×|×|
|COFF/PE tlumič (DUMPBIN. exe)|×|×|×|×|
|Editor COFF/PE (nástroje Editbin. exe)|×|×|×|×|
|MASM (ml. exe)|||×|×|
|Spy++|||×|×|
|ErrLook|||×|×|
|AtlTrace|||×|×|
|Devenv.com|||×|×|
|Odvozená pravidla|||×|×|
|Upgrade projektů VCBuild. vcproj na MSBuild (VCUpgrade. exe)|×|×|×|×|
|Optimalizace na základě profilu|||×|×|

## <a name="debugging-features"></a>Funkce ladění

|Funkce ladění|Visual Studio Express pro Windows|Visual Studio Express pro desktopovou plochu Windows|Visual Studio Professional/komunita|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Nativní ladění|×|×|×|×|
|Natvis (vizualizace nativního typu)|×|×|×|×|
|Ladění grafiky|×||×|×|
|Spravované ladění||×|×|×|
|Využití GPU|×||×|×|
|Využití paměti|×||×|×|
|Vzdálené ladění|×|×|×|×|
|Ladění SQL|||×|×|
|Analýza statického kódu|Limitovan|Limitovan|×|×|

## <a name="designers-and-editors"></a>Návrháři a editory

|Návrhář nebo Editor|Visual Studio Express pro Windows|Visual Studio Express pro desktopovou plochu Windows|Visual Studio Professional/komunita|Visual Studio Enterprise|
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Návrhář XAML|×||×|×|
|Návrhář/Editor stylu CSS|×|×|×|×|
|Návrhář nebo editor HTML|×|×|×|×|
|Editor XML|×|×|×|×|
|Editor zdrojového kódu|×|×|×|×|
|Funkce pro produktivitu: refaktoring, C++ IntelliSense, formátování kódu|×|×|×|×|
|Návrhář formulářů Windows||×|×|×|
|Návrhář dat|||×|×|
|Nativní editor prostředků (soubory. RC)|||×|×|
|Editory prostředků|×|×|×|×|
|Editor modelů|×||×|×|
|Návrhář shaderů|×||×|×|

## <a name="data-features"></a>Datové funkce

|Funkce dat|Visual Studio Express pro Windows|Visual Studio Express pro desktopovou plochu Windows|Visual Studio Professional/komunita|Visual Studio Enterprise|
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Návrhář dat|||×|×|
|Datové objekty|||×|×|
|Webové služby|||×|×|
|Průzkumník serveru|||×|×|

## <a name="build-and-project-systems"></a>Systémy sestavení a projektů

|Funkce Build nebo Project|Visual Studio Express pro Windows|Visual Studio Express pro desktopovou plochu Windows|Visual Studio Professional/komunita|Visual Studio Enterprise|
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Sestavení příkazového řádku (MSBuild. exe)|×|×|×|×|
|Nativní cílení na více platforem||×|×|×|
|Spravované cílení na více platforem||×|×|×|
|Paralelní sestavení|×|×|×|×|
|Přizpůsobení sestavení|×|×|×|×|
|Rozšíření stránek vlastností|×|×|×|×|

## <a name="automation-and-extensibility"></a>Automatizace a rozšiřitelnost

|Automatizace a rozšiřitelnost|Visual Studio Express pro Windows|Visual Studio Express pro desktopovou plochu Windows|Visual Studio Professional/komunita|Visual Studio Enterprise|
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Rozšiřitelné objektové modely|||×|×|
|Model kódu|||×|×|
|Model projektu|||×|×|
|Model editoru prostředků|||×|×|
|Model průvodce|||×|×|
|Model objektu ladicího programu|||×|×|

## <a name="application-lifecycle-management-tools"></a>Nástroje pro správu životního cyklu aplikací

||||||
|-|-|-|-|-|
|Nástroj|Visual Studio Express pro Windows|Visual Studio Express pro desktopovou plochu Windows|Visual Studio Professional/komunita|Visual Studio Enterprise|
|Testování částí (nativní rozhraní)|×|×|×|×|
|Testování částí (spravované rozhraní)||×|×|×|
|Pokrytí kódu||||×|
|Manuální testování||||×|
|nahodilé testování||||×|
|Správa testovacích případů||||×|
|Mapa kódu a grafy závislostí|||jen pro čtení|×|
|Ladění mapy kódu||||×|

## <a name="see-also"></a>Viz také

[Instalace sady Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Co je nového v aplikaci Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[C++typy projektů v aplikaci Visual Studio](../build/reference/visual-cpp-project-types.md)

::: moniker-end
