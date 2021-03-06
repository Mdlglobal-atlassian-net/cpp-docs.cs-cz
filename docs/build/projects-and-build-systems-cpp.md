---
title: Projekty C/C++ a systémy sestavení v aplikaci Visual Studio
ms.description: Use Visual Studio to compile and build C++ projects for Windows, ARM or Linux based on any project system.
ms.date: 07/17/2019
helpviewer_keywords:
- builds [C++]
- C++ projects, building
- projects [C++], building
- builds [C++], options
- C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
ms.topic: overview
ms.openlocfilehash: 3d82ac4569e06a4472047a79da60032ad2db43ca
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078475"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>Projekty C/C++ a systémy sestavení v aplikaci Visual Studio

Sadu Visual Studio můžete použít k úpravám, kompilování a sestavení jakékoli základny kódu C++ s plnou podporou technologie IntelliSense bez nutnosti převádět tento kód do projektu sady Visual Studio nebo kompilovat pomocí sady nástrojů MSVC. Například můžete upravit projekt CMake pro různé platformy v sadě Visual Studio na počítači s Windows a potom ho zkompilovat pro Linux pomocí g + + na vzdáleném počítači se systémem Linux.

## <a name="c-compilation"></a>Kompilace C++

Pro *sestavení* programu C++ znamená pro zkompilování zdrojového kódu z jednoho nebo více souborů a následné propojení těchto souborů do spustitelného souboru (. exe), knihovny dynamického načtení (. dll) nebo statické knihovny (. lib).

Základní kompilace C++ zahrnuje tři hlavní kroky:

- Preprocesor jazyka C++ transformuje všechny #directives a definice maker v každém zdrojovém souboru. Tím se vytvoří *jednotka překladu*.
- Kompilátor jazyka C++ zkompiluje každou jednotku překladu do souborů objektů (. obj), přičemž bylo nastaveno použití všech možností kompilátoru.
- *Linker* sloučí soubory objektů do jediného spustitelného souboru, přičemž použije Možnosti linkeru, které byly nastaveny.

## <a name="the-msvc-toolset"></a>Sada nástrojů MSVC

Kompilátor jazyka Microsoft C++, linker, standardní knihovny a související nástroje tvoří sadu nástrojů kompilátoru MSVC (označované také jako sada nástrojů nebo "Build Tools"). Ty jsou součástí sady Visual Studio. Můžete si také stáhnout a používat sadu nástrojů jako samostatný balíček zdarma z [umístění pro stahování nástrojů sestavení pro Visual Studio 2019](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019).

Jednoduché programy můžete sestavit vyvoláním kompilátoru MSVC (CL. exe) přímo z příkazového řádku. Následující příkaz přijme jeden soubor zdrojového kódu a vyvolá CL. exe pro sestavení spustitelného souboru s názvem *Hello. exe*:

```cmd
cl /EHsc hello.cpp
```

Všimněte si, že v tomto příkladu kompilátor (CL. exe) automaticky vyvolá preprocesor jazyka C++ a linker, aby vytvořil finální výstupní soubor.  Další informace najdete v tématu [sestavování na příkazovém řádku](building-on-the-command-line.md).

## <a name="build-systems-and-projects"></a>Systémy a projekty pro sestavování

Většina reálných programů používá určitý druh *systému sestavení* ke správě složitosti kompilace více zdrojových souborů pro více konfigurací (tj. ladění vs. Release), více platforem (x86, x64, ARM atd.), vlastních kroků sestavení a dokonce i více spustitelných souborů, které musí být zkompilovány v určitém pořadí. Nastavení provedete v konfiguračních souborech sestavení a systém sestavení přijímá tento soubor jako vstup před tím, než vyvolá kompilátor. Sada zdrojových souborů a souborů konfigurace sestavení potřebných k sestavení spustitelného souboru se nazývá *projekt*.

V následujícím seznamu jsou uvedeny různé možnosti pro projekty sady Visual Studio – C++:

- pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio vytvořte projekt sady Visual Studio a nakonfigurujte ho pomocí stránek vlastností. Projekty sady Visual Studio vytváří programy, které běží v systému Windows. Přehled naleznete v tématu [kompilace a sestavování](/visualstudio/ide/compiling-and-building-in-visual-studio) v dokumentaci k sadě Visual Studio.

