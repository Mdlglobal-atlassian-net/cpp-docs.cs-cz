---
title: Nástroje a funkce C++ v různých edicích sady Visual Studio
ms.date: 05/21/2019
helpviewer_keywords:
- tools and platforms [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: 88eb66440df023254cb806c03a00aa2d71980305
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366787"
---
# <a name="c-tools-and-features-in-visual-studio-editions"></a>Nástroje a funkce C++ v různých edicích sady Visual Studio

::: moniker range=">=vs-2019"

Následující funkce Jazyka C++ jsou k dispozici ve Visual Studiu 2019. Pokud není uvedeno jinak, všechny funkce jsou k dispozici ve všech edicích: Visual Studio Community, Visual Studio Professional a Visual Studio Enterprise. Některé funkce vyžadují specifické úlohy nebo volitelné součásti, které můžete nainstalovat pomocí instalačního programu sady Visual Studio.

## <a name="platforms"></a>Platformy

- Windows Desktop
- Univerzální platforma Windows (tablet, pc, Xbox, IoT a HoloLens))
- Linux
- Android
- iOS

## <a name="compilers"></a>Kompilátory

- 32bitový kompilátor MSVC pro x86, x64, ARM a ARM64
- 64bitový kompilátor MSVC pro x86, x64, ARM a ARM64
- Křížový kompilátor GCC pro ARM
- Clang/LLVM
  - Ve Windows Clang/LLVM 7.0, cílení x86 nebo x64 (pouze podpora CMake). Jiné verze Clang mohou fungovat, ale nejsou oficiálně podporovány.
  - Na Linuxu, jakékoliv Clang / LLVM instalace podporované distro.

## <a name="c-workloads"></a>Úlohy jazyka C++

Visual Studio obsahuje následující úlohy pro vývoj c++. Můžete nainstalovat některé nebo všechny z nich, spolu s dalšími úlohami, jako je vývoj .NET Desktop, Vývoj Pythonu, Vývoj Azure, Vývoj rozšíření Sady Visual Studio a další.

### <a name="desktop-development-with-c"></a>Vývoj desktopových aplikací pomocí C++

Zahrnuty:

- Základní desktopové funkce C++

Volitelné součásti:

- Nástroje sestavení MSVC v142 - VS 2019 C++ x64/x86 (v14.21)
- Windows 10 SDK (10.0.17763.0)
- Ladicí program Just-In-Time
- Nástroje pro profilování jazyka C++
- Nástroje C++ CMake pro Windows
- C++ ATL pro nástroje sestavení v142 (x86 & x64)
- Testovací adaptér pro boost.test
- Testovací adaptér pro test Google
- Live Share
- IntelliCode
- IntelliTrace (pouze organizace)
- C++ Knihovna MFC pro nástroje sestavení v142 (x86 & x64)
- Podpora C++/CLI pro nástroje sestavení v142 (14.21)
- Moduly C++ pro nástroje pro sestavení v142 (x64/x86 – experimentální)
- Kompilátor Clang pro Windows
- IncrediBuild - Zrychlení sestavení
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- Nástroje sestavení MSVC v141 - VS 2017 C++ x64/x86 (v14.16)
- MSVC v140 - VS 2015 C++ nástroje pro sestavení (v14.00)

### <a name="linux-development-with-c"></a>Vývoj linuxových aplikací v jazyce C++

Zahrnuty:

- Základní funkce C++
- Windows Universal C Runtime
- C++ pro vývoj Linuxu

Volitelné součásti:

- C++ CMake nástroje pro Linux
- Vložené a ioT vývojové nástroje

### <a name="universal-windows-platform-development"></a>Vývoj univerzální platformy Windows

Zahrnuty:

- Blend for Visual Studio
- Nativní rozhraní .NET a standard .NET
- Správce balíčků NuGet
- Univerzální nástroje platformy Windows
- Windows 10 SDK (10.0.17763.0)

Volitelné součásti:

