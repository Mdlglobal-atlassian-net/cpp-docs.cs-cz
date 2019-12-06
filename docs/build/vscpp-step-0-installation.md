---
title: Instalace podpory jazyka C++ v sadě Visual Studio
description: Nainstalovat podporu sady Visual Studio pro VisualC++
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: a20a2432cbf8c4dc5f211f6f483c0084888f1199
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857161"
---
# <a name="install-c-support-in-visual-studio"></a>Instalace podpory jazyka C++ v sadě Visual Studio

Pokud jste ještě nestáhli a nainstalovali Visual Studio a C++ Visual Tools, tady je postup, jak začít.

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Instalace sady Visual Studio 2019

Vítá vás Visual Studio 2019! V této verzi si snadno zvolíte a nainstalujete jenom ty funkce, které potřebujete. A kvůli jejich menšímu minimálnímu množství je instalace rychle a s menším dopadem na systém.

> [!NOTE]
> Toto téma se vztahuje na instalaci sady Visual Studio ve Windows. [Visual Studio Code](https://code.visualstudio.com/) je zjednodušené vývojové prostředí pro různé platformy, které běží na systémech Windows, Mac a Linux. Rozšíření Microsoft [C/C++ pro Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) podporuje technologii IntelliSense, ladění, formátování kódu, automatické dokončování. Visual Studio pro Mac nepodporuje Microsoft C++, ale podporuje jazyky .NET a vývoj pro různé platformy. Pokyny k instalaci najdete v tématu [instalace Visual Studio pro Mac](/visualstudio/mac/installation/).

Chcete vědět více o tom, co je nového v této verzi? Přečtěte si [poznámky k verzi](/visualstudio/releases/2019/release-notes/)sady Visual Studio.

Připraveno k instalaci? Provedeme vás přes něj krok za krokem.

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Krok 1: Ujistěte se, že váš počítač připravený pro sadu Visual Studio

Před zahájením instalace sady Visual Studio:

1. Zkontrolujte, [požadavky na systém](/visualstudio/releases/2019/system-requirements). Tyto požadavky vám pomůžou zjistit, jestli váš počítač podporuje Visual Studio 2019.

1. Použijte nejnovější aktualizace Windows. Tyto aktualizace zkontrolujte, zda má počítač nejnovější aktualizace zabezpečení a požadované systémové komponenty pro sadu Visual Studio.

1. Restartování počítače. Restartování zajistí, že instalaci sady Visual Studio nebudou bránit probíhající instalace nebo aktualizace.

1. Uvolněte místo. Odeberte nepotřebné soubory a aplikace z % SystemDrive %, například spuštěním aplikace Vyčištění disku.

Dotazy týkající se spouštění předchozích verzí sady Visual Studio vedle sebe se sadou Visual Studio 2019 naleznete na stránce [cílení a kompatibilita platformy Visual studio 2019](/visualstudio/releases/2019/compatibility/) .

### <a name="step-2---download-visual-studio"></a>Krok 2: stažení sady Visual Studio

Dále si stáhněte soubor zaváděcího nástroje sady Visual Studio. Chcete-li to provést, zvolte následující tlačítko, zvolte požadovanou verzi sady Visual Studio, zvolte možnost **Uložit**a pak zvolte možnost **Otevřít složku**.

 > [!div class="button"]
 > [Stáhnout Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>Krok 3: instalace instalační program sady Visual Studio

Spuštěním souboru zaváděcího nástroje nainstalujte Instalační program pro Visual Studio. Tento nový odlehčený instalační program zahrnuje všechno, co potřebujete k instalaci i přizpůsobení sady Visual Studio.

1. Z vaší **stáhne** složky, dvakrát klikněte na panel zaváděcí nástroj, který odpovídá nebo se podobá následující soubory:

   * **vs_community.exe** pro Visual Studio Community
   * **vs_professional.exe** for Visual Studio Professional
   * **vs_enterprise.exe** pro Visual Studio Enterprise

   Pokud se zobrazí upozornění na řízení uživatelských účtů, vyberte **Ano**.

1. Požádáme vás potvrďte Microsoft [licenční podmínky](https://visualstudio.microsoft.com/license-terms/) a Microsoft [prohlášení o zásadách](https://privacy.microsoft.com/privacystatement). Zvolte **pokračovat**.

### <a name="step-4---choose-workloads"></a>Krok 4 – Výběr úloh

Až instalační program nainstalujete, můžete ho použít k přizpůsobení instalace tak, že vyberete *úlohy*nebo sady funkcí, které chcete. Tady je způsob.

1. Najít úlohu, kterou chcete v **instalaci sady Visual Studio** obrazovky.

   ![Visual Studio 2019: instalace úlohy](../get-started/media/vs-installer-workloads.png)

   U možnosti C++ základní podpora vyberte úlohu vývoj pro počítače pomocí C++úlohy. Obsahuje výchozí základní editor, který obsahuje základní podporu pro více než 20 jazycích, schopnost otevírat a upravovat kód z libovolné složky bez nutnosti vytvářet projekt, editaci kódu a integrované správy zdrojového kódu.

   Další úlohy podporují jiné druhy C++ vývoje. Například vyberte úlohu Univerzální platforma Windows vývoj pro vytváření aplikací, které používají prostředí Windows Runtime pro Microsoft Store. Pokud chcete vytvořit hry, C++které používají rozhraní DirectX, Unreal a Cocos2d, vyberte vývoj her pomocí. Pro cílení platforem Linux C++, včetně vývoje IoT, vyberte vývoj pro Linux pomocí.

   V podokně **podrobností o instalaci** jsou uvedeny zahrnuté a volitelné komponenty nainstalované jednotlivými úlohami. V tomto seznamu můžete vybrat volitelné součásti nebo zrušit jejich výběr. Například pro podporu vývoje pomocí sad nástrojů kompilátoru sady Visual Studio 2017 nebo 2015 vyberte volitelné komponenty MSVC v141 nebo MSVC v140. Můžete přidat podporu pro MFC, jazykové rozšíření experimentálních modulů, IncrediBuild a další.

1. Jakmile vyberete úlohy a volitelné součásti, které chcete, klikněte na tlačítko **nainstalovat**.

    V dalším kroku stav obrazovek, které zobrazí průběh instalace sady Visual Studio.

> [!TIP]
> Kdykoli po instalaci můžete nainstalovat úlohy nebo komponenty, které nenainstaloval původně. Pokud máte Visual Studio otevřete, přejděte na **nástroje** > **získat nástroje a funkce...**  tím se otevře instalačního programu sady Visual Studio. Nebo otevřete **instalační program sady Visual Studio** z nabídky Start. Odtud můžete zvolit úlohy nebo komponenty, které chcete nainstalovat. Pak zvolte **Upravit**.

### <a name="step-5---choose-individual-components-optional"></a>Krok 5 – výběr jednotlivých komponent (volitelné)

Pokud nechcete použít funkci úlohy k přizpůsobení instalace sady Visual Studio nebo chcete přidat další součásti, než kolik je potřeba, můžete to udělat tak, že nainstalujete nebo přidáte jednotlivé komponenty z karty **jednotlivé komponenty** . Zvolte, co chcete, a pak postupujte podle pokynů.

  ![Visual Studio 2019 – instalace jednotlivých komponent](../get-started/media/vs-installer-individual-components.png "Instalovat jednotlivé součásti sady Visual Studio")

### <a name="step-6---install-language-packs-optional"></a>Krok 6 – instalace jazykových sad (volitelné)

Ve výchozím nastavení instalační program pokusí tak, aby odpovídala jazyku operačního systému při prvním spuštění. Chcete-li nainstalovat sadu Visual Studio v jazyce podle vašeho výběru, zvolte kartu **jazykové sady** z instalační program pro Visual Studio a potom postupujte podle pokynů.

  ![Visual Studio 2019 – instalace jazykových sad](../get-started/media/vs-installer-language-packs.png "Nainstalovat jazykové sady pro Visual Studio")

#### <a name="change-the-installer-language-from-the-command-line"></a>Změnit jazyk instalačního programu z příkazového řádku

Dalším způsobem, že můžete změnit výchozí jazyk je spuštění instalačního programu z příkazového řádku. Například můžete vynutit instalační program pro spuštění v anglickém jazyce pomocí následujícího příkazu: `vs_installer.exe --locale en-US`. Instalační program si toto nastavení zapamatuje, jakmile bude příště spuštěn. Instalační program podporuje následující klíčová slova jazyka: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru a tr-tr.

### <a name="step-7---change-the-installation-location-optional"></a>Krok 7: Změna umístění instalace (volitelné)

Nároky na instalaci sady Visual Studio můžete snížit na systémové jednotce. Můžete se rozhodnout, zda budou přesunuty mezipaměť pro stahování, sdílených komponent, sady SDK a nástrojů na jiné jednotky a sady Visual Studio na disku, na kterém běží nejrychlejší.

  ![Visual Studio 2019 – Změna umístění instalace](../get-started/media/vs-installer-installation-locations.png "Změna umístění instalace")

> [!IMPORTANT]
> Můžete vybrat jinou jednotku pouze při první instalaci sady Visual Studio. Pokud jste ho už nainstalovali a chcete změnit jednotky, musíte odinstalovat sadu Visual Studio a pak ji znovu nainstalovat.

### <a name="step-8---start-developing"></a>Krok 8: začít s vývojem

1. Po dokončení instalace sady Visual Studio klikněte na tlačítko **Spustit** a začněte s vývojem v aplikaci Visual Studio.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

1. Do vyhledávacího pole zadejte typ aplikace, kterou chcete vytvořit, aby se zobrazil seznam dostupných šablon. Seznam šablon závisí na úlohách, které jste si zvolili během instalace. Pokud chcete zobrazit různé šablony, vyberte jiné úlohy.

   Hledání konkrétního programovacího jazyka můžete filtrovat také pomocí rozevíracího seznamu **jazyk** . Filtrovat můžete také pomocí seznamu **platforem** a seznamu **typ projektu** .

1. Visual Studio otevře nový projekt a Vy jste připravení na kód!

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Instalace sady Visual Studio 2017

V aplikaci Visual Studio 2017 je snadné zvolit a nainstalovat pouze funkce, které potřebujete. A kvůli jejich menšímu minimálnímu množství je instalace rychle a s menším dopadem na systém.

### <a name="prerequisites"></a>Požadavky

- Širokopásmové připojení k Internetu. Instalační program sady Visual Studio může stáhnout několik gigabajtů dat.

- Počítač se systémem Microsoft Windows 7 nebo novější verzí. Pro nejlepší vývojové prostředí doporučujeme Windows 10. Před instalací sady Visual Studio se ujistěte, že jsou v systému nainstalovány nejnovější aktualizace.

- Dostatek volného místa na disku. Visual Studio vyžaduje aspoň 7 GB místa na disku a v případě, že je nainstalovaná spousta běžných možností, může trvat 50 GB nebo víc. Doporučujeme ji nainstalovat na jednotku C:.

Podrobnosti o požadavcích na místo na disku a operačních systémech najdete v tématu [požadavky na systém pro produktovou řadu Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs). Instalační program oznamuje, kolik místa na disku je potřeba pro vybrané možnosti.

### <a name="download-and-install"></a>Stažení a instalace

1. Stáhněte si nejnovější instalační program sady Visual Studio 2017 pro Windows.

   > [!div class="nextstepaction"]
   > [Nainstalovat sadu Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Edice Community je pro jednotlivé vývojáře, školní výuka, vědecký výzkum a vývoj open source. Pro jiné účely, nainstalujte [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) nebo [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

1. Najděte instalační soubor, který jste stáhli a spustili. Může se zobrazit v prohlížeči nebo ho můžete najít ve složce stažené soubory. Instalační program potřebuje ke spuštění oprávnění správce. Může se zobrazit dialogové okno **řízení uživatelských účtů** , které vás požádá o udělení oprávnění, aby instalační program mohl provést změny v systému. Vyberte **Ano**. Pokud máte problémy, najděte stažený soubor v Průzkumníkovi souborů, klikněte pravým tlačítkem na ikonu instalačního programu a v místní nabídce vyberte **Spustit jako správce** .

   ![Stažení a instalace Instalační program pro Visual Studio](media/vscpp-concierge-run-installer.gif "Stažení a instalace Instalační program pro Visual Studio")

1. Instalační program vám nabídne seznam úloh, které jsou skupiny související možnosti jsou pro vývoj pro konkrétní oblasti. Podpora pro C++ je teď součástí volitelných úloh, které se ve výchozím nastavení neinstalují.

   ![Vývoj desktopových C++ aplikací s využitím úloh](media/desktop-development-with-cpp.png "Vývoj desktopových aplikací pomocí C++")

   V C++případě vyberte možnost **vývoj pro stolní C++ počítače pomocí** úlohy a pak zvolte možnost **nainstalovat**.

   ![Instalace desktopového vývoje pomocí C++ úlohy](media/vscpp-concierge-choose-workload.gif "Instalace desktopového vývoje pomocí C++ úlohy")

1. Po dokončení instalace spusťte kliknutím na tlačítko **Spustit** aplikaci Visual Studio.

   Při prvním spuštění aplikace Visual Studio budete vyzváni k přihlášení pomocí účtu Microsoft. Pokud ho nemáte, můžete jeden vytvořit zdarma. Také je nutné zvolit motiv. Nedělejte si starosti, můžete ho později změnit, pokud chcete.

   Může to trvat několik minut, než se Visual Studio připraví na použití při prvním spuštění. Tady je to, co vypadá jako v rychlém časovém intervalu:

   ![Přihlášení k Visual Studiu 2017](media/vscpp-quickstart-first-run.gif "Přihlášení k Visual Studiu 2017")

   Visual Studio se spustí mnohem rychleji, když ho znovu spustíte.

1. Po otevření sady Visual Studio zkontrolujte, zda je zvýrazněna ikona příznak v záhlaví okna:

   ![Příznak oznámení sady Visual Studio 2017](media/vscpp-first-start-page-flag.png "Příznak oznámení sady Visual Studio 2017")

   Pokud je zvýrazněná, vyberte ji a otevřete okno **oznámení** . Pokud jsou k dispozici nějaké aktualizace pro Visual Studio, doporučujeme je nainstalovat hned. Až se instalace dokončí, restartujte Visual Studio.

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Instalace sady Visual Studio 2015

Pokud chcete nainstalovat sadu Visual Studio 2015, Projděte si [část stažení starších verzí sady Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Spusťte instalační program a zvolte možnost **vlastní instalace** a pak zvolte C++ součást. Chcete- C++ li přidat podporu existující instalace sady Visual Studio 2015, klikněte na tlačítko Start systému Windows a zadejte příkaz **Přidat odebrat programy**. Spusťte program ze seznamu výsledků a poté vyhledejte instalaci sady Visual Studio 2015 v seznamu nainstalovaných programů. Poklikejte na ni a pak zvolte **Upravit** a vyberte komponenty vizuálu C++ k instalaci.

Obecně doporučujeme, abyste používali Visual Studio 2017 i v případě, že potřebujete zkompilovat kód pomocí kompilátoru sady Visual Studio 2015. Další informace najdete v tématu [pomocí nativního cílení na více platforem v sadě Visual Studio sestavení starých projektů](../porting/use-native-multi-targeting.md).

::: moniker-end

Po spuštění sady Visual Studio jste připraveni pokračovat k dalšímu kroku.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Vytvořit C++ projekt](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
