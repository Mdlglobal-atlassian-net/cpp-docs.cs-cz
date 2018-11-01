---
title: Sestavení a spuštění projektu aplikace konzoly C++
description: Sestavte a spusťte konzolovou aplikaci Hello World v jazyce Visual C++
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: tutorial
ms.devlang: C++
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
ms.openlocfilehash: 89681b4f6b2ff2780cc8dc1947e2ad758d294b48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467831"
---
# <a name="build-and-run-a-c-console-app-project"></a>Sestavení a spuštění projektu aplikace konzoly C++

Když máte vytvořený projekt konzolové aplikace jazyka C++ a zadali kódu, sestavení a spuštění v rámci sady Visual Studio spusťte jej jako samostatné aplikace z příkazového řádku.

## <a name="prerequisites"></a>Požadavky

- Sada Visual Studio s vývoj desktopových aplikací pomocí úlohy pro C++ nainstalovaný a spuštěný ve vašem počítači. Pokud ještě není nainstalovaný, postupujte podle kroků v [podpora instalace jazyka C++ v sadě Visual Studio](../build/vscpp-step-0-installation.md).

- Vytvoření "Hello, World!" projekt a zadejte jeho zdrojový kód. Pokud jste to ještě neudělali, postupujte podle kroků v [vytvoření projektu aplikace konzoly C++](../build/vscpp-step-1-create.md).

Pokud aplikace Visual Studio vypadá to, jste připraveni k sestavení a spuštění aplikace:

   ![Průvodce je připraven vytvořit nový projekt](../build/media/vscpp-ready-to-build.png "Průvodce je připraven vytvořit nový projekt")

## <a name="build-and-run-your-code-in-visual-studio"></a>Sestavení a spuštění kódu v sadě Visual Studio

1. Chcete-li projekt sestavit, zvolte **sestavit řešení** z **sestavení** nabídky. **Výstup** okno zobrazuje výsledky procesu sestavení.

   ![Sestavte projekt](../build/media/vscpp-build-solution.gif "sestavení projektu")

1. Chcete-li spustit kód, na panelu nabídek, zvolte **ladění**, **spustit bez ladění**.

   ![Spustit projekt](../build/media/vscpp-start-without-debugging.gif "spustit projekt")

   Okno konzoly otevře a spustí vaši aplikaci. Když spustíte aplikaci konzoly v sadě Visual Studio, spustí váš kód a pak vypíše "stisknutím libovolné klávesy, abyste mohli pokračovat. . ." získáte možnost zobrazit výstup.

Blahopřejeme! Vytvoření první "Hello, world!" Konzolová aplikace v sadě Visual Studio! Stisknutím jakékoli klávesy zavřete okno konzoly a vraťte se do sady Visual Studio.

[Můžu narazili na problém.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Spuštění kódu v příkazovém okně

Za normálních okolností spuštění aplikace konzoly příkazového řádku, není v sadě Visual Studio. Jakmile vaše aplikace je vytvořená pomocí sady Visual Studio, můžete ji spustit z jakékoli okno příkazového řádku. Tady je postup pro vyhledání a spuštění nové aplikace v okně příkazového řádku.

1. V **Průzkumníka řešení**, vyberte HelloWorld řešení a klikněte pravým tlačítkem na otevřete místní nabídku. Zvolte **otevřít složku v Průzkumníku souborů** otevřete **Průzkumníka souborů** okna ve složce řešení HelloWorld.

1. V **Průzkumníka souborů** okno, otevřete složku ladění. Tato položka obsahuje vaši aplikaci, HelloWorld.exe a pár dalších ladění souborů. Vyberte HelloWorld.exe, podržte stisknutou klávesu Shift a klikněte pravým tlačítkem na otevřete místní nabídku. Zvolte **kopie jako cestu** zkopírovat cestu do vaší aplikace do schránky.

1. Chcete-li otevřít okno příkazového řádku, stiskněte klávesu Windows-R otevřete **spustit** dialogového okna. Zadejte *cmd.exe* v **otevřít** textové pole, klikněte na tlačítko **OK** spustit okno příkazového řádku.

1. V okně příkazového řádku klikněte pravým tlačítkem a vložte cestu do vaší aplikace do příkazového řádku. Stiskněte klávesu Enter pro spuštění vaší aplikace.

   ![Spuštění aplikace příkazového řádku](../build/media/vscpp-run-in-cmd.gif "spuštění aplikace příkazového řádku")

Blahopřejeme, právě jste vytvořili a spustíte aplikaci konzoly v sadě Visual Studio.

[Můžu narazili na problém.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Další kroky

Jakmile jste vytvořili a spustili Tato jednoduchá aplikace, budete připravení na složitější projekty. Zobrazit [pomocí integrovaného vývojového prostředí sady Visual Studio pro vývoj v jazyce C++ Desktop](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md) podrobné návody, které prozkoumat možnosti jazyka Visual C++ v sadě Visual Studio.

## <a name="troubleshooting-guide"></a>Průvodce odstraňováním potíží

Jsou zde pro řešení běžných potíží s když vytvoříte svůj první projekt C++.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Sestavte a spusťte váš kód v problémy v sadě Visual Studio

Pokud červenou vlnovkou Microsoft.VSTS.Common nic v editoru zdrojového kódu, sestavení může být chyby nebo varování. Zkontrolujte, jestli váš kód odpovídá příklad v pravopisu, interpunkce a případ.

[Vrať se.](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Spuštění kódu v příkazovém okně problémy

Můžete také přejít ke složce řešení ladění na příkazový řádek pro spuštění vaší aplikace. Nelze spustit aplikaci z jiných adresářů bez zadání cesta k aplikaci. Můžete však zkopírovat vaší aplikace do jiného adresáře a spustit ho odtud.

Pokud nevidíte **kopie jako cestu** v místní nabídce zrušit v nabídce a potom podržte stisknutou klávesu Shift a znovu otevřete. Toto platí jenom pro usnadnění práce. Můžete také zkopírovat cestu ke složce z panelu hledání v Průzkumníkovi souborů a vložte ho do **spustit** dialogového okna a potom zadejte název spustitelný soubor na konci. Je jen trochu více psát, ale má stejný výsledek.

[Vrať se.](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
