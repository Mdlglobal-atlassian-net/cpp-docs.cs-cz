---
title: Nasazení aplikace pomocí redistribuovatelného balíčku (C++)
ms.date: 04/23/2019
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
ms.openlocfilehash: d2bd0794a67cf70b9da0499e3d2cafa553531fe1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370245"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Návod: Nasazení aplikace Visual C++ s použitím redistribuovatelného balíčku Visual C++

Tento podrobný článek popisuje, jak použít visual c++ redistribuovatelný balíček k nasazení aplikace Visual C++.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu musíte mít tyto součásti:

- Počítač s nainstalovaným souborem Visual Studio.

- Další počítač, který nemá knihovny Visual C++.

### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Použití redistribuovatelného balíčku Visual C++ k nasazení aplikace

1. Vytvořte a vytvořte aplikaci knihovny MFC podle kroků v [návodu: Nasazení aplikace Visual C++ pomocí instalačního projektu](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Vytvořte soubor, pojmenujte jej setup.bat a přidejte do něj následující příkazy. Změňte `MyMFCApplication` název projektu.

    ```cmd
    @echo off
    vcredist_x86.exe
    mkdir "C:\Program Files\MyMFCApplication"
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"
    ```

1. Vytvořte vlastní extrahovací instalační soubor:

   1. Na příkazovém řádku nebo v okně **Spustit** spusťte soubor iexpress.exe.

   1. Vyberte **Vytvořit nový soubor směrnice o vlastní extrakci** a pak zvolte tlačítko **Další.**

   1. Vyberte **Extrahovat soubory a spusťte příkaz instalace** a pak zvolte **Další**.

   1. Do textového pole zadejte název aplikace Knihovny MFC a pak zvolte **Další**.

   1. Na stránce **S výzvou k potvrzení** vyberte Bez **výzvy** a pak zvolte **Další**.

   1. Na stránce **Licenční smlouva** vyberte **Nezobrazovat licenci** a pak zvolte **Další**.

   1. Na stránce **Zabalené soubory** přidejte následující soubory a pak zvolte **Další**.

      - Aplikace MFC (soubor.exe).

      - vcredist_x86.exe. V sadě Visual Studio 2015 je tento soubor umístěn v *%VCINSTALLDIR%redist\\1033\\*. V souborech Visual Studio 2017 a Visual Studio 2019 je tento soubor umístěn v *%VCToolsRedistDir%*. Můžete si také [stáhnout nejnovější podporovaný redist soubor od společnosti Microsoft](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads).

      - Soubor setup.bat, který jste vytvořili v předchozím kroku.

   1. Na stránce **Instalovat program ke spuštění** zadejte do textového pole Instalovat **program** následující příkazový řádek a pak zvolte **Další**.

      **cmd.exe /c "setup.bat"**

   1. Na stránce **Zobrazit okno** vyberte **Výchozí** a pak zvolte **Další**.

   1. Na stránce **Dokončená zpráva** vyberte **Žádná zpráva** a pak zvolte **Další**.

   1. Na stránce **Název balíčku a možnosti** zadejte název vlastního extrahovacího instalačního souboru, vyberte **Uložit soubory pomocí možnosti Dlouhý název souboru v možnosti Balíček** a pak zvolte **Další**. Konec názvu souboru musí být Setup.exe – například *MyMFCApplicationSetup.exe*.

   1. Na stránce **Konfigurovat restartování** vyberte **Možnost Nerestartovat** a pak zvolte **Další**.

   1. Na stránce **Uložit vlastní extrakci** vyberte **Uložit soubor SED (Save Self Extraction Directive)** a pak zvolte **Další**.

   1. Na stránce **Vytvořit balíček** zvolte **Další**. Zvolte **Dokončit**.

1. Otestujte samorozbalovací instalační soubor v jiném počítači, který nemá knihovny Visual C++:

   1. V druhém počítači stáhněte kopii instalačního souboru a nainstalujte ji spuštěním a podle pokynů, které poskytuje. V závislosti na vybraných možnostech může instalace vyžadovat příkaz **Spustit jako správce.**

   1. Spusťte aplikaci Knihovny MFC.

      Samorozbalovací instalační soubor nainstaluje aplikaci knihovny MFC, která je ve složce zadané v kroku 2. Aplikace se úspěšně spustí, protože instalační program redistribuovatelného balíčku Visual C++ je součástí instalačního souboru pro samorozbalování.

      > [!IMPORTANT]
      > Chcete-li zjistit, která verze runtime je nainstalována, instalační\\program\\zkontroluje klíč\\\\ \\registru HKLM\\SOFTWARE Microsoft VisualStudio\\_verze_\\VC Runtimes_platformy_\\Verze. Pokud je aktuálně nainstalovaná verze novější než verze, kterou se instalátor pokouší nainstalovat, instalační program vrátí úspěch bez instalace starší verze a ponechá další položku na stránce nainstalovaných programů v Ovládacích panelech.

## <a name="see-also"></a>Viz také

[Příklady nasazení](deployment-examples.md)<br/>
