---
title: "IDE a nástrojů pro vývoj Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, development tools
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01d4898b2d67de4b23d31227e572c0f270aa6f37
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2018
---
# <a name="ide-and-tools-for-visual-c-development"></a>IDE a nástrojů pro vývoj Visual C++

V rámci z prostředí Visual Studio integrované vývoj prostředí (IDE) Microsoft Visual C++ (MSVC) sdílí mnoho windows a nástroje pro společné s jinými jazyky. Mnoho funkcí, včetně **Průzkumníku řešení**, editoru kódu a ladicí program, jsou popsané v části [Visual Studio IDE](/visualstudio/ide/visual-studio-ide). Často sdílené nástroj nebo okna má mírně odlišné sadu funkcí pro jazyk C++ než pro jazyky .NET nebo Javascript. Některé windows nebo nástroje jsou k dispozici pouze Visual Studio Pro nebo Visual Studio Enterprise.

Kromě sdílené nástrojů v prostředí Visual Studio IDE MSVC má několik nástrojů speciálně pro vývoj nativního kódu. Tyto nástroje jsou také uvedené v tomto článku. Seznam, které jsou k dispozici v každé edici sady Visual Studio tools najdete v tématu [funkcí v edicích Visual Studio a nástrojů pro Visual C++](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="creating-a-solution-and-projects"></a>Vytváření řešení a projekty

A *projektu* je v podstatě sadu soubory zdrojového kódu a prostředkům, například bitové kopie nebo datové soubory, které jsou součástí spustitelného souboru. Visual Studio 2017 může podporovat všechny systém sestavení nebo vlastní sestavovací nástroje, které chcete použít s plnou podporu pro technologii Intellisense, procházení a ladění:

- MSBuild je systém nativní sestavení pro Visual Studio a často je nejlepší volbou pro aplikace pro univerzální platformu Windows (UWP) nebo starší verze aplikací klasické pracovní plochy Windows, které používají MFC nebo ATL. Další informace o projekty využívající MSBuild C++ najdete v tématu [vytváření a správa projekty využívající MSBuild](creating-and-managing-visual-cpp-projects.md).
- CMake je systém, který je integrován do prostředí Visual Studio IDE, když instalujete vývoj aplikací C++ zatížení sestavení napříč platformami. Další informace najdete v tématu [CMake projektů v jazyce Visual C++](cmake-tools-for-visual-cpp.md).
- Všechny ostatní C++ sestavení systému, včetně přijít kolekce souborů, je podporován pomocí funkce Otevřít složku. Můžete vytvořit jednoduché soubory JSON k vyvolání vašeho programu sestavení a konfiguraci relace ladění. Další informace najdete v tématu [přineste kódu C++ pro Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/04/14/bring-your-cpp-code-to-visual-studio/).

### <a name="project-templates-msbuild"></a>Šablony projektů (MSBuild)

Visual Studio obsahuje několik šablon pro projekty využívající MSBuild; Tyto šablony obsahovat počáteční kód a nastavení potřebné pro celou řadu typů základní program. Obvykle můžete spustit výběrem **soubor** > **nový projekt** k vytvoření projektu ze šablony projektu, pak přidat nové soubory zdrojového kódu do tohoto projektu nebo psaní v souborech zadaný. Informace specifické pro projekty C++ a průvodců projektu najdete v tématu [vytváření a správa projekty Visual C++](../ide/creating-and-managing-visual-cpp-projects.md).

### <a name="application-wizards-msbuild"></a>Průvodci aplikací (MSBuild)

Visual Studio poskytuje průvodců pro některé typy projektu nástroje MSBuild, když zvolíte **soubor** > **nový projekt**. Průvodce vás provede procesem vytvoření nového projektu. To je užitečné pro typy projektů, které mají mnoho možností a nastavení. Další informace najdete v tématu [vytváření plochy projekty podle pomocí průvodců aplikací](../ide/creating-desktop-projects-by-using-application-wizards.md).

## <a name="creating-user-interfaces-with-designers-msbuild"></a>Vytvoření uživatelského rozhraní pomocí návrháře (MSBuild)

Pokud váš program má uživatelské rozhraní, jednu z první úloh je přidejte do ní s ovládacími prvky, jako jsou tlačítka, seznamy a tak dále. Visual Studio obsahuje návrhové ploše a sady nástrojů pro každý příchuť aplikace C++. Bez ohledu na to, jaký typ aplikace, kterou vytváříte, základní Rada je stejný: přetáhněte ovládací prvek z okna nástrojů a umístěte jej na návrhovou plochu do požadovaného umístění. Visual Studio na pozadí, generuje prostředků a vyžaduje, aby bylo pracovní kód. Potom napíšete kód naplnit ovládací prvky s daty nebo upravit jejich vzhled a chování.

Další informace o návrhu uživatelské rozhraní pro univerzální platformu Windows aplikaci najdete v tématu [návrhu a uživatelského rozhraní](https://developer.microsoft.com/en-us/windows/design).

Další informace o vytváření uživatelské rozhraní pro aplikace MFC najdete v tématu [aplikace MFC plochy](../mfc/mfc-desktop-applications.md). Informace o programů Win32 Windows najdete v tématu [aplikace systému Windows Desktop](../windows/windows-desktop-applications-cpp.md).

## <a name="writing-and-editing-code"></a>Zápis a úpravy kódu

### <a name="semantic-colorization"></a>Sémantické zabarvení

Po vytvoření projektu, všechny soubory projektu, se zobrazují v **Průzkumníku řešení** okno. Po kliknutí na soubor .h nebo sada v **Průzkumníku**, soubor se otevře v editoru kódu. Editor kódu je specializovaná textový editor pro C++ zdrojového kódu. Ho barevně označí klíčová slova jazyka, metodu a proměnná názvy a další elementy kódu, aby kód víc čitelný a srozumitelnější.

### <a name="intellisense"></a>IntelliSense

Editor kódu také podporuje několik funkcí, které společně se označují jako Intellisense. Můžete najeďte myší na metodu a najdete některé základní dokumentaci pro ni. Jakmile zadáte název proměnné třídy a. nebo ->, zobrazí se seznam členů instance této třídy. Pokud zadáte název třídy a pak::, zobrazí se seznam statické členy. Když začnete psát název třída nebo metoda, bude editoru kódu nabízí návrhy pro dokončení příkazu. Další informace najdete v tématu [pomocí IntelliSense](/visualstudio/ide/using-intellisense).

### <a name="code-snippets"></a>Fragmenty kódu

Intellisense – fragmenty kódu můžete použít ke generování běžně používané nebo složitý kód vytvoří s klávesu zástupce. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).

## <a name="navigating-code"></a>Navigace v kódu

**Zobrazení** nabídky poskytuje přístup k mnoha windows a nástroje pro navigaci v souborech kódu. Podrobné informace o těchto windows najdete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).

