---
title: Nasazení aplikace s použitím redistribuovatelného balíčku (C++)
ms.date: 09/17/2018
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
ms.openlocfilehash: ccf6b74096894c2e48258e6e0a60b807c7c6c5b4
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787024"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Návod: Nasazení aplikace v jazyce Visual C++ s použitím redistribuovatelného balíčku Visual C++

Tento článek popisuje, jak používat Visual C++ Redistributable Package k nasazení aplikace v jazyce Visual C++.

## <a name="prerequisites"></a>Požadavky

Tyto součásti k dokončení tohoto názorného postupu musíte mít:

- Počítač, který nemá nainstalovanou sadu Visual Studio.

- Další počítač, který nemá knihoven Visual C++.

### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Distribuovatelný balíček Visual C++ použít k nasazení aplikace

1.  Vytvoření a sestavení aplikace knihovny MFC podle postupu v [názorný postup: Nasazení aplikace v jazyce Visual C++ pomocí projektu instalace](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Vytvořte soubor, pojmenujte ho setup.bat a přidejte následující příkazy do ní. Změna `MyMFCApplication` na název vašeho projektu.

    ```cmd
    @echo off
    vcredist_x86.exe
    mkdir "C:\Program Files\MyMFCApplication"
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"
    ```

1. Vytvořte samorozbalovací soubor nastavení:

   1. Na příkazovém řádku nebo v **spustit** okna, spusťte iexpress.exe.

   1. Vyberte **vytvořit novou směrnici pro samorozbalovací soubor** a klikněte na tlačítko **Další** tlačítko.

   1. Vyberte **extrahujte soubory a spusťte instalační příkaz** a klikněte na tlačítko **Další**.

   1. Do textového pole zadejte název aplikace knihovny MFC a klikněte na tlačítko **Další**.

   1. Na **výzvu k potvrzení** stránce **bez výzvy** a klikněte na tlačítko **Další**.

   1. Na **licenční smlouvy** stránce **nezobrazují licenci** a klikněte na tlačítko **Další**.

   1. Na **zabalený soubory** stránce, přidejte následující soubory a pak zvolte **Další**.

      - Aplikace knihovny MFC (soubor .exe).

      - vcredist_x86.exe. Tento soubor je umístěn v \Program Files (x86) \Microsoft Visual Studio \<verze > \SDK\Bootstrapper\Packages\. Můžete také stáhnout tento soubor z [Microsoft](https://www.microsoft.com/download/confirmation.aspx?id=5555).

      - Soubor setup.bat, který jste vytvořili v předchozím kroku.

   1. Na **spuštění instalačního programu** stránku, **nainstalovat Program** textové pole, zadejte následující příkazový řádek a klikněte na tlačítko **Další**.

      **cmd.exe /c "setup.bat"**

   1. Na **zobrazení okna** stránce **výchozí** a klikněte na tlačítko **Další**.

   1. Na **dokončené zprávy** stránce **žádná zpráva** a klikněte na tlačítko **Další**.

   1. Na **název balíčku a možnosti** stránky, zadejte název samorozbalovací soubor instalace, vyberte **Store souborů s využitím dlouhý název souboru uvnitř balíčku** možnost a klikněte na tlačítko **Další**. Konci názvu souboru musí být například Setup.exe—for *MyMFCApplicationSetup.exe*.

   1. Na **konfigurace restartování** stránce **bez restartování** a klikněte na tlačítko **Další**.

   1. Na **uložit extrakci směrnici** stránce **uložit extrakci – direktiva () soubor SED** a klikněte na tlačítko **Další**.

   1. Na **vytvořit balíček** zvolte **Další**. Zvolte **Dokončit**.

1. Otestujte samorozbalovací instalační soubor na jiný počítač, který nemá knihoven Visual C++:

   1. V jiném počítači stáhnout si kopii instalačního souboru a pak nainstalujte ho spuštěním a následující kroky, které poskytuje. Vybrané možnosti instalace může trvat v závislosti **spustit jako správce** příkazu.

   1. Spuštění aplikace knihovny MFC.

      Samorozbalovací soubor Instalační program nainstaluje aplikace knihovny MFC, která je ve složce, která jste zadali v kroku 2. Spuštění aplikace je úspěšně, protože instalačního programu distribuovatelného balíčku Visual C++ je součástí samorozbalovací instalační soubor.

      > [!IMPORTANT]
      > Pokud chcete zjistit, která verze modulu runtime je nainstalovaná, instalační program zkontroluje \HKLM\SOFTWARE\Microsoft\VisualStudio klíče registru\\\<verze > \VC\Runtimes\\<platform>. Pokud aktuálně nainstalované verze je novější než verze, které instalační program se pokouší nainstalovat, instalační program vrátí úspěch bez instalace starší verze a ponechá další položky na stránce s nainstalovanými programy v Ovládacích panelech.

## <a name="see-also"></a>Viz také:

[Příklady nasazení](deployment-examples.md)<br/>
