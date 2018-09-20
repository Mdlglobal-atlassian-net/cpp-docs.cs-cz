---
title: IDE a nástroje pro vývoj v jazyce Visual C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 06/02/2018
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
ms.openlocfilehash: d4e7742afd3fecc4dd115624da0c1650dc662004
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412519"
---
# <a name="ide-and-tools-for-visual-c-development"></a>IDE a nástroje pro vývoj v jazyce Visual C++

Microsoft Visual C++ (MSVC) jako součást sady Visual Studio integrované vývojové prostředí (IDE), sdílí mnoho windows a nástroje společné s jiných jazycích. Mnoho z nich, včetně **Průzkumníka řešení**, editor kódu a ladicí program, jsou popsány v části [Visual Studio IDE](/visualstudio/ide/visual-studio-ide). Často sdílené nástroje nebo okno má mírně odlišnou sadu funkcí jazyka C++ než pro jazyky .NET nebo Javascript. Některé windows nebo nástroje jsou k dispozici pouze Visual Studio Pro nebo Visual Studio Enterprise.

Kromě sdílené nástroje v integrovaném vývojovém prostředí sady Visual Studio MSVC má několik nástrojů pro vývoj nativního kódu. Tyto nástroje jsou také uvedené v tomto článku. Seznam, které jsou k dispozici v každé edici sady Visual Studio tools najdete v tématu [nástrojů Visual C++ a funkcí v edicích nástroje Visual Studio](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="creating-a-solution-and-projects"></a>Vytváření řešení a projekty

A *projektu* je v podstatě sadu souborů se zdrojovým kódem a prostředky, jako jsou obrázky nebo data souborů, které jsou integrované do spustitelného souboru.

Visual Studio 2015 poskytuje podporu pro projekty MSBuild. Můžete si stáhnout rozšíření sady Visual Studio pro jiné systémy sestavení, jako je například Qt nebo CMake.

Visual Studio 2017 poskytuje podporu pro libovolný systém sestavení nebo vlastních sestavovacích nástrojů, které chcete použít s plnou podporou technologie IntelliSense, procházení a ladění:

- Nástroj MSBuild je systém nativní sestavení pro sadu Visual Studio a je často nejlepší volbou pro aplikace univerzální platformy Windows (UPW) nebo starší verzi aplikace klasické pracovní plochy Windows, které používají MFC ani ATL. Další informace o projekty založené na MSBuild C++, naleznete v tématu [vytváření a správa projekty využívající MSBuild](creating-and-managing-visual-cpp-projects.md).
- CMake je platformově univerzální sestavovací systém, který je integrovaný do rozhraní IDE sady Visual Studio, pokud provádíte instalaci vývoj desktopových aplikací pomocí úlohy pro C++. Další informace najdete v tématu [projekty CMake v jazyce Visual C++](cmake-tools-for-visual-cpp.md).
- Všechny ostatní C++ sestavovacího systému, včetně dojde ke ztrátě kolekce souborů, je podporované prostřednictvím funkce Otevřít složku. Vytvoříte jednoduchou soubory JSON k vyvolání programu sestavení a konfiguraci ladicí relace. Další informace najdete v tématu [přenos kódu C++ pro Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/04/14/bring-your-cpp-code-to-visual-studio/).

### <a name="project-templates-msbuild"></a>Šablony projektů (MSBuild)

Visual Studio obsahuje několik šablon pro projekty využívající MSBuild; Tyto šablony obsahují počáteční kód a nastavení potřebných pro celou řadu typů základní program. Obvykle Začněte volbou **souboru** > **nový projekt** vytvoření projektu ze šablony projektu, pak přidat nové soubory zdrojového kódu tohoto projektu, nebo začněte programovat v souborech k dispozici. Informace specifické pro projekty v jazyce C++ a průvodce, naleznete v tématu [vytváření a správa projektů Visual C++](../ide/creating-and-managing-visual-cpp-projects.md).

### <a name="application-wizards-msbuild"></a>Průvodci aplikací (MSBuild)

Visual Studio poskytuje průvodce pro některé typy projektu nástroje MSBuild při výběru **souboru** > **nový projekt**. Průvodce vás provede procesem vytvoření nového projektu. To je užitečné pro typy projektů, které mají mnoho možností a nastavení. Další informace najdete v tématu [vytváření Desktopu projekty podle pomocí průvodců aplikací](../ide/creating-desktop-projects-by-using-application-wizards.md).

## <a name="creating-user-interfaces-with-designers-msbuild"></a>Vytváření uživatelských rozhraní pomocí návrháře (MSBuild)

Pokud váš program má uživatelské rozhraní, jedním z prvních úkolů je přidejte do ní ovládací prvky jako tlačítka pole se seznamem a tak dále. Visual Studio obsahuje vizuální návrhová plocha a nástrojů pro každý flavor aplikace C++. Bez ohledu na to, jaký typ aplikace, kterou vytváříte, základní myšlenka je stejný: přetáhněte ovládací prvek z panelu nástrojů okna a umístěte jej na návrhovou plochu do požadovaného umístění. Na pozadí sada Visual Studio generuje zdroje a kód vyžaduje, aby to fungovalo. Potom napíšete kód pro naplnění ovládací prvky s daty nebo upravit jejich vzhled a chování.

Další informace o navrhování uživatelského rozhraní pro aplikace univerzální platformy Windows, naleznete v tématu [návrhu a uživatelské rozhraní](https://developer.microsoft.com/en-us/windows/design).

Další informace o vytváření uživatelského rozhraní pro aplikaci knihovny MFC naleznete v tématu [desktopových aplikací knihovny MFC](../mfc/mfc-desktop-applications.md). Informace o aplikacích Win32 Windows najdete v tématu [desktopových aplikací Windows](../windows/windows-desktop-applications-cpp.md).

## <a name="writing-and-editing-code"></a>Psaní a úpravy kódu

### <a name="semantic-colorization"></a>Sémantického barevného zvýraznění

Když vytvoříte projekt, všechny soubory projektu jsou zobrazeny v **Průzkumníka řešení** okna. Když kliknete na soubor .h a .cpp v **Průzkumníka řešení**, soubor se otevře v editoru kódu. Editor kódu je specializované textový procesor pro zdrojový kód jazyka C++. Barevně ho označí klíčová slova jazyka, názvu proměnné a metody a další prvky kódu změňte kód čitelnější a lépe pochopit.

### <a name="intellisense"></a>IntelliSense

Editor kódu rovněž podporuje několik funkcí, které společně se označují jako IntelliSense. Můžete najeďte myší metodu a zobrazit některé základní dokumentaci pro něj. Jakmile zadáte název proměnné třídy a. nebo ->, zobrazí se seznam členů instance této třídy. Pokud zadáte název třídy a pak::, zobrazí se seznam statické členy. Když začnete psát název třídy nebo metody, editor kódu nabídne návrhy na dokončení příkazu. Další informace najdete v tématu [pomocí technologie IntelliSense](/visualstudio/ide/using-intellisense).

### <a name="code-snippets"></a>Fragmenty kódu

Fragmenty kódu technologie IntelliSense můžete použít ke generování běžně používaných nebo složitý kód vytvoří místní jedním stisknutím tlačítka. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).

## <a name="navigating-code"></a>Navigace v kódu

**Zobrazení** nabídka poskytuje přístup k mnoha windows a nástroje pro navigaci v rámci souborů s kódy. Podrobné informace o těchto oken naleznete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).

