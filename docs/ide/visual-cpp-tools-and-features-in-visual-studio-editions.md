---
title: "Nástroje Visual C++ a funkcí v edicích sady Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/28/2018
ms.technology:
- cpp-ide
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- versions [C++]
- Visual C++, versions
- editions [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1bab6eda1c5c0d2d852d3a678f588f0539495001
ms.sourcegitcommit: 4e01d36ffa64ea11bacf589f79d2f1df947e2510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2018
---
# <a name="visual-c-tools-and-features-in-visual-studio-editions"></a>Funkcí v edicích sady Visual Studio a nástrojů pro Visual C++

Funkce Visual C++, které jsou k dispozici v sadě Visual Studio naleznete v následujících tabulkách. Znak X v buňce označuje, že je tato funkce není k dispozici. prázdná buňka označuje, že tato funkce není k dispozici. Poznámky v závorkách znamenat, že funkce je k dispozici, ale s omezeným přístupem.

## <a name="platforms"></a>Platformy

||||||
|-|-|-|-|-|
|Platforma|Visual Studio Express for Windows 10|Visual Studio Express for Windows Desktop|Visual Studio Community/Professional|Visual Studio Enterprise|
|Windows Desktop||X|X|X|
|Univerzální platformu Windows ((telefon, tablet, počítače, Xbox, IoT a HoloLens))|X||X|X|
|Microsoft Store 8.1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>Kompilátory

|Kompilátoru|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|32-bit X86 kompilátoru|X|X|X|X|
|X86_arm cross kompilátoru|X||X|X|
|64-bit [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] kompilátoru|||X|X|
|X86_ [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] mezi kompilátoru|X|X|X|X|

## <a name="libraries-and-headers"></a>Knihovny a hlavičky

|Knihovna nebo záhlaví|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Záhlaví systému Windows a knihoven a knihovny CRT|(X)|X|X|X|
|Standardní knihovna C++|X|X|X|X|
|ATL|||X|X|
|MFC|||X|X|
|.NET Framework – knihovna tříd||X|X|X|
|Knihovna podpory C++ pro .NET||X|X|X|
|OpenMP|X|X|X|X|

## <a name="project-templates"></a>Šablony projektů

|Šablony|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Šablony XAML pro UPW, Windows 8.1, Windows Phone 8.0|X||X|X|
|Aplikace Direct3D|X||X|X|
|Knihovny DLL (Universal Windows)|X||X|X|
|Statické knihovny (Universal Windows)|X||X|X|
|Součást prostředí Windows Runtime|X||X|X|
|Jednotka testování aplikace (univerzální pro Windows)|X||X|X|
|Projekt knihovny ATL|||X|X|
|Knihovna tříd (CLR)||X|X|X|
|Konzolová aplikace CLR||X|X|X|
|CLR Empty Project||X|X|X|
|Vlastní průvodce|||X|X|
|Prázdný projekt||X|X|X|
|Projektem souboru pravidel||X|X|X|
|Ovládací prvek ActiveX knihovny MFC|||X|X|
|Aplikace MFC|||X|X|
|MFC DLL|||X|X|
|Testovacího projektu|X|X|X|X|
|Konzolové aplikace Win32||X|X|X|
|Projekt Win32||X|X|X|

## <a name="tools"></a>Nástroje

|Nástroj|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Přírůstkové Linkeru (Link.exe)|X|X|X|X|
|Nástroj Údržba programu (Nmake.exe)||X|X|X|
|Lib Generator (Lib.exe)|X|X|X|X|
|Kompilátor prostředků Windows (Rc.exe)|X|X|X|X|
|Prostředek systému Windows pro objekt převaděče (CvtRes.exe)||X|X|X|
|Nástroj Údržba informací (BscMake.exe) procházení|X|X|X|X|
|Název C++ Undecorator (Undname.exe)|X|X|X|X|
|Vypisovač COFF/PE (Dumpbin.exe)|X|X|X|X|
|Editor COFF/PE (Editbin.exe)|X|X|X|X|
|MASM (Ml.exe)|||X|X|
|Spy++|||X|X|
|Errlook –|||X|X|
|AtlTrace|||X|X|
|Devenv.com|||X|X|
|Odvozená pravidla|||X|X|
|Aktualizace projektů VCBuild k MSBuild (VCUpgrade.exe)|X|X|X|X|
|Optimalizace na základě profilu|||X|X|

## <a name="debugging-features"></a>Funkce ladění

|Funkce ladění|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Nativní ladění|X|X|X|X|
|natvis (vizualizace nativní typ)|X|X|X|X|
|Ladění grafiky|X||X|X|
|Spravované ladění||X|X|X|
|Využití GPU|X||X|X|
|Využití paměti|X||X|X|
|Vzdálené ladění|X|X|X|X|
|SQL Debugging|||X|X|
|Statická analýza kódu|Omezené|Omezené|X|X|

## <a name="designers-and-editors"></a>Návrháři a editory

|Návrhář nebo editoru|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Návrhář XAML|X||X|X|
|Editor návrháře stylu CSS|X|X|X|X|
|Návrhář/Editor HTML|X|X|X|X|
|XML Editor|X|X|X|X|
|Editor zdrojového kódu|X|X|X|X|
|Funkce produktivitu: Refaktoring, technologii IntelliSense, formátování kódu C++|X|X|X|X|
|Návrhář formulářů Windows||X|X|X|
|Návrhář dat|||X|X|
|Editor prostředků nativní (soubory .rc)|||X|X|
|Editory prostředků|X|X|X|X|
|Editor modelu|X||X|X|
|Návrhář shaderu|X||X|X|

## <a name="data-features"></a>Datových funkcích

|Funkce dat|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Návrhář dat|||X|X|
|Datové objekty|||X|X|
|Webové služby|||X|X|
|Průzkumník serveru|||X|X|

## <a name="build-and-project-systems"></a>Sestavení a systémy projektu

|Sestavení nebo funkce projektu|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Sestavení příkazového řádku (msbuild.exe.)|X|X|X|X|
|Nativní cílení na více||X|X|X|
|Spravované cílení na více||X|X|X|
|Paralelní sestavení|X|X|X|X|
|Přizpůsobení sestavení|X|X|X|X|
|Rozšiřitelnost stránek vlastností|X|X|X|X|

## <a name="automation-and-extensibility"></a>Automatizace a rozšiřitelnost

|Automatizace a rozšiřitelnost|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Objektové modely rozšíření|||X|X|
|Model kódu|||X|X|
|Model projektu|||X|X|
|Model editoru prostředků|||X|X|
|Průvodce modelu|||X|X|
|Ladicí program objektový Model|||X|X|

## <a name="application-lifecycle-management-tools"></a>Nástroje pro správu životního cyklu aplikací

||||||
|-|-|-|-|-|
|Nástroj|Visual Studio Express pro Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|Testování částí (nativní framework)|X|X|X|X|
|Testování částí (spravované framework)||X|X|X|
|Pokrytí kódu||||X|
|Manuální testování||||X|
|průzkumné testování||||X|
|Správa testovacích případů||||X|
|Kód grafy mapy a závislostí|||jen pro čtení|X|
|Ladění mapy kódu||||X|

## <a name="see-also"></a>Viz také

[Instalace sady Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Co je nového v sadě Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Typy projektů Visual C++](../ide/visual-cpp-project-types.md)<br/>
[SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686)<br/>
