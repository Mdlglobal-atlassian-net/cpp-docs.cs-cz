---
title: Nasazení aplikace v jazyce Visual C++ pomocí projektu instalace
ms.date: 04/25/2019
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
ms.openlocfilehash: 6829e917ed0a0e27bea7f42eb9bcfb2b9ad5d2e1
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877370"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Návod: Nasazení aplikace v jazyce Visual C++ pomocí projektu instalace

Popisuje, jak nasadit aplikace v jazyce Visual C++ pomocí projektu instalace.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Počítač s nainstalovanou sadu Visual Studio.

- Další počítač, který nemá knihoven Visual C++.

## <a name="create-the-setup-project"></a>Vytvoření projektu instalace

Pokyny pro vytvoření projektu instalace se liší v závislosti na tom, kterou verzi sady Visual Studio jste nainstalovali. Ujistěte se, že máte volič verze v horním vlevo nastavené na správné verzi.

::: moniker range="=vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>Vytvoření projektu v aplikaci Visual Studio 2019

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu** otevřít **vytvořte nový projekt** dialogové okno.

   ![Projekt aplikace knihovny MFC](media/vs2019-mfc-app-new-project.png "aplikaci nové knihovny MFC")

1. V horní části dialogového okna zadejte `MFC` do vyhledávacího pole a klikněte na tlačítko **aplikace knihovny MFC** ze seznamu výsledků. Pokud ho nevidíte, budete muset spustit program Instalační program sady Visual Studio v nabídce Windows Start a klikněte na  **C++ úloha Desktop Development** dlaždici. V části **jednotlivé komponenty**, ověřte, že je zaškrtnuté políčko komponentu knihovny MFC.

1. Na další stránce zadejte název projektu a zadejte umístění projektu, v případě potřeby.

1. Zvolte **vytvořit** pro vytvoření projektu klienta. Když **Průvodce aplikací knihovny MFC** se zobrazí, přijměte všechny výchozí hodnoty.

1. Změňte konfiguraci aktivního řešení na **vydání**. Z **sestavení** nabídce vyberte možnost **Správce konfigurace**. Z **nástroje Configuration Manager** dialogu **vydání** z **konfigurace aktivního řešení** rozevíracího seznamu. Klikněte na **Zavřít**.

1. Stisknutím klávesy **Ctrl**+**Shift**+**B** k sestavení aplikace. Případně na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. Sestavení aplikace umožňuje nastavení projektu používají výstup tohoto projektu aplikace knihovny MFC.

1. Pokud jste tak již neučinili, stáhněte si rozšíření Microsoft projektů instalačního programu sady Visual Studio. Rozšíření je zdarma pro vývojáře v sadě Visual Studio a přidá funkce šablon projektů instalace a nasazení do sady Visual Studio. Pokud jste připojeni k Internetu, v sadě Visual Studio, zvolte **rozšíření** > **spravovat rozšíření**. V části **rozšíření a aktualizace** dialogového okna, vyberte **Online** kartu a typ *projektů instalačního programu sady Visual Studio Microsoft* do vyhledávacího pole. Stisknutím klávesy **Enter**vyberte **sady Microsoft Visual Studio \<verze > Projekty instalačního programu**a klikněte na tlačítko **Stáhnout**. Zvolte spuštění a instalace rozšíření a potom restartujte Visual Studio.

   ![Projekt instalace sady Visual Studio](media/vs2019-extension-dialog-installer-project.png "pojmenujte projekt klienta")

1. Na řádku nabídek sady Visual Studio, zvolte **souboru** > **poslední projekty a řešení**a klikněte na tlačítko k otevření projektu.

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu** otevřít **vytvořte nový projekt** dialogové okno. Do vyhledávacího pole zadejte "Nastavení" a v seznamu výsledků zvolte **projektu instalace**.

1. Zadejte název projektu instalace v **název** pole. V **řešení** rozevíracího seznamu vyberte **přidat do řešení**. Zvolte **OK** pro vytvoření projektu instalace. A **souboru Assistant (ProjectName)** kartě se otevře v okně editoru.

