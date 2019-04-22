---
title: Instalace podpory jazyka C++ v sadě Visual Studio
description: Nainstalovat Visual Studio – podpora pro Visual C++
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 2c2bed4063194bdc3c0f3fbc405be6bf9a4031e7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58870777"
---
# <a name="install-c-support-in-visual-studio"></a>Instalace podpory jazyka C++ v sadě Visual Studio

Pokud jste ještě stáhli a nainstalovali aplikaci Visual Studio a nástrojů Visual C++ ještě, tady je postup, abyste mohli začít.

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Visual Studio 2019 Installation

Vítá vás Visual Studio 2019! V této verzi je snadno vybrat a instalace jen těch funkcí, které potřebujete. A z důvodu jeho nižší minimální nároky na místo, nainstaluje rychle a s menšími dopady na systém.

> [!NOTE]
> Toto téma platí pro instalaci sady Visual Studio na Windows. [Visual Studio Code](https://code.visualstudio.com/) je zjednodušené, multiplatformní vývojové prostředí, na kterém běží v systémech Windows, Mac a Linux. Microsoft [C/C++ pro Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) rozšíření podporuje technologii IntelliSense, ladění, formátování, automatické dokončování kódu. Visual Studio for Mac nepodporuje Microsoft C++, ale podporuje vývoj napříč platformami a jazyky rozhraní .NET. Pokyny k instalaci, naleznete v tématu [instalace sady Visual Studio pro Mac](/visualstudio/mac/installation/).

Chcete vědět více o tom, co je nového v této verzi? Visual Studio naleznete v tématu [poznámky k verzi](/visualstudio/releases/2019/release-notes/).

Připraveno k instalaci? Provedeme vás přes něj krok za krokem.

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Krok 1: Ujistěte se, že váš počítač připravený pro sadu Visual Studio

Před zahájením instalace sady Visual Studio:

1. Zkontrolujte, [požadavky na systém](/visualstudio/releases/2019/system-requirements). Tyto požadavky vám pomohli určit, jestli počítač podporuje Visual Studio 2019.

1. Použijte nejnovější aktualizace Windows. Tyto aktualizace zkontrolujte, zda má počítač nejnovější aktualizace zabezpečení a požadované systémové komponenty pro sadu Visual Studio.

1. Restartování počítače. Restartování zajistí, že instalaci sady Visual Studio nebudou bránit probíhající instalace nebo aktualizace.

1. Uvolněte místo. Odeberte nepotřebné soubory a aplikace z % SystemDrive %, například spuštěním aplikace Vyčištění disku.

Dotazy týkající se spouštění předchozích verzí sady Visual Studio souběžně s Visual Studio 2019, najdete v článku [Visual Studio. 2019 cílení na platformy a Kompatibilita](/visualstudio/releases/2019/compatibility/) stránky.

### <a name="step-2---download-visual-studio"></a>Krok 2: stažení sady Visual Studio

Dále si stáhněte soubor zaváděcího nástroje sady Visual Studio. Uděláte to tak, klikněte na následující tlačítko, zvolte edici sady Visual Studio, které chcete, zvolte **Uložit**a klikněte na tlačítko **otevřít složku**.

 > [!div class="button"]
 > [Stáhněte si Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>Krok 3: instalace instalační program sady Visual Studio

Spusťte soubor zaváděcí nástroj k instalaci instalačního programu sady Visual Studio. Tohoto nového zjednodušeného instalačního programu obsahuje všechno, co je potřeba nainstalovat i přizpůsobení sady Visual Studio.

1. Z vaší **stáhne** složky, dvakrát klikněte na panel zaváděcí nástroj, který odpovídá nebo se podobá následující soubory:

   * **vs_community.exe** pro Visual Studio Community
   * **vs_professional.exe** for Visual Studio Professional
   * **vs_enterprise.exe** pro Visual Studio Enterprise

   Pokud se zobrazí oznámení o řízení uživatelských účtů, zvolte **Ano**.

1. Požádáme vás potvrďte Microsoft [licenční podmínky](https://visualstudio.microsoft.com/license-terms/) a Microsoft [prohlášení o zásadách](https://privacy.microsoft.com/privacystatement). Zvolte **pokračovat**.

### <a name="step-4---choose-workloads"></a>Krok 4 – volba úlohy

Po dokončení instalace instalační program vám pomůže ho svou instalaci přizpůsobit tak, že vyberete *úlohy*, nebo sady, které chcete, aby funkcí. Tady je způsob.

1. Najít úlohu, kterou chcete v **instalaci sady Visual Studio** obrazovky.

   ![Visual Studio 2019: Nainstalujte úlohu](../get-started/media/vs-installer-workloads.png)

   Podpora jádra C++ zvolte úlohu "Vývoj desktopových aplikací pomocí C++". Obsahuje výchozí základní editor, který obsahuje základní podporu pro více než 20 jazycích, schopnost otevírat a upravovat kód z libovolné složky bez nutnosti vytvářet projekt, editaci kódu a integrované správy zdrojového kódu.

   Další úlohy podporují jiné druhy vývoj v jazyce C++. Například zvolte úlohu "Vývoj pro univerzální platformu Windows" k vytvoření aplikace, které používají Windows Runtime pro Microsoft Store. Zvolte možnost "Vývoj her pomocí C++" vytváření her, které používají rozhraní DirectX, Unreal nebo Cocos2d. Zvolte možnost "Vývoj pro Linux v C++" na cílové platformy Linux, včetně vývoje s IoT.

   **Podrobné informace o instalaci** podokno obsahuje zahrnuté a volitelné komponenty nainstalované při každé úloze. Můžete vybrat nebo zrušit výběr volitelné součásti v tomto seznamu. Například pro podporu vývoje aplikací pomocí sady Visual Studio 2017 nebo 2015 kompilátoru sady nástrojů, zvolte MSVC v141 nebo MSVC v140 volitelné součásti. Můžete přidat podporu knihovny MFC, experimentální rozšíření jazyka moduly, IncrediBuild a další.

1. Po zvolení workload(s) a volitelné komponenty, které chcete vybrat **nainstalovat**.

    V dalším kroku stav obrazovek, které zobrazí průběh instalace sady Visual Studio.

> [!TIP]
> Kdykoli po instalaci můžete nainstalovat úlohy nebo komponenty, které nenainstaloval původně. Pokud máte Visual Studio otevřete, přejděte na **nástroje** > **získat nástroje a funkce...**  tím se otevře instalačního programu sady Visual Studio. Nebo otevřete **instalační program sady Visual Studio** z nabídky Start. Odtud můžete vybrat úlohy nebo komponenty, které chcete nainstalovat. Potom kliknutím na možnost **změnit**.

## <a name="step-5---choose-individual-components-optional"></a>Krok 5: zvolit jednotlivé součásti (volitelné)

Pokud nechcete použít funkci úlohy k přizpůsobení instalace sady Visual Studio nebo které chcete přidat další komponenty, než úloha nainstaluje, lze provést instalaci nebo přidáním jednotlivé komponenty z **jednotlivé komponenty** kartu. Zvolte, co chcete a pak postupujte podle pokynů.

  ![Visual Studio 2019 – instalace jednotlivých součástí](../get-started/media/vs-installer-individual-components.png "jednotlivých součástí instalace sady Visual Studio")

## <a name="step-6---install-language-packs-optional"></a>Krok 6 – instalace jazykových sad (volitelné)

Ve výchozím nastavení instalační program pokusí tak, aby odpovídala jazyku operačního systému při prvním spuštění. Chcete-li nainstalovat Visual Studio v jazyce podle vašeho výběru, zvolte **jazykových sad** kartu z instalačního programu sady Visual Studio a pak postupujte podle pokynů.

  ![Visual Studio 2019 – instalace jazykových sad](../get-started/media/vs-installer-language-packs.png "jazykové sady Nainstalujte Visual Studio")

### <a name="change-the-installer-language-from-the-command-line"></a>Změnit jazyk instalačního programu z příkazového řádku

Dalším způsobem, že můžete změnit výchozí jazyk je spuštění instalačního programu z příkazového řádku. Například můžete vynutit instalační program pro spuštění v anglickém jazyce pomocí následujícího příkazu: `vs_installer.exe --locale en-US`. Instalační program bude mějte na paměti Toto nastavení při příštím spuštění. Instalační program podporuje následující klíčová slova jazyka: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru a tr-tr.

### <a name="step-7---change-the-installation-location-optional"></a>Krok 7: Změna umístění instalace (volitelné)

Můžete snížit nároky na instalaci sady Visual Studio na systémovou jednotku. Můžete se rozhodnout, zda budou přesunuty mezipaměť pro stahování, sdílených komponent, sady SDK a nástrojů na jiné jednotky a sady Visual Studio na disku, na kterém běží nejrychlejší.

  ![Visual Studio 2019 - Změna umístění instalací](../get-started/media/vs-installer-installation-locations.png "Změna umístění instalace")

> [!IMPORTANT]
> Pouze při první instalaci sady Visual Studio, můžete vybrat jinou jednotku. Pokud jste již nainstalovali a chcete změnit jednotky, je nutné odinstalovat Visual Studio a pak ho znovu nainstalujte.

## <a name="step-8---start-developing"></a>Krok 8: začít s vývojem

1. Po dokončení instalace sady Visual Studio, zvolte **spuštění** tlačítko, abyste mohli začít vyvíjet pomocí sady Visual Studio.

1. V okně start zvolte **vytvořte nový projekt**.

1. Do vyhledávacího pole zadejte aplikace, kterou chcete vytvořit zobrazíte seznam dostupných šablon. Seznam šablon závisí na workload(s), kterou jste zvolili během instalace. Chcete-li zobrazit různé šablony služby, zvolte různé úlohy.

   Můžete také filtrovat hledání pro konkrétní programovací jazyk s využitím **jazyk** rozevíracího seznamu. Můžete filtrovat pomocí **platformy** seznamu a **typ projektu** příliš seznamu.

1. Visual Studio otevře nový projekt a jste připraveni kód!

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Visual Studio 2017 Installation

V sadě Visual Studio 2017 je snadné zvolte a instalace jen těch funkcí, které potřebujete. A z důvodu jeho nižší minimální nároky na místo, nainstaluje rychle a s menšími dopady na systém.

### <a name="prerequisites"></a>Požadavky

- Širokopásmové připojení k Internetu. Několik gigabajtů dat můžete stáhnout instalační program sady Visual Studio.

- Počítač, na kterém běží Microsoft Windows 7 nebo novější verze. Doporučujeme pro nejlepší vývojové prostředí Windows 10. Ujistěte se, že použijí nejnovější aktualizace vašeho systému před instalací sady Visual Studio.

- Dost volného místa na disku. Visual Studio vyžaduje alespoň 7 GB místa na disku a může trvat 50 GB a více, pokud jsou nainstalovány mnoho běžných možností. Doporučujeme, abyste že ho nainstalujete na jednotce C:.

Podrobnosti o místo na disku a požadavky na operační systém, najdete v části [Visual Studio produktová řada požadavky na systém](/visualstudio/productinfo/vs2017-system-requirements-vs). Instalační program hlásí, kolik místa na disku požadované pro možnosti, které vyberete.

### <a name="download-and-install"></a>Stažení a instalace

1. Stáhněte si nejnovější instalační program sady Visual Studio 2017 pro Windows.

   > [!div class="nextstepaction"]
   > [Nainstalovat sadu Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Edice Community je pro jednotlivé vývojáře, školní výuka, vědecký výzkum a vývoj open source. Pro jiné účely, nainstalujte [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) nebo [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

1. Najdete soubor Instalační program stáhnout a spustit ho. Může se zobrazit v prohlížeči, nebo může být pro vás ve složce stažené soubory. Instalační program potřebuje správce oprávnění ke spuštění. Může se zobrazit **řízení uživatelských účtů** dialogové okno s výzvou, abyste udělili oprávnění, aby instalační program provádět změny systému, zvolte **Ano**. Pokud máte potíže, vyhledejte stažený soubor v Průzkumníku souborů klikněte pravým tlačítkem na ikonu instalační program a zvolte **spustit jako správce** v místní nabídce.

   ![Stáhněte a nainstalujte Instalační program sady Visual Studio](media/vscpp-concierge-run-installer.gif "stáhnout a nainstalovat Instalační program sady Visual Studio")

1. Instalační program vám nabídne seznam úloh, které jsou skupiny související možnosti jsou pro vývoj pro konkrétní oblasti. Podpora jazyka C++ je teď součástí volitelné úlohy, které ve výchozím nastavení nenainstalují.

   ![Vývoj desktopových aplikací pomocí úlohy pro C++](media/desktop-development-with-cpp.png "vývoj desktopových aplikací pomocí C++")

   Pro jazyk C++, vyberte **vývoj desktopových aplikací pomocí C++** úloh a klikněte na tlačítko **nainstalovat**.

   ![Instalace vývoj desktopových aplikací pomocí úlohy pro C++](media/vscpp-concierge-choose-workload.gif "instalace vývoj desktopových aplikací pomocí úlohy pro C++")

1. Po dokončení instalace, zvolte **spuštění** tlačítko pro spuštění sady Visual Studio.

   Při prvním spuštění aplikace Visual Studio, budete vyzváni k přihlášení pomocí pověření Account Microsoft. Pokud ho nemáte, můžete jeden vytvořit zdarma. Musíte také zvolit jen motiv. Nedělejte si starosti, pokud chcete ji můžete změnit později.

   Visual Studio to trvat několik minut, než se připravit k použití při prvním spuštění. Zde je, jak to vypadá v rychlého časové závislosti:

   ![Přihlaste se Visual Studio 2017](media/vscpp-quickstart-first-run.gif "přihlášení Visual Studio 2017")

   Můžete ho spustit znovu spustí aplikace Visual Studio mnohem rychleji.

1. Při otevření sady Visual Studio, zkontrolujte, pokud je zvýrazněn příznak ikona v záhlaví okna:

   ![Příznak oznámení Visual Studio 2017](media/vscpp-first-start-page-flag.png "příznaku oznámení v sadě Visual Studio 2017")

   Pokud je zvýrazněn, vyberte ji a otevřete **oznámení** okna. Pokud nejsou k dispozici pro sadu Visual Studio žádné aktualizace, doporučujeme, abyste že je teď nainstalujete. Po dokončení instalace restartujte Visual Studio.

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Visual Studio 2015 Installation

Chcete-li nainstalovat sadu Visual Studio 2015, přejděte na [starší verze sady Visual Studio si můžete stáhnout](https://www.visualstudio.com/vs/older-downloads/). Spusťte instalační program a zvolte **vlastní instalace** a klikněte na tlačítko komponent C++. Chcete-li přidat podporu C++ do existující instalace sady Visual Studio 2015, klikněte na tlačítko Windows Start a typ **přidat nebo odebrat programy**. Otevřete program ze seznamu výsledků a pak v seznamu nainstalovaných programů najít instalaci sady Visual Studio 2015. Poklepejte na něj a pak zvolte **změnit** a vybrat součásti Visual C++ k instalaci.

Obecně platí důrazně doporučujeme použít Visual Studio 2017, i v případě, že budete potřebovat ke kompilaci kódu pomocí kompilátoru Visual Studio 2015. Další informace najdete v tématu [pomocí nativního cílení na více platforem v sadě Visual Studio sestavení starých projektů](../porting/use-native-multi-targeting.md).

::: moniker-end

Když je spuštěná sada Visual Studio, jste připraveni pokračovat k dalšímu kroku.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Vytvoření projektu jazyka C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
