---
title: Sestavení a spuštění projektu aplikace konzoly C++
description: Sestavení a spuštění aplikace konzoly Hello World v Visual C++
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

Vytvořili jste projekt konzolové aplikace C++ a zadali jste kód. Nyní ji můžete sestavit a spustit v rámci sady Visual Studio. Pak ji spusťte jako samostatnou aplikaci z příkazového řádku.

## <a name="prerequisites"></a>Požadavky

- Máte aplikaci Visual Studio s nainstalovanou a spuštěnou úlohou vývoj desktopových aplikací v jazyce C++. Pokud ještě není nainstalován, postupujte podle kroků v části [Instalace podpory C++ v aplikaci Visual Studio](vscpp-step-0-installation.md).

- Vytvořit "Hello, World!" projekt a zadejte jeho zdrojový kód. Pokud jste tento krok ještě neudělali, postupujte podle kroků v části [Vytvoření projektu konzolové aplikace C++](vscpp-step-1-create.md).

Pokud Visual Studio vypadá takto, jste připraveni sestavit a spustit aplikaci:

   ![Připraveno k vytvoření nového projektu](media/vscpp-ready-to-build.png "Připraveno k vytvoření nového projektu")

## <a name="build-and-run-your-code-in-visual-studio"></a>Sestavení a spuštění kódu v aplikaci Visual Studio

1. Chcete-li sestavit projekt, v nabídce **sestavení** klikněte na příkaz **Sestavit řešení** . V okně **výstup** se zobrazí výsledky procesu sestavení.

   ![Sestavení projektu](media/vscpp-build-solution.gif "Sestavení projektu")

1. Chcete-li spustit kód, na panelu nabídek vyberte možnost **ladit**, **Spustit bez ladění**.

   ![Spustit projekt](media/vscpp-start-without-debugging.gif "Spustit projekt")

   Otevře se okno konzoly a pak se spustí vaše aplikace. Když spustíte konzolovou aplikaci v aplikaci Visual Studio, spustí se váš kód a potom se zobrazí zpráva pro pokračování stiskněte libovolnou klávesu. . ." abyste měli možnost zobrazit výstup.

Blahopřejeme! Vytvořili jste první "Hello, World!" Konzolová aplikace v aplikaci Visual Studio! Stisknutím klávesy zavřete okno konzoly a vraťte se do sady Visual Studio.

[Narazili jsme na problém.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Spuštění kódu v příkazovém okně

Obvykle spouštíte konzolové aplikace z příkazového řádku, nikoli v aplikaci Visual Studio. Po sestavení aplikace v aplikaci Visual Studio ji můžete spustit z libovolného okna příkazu. Tady je postup, jak najít a spustit novou aplikaci v okně příkazového řádku.

1. V **Průzkumník řešení**vyberte řešení HelloWorld (ne projekt HelloWorld) a kliknutím pravým tlačítkem otevřete místní nabídku. Zvolením možnosti **Otevřít složku v Průzkumníkovi souborů** otevřete okno **Průzkumníka souborů** ve složce řešení HelloWorld.

1. V okně **Průzkumník souborů** otevřete složku ladění. Tato složka obsahuje vaši aplikaci, *HelloWorld. exe*a několik dalších souborů pro ladění. Podržte stisknutou klávesu **SHIFT** a kliknutím pravým tlačítkem na soubor *HelloWorld. exe* otevřete kontextovou nabídku. Zvolením možnosti **Kopírovat jako cestu** zkopírujte cestu k aplikaci do schránky.

1. Chcete-li otevřít okno příkazového řádku, stiskněte kombinaci kláves **Windows + R** a otevřete dialogové okno **spuštění** . Do textového pole **otevřít** zadejte *cmd. exe* a pak zvolte **OK** . tím spustíte okno příkazového řádku.

1. V okně příkazového řádku kliknutím pravým tlačítkem myši vložte cestu do aplikace do příkazového řádku. Pro spuštění aplikace stiskněte klávesu ENTER.

   ![Spusťte aplikaci na příkazovém řádku.](media/vscpp-run-in-cmd.gif "Spusťte aplikaci na příkazovém řádku.")

Blahopřejeme, vytvořili jste a spustili konzolovou aplikaci v aplikaci Visual Studio!

[Narazili jsme na problém.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Další kroky

Po vytvoření a spuštění této jednoduché aplikace jste připraveni na složitější projekty. Další informace najdete v tématu [použití integrovaného vývojového prostředí (IDE) sady Visual Studio pro C++ Desktop](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md). Obsahuje podrobnější návody, které Prozkoumejte možnosti Microsoft C++ v aplikaci Visual Studio.

## <a name="troubleshooting-guide"></a>Průvodce odstraňováním potíží

Zde najdete řešení běžných problémů při vytváření prvního projektu v jazyce C++.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Sestavování a spouštění kódu v aplikaci Visual Studio: problémy

Pokud se červené vlnovky zobrazují pod jakýmkoli editorem zdrojového kódu, může být sestavení v případě chyb nebo upozornění. Zkontrolujte, zda váš kód odpovídá příkladu v pravopisu, interpunkci a velikosti písmen.

[Vrať se.](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Spuštění kódu v příkazovém okně: problémy

Pokud cesta zobrazená v Průzkumníkovi souborů končí na * \\HelloWorld\\Hello*, otevřeli jste *projekt* HelloWorld namísto *řešení*HelloWorld. Složku pro ladění, která neobsahuje vaši aplikaci, zapamatujete. Přejděte nahoru na úroveň v Průzkumníkovi souborů, abyste se dostali do složky řešení, na první *HelloWorld* v cestě. Tato složka také obsahuje složku pro ladění a v ní najdete aplikaci.

Můžete také přejít do složky ladění řešení na příkazovém řádku a spustit tak aplikaci. Vaše aplikace se nebude spouštět z jiných adresářů bez určení cesty k aplikaci. Můžete ale zkopírovat aplikaci do jiného adresáře a spustit ji odtud. Je také možné ji zkopírovat do adresáře zadaného proměnnou prostředí PATH a pak ji spustit odkudkoli.

Pokud nevidíte v místní nabídce příkaz **Kopírovat jako cestu** , zavřete nabídku a potom stiskněte klávesu **SHIFT** , zatímco ji znovu otevřete. Tento příkaz je jenom pro pohodlí. Můžete také zkopírovat cestu ke složce z panelu hledání v Průzkumníkovi souborů a vložit ji do dialogového okna **Spustit** a pak na konci zadat název spustitelného souboru. Je to jen pár dalších psaní, ale má stejný výsledek.

[Vrať se.](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
