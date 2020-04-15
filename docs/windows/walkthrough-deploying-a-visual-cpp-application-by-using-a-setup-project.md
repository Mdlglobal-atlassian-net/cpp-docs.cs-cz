---
title: Nasazení aplikace Visual C++ pomocí instalačního projektu
ms.date: 04/25/2019
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
ms.openlocfilehash: 8a1242140154c5a0123d71b83983fae20cab5d7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374359"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Návod: Nasazení aplikace Visual C++ pomocí projektu instalace

Popisuje, jak použít projekt instalace k nasazení aplikace Visual C++.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Počítač s nainstalovanou aplikací Visual Studio.

- Další počítač, který nemá knihovny Visual C++.

## <a name="create-the-setup-project"></a>Vytvoření projektu nastavení

Pokyny pro vytvoření projektu instalace se liší v závislosti na verzi sady Visual Studio, kterou jste nainstalovali. Chcete-li zobrazit dokumentaci k upřednostňované verzi sady Visual Studio, použijte ovládací prvek pro výběr **verze.** Nachází se v horní části obsahu na této stránce.

::: moniker range="=vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>Vytvoření projektu v sadě Visual Studio 2019

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu** a otevřete dialogové okno Vytvořit **nový projekt.**

   ![Projekt aplikace knihovny MFC](media/vs2019-mfc-app-new-project.png "Nová aplikace MFC")

1. V horní části dialogového `MFC` okna zadejte do vyhledávacího pole a pak ze seznamu výsledků zvolte **aplikaci knihovny MFC.** Pokud ji nevidíte, budete muset spustit instalační program sady Visual Studio z nabídky Start systému Windows a kliknout na dlaždici **pracovního vytížení vývoje plochy jazyka C++.** V **části Jednotlivé součásti**zkontrolujte, zda je zaškrtnuta součást knihovny MFC.

1. Na další stránce zadejte název projektu a v případě potřeby zadejte umístění projektu.

1. Zvolte tlačítko **Vytvořit** pro vytvoření klientského projektu. Po spuštění **Průvodce aplikací knihovny MFC** přijměte všechny výchozí hodnoty.

1. Změňte konfiguraci aktivního řešení na **Verzi**. V nabídce **Sestavení** vyberte **Možnost Konfigurace jeslí**. V dialogovém okně **Správce konfigurace** vyberte **možnost Uvolnit** z rozevíracího pole **Konfigurace aktivního řešení.** Klikněte na **Zavřít**.

1. Stisknutím **klávesy Ctrl**+**Shift**+**B** vytvořte aplikaci. Nebo v nabídce **Sestavení** klikněte na **Build Solution**. Vytvoření aplikace umožňuje projektu nastavení použít výstup tohoto projektu aplikace knihovny MFC.

1. Pokud jste tak ještě neučinili, stáhněte si rozšíření Microsoft Visual Studio Installer Projects. Rozšíření je zdarma pro vývojáře sady Visual Studio a přidává funkce šablony projektu instalace a nasazení do sady Visual Studio. Když jste připojení k Internetu, v sadě Visual Studio zvolte **Rozšíření** > **Spravovat rozšíření**. V dialogovém **okně Rozšíření a aktualizace** vyberte kartu **Online** a do vyhledávacího pole zadejte *instalační projekty sady Microsoft Visual Studio.* Stiskněte **enter**, vyberte **verzi sady Microsoft Visual Studio \<> Projekty instalačníslužby**a klepněte na tlačítko **Stáhnout**. Zvolte spuštění a instalaci rozšíření a restartujte aplikaci Visual Studio.

   ![Projekt nastavení sady Visual Studio](media/vs2019-extension-dialog-installer-project.png "Pojmenovat projekt klienta")

1. Na panelu nabídek Sady Visual Studio zvolte **Soubor** > **posledních projektů a řešení**a pak zvolte znovu otevřít projekt.

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu** a otevřete dialogové okno Vytvořit **nový projekt.** Do vyhledávacího pole zadejte "Setup" a v seznamu výsledků zvolte **Setup Project**.

1. Do pole **Název** zadejte název projektu instalace. V rozevíracím seznamu **Řešení** vyberte **Přidat do řešení**. Zvolte tlačítko **OK** pro vytvoření projektu nastavení. V okně editoru se otevře karta **Pomocník se soubory (Název_projektu).**

