---
title: Nástroje Visual C++ a funkcí v edicích sady Visual Studio
ms.date: 02/28/2018
helpviewer_keywords:
- versions [C++]
- Visual C++, versions
- editions [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: 3e5b173741700ed6cccf95b479eb5693a62ed02e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786959"
---
# <a name="visual-c-tools-and-features-in-visual-studio-editions"></a>Nástroje Visual C++ a funkcí v edicích sady Visual Studio

Následující tabulky popisují funkce Visual C++, které jsou k dispozici v sadě Visual Studio. X v buňce znamená, že funkce je k dispozici. prázdná buňka znamená, že tato funkce není k dispozici. Poznámky v závorkách označují, že funkce je k dispozici, ale s omezeným přístupem.

## <a name="platforms"></a>Platformy

||||||
|-|-|-|-|-|
|Platforma|Visual Studio Express for Windows 10|Visual Studio Express for Windows Desktop|Visual Studio Community/Professional|Visual Studio Enterprise|
|Plocha Windows||X|X|X|
|Univerzální platforma Windows ((telefonu, tabletu, počítače, Xbox, IoT a HoloLens))|X||X|X|
|Microsoft Store 8.1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>Kompilátory

|Kompilátor|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|X86 32-bit kompilátor|X|X|X|X|
|X86_arm cross-compiler|X||X|X|
|x64 64-bit kompilátor|||X|X|
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
|OpenMP|X|X|X|X|

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
[Typy projektů Visual C++](../build/reference/visual-cpp-project-types.md)<br/>
[SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686)<br/>
