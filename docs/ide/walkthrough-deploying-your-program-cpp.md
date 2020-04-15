---
title: 'Návod: Nasazení programu (C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
ms.openlocfilehash: eacbcef82f240589e71b59f80d8e19602ceda869
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365011"
---
# <a name="walkthrough-deploying-your-program-c"></a>Návod: Nasazení programu (C++)

Nyní, když jste vytvořili aplikaci vyplněním předchozích souvisejících návodů, je posledním krokem vytvoření instalačního programu, aby ostatní uživatelé mohli nainstalovat program do svých počítačů. Pro instalační program přidáte nový projekt do stávajícího řešení. Výstupem tohoto nového projektu je soubor setup.exe, který nainstaluje aplikaci do jiného počítače.

Návod ukazuje, jak pomocí Instalační služby systému Windows nasadit aplikaci. ClickOnce můžete také použít k nasazení aplikace. Další informace naleznete v [tématu ClickOnce Deployment for Visual C++ Applications](../windows/clickonce-deployment-for-visual-cpp-applications.md). Další informace o nasazení obecně naleznete v [tématu Nasazení aplikací, služeb a součástí](/visualstudio/deployment/deploying-applications-services-and-components).

## <a name="prerequisites"></a>Požadavky

- Návod předpokládá, že rozumíte základům jazyka C++.

- Také předpokládá, že jste dokončili předchozí související návody, které jsou uvedeny v [části Použití ide sady Visual Studio pro vývoj plochy jazyka C++](using-the-visual-studio-ide-for-cpp-desktop-development.md).

- Návod nelze dokončit v expresních edicích sady Visual Studio.

## <a name="install-the-visual-studio-setup-and-deployment-project-template"></a>Instalace šablony projektu nastavení a nasazení sady Visual Studio

Postup v této části se liší v závislosti na verzi sady Visual Studio, kterou jste nainstalovali. Chcete-li zobrazit dokumentaci k upřednostňované verzi sady Visual Studio, použijte ovládací prvek pro výběr **verze.** Nachází se v horní části obsahu na této stránce.

<!-- markdownlint-disable MD034 -->

::: moniker range="vs-2019"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2019"></a>Instalace šablony projektu instalace a nasazení pro Visual Studio 2019

1. Pokud jste tak ještě neučinili, stáhněte si rozšíření Microsoft Visual Studio Installer Projects. Rozšíření je zdarma pro vývojáře sady Visual Studio a přidává funkce šablony projektu instalace a nasazení do sady Visual Studio. Když jste připojení k Internetu, v sadě Visual Studio zvolte **Rozšíření** > **Spravovat rozšíření**. V dialogovém **okně Rozšíření a aktualizace** vyberte kartu **Online** a do vyhledávacího pole zadejte *instalační projekty sady Microsoft Visual Studio.* Stiskněte **klávesu Enter**, vyberte **položku Microsoft Visual \<Studio verze> Instalační projekty**a klepněte na tlačítko **Stáhnout**. Zvolte spuštění a instalaci rozšíření a restartujte aplikaci Visual Studio.

1. Na panelu nabídek Sady Visual Studio zvolte **Soubor** > **posledních projektů a řešení**a pak zvolte znovu otevřít projekt.

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu** a otevřete dialogové okno Vytvořit **nový projekt.** Do vyhledávacího pole zadejte "Setup" a v seznamu výsledků zvolte **Setup Project**.

1. Do pole **Název** zadejte název projektu instalace. V rozevíracím seznamu **Řešení** vyberte **Přidat do řešení**. Zvolte tlačítko **OK** pro vytvoření projektu nastavení. V okně editoru se otevře karta **Pomocník se soubory (Název_projektu).**

1. Klikněte pravým tlačítkem myši na uzel **Složky aplikace** a vyberte **Přidat** > **výstup projektu,** abyste otevřeli dialogové okno Přidat výstupní **skupinu projektu.**

1. V dialogovém okně vyberte **Primární výstup** a klepněte na **OK**. Zobrazí se nová položka s názvem **Primární výstup z hry (Aktivní).**

1. Vyberte položku **Primární výstup ze hry (Aktivní)**, klepněte pravým tlačítkem myši a zvolte Vytvořit zástupce **primárního výstupu ze hry (Aktivní).** Zobrazí se nová položka s názvem **Zástupce primárního výstupu z hry (Aktivní).**

1. Přejmenujte zkratku položky na *Hru*a potom ji přetáhněte do uzlu **nabídky Programy uživatele** na levé straně okna.

1. V **Průzkumníku řešení**vyberte projekt **Instalační služba hry** a zvolte **Zobrazit** > **okno vlastností** nebo stiskněte **F4** a otevřete okno **Vlastnosti.**

1. Zadejte další podrobnosti tak, jak chcete, aby se zobrazovaly v instalačním programu.  Pro **adresu SupportUrl**použijte například *contoso* pro **výrobce**, *instalační službu hry* pro název **produktu**a *https\://www.contoso.com* .