### <a name="solution-explorer"></a>Průzkumník řešení

Ve všech edicích sady Visual Studio, použijte **Průzkumníka řešení** podokně přecházet mezi soubory v projektu. Rozbalte .h a .cpp soubor ikony zobrazení třídy v souboru. Rozšiřte třídu zobrazíte její členy. Dvakrát klikněte na člen přejděte do jeho definice nebo implementace v souboru.

### <a name="class-view-and-code-definition-window"></a>Zobrazení tříd a okně Definice kódu

Použití **zobrazení tříd** podokno zobrazíte obory názvů a třídy u všech souborů, včetně částečné třídy. Můžete rozbalit každý obor názvů nebo třídy jejích členů a dvakrát klikněte na člen, který chcete přejít do tohoto umístění ve zdrojovém souboru. Pokud otevřete **okno Definice kódu**, můžete zobrazit definice nebo implementaci daného typu, když je vyberete v **zobrazení tříd**.

### <a name="object-browser"></a>prohlížeč objektů

Použití **prohlížeče objektů** a prozkoumejte informace o typu v součásti prostředí Windows Runtime (soubory .winmd), sestavení .NET a COM knihoven typů. Není použit s knihovnami DLL Win32.

### <a name="go-to-definitiondeclaration"></a>Přejít na definice nebo deklarace

