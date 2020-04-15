---
title: Přehled vývoje v jazyce C++ v sadě Visual Studio
description: Visual Studio IDE podporuje vývoj Jazyka C++ v systémech Windows, Linux, Android a iOS s editorem kódu, ladicím programem, testovacími rámci, statickými analyzátory a dalšími programovacími nástroji.
ms.date: 12/02/2019
helpviewer_keywords:
- Visual C++, development tools
author: corob-msft
ms.author: corob
ms.openlocfilehash: 4e04e189b44fe61759a9422139d856ab8a09f201
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "77415714"
---
# <a name="overview-of-c-development-in-visual-studio"></a>Přehled vývoje v jazyce C++ v sadě Visual Studio

Jako součást integrovaného vývojového prostředí sady Visual Studio (IDE) sdílí microsoft c++ (MSVC) mnoho oken a nástrojů společně s jinými jazyky. Mnoho z nich, včetně **Průzkumníka řešení**, editoru kódu a ladicího programu, jsou dokumentovány v rámci [rozhraní IDE sady Visual Studio](/visualstudio/get-started/visual-studio-ide). Sdílený nástroj nebo okno má často mírně odlišnou sadu funkcí pro jazyk C++ než pro jiné jazyky. Několik oken nebo nástrojů je k dispozici pouze v edicích Visual Studio Professional nebo Visual Studio Enterprise.