### <a name="solution-explorer"></a>Průzkumník řešení

Ve všech edicích sady Visual Studio, použijte **Průzkumníku řešení** podokně navigace mezi soubory v projektu. Rozbalte .h nebo sada soubor ikony zobrazení třídy v souboru. Rozbalte třídu zobrazíte její členy. Dvakrát klikněte na člena, přejděte na jeho definice nebo implementace v souboru.

### <a name="class-view-and-code-definition-window"></a>Zobrazení tříd a definice kódu – okno

Použití **zobrazení tříd** podokno zobrazíte obory názvů a třídy do všech souborů, včetně částečné třídy. Můžete rozbalit každý obor názvů nebo třídy, které chcete zobrazit členy a dvakrát klikněte na člen přejděte do tohoto umístění ve zdrojovém souboru. Pokud otevřete **definice kódu – okno**, když zvolíte ho můžete zobrazit definice nebo implementace typu **zobrazení tříd**.

### <a name="object-browser"></a>prohlížeč objektů

Použití **Prohlížeč objektů** a prozkoumejte informace o typu v prostředí Windows Runtime součásti (.winmd soubory), sestavení .NET a COM knihovny typů. Se nepoužívá s Win32 knihovny DLL.

### <a name="go-to-definitiondeclaration"></a>Přejít na definici/deklarace

Stisknutím klávesy F12 na všechny proměnné název nebo člen rozhraní API přejít k příslušné definici. Pokud definice není v souboru .winmd (pro UPW nebo Windows 8.x Store aplikaci), pak se zobrazí informace o typu v prohlížeči objektů. Můžete také **přejít k definici** nebo **přejděte k deklaraci** pravým tlačítkem myši na název proměnné nebo typ a zvolením možnosti v místní nabídce.

### <a name="find-all-references"></a>Najít všechny odkazy

V souboru zdrojového kódu, klikněte pravým tlačítkem stačí nastavit ukazatel myši nad název typ nebo metoda nebo proměnné a zvolte **najít všechny odkazy** vrácení seznamu každé umístění v souboru, projekt nebo řešení, kde se používá typ. **Najít všechny odkazy** je inteligentního a vrátí pouze instance stejné identické proměnné, i v případě, že mají stejný název jiné proměnné v jiném oboru.

## <a name="add-and-edit-resources--msbuild"></a>Přidávání a úprava prostředků (MSBuild)

Termín *prostředků* v kontextu sady Visual Studio plochy projektu patří sem například dialogových oken, ikony, lokalizovatelný řetězce, úvodní obrazovky, databázové připojovací řetězce nebo jakékoli libovolná data, která chcete zahrnout do spustitelný soubor.

