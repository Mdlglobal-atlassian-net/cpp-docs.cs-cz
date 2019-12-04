---
title: Přehled vývoje v jazyce C++ v sadě Visual Studio
description: Rozhraní IDE sady Visual Studio C++ podporuje vývoj v systémech Windows, Linux, Android a iOS pomocí editoru kódu, ladicího programu, testovacích architektur, statických analyzátorů a dalších programovacích nástrojů.
ms.date: 12/02/2019
helpviewer_keywords:
- Visual C++, development tools
author: corob-msft
ms.author: corob
ms.openlocfilehash: d72ea2ab4fa83259152101b357c6b2b69e74c723
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810621"
---
# <a name="overview-of-c-development-in-visual-studio"></a>Přehled vývoje v jazyce C++ v sadě Visual Studio

V rámci integrovaného vývojového prostředí (IDE) sady Visual Studio sdílí C++ Microsoft (MSVC) mnoho oken a nástrojů, které jsou společné pro jiné jazyky. Mnohé z těchto prvků, včetně **Průzkumník řešení**, editoru kódu a ladicího programu, jsou zdokumentovány v rámci sady [Visual Studio IDE](/visualstudio/get-started/visual-studio-ide). Sdílený nástroj nebo okno má často mírně odlišnou sadu funkcí C++ než pro jiné jazyky. Několik oken nebo nástrojů je k dispozici pouze v edicích Visual Studio Professional nebo Visual Studio Enterprise.

