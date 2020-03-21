---
title: Projekty sady Visual Studio –C++
ms.date: 10/25/2019
helpviewer_keywords:
- ATL projects, creating
- Visual Studio C++ projects, creating
- projects [C++], creating
- Visual Studio C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: 3694478e22bfd2a3c58a72ba0c3ad2d15351bc9f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078697"
---
# <a name="visual-studio-projects---c"></a>Projekty sady Visual Studio – C++

*Projekt sady Visual Studio* je projekt založený na systému sestavení MSBuild. Nástroj MSBuild je nativním systémem sestavení pro Visual Studio a obecně se jedná o nejlepší systém sestavení, který se používá pro programy specifické pro systém Windows. Nástroj MSBuild je těsně integrovaný se sadou Visual Studio, ale můžete ho použít také z příkazového řádku. Pro projekty pro různé platformy nebo projekty, které používají open source knihovny, doporučujeme používat [projekty cmake v sadě Visual Studio](cmake-projects-in-visual-studio.md) v sadě visual Studio 2017 a novějších. Informace o tom, jak upgradovat projekty MSBuild ze starších verzí sady Visual Studio, najdete v [Průvodci přenosem a upgradem Microsoftu C++ ](../porting/visual-cpp-porting-and-upgrading-guide.md).

## <a name="create-a-project"></a>Vytvoření projektu

::: moniker range="vs-2019"

Můžete C++ vytvořit projekty výběrem možnosti **soubor** > **Nový** > **projekt**a potom nastavením jazyka. **Language** C++ V seznamu výsledků se zobrazí seznam šablon projektu, které můžete filtrovat nastavením typu **platforma** nebo **projektu** a zadáním klíčových slov do vyhledávacího pole.

   ![Šablony projektů sady Visual Studio 2019](../build/media/vs2019-choose-console-app.png "Visual Studio 2019 – dialog nového projektu")

::: moniker-end

::: moniker range="vs-2017"

C++ Můžete vytvořit projekty kliknutím na **soubor** > **Nový** > **projekt**a pak v levém podokně C++ zvolíte možnost Visual. V prostředním podokně se zobrazí seznam šablon projektu:

   ![Šablony projektů](../overview/media/vs2017-new-project.png "Visual Studio 2017 – dialog nového projektu")

::: moniker-end

Další informace o všech výchozích šablonách projektů, které jsou součástí sady Visual Studio, naleznete v tématu [ C++ šablony projektů v aplikaci Visual Studio](reference/visual-cpp-project-types.md). Můžete vytvořit vlastní šablony projektu. Další informace naleznete v tématu [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).

Po vytvoření projektu se zobrazí v okně [Průzkumník řešení](/visualstudio/ide/solutions-and-projects-in-visual-studio) :

   ![Průzkumník řešení](media/mathlibrary-solution-explorer-153.png)

Při vytváření nového projektu je také vytvořen soubor řešení (. sln). Do řešení můžete přidat další projekty tak, že na něj kliknete pravým tlačítkem v **Průzkumník řešení**. Soubor řešení se používá ke koordinaci závislostí sestavení, pokud máte více souvisejících projektů, ale není mnohem více. Všechny možnosti kompilátoru jsou nastaveny na úrovni projektu.

## <a name="add-items"></a>Přidat položky

Do projektu přidejte soubory zdrojového kódu, ikony nebo jiné položky tak, že kliknete pravým tlačítkem na projekt v **Průzkumník řešení** a zvolíte **Přidat > nový** nebo **Přidat > existující**.

## <a name="add-third-party-libraries"></a>Přidat knihovny třetích stran

K přidání knihoven třetích stran použijte Správce balíčků [vcpkg](vcpkg.md) . Spusťte krok integrace sady Visual Studio a nastavte cesty k této knihovně, když na ni odkazujete z libovolného projektu sady Visual Studio.

## <a name="set-compiler-options-and-other-build-properties"></a>Nastavení možností kompilátoru a dalších vlastností sestavení

Chcete-li konfigurovat nastavení sestavení pro projekt, klikněte pravým tlačítkem myši na projekt v **Průzkumník řešení** a vyberte možnost **vlastnosti**. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](working-with-project-properties.md).

## <a name="compile-and-run"></a>Zkompilovat a spustit

Chcete-li zkompilovat a spustit nový projekt, stiskněte klávesu **F5** nebo klikněte na *rozevírací nabídku ladění* se zelenou šipkou na hlavním panelu nástrojů. *Rozevírací seznam konfigurace* je tam, kde si zvolíte, jestli chcete provést *ladění* nebo *vydání* buildu (nebo nějaké jiné vlastní konfigurace).

Nový projekt se zkompiluje bez chyb. Při přidávání vlastního kódu můžete občas způsobit chybu nebo aktivovat upozornění. Chyba zabrání dokončení sestavení; Upozornění ne. Všechny chyby a upozornění se zobrazí v okno Výstup i Seznam chyb při sestavování projektu.

   ![Okno výstup a seznam chyb](../overview/media/vs2017-output-error-list.png)

V Seznam chyb můžete stisknutím klávesy **F1** na zvýrazněné chybě přejít na příslušné téma dokumentace.

## <a name="in-this-section"></a>V tomto oddílu

[Nastavení vlastností kompilátoru a sestavení C++ v sadě Visual Studio](working-with-project-properties.md)<br/>
Jak používat stránky vlastností a seznamy vlastností k určení nastavení projektu.

[Referenční knihovny a komponenty v okamžiku sestavení](adding-references-in-visual-cpp-projects.md)<br/>
Jak do projektu zahrnout komponenty knihovny, DLL, COM a .NET.

[Uspořádání výstupních souborů projektu](how-to-organize-project-output-files-for-builds.md)<br/>
Jak přizpůsobit umístění spustitelných souborů vytvořených v procesu sestavení.

[Postup vlastního sestavení a události sestavení](understanding-custom-build-steps-and-build-events.md)<br/>
Jak přidat libovolný příkaz do procesu sestavení v určených bodech.

[Vytvoření projektu z existujícího kódu](how-to-create-a-cpp-project-from-existing-code.md)<br/>
Vytvoření nového projektu sady Visual Studio z volné kolekce zdrojových souborů.

## <a name="see-also"></a>Viz také

[Projekty a systémy sestavení](projects-and-build-systems-cpp.md)<br>
[Průvodce C++ přenosem a upgradem Microsoftu](../porting/visual-cpp-porting-and-upgrading-guide.md)
