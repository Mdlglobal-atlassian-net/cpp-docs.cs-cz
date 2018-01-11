---
title: "Sestavení a spuštění projektu jazyka C++ konzole aplikace | Microsoft Docs"
description: "Nainstalovat Visual Studio – podpora pro Visual C++"
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: get-started-article
ms.technology: devlang-C++
ms.devlang: C++
dev_langs: C++
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a5b9c250b102b7d8847e99b87139136bc7df808b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="build-and-run-a-c-console-app-project"></a>Sestavení a spuštění projektu aplikace konzoly jazyka C++

Když jste vytvořili projekt aplikace konzoly C++ a kódu, sestavit a spustit v sadě Visual Studio pak spusťte jako samostatnou aplikaci z příkazového řádku.

## <a name="prerequisites"></a>Požadavky

- Visual Studio s vývoj aplikací máte C++ zatížení nainstalovaná a spuštěná v počítači. Pokud ještě není nainstalovaná, postupujte podle kroků v [podpory nainstalovat C++ v sadě Visual Studio](../build/vscpp-step-0-installation.md).

- Vytvoření "Hello, World!" projekt a zadejte jeho zdrojový kód. Pokud jste to ještě neudělali, postupujte podle kroků v [vytvoření projektu aplikace konzoly C++](../build/vscpp-step-1-create.md).

Pokud Visual Studio vypadá to, jste připraveni k sestavení a spuštění aplikace:

   ![Průvodce je připraven vytvořit nový projekt](../build/media/vscpp-ready-to-build.png "Průvodce je připraven vytvořit nový projekt")

## <a name="build-and-run-your-code-in-visual-studio"></a>Sestavení a spuštění kódu v sadě Visual Studio

1. Pokud chcete vytvořit projekt, vyberte **sestavit řešení** z **sestavení** nabídky. **Výstup** v okně se zobrazí výsledky procesu sestavení.

   ![Sestavení projektu](../build/media/vscpp-build-solution.gif "sestavení projektu")

1. Chcete-li spustit kód, na panelu nabídek, zvolte **ladění**, **spustit bez ladění**.

   ![Spusťte projekt](../build/media/vscpp-start-without-debugging.gif "spusťte projekt")

    Okno konzoly otevře a spustí aplikace. Když spustíte konzolovou aplikaci v sadě Visual Studio, spuštění kódu a pak výtisků "stisknutím libovolné klávesy pokračujte. . ." získáte možnost zobrazit výstup.

Blahopřejeme! Jste vytvořili první "Hello, world!" konzolové aplikace v sadě Visual Studio! Stiskněte klávesu zrušit okno konzoly a vrátíte se k sadě Visual Studio.

[Byl spuštěn na problém.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Spuštění kódu v příkazovém okně

Za normálních okolností spustit konzolu aplikace příkazového řádku, není v sadě Visual Studio. Po aplikaci Visual Studio, ho můžete spustit z jakékoli příkazové okno. Zde je způsob vyhledání a spuštění nové aplikace v okně příkazového řádku.

1. V **Průzkumníku řešení**vyberte HelloWorld řešení a pravým tlačítkem a otevřete kontextu nabídku. Zvolte **otevřete složky v Průzkumníku souborů** otevřete **Průzkumníka souborů** okno ve složce HelloWorld řešení.

1. V **Průzkumníka souborů** okno, otevřete složku ladění. Tato položka obsahuje aplikace, HelloWorld.exe a několik dalších soubory ladění. Vyberte HelloWorld.exe, podržte stisknutou klávesu Shift a pravým tlačítkem a otevřete kontextu nabídku. Zvolte **kopie jako cestu** zkopírujte cestu do vaší aplikace do schránky.

1. Chcete-li otevřít okno příkazového řádku, stiskněte klávesu Windows-R otevřete **spustit** dialogové okno. Zadejte *cmd.exe* v **otevřete** textovému poli, zvolte **OK** spustit okno příkazového řádku.

1. V okně příkazového řádku klikněte pravým tlačítkem myši, vložte cestu do vaší aplikace do příkazového řádku. Stiskněte klávesu Enter pro spuštění aplikace.

   ![Spuštění aplikace příkazového řádku](../build/media/vscpp-run-in-cmd.gif "spuštění aplikace příkazového řádku")

Blahopřejeme, jste vytvořené a spusťte konzolovou aplikaci v sadě Visual Studio.

[Byl spuštěn na problém.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Další kroky

Jakmile jste vytvořené a spusťte tento jednoduchou aplikaci, jste připraveni pro složitější projekty. V tématu [pomocí prostředí Visual Studio IDE pro vývoje v jazyce C++ plochy](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md) podrobné návody, které prozkoumat možnosti aplikace Visual C++ v sadě Visual Studio.

## <a name="troubleshooting-guide"></a>Průvodce odstraňováním potíží s

Tohoto prostoru pro řešení pro běžné problémy při vytvoření prvního projektu C++.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Sestavení a spuštění kódu v sadě Visual Studio problémy

Pokud se zobrazí červený podtržení vlnovkou pod nic v editoru zdrojového kódu, sestavení může mít chyby nebo upozornění. Zkontrolujte, jestli odpovídá kódu v příkladu v pravopis a interpunkce a písmena.

[Vrať se.](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Spuštění kódu v příkazovém okně problémy

Můžete také přejít do složky ladění řešení na příkazovém řádku ke spouštění vaší aplikace. Aplikaci nelze spustit z dalších adresářů bez určení cesty k aplikaci. Můžete však kopírovat aplikace do jiného adresáře a spusťte jej z.

[Vrať se.](#run-your-code-in-a-command-window)


<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
