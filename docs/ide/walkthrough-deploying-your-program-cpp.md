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
ms.openlocfilehash: 5cc4ead7aaef2ffa56870a374b0b73d16eb31521
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400957"
---
# <a name="walkthrough-deploying-your-program-c"></a>Návod: Nasazení programu (C++)

Teď, když jste vytvořili aplikaci provedením dříve související návody, posledním krokem je vytvoření instalátoru, tak, aby ostatní uživatelé mohou nainstalovat program na svých počítačích. Pro instalační program přidáte nový projekt do existujícího řešení. Výstup tohoto nového projektu je soubor setup.exe, který nainstaluje vaši aplikaci na jiném počítači.

Návodu ukazuje způsob použití Instalační služby systému Windows pro nasazení aplikace. Můžete také použít ClickOnce k nasazení aplikace. Další informace najdete v tématu [ClickOnce – nasazení pro aplikace Visual C++](../windows/clickonce-deployment-for-visual-cpp-applications.md). Další informace o nasazení, najdete v části [nasazování aplikací, služeb a komponent](/visualstudio/deployment/deploying-applications-services-and-components).

## <a name="prerequisites"></a>Požadavky

- Návod předpokládá, že chápete základy jazyka C++.

- Dále předpokládá, že jste dokončili dříve související návody, které jsou uvedeny v [pomocí integrovaného vývojového prostředí sady Visual Studio pro vývoj v jazyce C++ Desktop](using-the-visual-studio-ide-for-cpp-desktop-development.md).

- Návod nelze dokončit v edicích Express sady Visual Studio.

## <a name="install-the-visual-studio-setup-and-deployment-project-template"></a>Instalace sady Visual Studio šablona projektu instalace a nasazení

Kroky v této části se liší v závislosti na tom, kterou verzi sady Visual Studio jste nainstalovali. Ujistěte se, že se že volič verze v levé horní části této stránky jsou správně nastavena.

::: moniker range="vs-2019"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2019"></a>Instalace pro Visual Studio 2019 instalace a nasazení projektové šablony

1. Pokud jste tak již neučinili, stáhněte si rozšíření Microsoft projektů instalačního programu sady Visual Studio. Rozšíření je zdarma pro vývojáře v sadě Visual Studio a přidá funkce šablon projektů instalace a nasazení do sady Visual Studio. Pokud jste připojeni k Internetu, v sadě Visual Studio, zvolte **rozšíření** > **spravovat rozšíření**. V části **rozšíření a aktualizace** dialogového okna, vyberte **Online** kartu a typ *projektů instalačního programu sady Visual Studio Microsoft* do vyhledávacího pole. Spuštění **Enter**vyberte **sady Microsoft Visual Studio \<verze > Projekty instalačního programu**a klikněte na tlačítko **Stáhnout**. Zvolte spuštění a instalace rozšíření a potom restartujte Visual Studio.

1. Na řádku nabídek sady Visual Studio, zvolte **souboru** > **poslední projekty a řešení**a klikněte na tlačítko k otevření projektu.

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu** otevřít **vytvořte nový projekt** dialogové okno. Do vyhledávacího pole zadejte "Nastavení" a v seznamu výsledků zvolte **projektu instalace**.

1. Zadejte název projektu instalace v **název** pole. V **řešení** rozevíracího seznamu vyberte **přidat do řešení**. Zvolte **OK** pro vytvoření projektu instalace. A **souboru Assistant (ProjectName)** kartě se otevře v okně editoru.

1. Klikněte pravým tlačítkem myši **složky aplikace** uzel a vyberte možnost **přidat** > **výstup projektu** otevřete **Přidat výstupní skupinu projektu**dialogové okno.

1. V dialogovém okně vyberte **primární výstup** a klikněte na tlačítko **OK**. Nová položka s názvem **primární výstup ze hry (aktivní)** se zobrazí.

1. Vyberte položku **primární výstup ze hry (aktivní)** klikněte pravým tlačítkem a zvolte **vytvořit zástupce na primární výstup ze hry (aktivní)** . Nová položka s názvem **zástupce primární výstup ze hry (aktivní)** se zobrazí.

1. Přejmenovat položku místní *hru*, pak přetažení položky do **Uživatelská nabídka programy** uzlu na levé straně okna.

1. V **Průzkumníka řešení**, vyberte **instalátor hry** projekt a zvolte **zobrazení** > **okno vlastností** nebo stiskněte tlačítko  **F4** otevřít **vlastnosti** okna.

1. Zadejte další podrobnosti, jak chcete, aby se objevily v instalačním programu.  Například použít *Contoso* pro **výrobce**, *instalátor hry* pro **název produktu**, a *http\://www.contoso.com* pro **SupportUrl**.

