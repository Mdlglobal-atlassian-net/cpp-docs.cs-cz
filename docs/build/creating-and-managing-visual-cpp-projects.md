---
title: Visual Studio Projects - C++
ms.date: 12/12/2018
helpviewer_keywords:
- ATL projects, creating
- Visual Studio C++ projects, creating
- projects [C++], creating
- Visual Studio C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: 30d3b13ba4d392cdc5d1c7c611b61066503647a2
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837050"
---
# <a name="visual-studio-projects---c"></a>Projekty Visual Studio – C++

A *projektu sady Visual Studio* je projekt založený na systému sestavení nástroje MSBuild. Nástroj MSBuild je systém nativní sestavení pro sadu Visual Studio a je obvykle že nejlepší vytvořit systém pro aplikace UWP, jakož i desktopových aplikací, které používají knihovny MFC nebo ATL, komponenty modelu COM a jiných programů specifické pro Windows. Nástroj MSBuild je úzce integrovaná s Visual Studio, ale můžete ho použít také z příkazového řádku. 

## <a name="create-a-project"></a>Vytvoření projektu

::: moniker range="vs-2019"

Můžete vytvořit C++ projektů výběrem **souboru** > **nový** > **projektu**, pak nastavení **jazyk** k C++. V seznamu výsledků se zobrazí seznam šablon projektů, které můžete filtrovat tak, že nastavíte **platformy** nebo **typu projektu** a zadáním klíčových slov do pole Hledat. 

   ![Šablony projektů Visual Studio. 2019](../build/media/vs2019-choose-console-app.png "Visual Studio 2019 nový projekt dialogového okna")

::: moniker-end

::: moniker range="vs-2017"

Můžete vytvořit C++ projektů výběrem **souboru** > **nový** > **projektu**, výběrem Vizuálu C++ v levém podokně. V prostředním podokně se zobrazí seznam šablon projektů:

   ![Šablony projektů](../overview/media/vs2017-new-project.png "Visual Studio 2017 projektu nové dialogové okno")

::: moniker-end

Další informace o všechny výchozí šablony projektů, které jsou zahrnuty v sadě Visual Studio najdete v tématu [šablony projektů C++ v sadě Visual Studio](reference/visual-cpp-project-types.md). Můžete vytvořit vlastní šablony projektu. Další informace najdete v tématu [jak: Vytváření šablon projektu](/visualstudio/ide/how-to-create-project-templates).

Po vytvoření projektu se zobrazí v [Průzkumníka řešení](/visualstudio/ide/solutions-and-projects-in-visual-studio) okno:

   ![Průzkumník řešení](media/mathlibrary-solution-explorer-153.png)

Když vytvoříte nový projekt, se také vytvoří soubor řešení (.sln). Další projekty do řešení můžete přidat kliknutím pravým tlačítkem myši na něj v **Průzkumníka řešení**. Soubor řešení se používá ke koordinaci závislosti sestavení, když máte několik souvisejících projektů, ale nebude ještě mnohem víc než. Všechny možnosti kompilátoru nastavují na úrovni projektu.

## <a name="add-items"></a>Přidat položky

Přidání souborů se zdrojovým kódem, ikony nebo jiné položky do projektu kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení** a zvolíte **Přidat > Nová** nebo **Přidat > existující**.

## <a name="add-third-party-libraries"></a>Přidání knihovny třetích stran

Chcete-li přidat knihovny třetích stran, použijte [vcpkg](vcpkg.md) Správce balíčků. Spusťte krok integrace sady Visual Studio k nastavení cesty k této knihovně při odkazování z libovolného projektu sady Visual Studio. 

## <a name="set-compiler-options-and-other-build-properties"></a>Nastavit možnosti kompilátoru a další vlastnosti sestavení

Ke konfiguraci nastavení sestavení pro projekt, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a zvolte **vlastnosti**. Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](working-with-project-properties.md).

## <a name="compile-and-run"></a>Kompilace a spuštění

Chcete-li zkompilovat a spustit nový projekt, stiskněte **F5** nebo klikněte na tlačítko *ladění rozevírací seznam* s zelenou šipku na hlavním panelu nástrojů. *Rozevírajícího seznamu konfigurace* je, kde můžete zvolit, jestli se má provést *ladění* nebo *vydání* sestavení (nebo některé vlastní konfigurace).

Nový projekt zkompiluje bez chyb. Při přidávání vlastního kódu, mohou čas od času zavést chybu nebo aktivovat upozornění. Chyba zabrání dokončení; sestavení upozornění je nepodporuje. Všechny chyby a upozornění se zobrazí v okně Výstup a v seznamu chyb při sestavení projektu. 

   ![Výstupní okno a seznamu chyb](../overview/media/vs2017-output-error-list.png)

V seznamu chyb, můžete stisknout **F1** na zvýrazněné chyby, přejděte na téma dokumentace týkající se jeho.

## <a name="in-this-section"></a>V tomto oddílu

[Nastavení vlastností kompilátoru a sestavení C++ v sadě Visual Studio](working-with-project-properties.md)<br/>
Jak používat stránky vlastností a vlastností k určení nastavení projektu.

[Referenční knihovny a komponenty v okamžiku sestavení](adding-references-in-visual-cpp-projects.md)<br/>
Postup zahrnutí knihovny DLL, komponenty COM a .NET v projektu.
 
[Uspořádání výstupních souborů projektu](how-to-organize-project-output-files-for-builds.md)<br/>
Postup přizpůsobení umístění spustitelné soubory vytvořené během procesu sestavení.

[Postup vlastního sestavení a události sestavení](understanding-custom-build-steps-and-build-events.md)<br/>
Postup přidání jakékoli libovolný příkaz do procesu sestavení na zadané body.

[Vytvoření projektu z existujícího kódu](how-to-create-a-cpp-project-from-existing-code.md)<br/>
Jak vytvořit nový projekt sady Visual Studio z kolekce dojde ke ztrátě zdrojových souborů.

## <a name="see-also"></a>Viz také:

[Projekty a systémy sestavení](projects-and-build-systems-cpp.md)<br>