Stisknutím klávesy F12 na libovolnou proměnnou název nebo člen rozhraní API přejít k jeho definici. Pokud definice není v souboru winmd (pro UPW ani Windows 8.x Store aplikaci), pak se zobrazí informace o typu v prohlížeči objektů. Můžete také zvolit **přejít k definici** nebo **přejít k deklaraci** kliknutím pravým tlačítkem na název proměnné nebo typ a výběru možnosti v místní nabídce.

### <a name="find-all-references"></a>Najít všechny odkazy

V souboru zdrojového kódu, klikněte pravým tlačítkem kurzorem myši nad název typu nebo metody nebo proměnné a zvolte **najít všechny odkazy** vrátit seznam jakémkoliv místě v souboru, projekt nebo řešení, kde se typ používá. **Najít všechny odkazy** je inteligentní a vrací pouze instance stejné identické proměnné i v případě, že jiné proměnné v jiném oboru mít stejný název.

## <a name="add-and-edit-resources--msbuild"></a>Přidat a upravit prostředky (MSBuild)

Termín *prostředků* v rámci sady Visual Studio zahrnuje desktopový projekt věci jako dialogová okna, ikony, lokalizovatelných řetězců, úvodní obrazovky, databázové připojovací řetězce nebo libovolná data, který chcete zahrnout spustitelný soubor.

Další informace o přidávání a úprava prostředků v nativních desktopových projektů C++, naleznete v tématu [práce se zdrojovými soubory](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Sestavení (kompilace a odkaz)

Zvolte **sestavení** > **sestavit řešení** v nabídce panelu, nebo zadejte kombinaci kláves Ctrl + Shift + B ke kompilaci a odkaz projekt. K vytvoření spustitelného kódu, použije sada Visual Studio [MSBuild](/visualstudio/msbuild/msbuild1) nebo CMake nebo cokoli, co sestavení prostředí nastavíte prostřednictvím **otevřít složku**. Pro projekty MSBuild, nastavíte možnosti Obecné sestavení v rámci **nástroje** > **možnosti** > **projekty a řešení** a můžete nastavit vlastnosti pro konkrétní projekty v rámci **projektu** > **vlastnosti**. Chyby a upozornění sestavení jsou uvedeny v seznamu chyb (Ctrl +\\, E). Projekty MSBuild bez se nakonfigurují se soubory JSON, které vytvoříte v Průzkumníku řešení. Všechno, co sestavovací systém, používáte, **výstup** okno (Alt + 2) zobrazí informace o procesu sestavení. Další informace o konfiguracích MSBuild naleznete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md) a [sestavení projektů C++ v sadě Visual Studio](../ide/building-cpp-projects-in-visual-studio.md).

