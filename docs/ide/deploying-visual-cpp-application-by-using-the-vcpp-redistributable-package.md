---
title: Nasazení aplikace s použitím redistribuovatelného balíčku (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e213d5d91c229f7f07bc383f0a0158d85c05cf2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434502"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Návod: Nasazení aplikace Visual C++ s použitím redistribuovatelného balíčku Visual C++

Tento článek popisuje, jak používat Visual C++ Redistributable Package k nasazení aplikace v jazyce Visual C++.

## <a name="prerequisites"></a>Požadavky

Tyto součásti k dokončení tohoto názorného postupu musíte mít:

- Počítač, který nemá nainstalovanou sadu Visual Studio.

- Další počítač, který nemá knihoven Visual C++.

### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Distribuovatelný balíček Visual C++ použít k nasazení aplikace

1. Vytvořte a sestavte aplikaci MFC podle prvních tří kroků v [návod: nasazení Visual C++ Application By Using a Setup Project](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

2. Vytvořte soubor, pojmenujte ho setup.bat a přidejte následující příkazy do ní. Změna `MyMFCApplication` na název vašeho projektu.

    ```cmd
    @echo off
    vcredist_x86.exe
    mkdir "C:\Program Files\MyMFCApplication"
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"
    ```

3. Vytvořte samorozbalovací soubor nastavení:

   1. Na příkazovém řádku nebo v **spustit** okna, spusťte iexpress.exe.

   2. Vyberte **vytvořit novou směrnici pro samorozbalovací soubor** a klikněte na tlačítko **Další** tlačítko.

   3. Vyberte **extrahujte soubory a spusťte instalační příkaz** a klikněte na tlačítko **Další**.

   4. Do textového pole zadejte název aplikace knihovny MFC a klikněte na tlačítko **Další**.

   5. Na **výzvu k potvrzení** stránce **bez výzvy** a klikněte na tlačítko **Další**.

   6. Na **licenční smlouvy** stránce **nezobrazují licenci** a klikněte na tlačítko **Další**.

   7. Na **zabalený soubory** stránce, přidejte následující soubory a pak zvolte **Další**.

      - Aplikace knihovny MFC (soubor .exe).

      - VCRedist_x86.exe. Tento soubor je umístěn v \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\vcredist_x86\\.

      - Soubor setup.bat, který jste vytvořili v předchozím kroku.

   8. Na **spuštění instalačního programu** stránku, **nainstalovat Program** textové pole, zadejte následující příkazový řádek a klikněte na tlačítko **Další**.

      **cmd.exe /c "setup.bat"**

   9. Na **zobrazení okna** stránce **výchozí** a klikněte na tlačítko **Další**.

   10. Na **dokončené zprávy** stránce **žádná zpráva** a klikněte na tlačítko **Další**.

   11. Na **název balíčku a možnosti** stránky, zadejte název samorozbalovací soubor instalace, vyberte **Store souborů s využitím dlouhý název souboru uvnitř balíčku** možnost a klikněte na tlačítko **Další**. Konci názvu souboru musí být Setup.exe—for například MyMFCApplicationSetup.exe.

   12. Na **konfigurace restartování** stránce **bez restartování** a klikněte na tlačítko **Další**.

   13. Na **uložit extrakci směrnici** stránce **uložit extrakci – direktiva () soubor SED** a klikněte na tlačítko **Další**.

   14. Na **vytvořit balíček** zvolte **Další**.

4. Otestujte samorozbalovací instalační soubor na jiný počítač, který nemá knihoven Visual C++:

   1. V jiném počítači stáhnout si kopii instalačního souboru a pak nainstalujte ho spuštěním a následující kroky, které poskytuje.

   2. Spuštění aplikace knihovny MFC.

      Samorozbalovací soubor Instalační program nainstaluje aplikace knihovny MFC, která je ve složce, která jste zadali v kroku 2. Spuštění aplikace je úspěšně, protože instalačního programu distribuovatelného balíčku Visual C++ je součástí samorozbalovací instalační soubor.

      > [!IMPORTANT]
      > Pokud chcete zjistit, která verze modulu runtime je nainstalovaná, instalační program zkontroluje \HKLM\SOFTWARE\Microsoft\VisualStudio\11.0\VC\Runtimes klíče registru\\[platforma]. Pokud aktuálně nainstalované verze je novější než verze, které instalační program se pokouší nainstalovat, instalační program vrátí úspěch bez instalace starší verze a ponechá další položky na stránce s nainstalovanými programy v Ovládacích panelech.

## <a name="see-also"></a>Viz také

[Příklady nasazení](../ide/deployment-examples.md)