Kromě sdílených nástrojů v integrovaném vývojovém prostředí sady Visual Studio má MSVC několik nástrojů konkrétně pro vývoj nativních kódu. Tyto nástroje jsou také uvedeny v tomto článku. Seznam nástrojů, které jsou k dispozici v jednotlivých edicích aplikace Visual Studio, naleznete v tématu [ C++ nástroje a funkce v edicích sady Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="create-projects"></a>vytvářet projekty,

*Projekt* je v podstatě sada souborů zdrojového kódu a prostředků, jako jsou obrázky nebo datové soubory, které jsou integrovány do spustitelného programu nebo knihovny.

Visual Studio poskytuje podporu pro všechny projektové systémy nebo nástroje pro vlastní sestavení, které chcete použít, a plnou podporu pro technologii IntelliSense, procházení a ladění:

- **MSBuild** je nativní projektový systém pro Visual Studio. Když vyberete **soubor** > **Nový** > **projekt** z hlavní nabídky, uvidíte spoustu druhů *šablon projektů* MSBuild, které vám pomohou začít rychle vyvíjet různé druhy C++ aplikací.

   ::: moniker range="vs-2019"

   ![Nové šablony projektů](../build/media/mathclient-project-name-2019.png "Visual Studio 2019 – dialog nového projektu")

   ::: moniker-end

   ::: moniker range="<=vs-2017"

   ![Šablony projektů](media/vs2017-new-project.png "Visual Studio 2017 – dialog nového projektu")

   ::: moniker-end

   Obecně platí, že byste měli použít tyto šablony pro nové projekty, pokud nepoužíváte existující projekty CMake nebo používáte jiný systém projektu. Další informace najdete v tématu [vytváření a správa projektů založených na msbuildu](../build/creating-and-managing-visual-cpp-projects.md).

- **Cmake** je systém sestavení pro různé platformy, který je integrovaný do integrovaného vývojového prostředí sady Visual Studio, když instalujete C++ desktopový vývoj s využitím úlohy. Šablonu projektu CMake můžete použít pro nové projekty nebo jednoduše otevřít složku se souborem CMakeLists. txt. Další informace najdete v tématu [projekty cmake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md).

- Všechny ostatní C++ systémy sestavení, včetně volné kolekce souborů, jsou podporovány prostřednictvím funkce **Otevřít složku** . Vytvoříte jednoduché soubory JSON pro vyvolání programu sestavení a nakonfigurujete relace ladění. Další informace naleznete v tématu [Otevřít složku projekty pro C++ ](../build/open-folder-projects-cpp.md).

## <a name="add-to-source-control"></a>Přidat do správy zdrojového kódu

Správa zdrojového kódu umožňuje koordinovat práci mezi několika vývojáři, izolovat probíhající práci z produkčního kódu a zálohovat zdrojový kód. Visual Studio podporuje Git a [Správa verzí Team Foundation \(TFVC\)](/azure/devops/repos/tfvc/) prostřednictvím svého **Team Explorer** okna. 

::: moniker range="vs-2019"

![Team Explorer](media/vs2019-team-explorer.png "Visual Studio 2017 Team Explorer")

::: moniker-end

::: moniker range="<=vs-2017"

![Team Explorer](media/vs2017-team-explorer.png "Visual Studio 2017 Team Explorer")

::: moniker-end

Další informace o integraci Git s úložištěmi v Azure najdete v tématu [sdílení kódu pomocí sady Visual Studio 2017 a Azure Repos Gitu](/azure/devops/repos/git/share-your-code-in-git-vs-2017). Informace o integraci Git s GitHubem najdete v tématu [rozšíření GitHub pro Visual Studio](https://visualstudio.github.com/).

## <a name="obtain-libraries"></a>Získat knihovny

Pomocí Správce balíčků [vcpkg](../build/vcpkg.md) můžete získat a nainstalovat knihovny třetích stran. Přes 900 open source knihovny jsou aktuálně k dispozici v katalogu.

## <a name="create-user-interfaces-with-designers"></a>Vytváření uživatelských rozhraní pomocí návrhářů

Pokud má program uživatelské rozhraní, můžete použít návrháře k jeho rychlému naplnění ovládacími prvky, jako jsou tlačítka, seznamy a tak dále. Když přetáhnete ovládací prvek z okna panelu nástrojů a umístíte ho na návrhovou plochu, Visual Studio vygeneruje prostředky a kód potřebný k tomu, aby všechno fungovalo. Potom napíšete kód pro přizpůsobení vzhledu a chování.

![Návrhář a sada nástrojů](media/vs2017-toolbox-designer.png "Sada nástrojů a Návrhář sady Visual Studio 2017")

Další informace o návrhu uživatelského rozhraní pro aplikaci Univerzální platforma Windows najdete v tématu [design a UI](https://developer.microsoft.com/windows/design).

Další informace o vytvoření uživatelského rozhraní pro aplikaci knihovny MFC naleznete v tématu [MFC Desktop Applications](../mfc/mfc-desktop-applications.md). Informace o programech Win32 systému Windows najdete v tématu [desktopové aplikace systému Windows](../windows/windows-desktop-applications-cpp.md).

## <a name="write-code"></a>Psaní kódu

Po vytvoření projektu jsou všechny soubory projektu zobrazeny v okně **Průzkumník řešení** . ( *Řešení* je logický kontejner pro jeden nebo více souvisejících projektů.) Když kliknete na soubor. h nebo. cpp v **Průzkumník řešení**, soubor se otevře v editoru kódu.

![Průzkumník řešení a Editor kódu](media/vs2017-solution-explorer-code-editor.png "Visual Studio 2017 Průzkumník řešení a Editor kódu")

Editor kódu je specializovaný textový procesor pro C++ zdrojový kód. Barevná klíčová slova jazyka, metody a názvy proměnných a další prvky kódu, aby byl kód čitelnější a snazší pochopit. Poskytuje také nástroje pro refaktoring kódu, navigaci mezi různými soubory a porozumění způsobu strukturování kódu. Další informace najdete v tématu [zápis a refaktoring kódu](../ide/writing-and-refactoring-code-cpp.md).

## <a name="add-and-edit-resources"></a>Přidání a úprava prostředků

Program nebo knihovna DLL systému Windows obvykle zahrnuje některé *prostředky*, jako jsou dialogy, ikony, obrázky, lokalizovatelné řetězce, úvodní obrazovky, databázové připojovací řetězce nebo libovolná data. Visual Studio obsahuje nástroje pro přidávání a úpravu prostředků. Další informace najdete v tématu [práce se soubory prostředků](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Sestavení (kompilace a propojení)

Na panelu nabídek vyberte **sestavení** **řešení** sestavení > nebo zadejte kombinaci kláves **CTRL + SHIFT + B** pro zkompilování a propojení projektu. Chyby a varování sestavení jsou hlášeny v Seznam chyb (**CTRL +\\, E**). Okno **výstup** (**ALT + 2**) zobrazuje informace o procesu sestavení.

![okno Výstup a Seznam chyb](media/vs2017-output-error-list.png "Okno výstupu sady Visual Studio 2017 a Seznam chyb")

Další informace o konfiguraci sestavení naleznete v tématu [práce s vlastnostmi projektu](../build/working-with-project-properties.md) a [projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md).

Můžete také použít kompilátor (CL. exe) a mnoho dalších samostatných nástrojů souvisejících s sestavením, jako je například NMAKE a LIB přímo z příkazového řádku. Další informace naleznete v tématu [sestavováníC++ c/Code na příkazovém řádku a v](../build/building-on-the-command-line.md) tématu [C/C++ Building reference](../build/reference/c-cpp-building-reference.md).

## <a name="debug"></a>Ladit

Ladění můžete spustit stisknutím klávesy **F5**. Spuštění se pozastaví u všech zarážek, které jste nastavili (stisknutím klávesy **F9**). Můžete také krokovat kód jedním řádkem v čase (**F10**), zobrazit hodnoty proměnných nebo registrů a dokonce i v některých případech provádět změny v kódu a pokračovat v ladění bez nutnosti opětovné kompilace. Následující ilustrace znázorňuje relaci ladění, ve které je spuštění zastaveno na zarážce. Hodnoty členů struktury dat jsou viditelné v **okně kukátko**.

![Relace ladění](media/vs2017-debug-watch.png "Relace ladění sady Visual Studio 2017")

Další informace najdete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="test"></a>Test

Sada Visual Studio obsahuje rozhraní pro testování částí společnosti C++Microsoft pro a také podporu pro zvýšení. Test, Google test a CTest. Spusťte testy z okna **Průzkumníka testů** :

![Průzkumník testů](media/cpp-test-explorer-passed.png "Průzkumník testů sady Visual Studio 2017")

Další informace naleznete v tématu [ověřování kódu pomocí testů jednotek](/visualstudio/test/unit-test-your-code) a [zápis testů jednotek pro C/C++ v aplikaci Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp).

## <a name="analyze"></a>Analyzovat

Visual Studio obsahuje nástroje pro analýzu statického kódu, které mohou detekovat potenciální problémy ve zdrojovém kódu. Tyto nástroje zahrnují implementaci kontrol [ C++ základních pravidel pokynů](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) . Další informace naleznete v tématu [Analýza kódu pro C/C++ Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

## <a name="deploy-completed-applications"></a>Nasazení dokončených aplikací

Pomocí Microsoft Store můžete do zákazníků nasadit tradiční aplikace klasické pracovní plochy i aplikace UWP. Nasazení CRT se zpracovává automaticky na pozadí. Další informace najdete v tématu [publikování aplikací a her pro Windows](/windows/uwp/publish/).

Nativní C++ plochu můžete nasadit i na jiný počítač. Další informace najdete v tématu [nasazení desktopových aplikací](../windows/deploying-native-desktop-applications-visual-cpp.md).

Další informace o nasazování programu C++/CLI najdete v tématu [Průvodce nasazením pro vývojáře](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="next-steps"></a>Další kroky

Prozkoumejte další Visual Studio na základě společně s některou z těchto úvodní články:

> [!div class="nextstepaction"]
> [Naučte se používat editor kódu.](/visualstudio/get-started/tutorial-editor)

> [!div class="nextstepaction"]
> [Seznamte se s projekty a řešení](/visualstudio/get-started/tutorial-projects-solutions)