- IntelliCode
- IntelliTrace (pouze organizace)
- Připojení zařízení USB
- Nástroje univerzální platformy Windows pro C++ (v142)
- Nástroje univerzální platformy Windows pro C++ (v141)
- Grafický ladicí program a profiler GPU pro DirectX
- Windows 10 SDK (10.0.18362.0)
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- Nástroje pro architekturu a analýzu

### <a name="c-game-development"></a>Vývoj her C++

Zahrnuty:

- Základní funkce C++
- Windows Universal C Runtime
- Redistribuovatelná aktualizace C++ 2019
- Nástroje sestavení MSVC v142 - VS 2019 C++ x64/x86 (v14.21)

Volitelné součásti:

- Nástroje pro profilování jazyka C++
- Windows 10 SDK (10.0.17763.0)
- IntelliCode
- IntelliTrace (pouze organizace)
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- IncrediBuild - Zrychlení sestavení
- Cocos
- Instalátor unreal engine
- Podpora IDE Android pro unreal engine

### <a name="mobile-development-with-c"></a>Vývoj mobilních aplikací v jazyce C++

Zahrnuty:

- Základní funkce C++
- Nastavení sady Android SDK (úroveň rozhraní API 25) (místní instalace pro vývoj pro mobilní zařízení s C++)

Volitelné součásti:

- Android NDK (R16B)
- Pašanek Apache (1.9.3)
- Vývojové nástroje pro Android pro C++
- IntelliCode
- Google Android Emulátor (API Úroveň 25) (místní instalace)
- Intel Hardware Accelerated Execution Manager (HAXM) (místní instalace)
- Android NDK (R16B) (32bit)
- Vývojové nástroje pro iOS v C++
- IncrediBuild - Zrychlení sestavení

## <a name="individual-components"></a>Jednotlivé komponenty

Tyto součásti můžete nainstalovat nezávisle na jakékoli pracovní zátěži.

- Diagnostika javascriptu
- Live Share
- C++ Univerzální platforma Windows runtime pro v142 nástroje pro sestavení
- Publikování clickonce
- Projekty instalačního programu sady Microsoft Visual Studio

## <a name="libraries-and-headers"></a>Knihovny a záhlaví

- Záhlaví a knihovny systému Windows
- Prostředí Windows Universal C Runtime (CRT)
- Standardní knihovna C++
- ATL
- MFC
- .NET Framework – knihovna tříd
- Knihovna podpory jazyka C++ pro rozhraní .NET
- OpenMP 2.0
- Více než 900 open-source knihoven prostřednictvím katalogu vcpkg

## <a name="build-and-project-systems"></a>Vytváření a projektové systémy

- CMake
- Jakýkoli systém sestavení přes otevřenou složku
- Sestavení příkazového řádku (msbuild.exe)
- Nativní vícenásobné cílení
- Spravované vícenásobné cílení
- Paralelní sestavení
- Vlastní nastavení sestavení
- Rozšiřitelnost stránek vlastností

## <a name="project-templates"></a>Šablony projektů

Následující šablony projektu jsou k dispozici v závislosti na úlohách, které jste nainstalovali.

Plocha systému Windows:

- Prázdný projekt
- Konzolová aplikace
- Desktopový průvodce pro Windows
- Aplikace pro stolní počítače systému Windows
- Projekt sdílené položky
- Aplikace MFC
- Knihovna dynamických odkazů
- Prázdný projekt CLR
- Konzolová aplikace CLR
- Statická knihovna
- Projekt CMake
- Projekt ATL
- Knihovna dynamických odkazů knihovny MFC
- Knihovna tříd CLR
- Projekt makefile (Windows)
- MFC ActiveXControl
- Nativní projekt testování částí
- Google Test

Univerzální platforma Windows (C++/CX):

- Prázdná aplikace
- Aplikace DirectX 11 a XAML
- Aplikace DirectX 11
- Aplikace DirectX 12
- Testovací aplikace jednotky
- DLL
- Součást prostředí Windows Runtime
- Statická knihovna
- Projekt Windows Application Packaging

