---
title: Nasazení aplikace v jazyce Visual C++ pomocí projektu instalace
ms.date: 09/17/2018
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
ms.openlocfilehash: e2d83d45f1369e250b24708edd17f4004e030a17
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786662"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Návod: Nasazení aplikace v jazyce Visual C++ pomocí projektu instalace

Popisuje, jak nasadit aplikace v jazyce Visual C++ pomocí projektu instalace.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Počítač s nainstalovanou sadu Visual Studio.

- Další počítač, který nemá knihoven Visual C++.

### <a name="to-deploy-an-application-by-using-a-setup-project"></a>K nasazení aplikace pomocí projektu instalace

1. Vytvořte nový projekt. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.

1. Použití **MFC ApplicationWizard** vytvořit nové řešení sady Visual Studio. Najít průvodce, ze **nový projekt** dialogového okna rozbalte **Visual C++** uzlu, vyberte **MFC**vyberte **aplikace knihovny MFC**, zadejte název projektu a klikněte na **OK**. Klikněte na tlačítko **Dokončit**.

   > [!NOTE]
   > Pokud **aplikace knihovny MFC** chybí typ:<br/>
   > **Visual Studio 2017**: Vyberte **otevřít instalační program Visual Studio** v levém podokně **nový projekt** dialogové okno. Možnost umístěna ve složce instalace **vývoj desktopových aplikací pomocí C++** v **volitelné** součástí oddílu s názvem **Visual C++ MFC pro x86 a x64**.<br/>
   > **Visual Studio 2015**: Klikněte na tlačítko Windows Start a typ **přidat nebo odebrat programy**. Otevřete program ze seznamu výsledků a pak v seznamu nainstalovaných programů najít instalaci sady Microsoft Visual Studio 2015. Poklepejte na něj a pak zvolte **změnit** a vyberte **Microsoft Foundation Classes** komponentu pod **Visual C++**.

1. Změňte konfiguraci aktivního řešení na **vydání**. Z **sestavení** nabídce vyberte možnost **Správce konfigurace**. Z **nástroje Configuration Manager** dialogu **vydání** z **konfigurace aktivního řešení** rozevíracího seznamu. Klikněte na **Zavřít**.

1. Stisknutím klávesy **Ctrl**+**Shift**+**B** k sestavení aplikace. Případně na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. Sestavení aplikace umožňuje nastavení projektu používají výstup tohoto projektu aplikace knihovny MFC.

1. Pokud jste tak již neučinili, stáhněte si rozšíření Microsoft projektů instalačního programu sady Visual Studio. Rozšíření je zdarma pro vývojáře v sadě Visual Studio a přidá funkce šablon projektů instalace a nasazení do sady Visual Studio. Pokud jste připojeni k Internetu, v sadě Visual Studio, zvolte **nástroje** > **rozšíření a aktualizace**. V části **rozšíření a aktualizace** dialogového okna, vyberte **Online** kartu a typ *projektů instalačního programu sady Visual Studio Microsoft* do vyhledávacího pole. Spuštění **Enter**vyberte **sady Microsoft Visual Studio \<verze > Projekty instalačního programu**a klikněte na tlačítko **Stáhnout**. Zvolte spuštění a instalace rozšíření a potom restartujte Visual Studio.

1. V panelu nabídky zvolte **souboru** > **poslední projekty a řešení**a klikněte na tlačítko k otevření projektu.

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu** otevřít **nový projekt** dialogové okno. V levém podokně dialogového okna rozbalte **nainstalováno** > **ostatní typy projektů** uzlů a vyberte **instalační program sady Visual Studio**. V prostředním podokně vyberte **projektu instalace**.

1. Zadejte název projektu instalace v **název** pole. V **řešení** rozevíracího seznamu vyberte **přidat do řešení**. Zvolte **OK** pro vytvoření projektu instalace. A **souboru Assistant (ProjectName)** kartě se otevře v okně editoru.

1. Klikněte pravým tlačítkem myši **složky aplikace** uzel a vyberte možnost **přidat** > **výstup projektu** otevřete **Přidat výstupní skupinu projektu**dialogové okno. V dialogovém okně vyberte **primární výstup** a klikněte na tlačítko **OK**. Nová položka s názvem **primární výstup z ProjectName (aktivní)** se zobrazí.

1. Klikněte pravým tlačítkem na **složky aplikace** uzel a vyberte možnost **přidat** > **sestavení** otevřít **vyberte komponentu** dialogového okna pole. Vyberte a přidejte veškeré požadované knihovny DLL vyžadované program, jak je popsáno v následujícím článku [Determining Which DLLs to Redistribute](determining-which-dlls-to-redistribute.md).

1. Vyberte položku **primární výstup z ProjectName (aktivní)** klikněte pravým tlačítkem a zvolte **vytvořit zástupce na primární výstup z ProjectName (aktivní)**. Nová položka s názvem **zástupce primární výstup z ProjectName (aktivní)** se zobrazí. Vám může přejmenovat položky místní pak přetažení položky do **Uživatelská nabídka programy** uzlu na levé straně okna.

1. V panelu nabídky zvolte **sestavení** > **nástroje Configuration Manager**. V **projektu** tabulky v části **sestavení** sloupců, zaškrtněte políčko u projektu nasazení. Klikněte na **Zavřít**.

1. V panelu nabídky zvolte **sestavení** > **sestavit řešení** k sestavení projektu knihovny MFC a projekt nasazení.

1. Ve složce řešení vyhledejte program setup.exe vytvořený z projektu nasazení. Můžete zkopírovat tento soubor (a tento soubor .msi) k instalaci aplikace a jeho požadovaných souborů knihovny v jiném počítači. Spusťte instalační program na druhém počítači, který nemá knihoven Visual C++.

## <a name="see-also"></a>Viz také:

[Příklady nasazení](deployment-examples.md)<br/>
