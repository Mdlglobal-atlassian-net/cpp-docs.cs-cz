---
title: Instalace podpory jazyka C++ v sadě Visual Studio
description: Instalace podpory sady Visual Studio pro visual c++
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: d3018bef9254a8eab557057c035cde84310a2452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335370"
---
# <a name="install-c-support-in-visual-studio"></a>Instalace podpory jazyka C++ v sadě Visual Studio

Pokud jste si ještě nestáhli a nenainstalovali Visual Studio a nástroje Visual C++, tady je postup, jak začít.

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Instalace Visual Studia 2019

Vítáme vás v Visual Studiu 2019! V této verzi je snadné vybrat a nainstalovat pouze funkce, které potřebujete. A díky snížené minimální půdorysu se instaluje rychle a s menším dopadem na systém.

> [!NOTE]
> Toto téma se týká instalace sady Visual Studio v systému Windows. [Visual Studio Code](https://code.visualstudio.com/) je lehké vývojové prostředí napříč platformami, které běží na systémech Windows, Mac a Linux. Rozšíření Kódu Microsoft [C/C++ pro Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) podporuje technologii IntelliSense, ladění, formátování kódu, automatické dokončování. Visual Studio pro Mac nepodporuje Microsoft C++, ale podporuje jazyky .NET a vývoj napříč platformami. Pokyny k instalaci najdete [v tématu Instalace Visual Studia pro Mac](/visualstudio/mac/installation/).

Chcete se dozvědět více o tom, co dalšího je v této verzi nového? Podívejte se na [poznámky k verzi](/visualstudio/releases/2019/release-notes/)sady Visual Studio .

Jste připraveni k instalaci? Provedeme vás tím krok za krokem.

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Krok 1 – Ujistěte se, že je počítač připravený pro Visual Studio.

Než začnete instalovat Visual Studio:

1. Zkontrolujte [systémové požadavky](/visualstudio/releases/2019/system-requirements). Tyto požadavky vám pomohou zjistit, jestli váš počítač podporuje Visual Studio 2019.

1. Použijte nejnovější aktualizace systému Windows. Tyto aktualizace zajišťují, že počítač obsahuje nejnovější aktualizace zabezpečení a požadované systémové součásti sady Visual Studio.

1. Restartování. Restartování zajišťuje, že všechny čekající instalace nebo aktualizace nebrání instalaci sady Visual Studio.

1. Uvolněte místo. Odeberte nepotřebné soubory a aplikace z %SystemDrive % například spuštěním aplikace Vyčištění disku.

Dotazy týkající se spuštění předchozích verzí Visual Studia vedle Visual Studia 2019 najdete na stránce [Cílení a kompatibilita platformy Visual Studia 2019.](/visualstudio/releases/2019/compatibility/)

### <a name="step-2---download-visual-studio"></a>Krok 2 – stažení sady Visual Studio

Dále stáhněte soubor zaváděcího nástroje sady Visual Studio. Chcete-li tak učinit, zvolte následující tlačítko, zvolte požadovanou edici sady Visual Studio, zvolte **Uložit**a pak zvolte **Otevřít složku**.

 > [!div class="button"]
 > [Stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>Krok 3 – Instalace instalačního programu sady Visual Studio

Spusťte soubor zaváděcího nástroje a nainstalujte instalační program sady Visual Studio. Tento nový odlehčený instalační program obsahuje vše, co potřebujete k instalaci a přizpůsobení sady Visual Studio.

1. Ve složce **Soubory ke stažení** poklepejte na zaváděcí nástroj, který odpovídá jednomu z následujících souborů nebo je podobný:

   - **vs_community.exe** pro komunitu sady Visual Studio
   - **vs_professional.exe** pro Visual Studio Professional
   - **vs_enterprise.exe** pro Visual Studio Enterprise

   Pokud obdržíte oznámení o řízení uživatelských účtů, zvolte **Ano**.

1. Požádáme vás o potvrzení [licenčních podmínek společnosti](https://visualstudio.microsoft.com/license-terms/) Microsoft a [Prohlášení společnosti Microsoft o zásadách ochrany osobních údajů](https://privacy.microsoft.com/privacystatement). Zvolte **Pokračovat**.

### <a name="step-4---choose-workloads"></a>Krok 4 – výběr úloh

Po instalaci instalačního programu jej můžete použít k přizpůsobení instalace výběrem *požadovaných úloh*nebo sad funkcí. Jak na to:

1. Najdete pracovní vytížení, které chcete **na obrazovce Instalace sady Visual Studio.**

   ![Visual Studio 2019: Instalace úlohy](../get-started/media/vs-installer-workloads.png)

   Pro základní podporu jazyka C++ zvolte pracovní vytížení "Vývoj plochy s C++". Dodává se s výchozím editorem jádra, který zahrnuje základní podporu úprav kódu pro více než 20 jazyků, možnost otevřít a upravit kód z libovolné složky bez nutnosti projektu a integrovanou správu zdrojového kódu.

   Další úlohy podporují jiné druhy vývoje jazyka C++. Můžete například zvolit úlohu "Vývoj univerzální platformy Windows" a vytvářet aplikace, které používají prostředí Windows Runtime pro Microsoft Store. Chcete-li vytvořit hry, které používají rozhraní DirectX, Unreal a Cocos2d, zvolte "Vývoj her s C++". Zvolte "Vývoj Linuxu s C++" pro cílení linuxových platforem, včetně vývoje IoT.

   Podokno **podrobností instalace** obsahuje zahrnuté a volitelné součásti nainstalované jednotlivými úlohami. V tomto seznamu můžete vybrat nebo zrušit výběr volitelných součástí. Chcete-li například podporovat vývoj pomocí sad nástrojů kompilátoru sady Visual Studio 2017 nebo 2015, zvolte volitelné součásti MSVC v141 nebo MSVC v140. Můžete přidat podporu pro knihovnu MFC, rozšíření jazyka experimentální moduly, IncrediBuild a další.

1. Po výběru pracovního vytížení a volitelných součástí, které chcete, zvolte **Instalovat**.

   Dále se zobrazí stavové obrazovky, které zobrazují průběh instalace sady Visual Studio.

> [!TIP]
> Kdykoli po instalaci můžete nainstalovat úlohy nebo součásti, které jste původně nenainstalovali. Pokud máte otevřenou Visual Studio, přejděte na **nástroje** > **získat nástroje a funkce...** která otevře Instalační program sady Visual Studio. Nebo otevřete **Instalační program sady Visual Studio** z nabídky Start. Odtud můžete zvolit úlohy nebo součásti, které chcete nainstalovat. Potom zvolte **Změnit**.

### <a name="step-5---choose-individual-components-optional"></a>Krok 5 - Výběr jednotlivých součástí (volitelné)

Pokud nechcete používat funkci Úlohy k přizpůsobení instalace sady Visual Studio nebo chcete přidat více součástí, než nainstaluje pracovní vytížení, můžete tak učinit instalací nebo přidáním jednotlivých součástí na kartě **Jednotlivé součásti.**

  ![Visual Studio 2019 – instalace jednotlivých součástí](../get-started/media/vs-installer-individual-components.png "Instalace jednotlivých součástí sady Visual Studio")

### <a name="step-6---install-language-packs-optional"></a>Krok 6 – Instalace jazykových sad (volitelné)

Instalační program se ve výchozím nastavení pokusí při prvním spuštění přizpůsobit jazyk operačního systému. Chcete-li aplikaci Visual Studio nainstalovat v jazyce podle vašeho výběru, zvolte kartu **Jazykové balíčky** v instalační službě sady Visual Studio a postupujte podle pokynů.

  ![Visual Studio 2019 – instalace jazykových sad](../get-started/media/vs-installer-language-packs.png "Instalace jazykových sad Sady Visual Studio")

#### <a name="change-the-installer-language-from-the-command-line"></a>Změna jazyka instalačního programu z příkazového řádku

Dalším způsobem, jak můžete změnit výchozí jazyk, je spuštění instalačního programu z příkazového řádku. Můžete například vynutit spuštění instalačního programu v angličtině `vs_installer.exe --locale en-US`pomocí následujícího příkazu: . Instalační program si toto nastavení zapamatuje při příštím spuštění. Instalátor podporuje následující jazykové tokeny: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru a tr-tr.

### <a name="step-7---change-the-installation-location-optional"></a>Krok 7 – Změna umístění instalace (volitelné)

Můžete snížit nároky na instalaci sady Visual Studio na systémové jednotce. Můžete přesunout mezipaměť pro stahování, sdílené součásti, sady SDK a nástroje na různé jednotky a ponechat visual studio na jednotce, která ji spouští nejrychleji.

  ![Visual Studio 2019 – změna umístění instalace](../get-started/media/vs-installer-installation-locations.png "Změna umístění instalace")

> [!IMPORTANT]
> Jinou jednotku můžete vybrat pouze při první instalaci sady Visual Studio. Pokud jste ji již nainstalovali a chcete změnit jednotky, musíte odinstalovat Visual Studio a znovu ji nainstalovat.

### <a name="step-8---start-developing"></a>Krok 8 – Začněte vyvíjet

1. Po dokončení instalace sady Visual Studio zvolte tlačítko **Spustit** a s ním začít se vyvíjet.

1. V počátečním okně zvolte **Vytvořit nový projekt**.

1. Do vyhledávacího pole zadejte typ aplikace, kterou chcete vytvořit, abyste viděli seznam dostupných šablon. Seznam šablon závisí na zatížení, které jste zvolili během instalace. Chcete-li zobrazit různé šablony, zvolte různé úlohy.

   Hledání konkrétního programovacího jazyka můžete také filtrovat pomocí rozevíracího seznamu **Jazyk.** Můžete filtrovat pomocí seznamu **Platforma** a seznamu **typů projektu.**

1. Visual Studio otevře nový projekt a jste připraveni ke kódu!

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Instalace visual studia 2017

Ve Visual Studiu 2017 si můžete snadno vybrat a nainstalovat jen ty funkce, které potřebujete. A díky snížené minimální půdorysu se instaluje rychle a s menším dopadem na systém.

### <a name="prerequisites"></a>Požadavky

- Širokopásmové připojení k internetu. Instalační program sady Visual Studio může stáhnout několik gigabajtů dat.

- Počítač se systémem Microsoft Windows 7 nebo novějšími verzemi. Doporučujeme Windows 10 pro nejlepší vývojové prostředí. Před instalací sady Visual Studio se ujistěte, že jsou v systému použity nejnovější aktualizace.

- Dostatek volného místa na disku. Visual Studio vyžaduje alespoň 7 GB místa na disku a může trvat 50 GB nebo více, pokud je nainstalováno mnoho běžných možností. Doporučujeme jej nainstalovat na jednotku C: .

Podrobnosti o místě na disku a požadavcích na operační systém naleznete v [tématu Visual Studio Product Family System Requirements](/visualstudio/productinfo/vs2017-system-requirements-vs). Instalační program hlásí, kolik místa na disku je potřeba pro vybrané možnosti.

### <a name="download-and-install"></a>Stažení a instalace

1. Stáhněte si nejnovější instalační program Visual Studia 2017 pro Windows.

   > [!div class="nextstepaction"]
   > [Instalace komunity Visual Studia 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Komunitní vydání je určen pro jednotlivé vývojáře, výuku ve třídě, akademický výzkum a vývoj s otevřeným zdrojovým kódem. Pro další použití nainstalujte [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) nebo Visual Studio [2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

1. Najděte soubor instalačního programu, který jste stáhli, a spusťte jej. Může se zobrazit ve vašem prohlížeči nebo jej můžete najít ve složce Soubory ke stažení. Instalační program potřebuje ke spuštění oprávnění správce. Může se zobrazit dialogové okno **Řízení uživatelských účtů** s žádostí o povolení k provádění změn instalačního programu ve vašem systému. zvolte **Ano**. Pokud máte potíže, najděte stažený soubor v Průzkumníkovi souborů, klikněte pravým tlačítkem myši na ikonu instalačního programu a z kontextové nabídky zvolte **Spustit jako správce.**

   ![Stažení a instalace Instalačního programu sady Visual Studio](media/vscpp-concierge-run-installer.gif "Stažení a instalace Instalačního programu sady Visual Studio")

1. Instalační program vám zobrazí seznam úloh, což jsou skupiny souvisejících možností pro konkrétní oblasti vývoje. Podpora pro C++ je teď součástí volitelných úloh, které nejsou nainstalovány ve výchozím nastavení.

   ![Vývoj plochy s úlohami c++](media/desktop-development-with-cpp.png "Vývoj desktopových aplikací pomocí C++")

   V jazyce C++ vyberte vývoj plochy s úlohami **c++** a pak zvolte **Instalovat**.

   ![Instalace vývoje plochy s úlohami c++](media/vscpp-concierge-choose-workload.gif "Instalace vývoje plochy s úlohami c++")

1. Po dokončení instalace zvolte tlačítko **Spustit** a spusťte Visual Studio.

   Při prvním spuštění sady Visual Studio budete vyzváni k přihlášení pomocí účtu Microsoft. Pokud ho nemáte, můžete si ho vytvořit zdarma. Musíte také zvolit téma. Nebojte se, můžete jej změnit později, pokud chcete.

   Může trvat Několik minut, než se Visual Studio připraví k použití při prvním spuštění. Zde je to, co to vypadá v rychlém time-lapse:

   ![Přihlášení do Visual Studia 2017](media/vscpp-quickstart-first-run.gif "Přihlášení do Visual Studia 2017")

   Visual Studio se spustí mnohem rychleji, když jej spustíte znovu.

1. Když se Visual Studio otevře, zkontrolujte, jestli je zvýrazněná ikona příznaku v záhlaví:

   ![Příznak oznámení Visual Studia 2017](media/vscpp-first-start-page-flag.png "Příznak oznámení Visual Studia 2017")

   Pokud je zvýrazněná, vyberte ji, chcete-li otevřít okno **Oznámení.** Pokud jsou pro Visual Studio k dispozici nějaké aktualizace, doporučujeme je nyní nainstalovat. Po dokončení instalace restartujte visual studio.

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Instalace visual studia 2015

Pokud chcete nainstalovat Visual Studio 2015, přejděte ke [stažení starších verzí sady Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Spusťte instalační program a zvolte **Vlastní instalace** a pak zvolte komponentu C++. Chcete-li přidat podporu jazyka C++ k existující instalaci sady Visual Studio 2015, klepněte na tlačítko Start systému Windows a zadejte **příkaz Přidat odebrat programy**. Otevřete program ze seznamu výsledků a potom vyhledejte instalaci sady Visual Studio 2015 v seznamu nainstalovaných programů. Poklepejte na něj, pak zvolte **Změnit** a vyberte součásti Visual C++, které chcete nainstalovat.

Obecně doporučujeme používat Visual Studio 2017 i v případě, že potřebujete zkompilovat kód pomocí kompilátoru Visual Studio 2015. Další informace naleznete v [tématu Použití nativního vícenásobného cílení v sadě Visual Studio k vytváření starých projektů](../porting/use-native-multi-targeting.md).

::: moniker-end

Při spuštění sady Visual Studio jste připraveni pokračovat k dalšímu kroku.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Vytvoření projektu C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