Linux:

- Konzolová aplikace (Linux)
- Prázdný projekt (Linux)
- Malina Pi Blink
- Projekt Makefile (Linux)

## <a name="tools"></a>nástroje

- Přírůstkové propojovací zařízení (Link.exe)
- Nástroj Microsoft Makefile (Nmake.exe)
- Lib Generátor (Lib.exe)
- Kompilátor prostředků systému Windows (Rc.exe)
- Převaděč prostředků systému Windows (CvtRes.exe)
- Procházet nástroj pro údržbu informací (BscMake.exe)
- C++ Název Undecorator (Undname.exe)
- Sklápěč COFF/PE (Dumpbin.exe)
- Editor COFF/PE (Editbin.exe)
- MASM (Ml.exe)
- Spy++
- ErrPodívejte se
- AtlTrace
- Odvozená pravidla
- Optimalizace s asistencí profilu

## <a name="debugging-features"></a>Ladění funkcí

- Nativní ladění
- natvis (vizualizace nativního typu)
- Ladění grafiky
- Spravované ladění
- Využití GPU
- Využití paměti
- Vzdálené ladění
- Ladění SQL
- Analýza statického kódu

## <a name="designers-and-editors"></a>Návrháři a redaktoři

- Návrhář XAML
- Návrhář/editor stylů CSS
- Návrhář/editor HTML
- Editor XML
-  Editor zdrojového kódu
- Produktivita: Refaktoring, modul EDG IntelliSense, formátování kódu C++
- Návrhář formulářů Windows
- Návrhář dat
- Editor nativních prostředků (.rc soubory)
- Editory prostředků
- Editor modelů
- Návrhář shaderů
- Ověření živé závislosti (pouze pro podnik)
- Diagramy architektonických vrstev (pouze organizace)
- Ověření architektury (pouze podnik)
- Klon kódu (pouze organizace)

## <a name="data-features"></a>Datové funkce

- Návrhář dat
- Datové objekty
- Webové služby
- Průzkumník serveru

## <a name="automation-and-extensibility"></a>Automatizace a rozšiřitelnost

- Rozšiřitelnost objektových modelů
- Model kódu
- Model projektu
- Model editoru prostředků
- Model průvodce
- Objektový model ladicího programu

## <a name="application-lifecycle-management-tools"></a>Nástroje pro správu životního cyklu aplikací

- Testování částí (Microsoft Native C++, Boost.Test, Google Test, CTest)
- Grafy mapování kódu a závislostí (Professional a Enterprise)
- Pokrytí kódu (pouze pro podniky)
- Ruční testování (pouze pro podniky)
- Průzkumné testování (pouze enterprise)
- Správa testovacího případu (pouze enterprise)
- Integrace ladicího programu mapy kódu (pouze enterprise)
- Testování živých částí (pouze pro podnik)
- IntelliTrace (pouze organizace)
- IntelliTest (pouze pro podnik)
- Microsoft Fakes (Izolace testování částí) (pouze podnik)
- Pokrytí kódu (pouze pro podniky)

## <a name="see-also"></a>Viz také

[Instalace sady Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Co je nového v sadě Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Typy projektů Jazyka C++ v sadě Visual Studio](../build/reference/visual-cpp-project-types.md)

::: moniker-end

::: moniker range="<=vs-2017"

V následujících tabulkách jsou uvedeny funkce visual c++, které jsou dostupné ve Visual Studiu 2017. X v buňce označuje, že funkce je k dispozici; prázdná buňka označuje, že funkce není k dispozici. Poznámky v závorcích označují, že funkce je dostupná, ale omezená.

## <a name="platforms"></a>Platformy