Další informace o přidávání a úprava prostředků v nativní běžných projektů C++ najdete v tématu [práce se zdrojovými soubory](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Sestavení (kompilace a odkaz)

Zvolte **sestavení** > **sestavit řešení** v nabídce panelu nebo zadejte kombinaci kláves Ctrl + Shift + B pro kompilaci a propojení projektu. Pokud chcete vytvořit spustitelného kódu, Visual Studio použije [MSBuild](/visualstudio/msbuild/msbuild1) nebo CMake nebo ať sestavení prostředí byste nastavit prostřednictvím **otevřít složku**. U projektů MSBuild nastavíte možnosti Obecné sestavení v části **nástroje** > **možnosti** > **projekty a řešení** a je možné nastavit vlastnosti pro konkrétní projekty pod **projektu** > **vlastnosti**. V seznamu chyb jsou hlášené chyby a upozornění sestavení (Ctrl +\\, E). Bez MSBuild projekty jsou nakonfigurovány s soubory JSON, které vytvoříte v Průzkumníku řešení. Ať sestavení systému, které chcete použít, **výstup** okno (Alt + 2) se zobrazí informace o procesu sestavení. Další informace o konfiguracích MSBuild najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md) a [sestavení projektů C++ v sadě Visual Studio](../ide/building-cpp-projects-in-visual-studio.md).

Můžete také použít kompilátoru (cl.exe) a mnoha jiných samostatná sestavení související nástrojů, například NMAKE a LIB přímo z příkazového řádku. Další informace najdete v tématu [kódu sestavení C/C++ v příkazovém řádku](../build/building-on-the-command-line.md) a [odkaz sestavení C/C++](../build/reference/c-cpp-building-reference.md).

## <a name="test"></a>Test

Visual Studio zahrnuje částí unit test framework pro nativní C++ a C + +/ CLI. Další informace najdete v tématu [ověřování kódu pomocí testy jednotek](/visualstudio/test/unit-test-your-code) a [zápis testů jednotek aplikací pro C/C++ s Microsoft Unit Testing Framework pro C++](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)

## <a name="debug"></a>Ladit

Váš program můžete ladit stisknutím **F5** když je nastavená konfigurace projektu na ladění. Při ladění je můžete nastavit zarážky stisknutím **F9**, krok prostřednictvím kódu stisknutím **F10**, zobrazovat hodnoty zadané proměnné nebo registrů a to i v některých případech proveďte změny v kódu a pokračovat ladění bez znovu kompilace. Další informace najdete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="deploy-completed-applications"></a>Nasazení aplikací dokončené

Nasazení aplikace UWP zákazníkům prostřednictvím Windows Store prostřednictvím **projektu** > **úložiště** možnost nabídky. Nasazení CRT se proto automaticky na pozadí. Další informace najdete v tématu [prodejní aplikace](http://go.microsoft.com/fwlink/p/?LinkId=262280).

Když nasadíte nativní C++ desktopová aplikace do jiného počítače, je nutné nainstalovat aplikaci a všechny soubory knihovny, které je aplikace závislá. Existují tři způsoby, jak nasadit Universal C++ runtime (UCRT) pomocí aplikace: Centrální nasazení, místní nasazení nebo statické propojení. Další informace najdete v tématu [nasazení aplikace na ploše](../ide/deploying-native-desktop-applications-visual-cpp.md).

Další informace o nasazení C + +/ CLI programu, najdete v části [Průvodce nasazením pro vývojáře](/dotnet/framework/deployment/deployment-guide-for-developers),

## <a name="related-articles"></a>Související články

|||
|-|-|
|[Nástroje a funkce Visual C++ v různých edicích sady Visual Studio](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)|Zobrazí funkce, které jsou k dispozici v různých edicích sady Visual Studio.|
|[Vytváření a správa projekty využívající MSBuild](../ide/creating-and-managing-visual-cpp-projects.md)|Obsahuje přehled projekty využívající C++ MSBuild v sadě Visual Studio a odkazy na další články, které vysvětlují, jak vytvořit a spravovat je.|
|[CMake projektů v jazyce Visual C++](cmake-tools-for-visual-cpp.md).|Popisuje, jak vytvořit CMake nebo jiných bez MSBuild projektů v jazyce Visual C++.|
|[Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)|Popisuje, jak k sestavení projektů C++.|
|[Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)|Poskytuje přehled o nasazení aplikací C++ a odkazy na další články, které popisují nasazení podrobně.|
|[Průvodce přenosem a upgradem Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)|Podrobné informace o tom, jak upgradovat aplikací C++, které byly vytvořeny v dřívějších verzích sady Visual Studio a také k migraci aplikace, které byly vytvořeny pomocí nástrojů pro jiné než Visual Studio.|
|[Visual C++](../top/visual-cpp-in-visual-studio.md)|Popisuje klíčové funkce jazyka Visual C++ v systému Visual Studio a odkazy na zbytek dokumentace k jazyku Visual C++.|