1. Na řádku nabídek zvolte **Build** > **Configuration Manager**. V tabulce **Projekt** zaškrtněte ve sloupci **Sestavení** políčko **Game Installer**. Klikněte na **Zavřít**.

1. Na řádku nabídek zvolte **Sestavení** > **sestavení řešení** k sestavení projektu hry a game installer projektu.

1. Ve složce řešení vyhledejte program setup.exe, který byl vytvořen z projektu Game Installer, a spusťte jej a nainstalujte do počítače herní aplikaci. Tento soubor (a GameInstaller.msi) můžete zkopírovat a nainstalovat aplikaci a její požadované soubory knihovny do jiného počítače.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2017-and-earlier"></a>Instalace šablony projektu instalace a nasazení pro Visual Studio 2017 a starší

1. Když jste připojeni k Internetu, v aplikaci Visual Studio zvolte **Rozšíření a aktualizace** **nástrojů** > .

1. V části **Rozšíření a aktualizace**vyberte kartu **Online** a do vyhledávacího pole zadejte *Instalační projekty sady Microsoft Visual Studio.* Stiskněte **klávesu Enter**, vyberte **položku Microsoft Visual \<Studio verze> Instalační projekty**a klepněte na tlačítko **Stáhnout**.

1. Zvolte instalaci rozšíření a restartujte visual studio.

1. Na řádku nabídek zvolte **Soubor** > **posledních projektů a řešení**a pak zvolte **herní** řešení, které chcete znovu otevřít.

### <a name="to-create-a-setup-project-and-install-your-program"></a>Vytvoření instalačního projektu a instalace programu

1. Změňte konfiguraci aktivního řešení na Verzi. Na řádku nabídek zvolte **Build** > **Configuration Manager**. V dialogovém okně **Správce konfigurace** vyberte v rozevíracím seznamu **Konfigurace aktivního řešení** možnost **Uvolnit**. Chcete-li konfiguraci uložit, zvolte tlačítko **Zavřít.**

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu** a otevřete dialogové okno **Nový projekt.**

1. V levém podokně dialogového okna rozbalte uzly **Nainstalované** > **další typy projektů** a vyberte Instalační **službu sady Visual Studio**. V prostředním podokně vyberte **Instalační projekt**.

1. Do pole **Název** zadejte název projektu instalace. V tomto příkladu zadejte *Instalační program hry*. V rozevíracím seznamu **Řešení** vyberte **Přidat do řešení**. Zvolte tlačítko **OK** pro vytvoření projektu nastavení. V okně editoru se otevře karta **File Assistant (Game Installer).**

1. Klikněte pravým tlačítkem myši na uzel **Složky aplikace** a vyberte **Přidat** > **výstup projektu,** abyste otevřeli dialogové okno Přidat výstupní **skupinu projektu.**

1. V dialogovém okně vyberte **Primární výstup** a klepněte na **OK**. Zobrazí se nová položka s názvem **Primární výstup z hry (Aktivní).**

1. Vyberte položku **Primární výstup ze hry (Aktivní)**, klepněte pravým tlačítkem myši a zvolte Vytvořit zástupce **primárního výstupu ze hry (Aktivní).** Zobrazí se nová položka s názvem **Zástupce primárního výstupu z hry (Aktivní).**

1. Přejmenujte zkratku položky na *Hru*a potom ji přetáhněte do uzlu **nabídky Programy uživatele** na levé straně okna.

1. V **Průzkumníku řešení**vyberte projekt **Instalační služba hry** a zvolte **Zobrazit** > **okno vlastností** nebo stiskněte **F4** a otevřete okno **Vlastnosti.**

1. Zadejte další podrobnosti tak, jak chcete, aby se zobrazovaly v instalačním programu.  Pro **adresu SupportUrl**použijte například *contoso* pro **výrobce**, *instalační službu hry* pro název **produktu**a *https\://www.contoso.com* .

1. Na řádku nabídek zvolte **Build** > **Configuration Manager**. V tabulce **Projekt** zaškrtněte ve sloupci **Sestavení** políčko **Game Installer**. Klikněte na **Zavřít**.

1. Na řádku nabídek zvolte **Sestavení** > **sestavení řešení** k sestavení projektu hry a game installer projektu.

1. Ve složce řešení vyhledejte program setup.exe, který byl vytvořen z projektu Game Installer, a spusťte jej a nainstalujte do počítače herní aplikaci. Tento soubor (a GameInstaller.msi) můžete zkopírovat a nainstalovat aplikaci a její požadované soubory knihovny do jiného počítače.

::: moniker-end

## <a name="next-steps"></a>Další kroky

**Předchozí:** [Návod: Ladění projektu (C++)](walkthrough-debugging-a-project-cpp.md)

## <a name="see-also"></a>Viz také

[Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md)<br/>
[Nasazení desktopových aplikací](../windows/deploying-native-desktop-applications-visual-cpp.md)<br/>