- Otevřete složku, která obsahuje soubor CMakeLists. txt. Podpora CMake je integrovaná do sady Visual Studio. Pomocí integrovaného vývojového prostředí (IDE) můžete upravovat, testovat a ladit bez úprav souborů CMake jakýmkoli způsobem. To vám umožní pracovat ve stejném projektu CMake jako jiní uživatelé, kteří mohou používat různé editory. CMake je doporučený postup pro vývoj pro různé platformy. Další informace najdete v tématu [projekty cmake](cmake-projects-in-visual-studio.md).

- Otevřete volnou složku zdrojových souborů bez souboru projektu. Visual Studio bude k sestavování souborů používat heuristické metody. Toto je snadný způsob, jak zkompilovat a spustit malé konzolové aplikace. Další informace naleznete v tématu [Otevřít složku projekty](open-folder-projects-cpp.md).

- Otevřete složku, která obsahuje soubor pravidel nebo jakýkoli jiný konfigurační soubor systému sestavení. Aplikaci Visual Studio můžete nakonfigurovat tak, aby vyvolala libovolné příkazy sestavení přidáním souborů JSON do složky. Další informace naleznete v tématu [Otevřít složku projekty](open-folder-projects-cpp.md).

- Otevřete soubor pravidel systému Windows v aplikaci Visual Studio. Další informace najdete v tématu [Referenční příručka](reference/nmake-reference.md)k nástroji NMAKE.

## <a name="msbuild-from-the-command-line"></a>MSBuild z příkazového řádku

Nástroj MSBuild můžete vyvolat z příkazového řádku předáním souboru. vcxproj spolu s parametry příkazového řádku. Tento přístup vyžaduje dobrý význam nástroje MSBuild a je doporučen pouze v případě nezbytně nutného postupu. Další informace najdete v tématu [MSBuild](msbuild-visual-cpp.md).

## <a name="in-this-section"></a>V tomto oddílu

[Projekty sady Visual Studio](creating-and-managing-visual-cpp-projects.md) Jak vytvářet, konfigurovat a sestavovat projekty C++ v aplikaci Visual Studio pomocí svého nativního sestavovacího systému (MSBuild).

[Projekty cmake](cmake-projects-in-visual-studio.md) Jak kódovat, sestavovat a nasazovat projekty CMake v sadě Visual Studio.

[Projekty otevřené složky](open-folder-projects-cpp.md) Jak používat Visual Studio k vytváření kódu, sestavovat a nasazovat projekty C++ na základě libovolného systému sestavení nebo bez systému sestavení. Vůbec.

[Sestavení](release-builds.md) vydaných verzí Postup vytvoření a řešení potíží optimalizovaných sestavení vydaných verzí pro nasazení koncovým uživatelům.

[Použití sady nástrojů MSVC z příkazového řádku](building-on-the-command-line.md)<br/>
Popisuje, jak použít kompilátor C/C++ a sestavit nástroje přímo z příkazového řádku namísto použití integrovaného vývojového prostředí (IDE) sady Visual Studio.

[Vytváření knihoven DLL v aplikaci Visual Studio](dlls-in-visual-cpp.md) Jak vytvářet, ladit a nasazovat knihovny DLL jazyka C/C++ (sdílené knihovny) v aplikaci Visual Studio.

[Návod: vytvoření a použití statické knihovny](walkthrough-creating-and-using-a-static-library-cpp.md) Postup vytvoření binárního souboru. lib.

[Sestavování izolovaných aplikací C/C++ a souběžných sestavení](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md) Popisuje model nasazení pro desktopové aplikace pro Windows na základě nápadu izolovaných aplikací a souběžných sestavení.

[Konfigurace projektů C++ pro 64 cíle platformy x64](configuring-programs-for-64-bit-visual-cpp.md) Jak cílit na 64 hardware x64 pomocí nástrojů pro sestavení MSVC.

[Konfigurace projektů C++ pro procesory ARM](configuring-programs-for-arm-processors-visual-cpp.md) Jak používat nástroje pro sestavení MSVC k cílení na hardware ARM

[Optimalizace kódu](optimizing-your-code.md) Způsob optimalizace kódu různými způsoby, včetně optimalizace s asistencí programu.

[Konfigurace programů pro systém Windows XP](configuring-programs-for-windows-xp.md) Postup cílení na systém Windows XP pomocí nástrojů pro sestavení MSVC.

[Odkaz sestavení C/C++](reference/c-cpp-building-reference.md)<br/>
Obsahuje odkazy na referenční články o sestavování programu v jazyce C++, možnostech kompilátoru a linkeru a různých nástrojích sestavení.