||||||
|-|-|-|-|-|
|Platforma|Visual Studio Express pro Windows 10|Visual Studio Express pro plochu Windows|Visual Studio – komunita/profesionál|Visual Studio Enterprise|
|Windows Desktop||×|×|×|
|Univerzální platforma Windows ((telefon, tablet, počítač, Xbox, IoT a HoloLens))|×||×|×|
|Linux|×|×|
|Microsoft Store 8.1|||×|×|
|Windows Phone 8.0|||×|×|
|Android|||×|×|
|iOS|||×|×|

## <a name="compilers"></a>Kompilátory

|Kompilátoru|Visual Studio Express pro Windows|Visual Studio Express pro plochu Windows|Visual Studio Professional / Komunita|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|32bitový kompilátor X86 MSVC|×|×|×|×|
|X86_arm křížový kompilátor|×||×|×|
|64bitový kompilátor MSVC x64|||×|×|
|X86_ křížový kompilátor x64|×|×|×|×|

## <a name="libraries-and-headers"></a>Knihovny a záhlaví

|Knihovna nebo záhlaví|Visual Studio Express pro Windows|Visual Studio Express pro plochu Windows|Visual Studio Professional / Komunita|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Záhlaví a knihovny systému Windows a knihovna CRT|(X)|×|×|×|
|Standardní knihovna C++|×|×|×|×|
|ATL|||×|×|
|MFC|||×|×|
|.NET Framework – knihovna tříd||×|×|×|
|Knihovna podpory jazyka C++ pro rozhraní .NET||×|×|×|
|OpenMP 2.0|×|×|×|×|

## <a name="project-templates"></a>Šablony projektů

|Šablona|Visual Studio Express pro Windows|Visual Studio Express pro plochu Windows|Visual Studio Professional / Komunita|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Šablony XAML pro UPW, Windows 8.1, Windows Phone 8.0|×||×|×|
|Aplikace Direct3D|×||×|×|
|DLL (univerzální okna)|×||×|×|
|Statická knihovna (univerzální okna)|×||×|×|
|Součást prostředí Windows Runtime|×||×|×|
|Aplikace testování částí (univerzální windows)|×||×|×|
|Projekt ATL|||×|×|
|Knihovna tříd (CLR)||×|×|×|
|Aplikace konzoly CLR||×|×|×|
|Prázdný projekt CLR||×|×|×|
|Vlastní průvodce|||×|×|
|Prázdný projekt||×|×|×|
|Projekt makesouboru||×|×|×|
|Ovládací prvek ActiveX knihovny MFC|||×|×|
|Aplikace Knihovny MFC|||×|×|
|MFC DLL|||×|×|
|Testovací projekt|×|×|×|×|
|Aplikace win32 konzoly||×|×|×|
|Projekt Win32||×|×|×|

## <a name="tools"></a>nástroje

|Nástroj|Visual Studio Express pro Windows|Visual Studio Express pro plochu Windows|Visual Studio Professional / Komunita|Visual Studio Enterprise|
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Přírůstkové propojovací zařízení (Link.exe)|×|×|×|×|
|Nástroj pro údržbu programu (Nmake.exe)||×|×|×|
|Lib Generátor (Lib.exe)|×|×|×|×|
|Kompilátor prostředků systému Windows (Rc.exe)|×|×|×|×|
|Převaděč prostředků systému Windows (CvtRes.exe)||×|×|×|
|Procházet nástroj pro údržbu informací (BscMake.exe)|×|×|×|×|
|C++ Název Undecorator (Undname.exe)|×|×|×|×|
|Sklápěč COFF/PE (Dumpbin.exe)|×|×|×|×|
|Editor COFF/PE (Editbin.exe)|×|×|×|×|
|MASM (Ml.exe)|||×|×|
|Spy++|||×|×|
|ErrPodívejte se|||×|×|
|AtlTrace|||×|×|
|Devenv.com|||×|×|
|Odvozená pravidla|||×|×|
|Upgrade projektů VCBuild .vcproj na msbuild (VCUpgrade.exe)|×|×|×|×|
|Optimalizace s asistencí profilu|||×|×|

