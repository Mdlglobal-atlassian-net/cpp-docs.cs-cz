---
title: C++Nástroje a funkce v různých edicích sady Visual Studio
ms.date: 05/21/2019
helpviewer_keywords:
- tools and platforms [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: c5c0459888f8787fd8abba495395130d64a193e0
ms.sourcegitcommit: bde3279f70432f819018df74923a8bb895636f81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174777"
---
# <a name="c-tools-and-features-in-visual-studio-editions"></a>C++Nástroje a funkce v různých edicích sady Visual Studio


::: moniker range=">=vs-2019"


Následující C++ funkce jsou k dispozici v aplikaci Visual Studio 2019. Pokud není uvedeno jinak, jsou všechny funkce dostupné ve všech edicích: Visual Studio Community, Visual Studio Professional a Visual Studio Enterprise. Některé funkce vyžadují konkrétní úlohy nebo volitelné součásti, které můžete nainstalovat pomocí instalačního programu sady Visual Studio.

## <a name="platforms"></a>Platformy

- Plocha Windows
- Univerzální platforma Windows ((tablet PC, Xbox, IoT a HoloLens))
- Linux
- Android
- iOS

## <a name="compilers"></a>Kompilátory

- 32-bit kompilátor MSVC x86, x 64, ARM a ARM64
- 64bitovým kompilátorem MSVC pro x86, x 64, ARM a ARM64
- GCC křížový kompilátor pro ARM
- Clang/LLVM
  - Na Windows, Clang/LLVM 7.0 x86 nebo x64 (jenom podpora Cmaku). Jiné verze Clang mohou fungovat, ale nejsou oficiálně podporované.
  - V žádné instalaci Clang/LLVM podporována distribuce Linuxu.
 
## <a name="c-workloads"></a>C++Úlohy

Visual Studio obsahuje následující úlohy pro C++ vývoje. Můžete nainstalovat některé nebo všechny z nich, společně s další úlohy, jako jsou .NET Desktop Development, vývoj v jazyce Python, vývoj pro Azure, vývoj rozšíření sady Visual Studio a dalších.

### <a name="desktop-development-with-c"></a>Vývoj desktopových aplikací pomocí C++

Zahrnuté:
- C++– základní desktopové funkce

Volitelné součásti:
- MSVC v142 – VS 2019 C++ x64/x86 sestavení nástroje (v14.21)
- Windows 10 SDK (10.0.17763.0)
- Just-In-Time debugger
- Nástroje pro profilaci v C++
- Nástroje C++ CMake pro Windows
- C++ ATL pro nástroje pro vytváření v142 (x86 & x64)
- Testovací adaptér pro Boost.Test
- Testovací adaptér pro Google Test
- Live Share
- IntelliCode
- IntelliTrace (pouze v Enterprise)
- C++ MFC pro nástroje pro vytváření v142 (x86 & x64)
- C++/ Podpora rozhraní příkazového řádku pro nástroje pro vytváření v142 (14.21)
- Moduly C++ pro v142 sestavení nástroje (x64/x86 – experimentální)
- Clang kompilátor pro Windows
- IncrediBuild – urychlení sestavení
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- MSVC v141 – sady VS 2017 C++ x64/x86 sestavení nástroje (v14.16)
- MSVC v140 - VS 2015 C++ vytvářet nástroje (v14.00)

### <a name="linux-development-with-c"></a>Vývoj pro Linux v C++

Zahrnuté:
- C++ – základní funkce
- Windows Universal C Runtime
- C++ pro vývoj pro Linux

Volitelné součásti:
- Nástroje C++ CMake pro Linux
- Vložené a IoT vývojářské nástroje

### <a name="universal-windows-platform-development"></a>Vývoj pro univerzální platformu Windows

Zahrnuté:
- Blend for Visual Studio
- .NET native a .NET Standard
- Správce balíčků NuGet
- Nástroje pro univerzální platformu Windows
- Windows 10 SDK (10.0.17763.0)

Volitelné součásti:
- IntelliCode
- IntelliTrace (pouze v Enterprise)
- Připojení zařízení USB
- Nástroje pro univerzální platformu Windows C++ (v142)
- Nástroje pro univerzální platformu Windows C++ (v141)
- Ladicí program grafiky a profiler GPU pro DirectX
- Windows 10 SDK (10.0.18362.0)
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- Architektury a analytické nástroje

### <a name="c-game-development"></a>C++Vývoj her

Zahrnuté:
- C++ – základní funkce
- Windows Universal C Runtime
- C++ 2019 Redistributable Update
- MSVC v142 – VS 2019 C++ x64/x86 sestavení nástroje (v14.21)

Volitelné součásti:
- Nástroje pro profilaci v C++
- Windows 10 SDK (10.0.17763.0)
- IntelliCode
- IntelliTrace (pouze v Enterprise)
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- IncrediBuild – urychlení sestavení
- Cocos
- Instalační program Unreal Engine
- Podpora androidu integrovaného vývojového prostředí pro Unreal engine

### <a name="mobile-development-with-c"></a>Vývoj mobilních aplikací pomocí C++

Zahrnuté:
- C++ – základní funkce
- Instalace sady Android SDK (úroveň rozhraní API 25) (místní instalace pro vývoj mobilních aplikací pomocí C++)

Volitelné součásti:
- Android NDK (R16B)
- Apache Ant (1.9.3)
- Vývojové nástroje C++ pro Android
- IntelliCode
- Emulátor Google Android (API úrovně 25) (místní instalace)
- Intel Hardware Accelerated provádění Manager (HAXM) (místní instalace)
- Sada Android NDK (R16B) (32 bitů)
- Nástroje pro vývoj iOS C++
- IncrediBuild – urychlení sestavení


## <a name="individual-components"></a>Jednotlivé komponenty

Tyto součásti můžete nainstalovat samostatně z jakékoli pracovní zátěže.

- Diagnostika jazyka JavaScript
- Live Share
- Modul runtime C++ Universal Windows Platform pro v142 nástroje sestavení
- Publikování ClickOnce
- Microsoft Visual Studio Installer Projects

## <a name="libraries-and-headers"></a>Knihovny a hlavičky

- Knihovny a hlavičky Windows
- Windows Universal C Runtime (CRT)
- Standardní knihovna C++
- ATL
- MFC
- .NET Framework – knihovna tříd
- Knihovna podpory C++ pro rozhraní .NET
- OpenMP 2.0
- Více než 900 knihovny open-source prostřednictvím vcpkg katalogu

## <a name="build-and-project-systems"></a>Sestavit a projektovat systémy

- CMake
- Libovolná sestavení systému prostřednictvím funkce Otevřít složku
- Sestavení příkazového řádku (msbuild.exe)
- Nativní cílení na více platforem
- Spravované cílení na více platforem
- Paralelní sestavení
- Vlastní nastavení sestavení
- Rozšiřitelnost stránek vlastností

## <a name="project-templates"></a>Šablony projektů

Následující šablony projektů jsou k dispozici v závislosti na úlohy, které jste nainstalovali.

Plocha Windows:
- Prázdný projekt
- Konzolová aplikace
- Desktopový Průvodce pro Windows
- Aplikace klasické pracovní plochy Windows
- Projekt sdílené položky
- MFC App
- Dynamické knihovny DLL
- Prázdný projekt CLR
- Konzolová aplikace CLR
- Statická knihovna
- Projekt CMake
- Projekt knihovny ATL
- Knihovna MFC DLL
- Knihovna tříd CLR
- Projekt makefile (Windows)
- Ovládací prvek ActiveX knihovny MFC
- Nativní projekt testu jednotek
- Google Test

Universal Windows Platform (C++/CX):
- Prázdná aplikace
- Rozhraní DirectX 11 a XAML aplikací
- Aplikace DirectX 11
- Aplikace DirectX 12 
- Aplikace testů jednotek 
- DLL 
- Součást prostředí Windows Runtime 
- Statická knihovna 
- Projekt Windows Application Packaging

Linux:
- Konzolová aplikace (Linux)
- Prázdný projekt (Linux)
- Blikání Raspberry Pi
- Projekt makefile (Linux)

## <a name="tools"></a>Nástroje

- Přírůstkový Linker (Link.exe)
- Nástroj Microsoft Makefile (Nmake.exe)
- Generátor lib (Lib.exe)
- Kompilátor prostředků Windows (Rc.exe)
- Prostředků Windows pro převaděč objekt (CvtRes.exe)
- Procházet Nástroj Údržba informací (BscMake.exe)
- C++ Name Undecorator (Undname.exe)
- Tlumič COFF/PE (Dumpbin.exe)
- Editor COFF/PE (Editbin.exe)
- MASM (Ml.exe)
- Spy++
- Errlook –
- AtlTrace
- Odvozená pravidla
- Optimalizace na základě profilu

## <a name="debugging-features"></a>Funkce ladění

- Nativní ladění
- natvis (nativní typ vizualizace)
- Grafické ladění
- Spravované ladění
- Využití GPU
- Využití paměti
- Vzdálené ladění
- Ladění SQL
- Analýza statického kódu

## <a name="designers-and-editors"></a>Návrháři a editory

- Návrhář XAML
- Návrhář/Editor stylu CSS
- Návrhář/Editor HTML
- Editor XML
- Editor zdrojového kódu
- Pro zvýšení produktivity: Refaktoring, modul IntelliSense zaměstnance EDG C++ formátování kódu
- Návrhář formulářů Windows
- Návrhář dat
- Nativní Editor prostředků (.rc soubory)
- Editory prostředků
- Editor modelů
- Návrhář shaderů
- Živé ověření závislosti (pouze v Enterprise)
- Diagramy vrstev architektury (pouze v Enterprise)
- Ověření architektury (pouze v Enterprise)
- Klonování kódu (pouze v Enterprise)

## <a name="data-features"></a>Datových funkcích

- Návrhář dat
- Datové objekty
- Webové služby
- Průzkumník serveru

## <a name="automation-and-extensibility"></a>Automatizace a rozšiřitelnost

- Objektové modely rozšíření
- Model kódu
- Model projektu
- Model editoru prostředku
- Model průvodce
- Model objektu ladicího programu

## <a name="application-lifecycle-management-tools"></a>Nástroje pro správu životního cyklu aplikací

- Testování jednotek (nativní Microsoft C++, Boost.Test, Google Test, CTest)
- Kód grafy mapy a závislostí (Professional a Enterprise)
- Pokrytí kódu (pouze Enterprise)
- Manuální testování (pouze v Enterprise)
- Relace nahodilého testování (pouze v Enterprise)
- Správa testovacích případů (pouze v Enterprise)
- Ladicí program integrace mapy kódu (pouze v Enterprise)
- Live Unit Testing (pouze v Enterprise)
- IntelliTrace (pouze v Enterprise)
- IntelliTest (pouze v Enterprise)
- Microsoft Fakes (izolace pro testování jednotek) (pouze v Enterprise)
- Pokrytí kódu (pouze v Enterprise)

## <a name="see-also"></a>Viz také:

[Instalace sady Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Co je nového v sadě Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[C++typy projektů v sadě Visual Studio](../build/reference/visual-cpp-project-types.md)<br/>

::: moniker-end

::: moniker range="<=vs-2017"

Následující tabulky popisují Visual C++ funkce, které jsou k dispozici v sadě Visual Studio 2017. X v buňce znamená, že funkce je k dispozici. prázdná buňka znamená, že tato funkce není k dispozici. Poznámky v závorkách označují, že funkce je k dispozici, ale s omezeným přístupem.

## <a name="platforms"></a>Platformy

||||||
|-|-|-|-|-|
|Platforma|Visual Studio Express for Windows 10|Visual Studio Express for Windows Desktop|Visual Studio Community/Professional|Visual Studio Enterprise|
|Plocha Windows||X|X|X|
|Univerzální platforma Windows ((telefonu, tabletu, počítače, Xbox, IoT a HoloLens))|X||X|X|
|Linux|X|X|
|Microsoft Store 8.1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>Kompilátory

|Kompilátor|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|MSVC X86 32-bit kompilátor|X|X|X|X|
|X86_arm cross-compiler|X||X|X|
|MSVC x64 64-bit kompilátor|||X|X|
|X86_ x64 cross-compiler|X|X|X|X|

## <a name="libraries-and-headers"></a>Knihovny a hlavičky

|Knihovna nebo záhlaví|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Windows hlavičky a knihovny a Knihovna CRT|(X)|X|X|X|
|Standardní knihovna C++|X|X|X|X|
|ATL|||X|X|
|MFC|||X|X|
|.NET Framework – knihovna tříd||X|X|X|
|Knihovna podpory C++ pro rozhraní .NET||X|X|X|
|OpenMP 2.0|X|X|X|X|

## <a name="project-templates"></a>Šablony projektů

|Šablona|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Šablony XAML pro UPW, Windows 8.1, Windows Phone 8.0|X||X|X|
|Aplikace Direct3D|X||X|X|
|Knihovny DLL (Universal Windows)|X||X|X|
|Statická knihovna (Universal Windows)|X||X|X|
|Součást prostředí Windows Runtime|X||X|X|
|Aplikace testů jednotek (Universal Windows)|X||X|X|
|Projekt knihovny ATL|||X|X|
|Knihovna tříd (CLR)||X|X|X|
|Konzolová aplikace CLR||X|X|X|
|Prázdný projekt CLR||X|X|X|
|Vlastní průvodce|||X|X|
|Prázdný projekt||X|X|X|
|Projekt makefile||X|X|X|
|Ovládací prvek ActiveX knihovny MFC|||X|X|
|Aplikace MFC|||X|X|
|MFC DLL|||X|X|
|Projekt testů|X|X|X|X|
|Konzolová aplikace Win32||X|X|X|
|Projekt Win32||X|X|X|

## <a name="tools"></a>Nástroje

|Nástroj|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Přírůstkový Linker (Link.exe)|X|X|X|X|
|Nástroj pro údržbu programu (Nmake.exe)||X|X|X|
|Generátor lib (Lib.exe)|X|X|X|X|
|Kompilátor prostředků Windows (Rc.exe)|X|X|X|X|
|Prostředků Windows pro převaděč objekt (CvtRes.exe)||X|X|X|
|Procházet Nástroj Údržba informací (BscMake.exe)|X|X|X|X|
|C++ Name Undecorator (Undname.exe)|X|X|X|X|
|Tlumič COFF/PE (Dumpbin.exe)|X|X|X|X|
|Editor COFF/PE (Editbin.exe)|X|X|X|X|
|MASM (Ml.exe)|||X|X|
|Spy++|||X|X|
|Errlook –|||X|X|
|AtlTrace|||X|X|
|Devenv.com|||X|X|
|Odvozená pravidla|||X|X|
|Upgrade projektů VCBuild .vcproj na MSBuild (VCUpgrade.exe)|X|X|X|X|
|Optimalizace na základě profilu|||X|X|

## <a name="debugging-features"></a>Funkce ladění

|Funkce ladění|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Nativní ladění|X|X|X|X|
|natvis (nativní typ vizualizace)|X|X|X|X|
|Grafické ladění|X||X|X|
|Spravované ladění||X|X|X|
|Využití GPU|X||X|X|
|Využití paměti|X||X|X|
|Vzdálené ladění|X|X|X|X|
|Ladění SQL|||X|X|
|Analýza statického kódu|Limited|Limited|X|X|

## <a name="designers-and-editors"></a>Návrháři a editory

|Návrhář nebo Editor|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Návrhář XAML|X||X|X|
|Návrhář/Editor stylu CSS|X|X|X|X|
|Návrhář/Editor HTML|X|X|X|X|
|Editor XML|X|X|X|X|
|Editor zdrojového kódu|X|X|X|X|
|Pro zvýšení produktivity: Refaktoring, technologie IntelliSense, formátování kódu jazyka C++|X|X|X|X|
|Návrhář formulářů Windows||X|X|X|
|Návrhář dat|||X|X|
|Nativní Editor prostředků (.rc soubory)|||X|X|
|Editory prostředků|X|X|X|X|
|Editor modelů|X||X|X|
|Návrhář shaderů|X||X|X|

## <a name="data-features"></a>Datových funkcích

|Funkce dat|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Návrhář dat|||X|X|
|Datové objekty|||X|X|
|Webové služby|||X|X|
|Průzkumník serveru|||X|X|

## <a name="build-and-project-systems"></a>Sestavit a projektovat systémy

|Sestavení nebo projektu funkce|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Sestavení příkazového řádku (msbuild.exe)|X|X|X|X|
|Nativní cílení na více platforem||X|X|X|
|Spravované cílení na více platforem||X|X|X|
|Paralelní sestavení|X|X|X|X|
|Vlastní nastavení sestavení|X|X|X|X|
|Rozšiřitelnost stránek vlastností|X|X|X|X|

## <a name="automation-and-extensibility"></a>Automatizace a rozšiřitelnost

|Automatizace a rozšiřitelnost|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Objektové modely rozšíření|||X|X|
|Model kódu|||X|X|
|Model projektu|||X|X|
|Model editoru prostředku|||X|X|
|Model průvodce|||X|X|
|Model objektu ladicího programu|||X|X|

## <a name="application-lifecycle-management-tools"></a>Nástroje pro správu životního cyklu aplikací

||||||
|-|-|-|-|-|
|Nástroj|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|Testování jednotek (nativní rozhraní framework)|X|X|X|X|
|Testování jednotek (spravované framework)||X|X|X|
|Pokrytí kódu||||X|
|Manuální testování||||X|
|nahodilé testování||||X|
|Správa testovacích případů||||X|
|Kód mapy a závislostí grafů|||jen pro čtení|X|
|Ladění mapy kódu||||X|

## <a name="see-also"></a>Viz také:

[Instalace sady Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Co je nového v sadě Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[C++typy projektů v sadě Visual Studio](../build/reference/visual-cpp-project-types.md)<br/>

::: moniker-end