::: moniker-end

::: moniker range="=vs-2017"

### <a name="to-create-the-project-in-visual-studio-2017"></a>Vytvoření projektu v sadě Visual Studio 2017

1. Vytvoření nového projektu V nabídce **Soubor** přejděte na **Nový**a potom klepněte na **položku Project**.

1. Pomocí **Průvodce aplikací knihovny MFC** vytvořte nové řešení sady Visual Studio. Chcete-li průvodce najít, rozbalte v dialogovém okně **Nový projekt** uzel **Visual C++,** vyberte **knihovnu MFC**, vyberte **aplikaci knihovny MFC**, zadejte název projektu a klepněte na tlačítko **OK**. Klikněte na **Finish** (Dokončit).

   > [!NOTE]
   > Pokud typ **aplikace knihovny MFC** chybí, vyberte v levém podokně dialogového okna **Nový projekt** možnost Otevřít instalační program sady **Visual Studio.** Nainstalujte možnost umístěnou ve **vývoji plochy s C++** v části **Volitelné** komponenty s názvem **Visual C++ MFC pro x86 a x64**.

1. Změňte konfiguraci aktivního řešení na **Verzi**. V nabídce **Sestavení** vyberte **Možnost Konfigurace jeslí**. V dialogovém okně **Správce konfigurace** vyberte **možnost Uvolnit** z rozevíracího pole **Konfigurace aktivního řešení.** Klikněte na **Zavřít**.

1. Stisknutím **klávesy Ctrl**+**Shift**+**B** vytvořte aplikaci. Nebo v nabídce **Sestavení** klikněte na **Build Solution**. Vytvoření aplikace umožňuje projektu nastavení použít výstup tohoto projektu aplikace knihovny MFC.

1. Pokud jste tak ještě neučinili, stáhněte si rozšíření Microsoft Visual Studio Installer Projects. Rozšíření je zdarma pro vývojáře sady Visual Studio a přidává funkce šablony projektu instalace a nasazení do sady Visual Studio. Když jste připojeni k Internetu, v aplikaci Visual Studio zvolte**Rozšíření a aktualizace** **nástrojů** > . V dialogovém **okně Rozšíření a aktualizace** vyberte kartu **Online** a do vyhledávacího pole zadejte *instalační projekty sady Microsoft Visual Studio.* Stiskněte **enter**, vyberte **verzi sady Microsoft Visual Studio \<> Projekty instalačníslužby**a klepněte na tlačítko **Stáhnout**. Zvolte spuštění a instalaci rozšíření a restartujte aplikaci Visual Studio.

1. Na řádku nabídek zvolte **Soubor** > **posledních projektů a řešení**a pak zvolte znovu otevřít projekt.

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu** a otevřete dialogové okno **Nový projekt.** Potom v levém podokně dialogového okna rozbalte uzly **Nainstalované** > **další typy projektů** a vyberte Instalační **službu sady Visual Studio**. V prostředním podokně vyberte **Instalační projekt**.

1. Do pole **Název** zadejte název projektu instalace. V rozevíracím seznamu **Řešení** vyberte **Přidat do řešení**. Zvolte tlačítko **OK** pro vytvoření projektu nastavení. V okně editoru se otevře karta **Pomocník se soubory (Název_projektu).**

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-the-project-in-visual-studio-2015"></a>Vytvoření projektu v sadě Visual Studio 2015

1. Vytvoření nového projektu V nabídce **Soubor** přejděte na **Nový**a potom klepněte na **položku Project**.

1. Pomocí **Průvodce aplikací knihovny MFC** vytvořte nové řešení sady Visual Studio. Chcete-li průvodce najít, rozbalte v dialogovém okně **Nový projekt** uzel **Visual C++,** vyberte **knihovnu MFC**, vyberte **aplikaci knihovny MFC**, zadejte název projektu a klepněte na tlačítko **OK**. Klikněte na **Finish** (Dokončit).

   > [!NOTE]
   > Pokud chybí typ **aplikace knihovny MFC,** klepněte na tlačítko Start systému Windows a zadejte **příkaz Přidat programy**. Otevřete program ze seznamu výsledků a potom vyhledejte instalaci sady Microsoft Visual Studio 2015 v seznamu nainstalovaných programů. Poklepejte na něj, pak zvolte **Změnit** a vyberte komponentu **Microsoft Foundation Classes** v části Visual **C++**.