Můžete také použít kompilátoru (cl.exe) a mnoho dalších související s buildem samostatných nástrojů, například NMAKE a LIB přímo z příkazového řádku. Další informace najdete v tématu [kódu sestavení C/C++ v příkazovém řádku](../build/building-on-the-command-line.md) a [Reference sestavení C/C++](../build/reference/c-cpp-building-reference.md).

## <a name="test"></a>Test

Visual Studio obsahuje rozhraní testování částí pro nativní kód C++ a C + +/ CLI. Další informace najdete v tématu [ověřování kódu pomocí testování částí](/visualstudio/test/unit-test-your-code) a [zápis částí pro C/C++ se sadou Microsoft Unit Testing Framework pro C++](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)

## <a name="analyze"></a>Analyzovat

Visual Studio obsahuje nástroje pro analýzu statického kódu jazyka C++, včetně implementace [podle dokumentu C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) pravidla tyto moduly pro kontrolu. Další informace najdete v tématu [Code analysis for C/C++ – přehled](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

## <a name="debug"></a>Ladit

Program můžete ladit stisknutím kombinace kláves **F5** při konfiguraci projektu nastavena na ladění. Při ladění, které můžete nastavit zarážky stisknutím kombinace kláves **F9**, procházejte kódem po krocích stisknutím kombinace kláves **F10**, hodnoty zadané proměnné a registry, zobrazit a dokonce i v některých případech provádět změny v kódu a pokračovat ladění bez opětovné kompilace. Další informace najdete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="deploy-completed-applications"></a>Nasazení dokončené aplikace

Nasazení aplikace pro UPW pro zákazníky přes Microsoft Store prostřednictvím **projektu** > **Store** nabídky. Nasazení CRT zpracovává automaticky na pozadí. Další informace najdete v tématu [Windows publikovat aplikace a hry](/windows/uwp/publish/).

Když nasadíte nativní aplikaci klasické pracovní plochy jazyka C++ do jiného počítače, je nutné nainstalovat vlastní aplikace a všechny soubory knihoven, na kterých aplikace závisí. Existují tři způsoby, jak nasadit univerzální C++ runtime (UCRT) s aplikací: Centrální nasazení, místní nasazení nebo statického propojení. Další informace najdete v tématu [nasazení desktopových aplikací](../ide/deploying-native-desktop-applications-visual-cpp.md).

Další informace o nasazení a C + +/ CLI programu, najdete v článku [Průvodce nasazením pro vývojáře](/dotnet/framework/deployment/deployment-guide-for-developers),

## <a name="related-articles"></a>Související články

|||
|-|-|
|[Nástroje a funkce Visual C++ v různých edicích sady Visual Studio](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)|Ukazuje, jaké funkce jsou k dispozici v různých edicích sady Visual Studio.|
|[Vytvářet a spravovat projekty využívající MSBuild](../ide/creating-and-managing-visual-cpp-projects.md)|Poskytuje přehled o projekty využívající C++ MSBuild v sadě Visual Studio a odkazy na další články, které popisují, jak vytvořit a spravovat je.|
|[Projekty CMake v jazyce Visual C++](cmake-tools-for-visual-cpp.md).|Popisuje, jak sestavit CMake nebo jiné projekty jiné než MSBuild v jazyce Visual C++.|
|[Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)|Popisuje, jak vytvářet projekty C++.|
|[Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)|Poskytuje přehled o nasazení aplikací v jazyce C++ a odkazy na další články, které popisují nasazení podrobně.|
|[Průvodce přenosem a upgradem Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)|Podrobné informace o tom, jak upgradovat aplikací v jazyce C++, které byly vytvořeny v dřívějších verzích sady Visual Studio a postupu při migraci aplikací, které byly vytvořeny pomocí jiných nástrojů než Visual Studio.|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Popisuje klíčové funkce jazyka Visual C++ v systému Visual Studio a odkazy na zbytek dokumentace k jazyku Visual C++.|
