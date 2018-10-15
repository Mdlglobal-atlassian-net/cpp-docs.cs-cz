---
title: IDE a nástroje pro vývoj v jazyce Visual C++ | Dokumentace Microsoftu
description: Integrované vývojové prostředí sady Visual Studio podporuje vývoj v jazyce C++ ve Windows, Linux, Android a iOS pomocí editoru kódu, ladicí program, testovacích architektur, statické analyzátory a jiných programovacích nástrojích.
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, development tools
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31b9c0c8668ec16d84ad84627eb73a0f406eb21e
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328373"
---
# <a name="ide-and-compiler-tools-for-visual-c-development"></a>Integrované vývojové prostředí a kompilačních nástrojů pro vývoj v jazyce Visual C++

Microsoft Visual C++ (MSVC) jako součást sady Visual Studio integrované vývojové prostředí (IDE), sdílí mnoho windows a nástroje společné s jiných jazycích. Mnoho z nich, včetně **Průzkumníka řešení**, editor kódu a ladicí program, jsou popsány v části [Visual Studio IDE](/visualstudio/ide/visual-studio-ide). Často sdílené nástroje nebo okno má mírně odlišnou sadu funkcí jazyka C++ než pro jazyky .NET nebo JavaScript. Několik windows nebo nástroje jsou k dispozici pouze v edicích Visual Studio Professional nebo Visual Studio Enterprise.

