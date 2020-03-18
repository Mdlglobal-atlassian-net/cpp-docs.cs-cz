---
title: Nasazení aplikace pomocí redistribuovatelného balíčku (C++)
ms.date: 04/23/2019
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
ms.openlocfilehash: 1e09debc53e5b1b3e1eeaa6a63924b04fd2b7ca5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443888"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Návod: Nasazení aplikace Visual C++ s použitím redistribuovatelného balíčku Visual C++

V tomto podrobném článku se dozvíte, jak použít Visual C++ Redistributable Package k nasazení vizuální C++ aplikace.

## <a name="prerequisites"></a>Předpoklady

K dokončení tohoto Názorného postupu musíte mít tyto komponenty:

- Počítač, ve kterém je nainstalována aplikace Visual Studio.

- Další počítač, který nemá vizuální C++ knihovny.

### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Použití balíčku pro vizuální C++ distribuci k nasazení aplikace

1.  Vytvořte a sestavte aplikaci knihovny MFC pomocí kroků v [návodu: nasazení vizuální C++ aplikace pomocí projektu instalace](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Vytvořte soubor a pojmenujte ho Setup. bat a přidejte do něj následující příkazy. Změňte `MyMFCApplication` na název vašeho projektu.

    ```cmd
    @echo off
    vcredist_x86.exe
    mkdir "C:\Program Files\MyMFCApplication"
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"
    ```

1. Vytvořte samorozbalovací soubor instalačního programu:

   1. V příkazovém řádku nebo v okně **Spustit** spusťte IExpress. exe.

   1. Vyberte **vytvořit nový soubor direktivy pro extrakci** a pak klikněte na tlačítko **Další** .

   1. Vyberte **rozbalte položku soubory a spusťte instalační příkaz** a klikněte na tlačítko **Další**.

   1. Do textového pole zadejte název aplikace MFC a klikněte na tlačítko **Další**.

   1. Na stránce s **výzvou k potvrzení** vyberte možnost **bez výzvy** a pak zvolte možnost **Další**.

   1. Na stránce **Licenční smlouva** vyberte možnost **Nezobrazovat licenci** a klikněte na tlačítko **Další**.

   1. Na stránce **zabalené soubory** přidejte následující soubory a klikněte na tlačítko **Další**.

      - Vaše aplikace MFC (soubor. exe).

      - vcredist_x86.exe. V aplikaci Visual Studio 2015 je tento soubor umístěný ve složce *% VCINSTALLDIR% Redist\\1033\\* . V aplikaci Visual Studio 2017 a Visual Studio 2019 je tento soubor umístěný v umístění *% VCToolsRedistDir%* . Můžete si také [Stáhnout nejnovější podporovaný soubor pro distribuci od Microsoftu](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads).

      - Soubor Setup. bat, který jste vytvořili v předchozím kroku.

   1. Na stránce **instalovat program, který má být spuštěn** , zadejte do textového pole **instalovat program** následující příkazový řádek a klikněte na tlačítko **Další**.

      **cmd. exe/c "Setup. bat"**

   1. Na stránce **Zobrazit okno** vyberte **výchozí** a pak zvolte **Další**.

   1. Na stránce **Dokončená zpráva** vyberte možnost **žádná zpráva** a klikněte na tlačítko **Další**.

   1. Na stránce **název balíčku a možnosti** zadejte název souboru instalačního programu pro samorozbalovací soubory, v možnosti **balení vyberte soubory úložiště s dlouhým názvem** a klikněte na tlačítko **Další**. Konec názvu souboru musí být Setup. exe, například *MyMFCApplicationSetup. exe*.

   1. Na stránce **Konfigurovat restart** vyberte možnost **bez restartování** a pak klikněte na tlačítko **Další**.

   1. Na stránce **uložení direktivy pro extrakci osobníku** vyberte možnost **Uložit soubor s samočinnou extrakcí (SED)** a pak zvolte možnost **Další**.

   1. Na stránce **vytvořit balíček** klikněte na tlačítko **Další**. Klikněte na tlačítko **Dokončit**.

1. Test samorozbalovacího instalačního souboru na jiném počítači, který nemá vizuální C++ knihovny:

   1. V druhém počítači stáhněte kopii instalačního souboru a pak ji nainstalujte spuštěním a podle kroků, které poskytuje. V závislosti na vybraných možnostech může instalace vyžadovat příkaz **Spustit jako správce** .

   1. Spusťte aplikaci MFC.

      Samorozbalovací instalační soubor nainstaluje aplikaci MFC, která se nachází ve složce, kterou jste zadali v kroku 2. Aplikace je úspěšně spuštěna, protože instalační C++ program sady Visual Redistributable Package je zahrnut do souboru instalačního programu pro samorozbalovací soubory.

      > [!IMPORTANT]
      > Pokud chcete zjistit, která verze modulu runtime je nainstalovaná, instalační služba zkontroluje klíč registru \\HKLM\\SOFTWARE\\Microsoft\\VisualStudio\\_verze_\\VC\\runtime\\verze _platformy_\\. Pokud je aktuálně nainstalovaná verze novější než verze, kterou se instalační program pokouší nainstalovat, instalační program vrátí úspěch bez instalace starší verze a ponechá další položku na stránce nainstalované programy v Ovládacích panelech.

## <a name="see-also"></a>Viz také

[Příklady nasazení](deployment-examples.md)<br/>