1. V panelu nabídky zvolte **sestavení** > **nástroje Configuration Manager**. V **projektu** tabulky v části **sestavení** sloupců, zaškrtněte políčko u **instalátor hry**. Klikněte na **Zavřít**.

1. V panelu nabídky zvolte **sestavení** > **sestavit řešení** sestavit projekt hry a projektu instalátor hry.

1. Ve složce řešení vyhledejte program setup.exe vytvořený z projektu instalátor hry a pak jeho spuštěním nainstalujte hru ve vašem počítači. Můžete zkopírovat tento soubor (a nalezněte) k instalaci aplikace a jeho požadovaných souborů knihovny v jiném počítači.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2017-and-earlier"></a>Chcete-li nainstalovat instalace a nasazení šablony projektu pro Visual Studio 2017 a starší

1. Pokud jste připojeni k Internetu, v sadě Visual Studio, zvolte **nástroje** > **rozšíření a aktualizace**.

1. V části **rozšíření a aktualizace**, vyberte **Online** kartu a typ *projektů instalačního programu sady Visual Studio Microsoft* do vyhledávacího pole. Spuštění **Enter**vyberte **sady Microsoft Visual Studio \<verze > Projekty instalačního programu**a klikněte na tlačítko **Stáhnout**.

1. Zvolte možnost nainstalovat rozšíření a pak restartujte sadu Visual Studio.

1. V panelu nabídky zvolte **souboru** > **poslední projekty a řešení**a klikněte na tlačítko **hru** řešení, které ho znovu otevřít.

### <a name="to-create-a-setup-project-and-install-your-program"></a>Vytvoření projektu instalace a instalace aplikace

1. Změňte konfiguraci aktivního řešení na Release. V panelu nabídky zvolte **sestavení** > **nástroje Configuration Manager**. V **nástroje Configuration Manager** dialogovém okně **konfigurace aktivního řešení** rozevíracího seznamu vyberte **vydání**. Zvolte **Zavřít** tlačítko, čímž konfiguraci uložíte.

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu** otevřít **nový projekt** dialogové okno.

1. V levém podokně dialogového okna rozbalte **nainstalováno** > **ostatní typy projektů** uzly a pak vyberte **instalační program sady Visual Studio**. V prostředním podokně vyberte **projektu instalace**.

1. Zadejte název projektu instalace v **název** pole. V tomto příkladu zadejte *instalátor hry*. V **řešení** rozevíracího seznamu vyberte **přidat do řešení**. Zvolte **OK** pro vytvoření projektu instalace. A **Pomocník souboru (instalátor hry)** kartě se otevře v okně editoru.

1. Klikněte pravým tlačítkem myši **složky aplikace** uzel a vyberte možnost **přidat** > **výstup projektu** otevřete **Přidat výstupní skupinu projektu**dialogové okno.

1. V dialogovém okně vyberte **primární výstup** a klikněte na tlačítko **OK**. Nová položka s názvem **primární výstup ze hry (aktivní)** se zobrazí.

1. Vyberte položku **primární výstup ze hry (aktivní)** klikněte pravým tlačítkem a zvolte **vytvořit zástupce na primární výstup ze hry (aktivní)** . Nová položka s názvem **zástupce primární výstup ze hry (aktivní)** se zobrazí.

1. Přejmenovat položku místní *hru*, pak přetažení položky do **Uživatelská nabídka programy** uzlu na levé straně okna.

1. V **Průzkumníka řešení**, vyberte **instalátor hry** projekt a zvolte **zobrazení** > **okno vlastností** nebo stiskněte tlačítko  **F4** otevřít **vlastnosti** okna.

1. Zadejte další podrobnosti, jak chcete, aby se objevily v instalačním programu.  Například použít *Contoso* pro **výrobce**, *instalátor hry* pro **název produktu**, a *http\://www.contoso.com* pro **SupportUrl**.

1. V panelu nabídky zvolte **sestavení** > **nástroje Configuration Manager**. V **projektu** tabulky v části **sestavení** sloupců, zaškrtněte políčko u **instalátor hry**. Klikněte na **Zavřít**.

1. V panelu nabídky zvolte **sestavení** > **sestavit řešení** sestavit projekt hry a projektu instalátor hry.

1. Ve složce řešení vyhledejte program setup.exe vytvořený z projektu instalátor hry a pak jeho spuštěním nainstalujte hru ve vašem počítači. Můžete zkopírovat tento soubor (a nalezněte) k instalaci aplikace a jeho požadovaných souborů knihovny v jiném počítači.

::: moniker-end

## <a name="next-steps"></a>Další kroky

**Předchozí:** [Návod: Ladění projektu (C++)](walkthrough-debugging-a-project-cpp.md)

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md)<br/>
[Nasazení aplikací klasické pracovní plochy](../windows/deploying-native-desktop-applications-visual-cpp.md)<br/>