::: moniker-end

::: moniker range="=vs-2017"

### <a name="to-create-the-project-in-visual-studio-2017"></a>Chcete-li vytvořit projekt v sadě Visual Studio 2017

1. Vytvořte nový projekt. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.

1. Použití **Průvodce aplikací knihovny MFC** vytvořit nové řešení sady Visual Studio. Najít průvodce, ze **nový projekt** dialogového okna rozbalte **Visual C++** uzlu, vyberte **MFC**vyberte **aplikace knihovny MFC**, zadejte název projektu a klikněte na **OK**. Klikněte na tlačítko **Dokončit**.

   > [!NOTE]
   > Pokud **aplikace knihovny MFC** chybí typ, vyberte **otevřít instalační program Visual Studio** v levém podokně **nový projekt** dialogové okno. Možnost umístěna ve složce instalace **vývoj desktopových aplikací pomocí C++** v **volitelné** součástí oddílu s názvem **Visual C++ MFC pro x86 a x64**.

1. Změňte konfiguraci aktivního řešení na **vydání**. Z **sestavení** nabídce vyberte možnost **Správce konfigurace**. Z **nástroje Configuration Manager** dialogu **vydání** z **konfigurace aktivního řešení** rozevíracího seznamu. Klikněte na **Zavřít**.

1. Stisknutím klávesy **Ctrl**+**Shift**+**B** k sestavení aplikace. Případně na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. Sestavení aplikace umožňuje nastavení projektu používají výstup tohoto projektu aplikace knihovny MFC.

1. Pokud jste tak již neučinili, stáhněte si rozšíření Microsoft projektů instalačního programu sady Visual Studio. Rozšíření je zdarma pro vývojáře v sadě Visual Studio a přidá funkce šablon projektů instalace a nasazení do sady Visual Studio. Pokud jste připojeni k Internetu, v sadě Visual Studio, zvolte **nástroje** > **rozšíření a aktualizace**. V části **rozšíření a aktualizace** dialogového okna, vyberte **Online** kartu a typ *projektů instalačního programu sady Visual Studio Microsoft* do vyhledávacího pole. Stisknutím klávesy **Enter**vyberte **sady Microsoft Visual Studio \<verze > Projekty instalačního programu**a klikněte na tlačítko **Stáhnout**. Zvolte spuštění a instalace rozšíření a potom restartujte Visual Studio.

1. V panelu nabídky zvolte **souboru** > **poslední projekty a řešení**a klikněte na tlačítko k otevření projektu.

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu** otevřít **nový projekt** dialogové okno. V levém podokně dialogového okna rozbalte **nainstalováno** > **ostatní typy projektů** uzlů a vyberte **instalační program sady Visual Studio**. V prostředním podokně vyberte **projektu instalace**.

1. Zadejte název projektu instalace v **název** pole. V **řešení** rozevíracího seznamu vyberte **přidat do řešení**. Zvolte **OK** pro vytvoření projektu instalace. A **souboru Assistant (ProjectName)** kartě se otevře v okně editoru.

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-the-project-in-visual-studio-2015"></a>Chcete-li vytvořit projekt v sadě Visual Studio 2015

1. Vytvořte nový projekt. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.

1. Použití **Průvodce aplikací knihovny MFC** vytvořit nové řešení sady Visual Studio. Najít průvodce, ze **nový projekt** dialogového okna rozbalte **Visual C++** uzlu, vyberte **MFC**vyberte **aplikace knihovny MFC**, zadejte název projektu a klikněte na **OK**. Klikněte na tlačítko **Dokončit**.

   > [!NOTE]
   > Pokud **aplikace knihovny MFC** chybí typ, klikněte na tlačítko Windows Start a typ **přidat nebo odebrat programy**. Otevřete program ze seznamu výsledků a pak v seznamu nainstalovaných programů najít instalaci sady Microsoft Visual Studio 2015. Poklepejte na něj a pak zvolte **změnit** a vyberte **Microsoft Foundation Classes** komponentu pod **Visual C++**.