1. Změňte konfiguraci aktivního řešení na **Verzi**. V nabídce **Sestavení** vyberte **Nástroj Pro nástroj Konfigurace**. V dialogovém okně **Správce konfigurace** vyberte **možnost Uvolnit** z rozevíracího pole **Konfigurace aktivního řešení.** Klikněte na **Zavřít**.

1. Stisknutím **klávesy Ctrl**+**Shift**+**B** vytvořte aplikaci. Nebo v nabídce **Sestavení** klikněte na **Build Solution**. Vytvoření aplikace umožňuje projektu nastavení použít výstup tohoto projektu aplikace knihovny MFC.

1. Pokud jste tak ještě neučinili, stáhněte si rozšíření Microsoft Visual Studio Installer Projects. Rozšíření je zdarma pro vývojáře sady Visual Studio a přidává funkce šablony projektu instalace a nasazení do sady Visual Studio. Když jste připojeni k Internetu, v aplikaci Visual Studio zvolte**Rozšíření a aktualizace** **nástrojů** > . V dialogovém **okně Rozšíření a aktualizace** vyberte kartu **Online** a do vyhledávacího pole zadejte *instalační projekty sady Microsoft Visual Studio.* Stiskněte **enter**, vyberte **verzi sady Microsoft Visual Studio \<> Projekty instalačníslužby**a klepněte na tlačítko **Stáhnout**. Zvolte spuštění a instalaci rozšíření a restartujte aplikaci Visual Studio.

1. Na řádku nabídek zvolte **Soubor** > **posledních projektů a řešení**a pak zvolte znovu otevřít projekt.

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu** a otevřete dialogové okno **Nový projekt.** Potom v levém podokně dialogového okna rozbalte uzly **Nainstalované** > **další typy projektů** a vyberte Instalační **službu sady Visual Studio**. V prostředním podokně vyberte **Instalační projekt**.

1. Do pole **Název** zadejte název projektu instalace. V rozevíracím seznamu **Řešení** vyberte **Přidat do řešení**. Zvolte tlačítko **OK** pro vytvoření projektu nastavení. V okně editoru se otevře karta **Pomocník se soubory (Název_projektu).**

::: moniker-end

## <a name="add-items-to-the-project"></a>Přidání položek do projektu

1. Klikněte pravým tlačítkem myši na uzel **Složky aplikace** a vyberte **Přidat** > **výstup projektu,** abyste otevřeli dialogové okno Přidat výstupní **skupinu projektu.** V dialogovém okně vyberte **Primární výstup** a klepněte na **OK**. Zobrazí se nová položka s názvem **Primární výstup z názvu_aplikace ProjectName (Aktivní).**

1. Klepněte pravým tlačítkem myši na uzel **Složky aplikace** a výběrem **možnosti Přidat** > **sestavení** otevřete dialogové okno **Vybrat komponentu.** Vyberte a přidejte všechny požadované knihovny DLL, které program potřebuje, jak je popsáno v článku [Určení, které knihovny DLL budou dále distribuovat](determining-which-dlls-to-redistribute.md).

1. Vyberte položku **Primární výstup z názvu_projektu (Aktivní),** klepněte pravým tlačítkem myši a zvolte **Vytvořit zástupce primárního výstupu z názvu_projektu (Aktivní).** Zobrazí se nová položka s názvem **Zástupce primárního výstupu z názvu_aplikace ProjectName (Aktivní).** Můžete přejmenovat položku zástupce a potom položku přetáhnout do uzlu **nabídky Programy uživatele** na levé straně okna.

1. Na řádku nabídek zvolte **Build** > **Configuration Manager**. V tabulce **Projekt** zaškrtněte ve sloupci **Sestavení** políčko pro projekt nasazení. Klikněte na **Zavřít**.

1. Na řádku nabídek zvolte **Sestavení** > **sestavení řešení** k sestavení projektu knihovny MFC a projektu nasazení.

1. Ve složce řešení vyhledejte program setup.exe, který byl vytvořen z projektu nasazení. Tento soubor (a soubor MSI) můžete zkopírovat a nainstalovat aplikaci a požadované soubory knihovny do jiného počítače. Spusťte instalační program v druhém počítači, který nemá knihovny Visual C++.

## <a name="see-also"></a>Viz také

[Příklady nasazení](deployment-examples.md)<br/>
