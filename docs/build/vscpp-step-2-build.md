---
title: Sestavení a spuštění projektu aplikace konzoly C++
description: Vytvoření a spuštění konzolové aplikace Hello World ve Visual C++
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
ms.openlocfilehash: d1e92e598b370312730a7c4e208b935a264010bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749239"
---
# <a name="build-and-run-a-c-console-app-project"></a>Sestavení a spuštění projektu aplikace konzoly C++

Vytvořili jste projekt konzolové aplikace jazyka C++ a zadali kód. Teď ho můžete sestavit a spustit v rámci sady Visual Studio. Potom jej spusťte jako samostatnou aplikaci z příkazového řádku.

## <a name="prerequisites"></a>Požadavky

- Mít Visual Studio s desktopvývoj s c++ úlohy nainstalované a spuštěné v počítači. Pokud ještě není nainstalovaná, postupujte podle pokynů v [části Instalace podpory C++ v sadě Visual Studio](vscpp-step-0-installation.md).

- Vytvořte "Hello, World!" a zadejte jeho zdrojový kód. Pokud jste tento krok ještě neudělali, postupujte podle pokynů v části [Vytvoření projektu konzolové aplikace jazyka C++](vscpp-step-1-create.md).

Pokud Visual Studio vypadá takto, můžete aplikaci sestavit a spustit:

   ![Připraveno k sestavení nového projektu](media/vscpp-ready-to-build.png "Připraveno k sestavení nového projektu")

## <a name="build-and-run-your-code-in-visual-studio"></a>Sestavení a spuštění kódu v sadě Visual Studio

1. Chcete-li vytvořit projekt, zvolte **sestavení řešení** z nabídky **sestavení.** Okno **Výstup** zobrazuje výsledky procesu sestavení.

   ![Sestavení projektu](media/vscpp-build-solution.gif "Sestavení projektu")

1. Chcete-li kód spustit, zvolte na řádku nabídek možnost **Ladění**, **Spustit bez ladění**.

   ![Zahájení projektu](media/vscpp-start-without-debugging.gif "Zahájení projektu")

   Otevře se okno konzoly a potom spustí aplikaci. Když spustíte konzolovou aplikaci v sadě Visual Studio, spustí váš kód a vytiskne se "Stisknutím libovolné klávesy pokračujte . . ." abyste měli možnost vidět výstup.

Blahopřejeme! Vytvořil jsi svůj první "Ahoj, světe!" konzolové aplikace v sadě Visual Studio! Stisknutím klávesy zavřete okno konzoly a vraťte se do sady Visual Studio.

[Narazil jsem na problém.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Spuštění kódu v příkazovém okně

Obvykle spouštět konzolové aplikace na příkazovém řádku, nikoli v sadě Visual Studio. Jakmile je vaše aplikace vytvořená v sadě Visual Studio, můžete ji spustit z libovolného příkazového okna. Tady je postup, jak najít a spustit novou aplikaci v okně příkazového řádku.

1. V **Průzkumníku řešení**vyberte řešení HelloWorld (ne projekt HelloWorld) a klepnutím pravým tlačítkem myši otevřete kontextovou nabídku. Zvolte **Otevřít složku v Průzkumníkovi souborů,** chcete-li otevřít okno **Průzkumníka souborů** ve složce řešení HelloWorld.

1. V okně **Průzkumník souborů** otevřete složku Ladění. Tato složka obsahuje vaši aplikaci *HelloWorld.exe*a několik dalších ladicích souborů. Podržte klávesu **Shift** a kliknutím pravým tlačítkem myši na *helloworld.exe* otevřete kontextovou nabídku. Zvolte **Kopírovat jako cestu,** chcete-li zkopírovat cestu do aplikace do schránky.

1. Pokud chcete otevřít okno příkazového řádku, stisknutím **windows+r** otevřete dialogové okno **Spustit.** Zadejte *cmd.exe* do textového pole **Otevřít** a pak zvolte **OK,** chcete-li spustit okno příkazového řádku.

1. V okně příkazového řádku kliknutím pravým tlačítkem myši vložte cestu do aplikace do příkazového řádku. Stisknutím klávesy Enter spusťte aplikaci.

   ![Spuštění aplikace na příkazovém řádku](media/vscpp-run-in-cmd.gif "Spuštění aplikace na příkazovém řádku")

Gratulujeme, vytvořili jste a spusťte konzolovou aplikaci v sadě Visual Studio!

[Narazil jsem na problém.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Další kroky

Jakmile nastavíte a spustíte tuto jednoduchou aplikaci, jste připraveni na složitější projekty. Další informace naleznete [v tématu Použití ide sady Visual Studio pro vývoj plochy jazyka C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md). Obsahuje podrobnější návody, které zkoumají možnosti Microsoft C++ v sadě Visual Studio.

## <a name="troubleshooting-guide"></a>Průvodce odstraňováním potíží

Přijďte sem pro řešení běžných problémů při vytváření prvního projektu C++.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Vytvoření a spuštění kódu v sadě Visual Studio: problémy

Pokud červené vlnovky se zobrazí pod cokoli v editoru zdrojového kódu, sestavení může mít chyby nebo upozornění. Zkontrolujte, zda váš kód odpovídá příkladu pravopisu, interpunkce a velikosti písmen.

[Vrať se.](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Spuštění kódu v příkazovém okně: problémy

Pokud cesta zobrazená v Průzkumníku souborů končí v * \\HelloWorld\\HelloWorld*, jste otevřeli *projekt* HelloWorld namísto *helloworld řešení*. Budete zmateni složky Ladění, která neobsahuje vaši aplikaci. Přejděte o úroveň výš v Průzkumníkovi souborů, abyste se dostali do složky řešení, *prvníhelloworld* v cestě. Tato složka také obsahuje složky Ladění a najdete zde aplikaci.

Můžete také přejít do složky ladění řešení na příkazovém řádku a spustit aplikaci. Aplikace nebude spuštěna z jiných adresářů bez zadání cesty k aplikaci. Aplikaci však můžete zkopírovat do jiného adresáře a spustit ji odtud. Je také možné jej zkopírovat do adresáře určeného proměnnou prostředí PATH a spustit jej odkudkoli.

Pokud v místní nabídce nevidíte **Kopírovat jako cestu,** zavřete nabídku a při znovu otevření podržte klávesu **Shift.** Tento příkaz je jen pro pohodlí. Cestu ke složce můžete také zkopírovat z vyhledávacího panelu Průzkumníka souborů, vložit ji do dialogového okna **Spustit** a na konci zadat název spustitelného souboru. Je to jen trochu víc psaní, ale má stejný výsledek.

[Vrať se.](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