1. Změňte konfiguraci aktivního řešení na **vydání**. Z **sestavení** nabídce vyberte možnost **nástroje Configuration Manager**. Z **nástroje Configuration Manager** dialogu **vydání** z **konfigurace aktivního řešení** rozevíracího seznamu. Klikněte na **Zavřít**.

1. Stisknutím klávesy **Ctrl**+**Shift**+**B** k sestavení aplikace. Případně na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. Sestavení aplikace umožňuje nastavení projektu používají výstup tohoto projektu aplikace knihovny MFC.

1. Pokud jste tak již neučinili, stáhněte si rozšíření Microsoft projektů instalačního programu sady Visual Studio. Rozšíření je zdarma pro vývojáře v sadě Visual Studio a přidá funkce šablon projektů instalace a nasazení do sady Visual Studio. Pokud jste připojeni k Internetu, v sadě Visual Studio, zvolte **nástroje** > **rozšíření a aktualizace**. V části **rozšíření a aktualizace** dialogového okna, vyberte **Online** kartu a typ *projektů instalačního programu sady Visual Studio Microsoft* do vyhledávacího pole. Stisknutím klávesy **Enter**vyberte **sady Microsoft Visual Studio \<verze > Projekty instalačního programu**a klikněte na tlačítko **Stáhnout**. Zvolte spuštění a instalace rozšíření a potom restartujte Visual Studio.

1. V panelu nabídky zvolte **souboru** > **poslední projekty a řešení**a klikněte na tlačítko k otevření projektu.

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu** otevřít **nový projekt** dialogové okno. V levém podokně dialogového okna rozbalte **nainstalováno** > **ostatní typy projektů** uzlů a vyberte **instalační program sady Visual Studio**. V prostředním podokně vyberte **projektu instalace**.

1. Zadejte název projektu instalace v **název** pole. V **řešení** rozevíracího seznamu vyberte **přidat do řešení**. Zvolte **OK** pro vytvoření projektu instalace. A **souboru Assistant (ProjectName)** kartě se otevře v okně editoru.

::: moniker-end

## <a name="add-items-to-the-project"></a>Přidání položek do projektu

1. Klikněte pravým tlačítkem myši **složky aplikace** uzel a vyberte možnost **přidat** > **výstup projektu** otevřete **Přidat výstupní skupinu projektu**dialogové okno. V dialogovém okně vyberte **primární výstup** a klikněte na tlačítko **OK**. Nová položka s názvem **primární výstup z ProjectName (aktivní)** se zobrazí.

1. Klikněte pravým tlačítkem na **složky aplikace** uzel a vyberte možnost **přidat** > **sestavení** otevřít **vyberte komponentu** dialogového okna pole. Vyberte a přidejte veškeré požadované knihovny DLL vyžadované program, jak je popsáno v následujícím článku [Determining Which DLLs to Redistribute](determining-which-dlls-to-redistribute.md).

1. Vyberte položku **primární výstup z ProjectName (aktivní)** klikněte pravým tlačítkem a zvolte **vytvořit zástupce na primární výstup z ProjectName (aktivní)**. Nová položka s názvem **zástupce primární výstup z ProjectName (aktivní)** se zobrazí. Vám může přejmenovat položky místní pak přetažení položky do **Uživatelská nabídka programy** uzlu na levé straně okna.

1. V panelu nabídky zvolte **sestavení** > **nástroje Configuration Manager**. V **projektu** tabulky v části **sestavení** sloupců, zaškrtněte políčko u projektu nasazení. Klikněte na **Zavřít**.

1. V panelu nabídky zvolte **sestavení** > **sestavit řešení** k sestavení projektu knihovny MFC a projekt nasazení.

1. Ve složce řešení vyhledejte program setup.exe vytvořený z projektu nasazení. Můžete zkopírovat tento soubor (a tento soubor .msi) k instalaci aplikace a jeho požadovaných souborů knihovny v jiném počítači. Spusťte instalační program na druhém počítači, který nemá knihoven Visual C++.

## <a name="see-also"></a>Viz také:

[Příklady nasazení](deployment-examples.md)<br/>