Kromě sdílené nástroje v integrovaném vývojovém prostředí sady Visual Studio MSVC má několik nástrojů pro vývoj nativního kódu. Tyto nástroje jsou také uvedené v tomto článku. Seznam, které jsou k dispozici v každé edici sady Visual Studio tools najdete v tématu [nástrojů Visual C++ a funkcí v edicích nástroje Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="create-projects"></a>Vytváření projektů

A *projektu* je v podstatě sadu souborů se zdrojovým kódem a prostředky, jako jsou obrázky nebo data souborů, které jsou integrované do spustitelného souboru. 

Visual Studio 2015 poskytuje podporu pro projekty MSBuild. Můžete si stáhnout rozšíření sady Visual Studio pro jiné systémy sestavení, jako je například Qt nebo CMake.

Visual Studio 2017 poskytuje podporu pro libovolný systém sestavení nebo vlastních sestavovacích nástrojů, které chcete použít s plnou podporou technologie IntelliSense, procházení a ladění:

- **Nástroj MSBuild** je nativní sestavovací systém pro Visual Studio. Když vyberete **souboru** > **nový** > **projektu** z hlavní nabídky, se zobrazí různé druhy MSBuild *šablony projektu*  , které vám pomůžou začít rychlým vývojem různé druhy aplikací v jazyce C++.

   ![Šablony projektů](media/vs2017-new-project.png "Visual Studio 2017 projektu nové dialogové okno")

   Obecně platí abyste používali tyto šablony pro nové projekty Pokud nemáte konkrétní důvod používat CMake nebo jiný systém projektu. Mají některé projekty *průvodce* , který vás provede procesem vytvoření nového projektu. Další informace najdete v tématu [vytváření a správa projekty využívající MSBuild](creating-and-managing-visual-cpp-projects.md).

- **CMake** je platformově univerzální sestavovací systém, který je integrovaný do rozhraní IDE sady Visual Studio, pokud provádíte instalaci vývoj desktopových aplikací pomocí úlohy pro C++. Další informace najdete v tématu [projekty CMake v jazyce Visual C++](cmake-tools-for-visual-cpp.md).
- Všechny ostatní C++ sestavovacího systému, včetně dojde ke ztrátě kolekce souborů, je podporované prostřednictvím **otevřít složku** funkce. Vytvoříte jednoduchou soubory JSON k vyvolání programu sestavení a konfiguraci ladicí relace. Další informace najdete v tématu [projekty otevřít složku v jazyce Visual C++](non-msbuild-projects.md).

## <a name="add-to-source-control"></a>Přidat do správy zdrojového kódu

Správy zdrojového kódu umožňuje práci mezi více vývojářů, izolaci probíhající práce z produkčního kódu a zálohovat zdrojový kód. Visual Studio podporuje Git a [Team Foundation Version Control \(TFVC\) ](/azure/devops/repos/tfvc/) prostřednictvím jeho **Team Exploreru** okna.

![Team Explorer](media/vs2017-team-explorer.png "Team Exploreru sady Visual Studio 2017")

Další informace o Git integrace s úložišti v Azure najdete v tématu [sdílení kódu pomocí sady Visual Studio 2017 a Azure úložišť Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017). Informace o Git integraci s Githubem, najdete v tématu [rozšíření GitHub pro Visual Studio](https://visualstudio.github.com/).

## <a name="create-user-interfaces-with-designers"></a>Vytvoření uživatelského rozhraní pomocí návrháře

Pokud váš program má uživatelské rozhraní, můžete použít návrháře k rychle přidejte do ní ovládací prvky jako tlačítka pole se seznamem a tak dále. Když přetáhněte ovládací prvek z panelu nástrojů okna a umístěte jej na návrhovou plochu, Visual Studio vygeneruje zdroje a kód vyžaduje, aby to fungovalo. Potom napíšete kód upravit vzhled a chování.

![Návrháře a nástrojů](media/vs2017-toolbox-designer.png "návrháře a nástrojů sady Visual Studio 2017")

Další informace o navrhování uživatelského rozhraní pro aplikace univerzální platformy Windows, naleznete v tématu [návrhu a uživatelské rozhraní](https://developer.microsoft.com/windows/design).

Další informace o vytváření uživatelského rozhraní pro aplikaci knihovny MFC naleznete v tématu [desktopových aplikací knihovny MFC](../mfc/mfc-desktop-applications.md). Informace o aplikacích Win32 Windows najdete v tématu [desktopových aplikací Windows](../windows/windows-desktop-applications-cpp.md).

## <a name="write-code"></a>Psaní kódu

Když vytvoříte projekt, všechny soubory projektu jsou zobrazeny v **Průzkumníka řešení** okna. (A *řešení* je logický kontejner pro jeden nebo více souvisejících projektů.) Když kliknete na soubor .h a .cpp v **Průzkumníka řešení**, soubor se otevře v editoru kódu. 

![Průzkumník řešení a editor kódu](media/vs2017-solution-explorer-code-editor.png "editoru Průzkumníku řešení Visual Studio 2017 a kódu")

Editor kódu je specializované textový procesor pro zdrojový kód jazyka C++. Barevně ho označí klíčová slova jazyka, názvu proměnné a metody a další prvky kódu změňte kód čitelnější a lépe pochopit.

Další informace najdete v tématu [psaní a refaktoring kódu](writing-and-refactoring-code-cpp.md).

## <a name="add-and-edit-resources"></a>Přidat a upravit prostředky

Termín *prostředků* obsahují položky, jako je například dialogová okna, ikony, obrázky, lokalizovatelných řetězců, úvodní obrazovky, databázové připojovací řetězce nebo libovolná data, které chcete zahrnout do spustitelného souboru.

Další informace o přidávání a úprava prostředků v nativních desktopových projektů C++, naleznete v tématu [práce se zdrojovými soubory](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Sestavení (kompilace a odkaz)

Zvolte **sestavení** > **sestavit řešení** v nabídce panelu, nebo zadejte kombinaci kláves Ctrl + Shift + B ke kompilaci a odkaz projekt. Chyby a upozornění sestavení jsou uvedeny v seznamu chyb (Ctrl +\\, E). **Výstup** okno (Alt + 2) zobrazí informace o procesu sestavení.

![Výstup okna a seznamu chyb](media/vs2017-output-error-list.png "okně Výstup Visual Studio 2017 a seznamu chyb") Další informace o konfiguracích MSBuild naleznete v tématu [práce s vlastnostmi projektu](working-with-project-properties.md) a [Sestavení projektů C++ v sadě Visual Studio](building-cpp-projects-in-visual-studio.md).

Můžete také použít kompilátoru (cl.exe) a mnoho dalších související s buildem samostatných nástrojů, například NMAKE a LIB přímo z příkazového řádku. Další informace najdete v tématu [kódu sestavení C/C++ v příkazovém řádku](../build/building-on-the-command-line.md) a [Reference sestavení C/C++](../build/reference/c-cpp-building-reference.md).

## <a name="debug"></a>Ladit

Můžete spustit ladění stisknutím kombinace kláves **F5**. Pozastaví provádění na všechny zarážky, které jste nastavili. Můžete také krokovat kód jeden řádek v čase, zobrazení hodnot proměnných nebo registrů a dokonce i v některých případech provádět změny v kódu a pokračovat v ladění bez opětovné kompilace. Následující obrázek znázorňuje relaci ladění, ve kterém zastavením spuštění na zarážce. Hodnoty datových členů struktury jsou viditelné v **okna kukátka**.

![Ladicí relace](media/vs2017-debug-watch.png "relaci ladění Visual Studio 2017")

Další informace najdete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="test"></a>Test

Visual Studio obsahuje rozhraní pro testování jednotek native C++ a C + +/ CLI. Boost.Test, Google Test a CTest jsou také podporovány. Spuštění testů z **Průzkumník testů** okno:

![Průzkumník testů](media/cpp-test-explorer-passed.png "Visual Studio 2017 Test Explorer")

Další informace najdete v tématu [ověřování kódu pomocí testování částí](/visualstudio/test/unit-test-your-code) a [zápis testů jednotek pro C/C++ v sadě Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp).

## <a name="analyze"></a>Analyzovat

Visual Studio obsahuje analytické nástroje statického kódu, které dokáží detekovat potenciální problémy ve zdrojovém kódu. Mezi tyto nástroje patří implementace [podle dokumentu C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) pravidla tyto moduly pro kontrolu. Další informace najdete v tématu [Code analysis for C/C++ – přehled](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

## <a name="deploy-completed-applications"></a>Nasazení dokončené aplikace

Tradiční desktopové aplikace a aplikací pro UWP můžete nasadit pro zákazníky přes Microsoft Store. Nasazení CRT zpracovává automaticky na pozadí. Další informace najdete v tématu [Windows publikovat aplikace a hry](/windows/uwp/publish/).

Můžete taky nasadit nativní C++ desktop do jiného počítače pro další informace najdete v článku [nasazení desktopových aplikací](deploying-native-desktop-applications-visual-cpp.md).

Další informace o nasazení a C + +/ CLI programu, najdete v článku [Průvodce nasazením pro vývojáře](/dotnet/framework/deployment/deployment-guide-for-developers),

## <a name="related-articles"></a>Související články

|||
|-|-|
|[Nástroje a funkce Visual C++ v různých edicích sady Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md)|Ukazuje, jaké funkce jsou k dispozici v různých edicích sady Visual Studio.|
|[Vytvářet a spravovat projekty využívající MSBuild](creating-and-managing-visual-cpp-projects.md)|Poskytuje přehled o projekty využívající C++ MSBuild v sadě Visual Studio a odkazy na další články, které popisují, jak vytvořit a spravovat je.|
|[Projekty CMake v jazyce Visual C++](cmake-tools-for-visual-cpp.md).|Popisuje, jak sestavit CMake nebo jiné projekty jiné než MSBuild v jazyce Visual C++.|
|[Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)|Popisuje, jak vytvářet projekty C++.|
|[Nasazení aplikací klasické pracovní plochy](deploying-native-desktop-applications-visual-cpp.md)|Poskytuje přehled o nasazení aplikací v jazyce C++ a odkazy na další články, které popisují nasazení podrobně.|
|[Průvodce přenosem a upgradem Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)|Podrobné informace o tom, jak upgradovat aplikací v jazyce C++, které byly vytvořeny v dřívějších verzích sady Visual Studio a postupu při migraci aplikací, které byly vytvořeny pomocí jiných nástrojů než Visual Studio.|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Popisuje klíčové funkce jazyka Visual C++ v systému Visual Studio a odkazy na zbytek dokumentace k jazyku Visual C++.|