Kromě sdílených nástrojů v IDE sady Visual Studio má MSVC několik nástrojů speciálně pro vývoj nativního kódu. Tyto nástroje jsou také uvedeny v tomto článku. Seznam nástrojů, které jsou k dispozici v každé edici sady Visual Studio, najdete [v tématu Nástroje a funkce jazyka C++ v edicích Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="create-projects"></a>Vytváření projektů

*Projekt* je v podstatě sada souborů zdrojového kódu a zdrojů, jako jsou obrázky nebo datové soubory, které jsou integrovány do spustitelného programu nebo knihovny.

Visual Studio poskytuje podporu pro všechny projektové systémové nebo vlastní nástroje sestavení, které chcete použít, s plnou podporou pro IntelliSense, procházení a ladění:

- **MSBuild** je nativní projektový systém pro Visual Studio. Když vyberete **Soubor** > **nový** > **projekt** z hlavní nabídky, uvidíte mnoho druhů šablon *projektu* MSBuild, které vám pomohou začít rychle vyvíjet různé druhy aplikací jazyka C++.

   ::: moniker range="vs-2019"

   ![Nové šablony projektů](../build/media/mathclient-project-name-2019.png "Visual Studio 2019 Nový dialog projektu")

   ::: moniker-end

   ::: moniker range="<=vs-2017"

   ![Šablony projektů](media/vs2017-new-project.png "Visual Studio 2017 Nový dialog projektu")

   ::: moniker-end

   Obecně byste měli použít tyto šablony pro nové projekty, pokud nepoužíváte existující projekty CMake nebo nepoužíváte jiný systém projektu. Další informace naleznete v [tématu Vytváření a správa projektů založených na msbuild](../build/creating-and-managing-visual-cpp-projects.md).

- **CMake** je systém sestavení napříč platformami, který je integrován do integrovaného prostředí Visual Studio při instalaci vývoje plochy s úlohami jazyka C++. Šablonu projektu CMake můžete použít pro nové projekty nebo jednoduše otevřít složku se souborem CMakeLists.txt. Další informace naleznete [v tématu CMake projekty v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md).

- Všechny ostatní c++ sestavení systému, včetně volné kolekce souborů, je podporován prostřednictvím **funkce Otevřít složku.** Vytvoření jednoduchých souborů JSON pro vyvolání programu sestavení a konfiguraci relací ladění. Další informace naleznete v tématu [Open Folder projects for C++](../build/open-folder-projects-cpp.md).

## <a name="add-to-source-control"></a>Přidat do správy zdrojového kódu

Správa zdrojového kódu umožňuje koordinovat práci mezi více vývojáři, izolovat probíhající práci z produkčního kódu a zálohovat zdrojový kód. Visual Studio podporuje Git a [Team Foundation Version Control \(TFVC\) ](/azure/devops/repos/tfvc/) prostřednictvím okna **Průzkumníka týmu.**

::: moniker range="vs-2019"

![Team Explorer](media/vs2019-team-explorer.png "Průzkumník týmu Visual Studio 2017")

::: moniker-end

::: moniker range="<=vs-2017"

![Team Explorer](media/vs2017-team-explorer.png "Průzkumník týmu Visual Studio 2017")

::: moniker-end

Další informace o integraci Gitu s úložišti v Azure najdete v [tématu Sdílení kódu s Visual Studio 2017 a Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017). Informace o integraci Gitu s GitHubem najdete v tématu [GitHub Extension for Visual Studio](https://visualstudio.github.com/).

## <a name="obtain-libraries"></a>Získat knihovny

Pomocí správce balíčků [vcpkg](../build/vcpkg.md) získáte a nainstalujte knihovny třetích stran. V katalogu je aktuálně k dispozici více než 900 knihoven s otevřeným zdrojovým kódem.

## <a name="create-user-interfaces-with-designers"></a>Vytváření uživatelských rozhraní s návrháři

Pokud má váš program uživatelské rozhraní, můžete pomocí návrháře rychle naplnit ovládací prvky, jako jsou tlačítka, seznamy a tak dále. Když přetáhnete ovládací prvek z okna panelu nástrojů a přetáhněte jej na plochu návrhu, Visual Studio generuje prostředky a kód potřebný k tomu, aby vše fungovalo. Potom napište kód přizpůsobit vzhled a chování.

![Návrhář a sada nástrojů](media/vs2017-toolbox-designer.png "Sada nástrojů a návrhář visual studia 2017")

Další informace o návrhu uživatelského rozhraní pro aplikaci univerzální platformy Windows naleznete v [tématu Návrh a uživatelské rozhraní](https://developer.microsoft.com/windows/design).

Další informace o vytvoření uživatelského rozhraní pro aplikaci knihovny MFC naleznete v [tématu MFC Desktop Applications](../mfc/mfc-desktop-applications.md). Informace o programech systému Windows systému Win32 naleznete v [tématu Windows Desktop Applications](../windows/windows-desktop-applications-cpp.md).

## <a name="write-code"></a>Psaní kódu

Po vytvoření projektu se všechny soubory projektu zobrazí v okně **Průzkumník řešení.** (Řešení *solution* je logický kontejner pro jeden nebo více souvisejících projektů.) Když kliknete na soubor .h nebo CPP v **Průzkumníku řešení**, soubor se otevře v editoru kódu.

![Průzkumník řešení a editor kódu](media/vs2017-solution-explorer-code-editor.png "Průzkumník řešení Visual Studia 2017 a editor kódu")

Editor kódu je specializovaný textový procesor pro zdrojový kód jazyka C++. Je barva-kódy jazyk klíčová slova, metody a názvy proměnných, a další prvky kódu, aby se kód čitelnější a srozumitelnější. Poskytuje také nástroje pro refaktoring kódu, navigaci mezi různými soubory a pochopení struktury kódu. Další informace naleznete v [tématu Psaní a refaktoring kódu](../ide/writing-and-refactoring-code-cpp.md).

## <a name="add-and-edit-resources"></a>Přidání a úprava zdrojů

Program systému Windows nebo dll obvykle obsahuje některé *prostředky*, například dialogová okna, ikony, obrázky, lokalizovatelné řetězce, úvodní obrazovky, připojovací řetězce databáze nebo libovolná data. Visual Studio obsahuje nástroje pro přidávání a úpravy prostředků. Další informace naleznete v [tématu Práce se soubory prostředků](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Sestavení (kompilace a propojení)

Na řádku nabídek zvolte **Sestavit** > **řešení sestavení** nebo zadejte kombinaci kláves **Ctrl+Shift+B** pro kompilaci a propojení projektu. Chyby sestavení a upozornění jsou hlášeny v seznamu chyb (**Ctrl+\\, E**). **Okno Výstup** (**Alt+2**) zobrazuje informace o procesu sestavení.

![Okno výstupu a seznam chyb](media/vs2017-output-error-list.png "Okno Výstupu visual studia 2017 a seznam chyb")

Další informace o konfiguraci sestavení naleznete v [tématu Práce s vlastnostmi a](../build/working-with-project-properties.md) projekty projektu [a sestavovacími systémy](../build/projects-and-build-systems-cpp.md).

Kompilátor (cl.exe) a mnoho dalších samostatných nástrojů souvisejících s sestavením, jako je NMAKE a LIB, můžete také použít přímo z příkazového řádku. Další informace naleznete v [tématu Sestavení kódu C/C++ na příkazovém řádku](../build/building-on-the-command-line.md) a [c/c++ odkaz na budovu](../build/reference/c-cpp-building-reference.md).

## <a name="debug"></a>Ladit

Ladění můžete spustit stisknutím **klávesy F5**. Spuštění se pozastaví u všech nastavených zarážek (stisknutím **klávesy F9).** Můžete také krokovat kód po jednom řádku **(F10**), zobrazit hodnoty proměnných nebo registrů a dokonce i v některých případech provádět změny v kódu a pokračovat v ladění bez opětovné kompilace. Následující obrázek znázorňuje relaci ladění, ve které je zastaveno provádění na zarážky. Hodnoty členů datové struktury jsou viditelné v **okně kukátka**.

![Relace ladění](media/vs2017-debug-watch.png "Relace ladění sady Visual Studio 2017")

Další informace naleznete [v tématu Ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="test"></a>Test

Visual Studio obsahuje Microsoft Unit Test Framework pro C++, stejně jako podporu boost.test, Google Test a CTest. Spuštění testů z okna **Průzkumníka testů:**

![Průzkumník testů](media/cpp-test-explorer-passed.png "Průzkumník testů visual studia 2017")

Další informace naleznete [v tématu Ověření kódu pomocí testů částí](/visualstudio/test/unit-test-your-code) a testování [jednotek zápisu pro C/C++ v sadě Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp).

## <a name="analyze"></a>Analýza

Visual Studio obsahuje nástroje pro analýzu statického kódu, které mohou zjistit potenciální problémy ve zdrojovém kódu. Tyto nástroje zahrnují implementaci kontrolorů základních [pravidel jazyka C++.](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) Další informace naleznete v [tématu Analýza kódu pro přehled C/C++](/cpp/code-quality/code-analysis-for-c-cpp-overview).

## <a name="deploy-completed-applications"></a>Nasazení dokončených aplikací

Zákazníkům můžete nasadit tradiční desktopové aplikace i aplikace UPW prostřednictvím Microsoft Storu. Nasazení CRT je zpracována automaticky na pozadí. Další informace naleznete v [tématu Publish Windows apps and games](/windows/uwp/publish/).

Můžete také nasadit nativní pracovní plochu jazyka C++ do jiného počítače. Další informace naleznete v [tématu Nasazení desktopových aplikací](../windows/deploying-native-desktop-applications-visual-cpp.md).

Další informace o nasazení programu C++/CLI naleznete v [Příručce pro nasazení pro vývojáře](/dotnet/framework/deployment/deployment-guide-for-developers),

## <a name="next-steps"></a>Další kroky

Prozkoumejte visual studio dále podle následujících spolu s jedním z těchto úvodních článků:

> [!div class="nextstepaction"]
> [Naučte se používat editor kódu](/visualstudio/get-started/tutorial-editor)

> [!div class="nextstepaction"]
> [Další informace o projektech a řešeních](/visualstudio/get-started/tutorial-projects-solutions)