## <a name="debugging-features"></a>Ladění funkcí

|Funkce ladění|Visual Studio Express pro Windows|Visual Studio Express pro plochu Windows|Visual Studio Professional / Komunita|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Nativní ladění|×|×|×|×|
|natvis (vizualizace nativního typu)|×|×|×|×|
|Ladění grafiky|×||×|×|
|Spravované ladění||×|×|×|
|Využití GPU|×||×|×|
|Využití paměti|×||×|×|
|Vzdálené ladění|×|×|×|×|
|Ladění SQL|||×|×|
|Analýza statického kódu|Omezeně|Omezeně|×|×|

## <a name="designers-and-editors"></a>Návrháři a redaktoři

|Návrhář nebo editor|Visual Studio Express pro Windows|Visual Studio Express pro plochu Windows|Visual Studio Professional / Komunita|Visual Studio Enterprise|
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Návrhář XAML|×||×|×|
|Návrhář/editor stylů CSS|×|×|×|×|
|Návrhář/editor HTML|×|×|×|×|
|Editor XML|×|×|×|×|
| Editor zdrojového kódu|×|×|×|×|
|Funkce produktivity: Refaktoring, IntelliSense, Formátování kódu C++|×|×|×|×|
|Návrhář formulářů Windows||×|×|×|
|Návrhář dat|||×|×|
|Editor nativních prostředků (.rc soubory)|||×|×|
|Editory prostředků|×|×|×|×|
|Editor modelů|×||×|×|
|Návrhář shaderů|×||×|×|

## <a name="data-features"></a>Datové funkce

|Funkce dat|Visual Studio Express pro Windows|Visual Studio Express pro plochu Windows|Visual Studio Professional / Komunita|Visual Studio Enterprise|
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Návrhář dat|||×|×|
|Datové objekty|||×|×|
|Webové služby|||×|×|
|Průzkumník serveru|||×|×|

## <a name="build-and-project-systems"></a>Vytváření a projektové systémy

|Funkce sestavení nebo projektu|Visual Studio Express pro Windows|Visual Studio Express pro plochu Windows|Visual Studio Professional / Komunita|Visual Studio Enterprise|
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Sestavení příkazového řádku (msbuild.exe)|×|×|×|×|
|Nativní vícenásobné cílení||×|×|×|
|Spravované vícenásobné cílení||×|×|×|
|Paralelní sestavení|×|×|×|×|
|Vlastní nastavení sestavení|×|×|×|×|
|Rozšiřitelnost stránek vlastností|×|×|×|×|

## <a name="automation-and-extensibility"></a>Automatizace a rozšiřitelnost

|Automatizace a rozšiřitelnost|Visual Studio Express pro Windows|Visual Studio Express pro plochu Windows|Visual Studio Professional / Komunita|Visual Studio Enterprise|
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Rozšiřitelnost objektových modelů|||×|×|
|Model kódu|||×|×|
|Model projektu|||×|×|
|Model editoru prostředků|||×|×|
|Model průvodce|||×|×|
|Objektový model ladicího programu|||×|×|

## <a name="application-lifecycle-management-tools"></a>Nástroje pro správu životního cyklu aplikací

||||||
|-|-|-|-|-|
|Nástroj|Visual Studio Express pro Windows|Visual Studio Express pro plochu Windows|Visual Studio Professional / Komunita|Visual Studio Enterprise|
|Testování částí (nativní rámec)|×|×|×|×|
|Testování částí (spravované rozhraní)||×|×|×|
|Pokrytí kódu||||×|
|Ruční testování||||×|
|nahodilé testování||||×|
|Správa testovacích případů||||×|
|Grafy mapy kódu a závislostí|||jen pro čtení|×|
|Ladění mapy kódu||||×|

## <a name="see-also"></a>Viz také

[Instalace sady Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Co je nového v sadě Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Typy projektů Jazyka C++ v sadě Visual Studio](../build/reference/visual-cpp-project-types.md)

::: moniker-end
