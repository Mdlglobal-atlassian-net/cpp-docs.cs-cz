---
title: "Nasazení aplikace s použitím redistribuovatelného balíčku (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52e3b048f896f0cfd532cb3000617756af2dca92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Návod: Nasazení aplikace Visual C++ s použitím redistribuovatelného balíčku Visual C++
Tento článek podrobně popisuje, jak používat Visual C++ Redistributable Package k nasazení aplikace Visual C++.  
  
## <a name="prerequisites"></a>Požadavky  
 Tyto součásti pro dokončení tohoto návodu, musíte mít:  
  
-   Počítač, který má nainstalovanou sadu Visual Studio.  
  
-   Další počítač, který nemá knihovny jazyka Visual C++.  
  
### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Nasazení aplikace pomocí distribuovatelného balíčku Visual C++  
  
1.  Vytvořte a sestavte aplikaci MFC podle prvních tří kroků v [návod: nasazení Visual C++ aplikace pomocí projektu instalace](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).  
  
2.  Vytvoření souboru, název setup.bat a do ní přidejte následující příkazy. Změna `MyMFCApplication` na název projektu.  
  
    ```cmd
    @echo off  
    vcredist_x86.exe  
    mkdir "C:\Program Files\MyMFCApplication"  
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"  
    ```  
  
3.  Vytvořte soubor Samorozbalující instalační program:  
  
    1.  Na příkazovém řádku nebo v **spustit** okně Spusťte iexpress.exe.  
  
    2.  Vyberte **vytvořit novou směrnici pro samorozbalovací soubor** a potom zvolte **Další** tlačítko.  
  
    3.  Vyberte **extrahujte soubory a spustit instalační příkaz** a potom zvolte **Další**.  
  
    4.  Do textového pole zadejte název vaší aplikace knihovny MFC a potom zvolte **Další**.  
  
    5.  Na **výzvu k potvrzení** vyberte **bez výzvy** a potom zvolte **Další**.  
  
    6.  Na **licenční smlouvy** vyberte **nezobrazovat licenci** a potom zvolte **Další**.  
  
    7.  Na **zabalené soubory** stránce, přidejte následující soubory a pak vyberte **Další**.  
  
        -   Aplikace MFC (soubor .exe).  
  
        -   VCRedist_x86.exe. Tento soubor je umístěný v \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\vcredist_x86\\.  
  
        -   Setup.bat soubor, který jste vytvořili v předchozím kroku.  
  
    8.  Na **spuštění instalačního programu** stránky v **nainstalovat Program** textového pole, zadejte na příkazovém řádku následující a potom zvolte **Další**.  
  
         **cmd.exe /c "setup.bat"**  
  
    9. Na **zobrazit okno** vyberte **výchozí** a potom vyberte **Další**.  
  
    10. Na **dokončení zpráva** vyberte **žádná zpráva** a potom zvolte **Další**.  
  
    11. Na **název balíčku a možnosti** stránky, zadejte název pro samorozbalovací soubor instalace, vyberte **ukládat soubory pomocí dlouhý název souboru v balíčku** možnost a potom vyberte **Další**. Konci názvu souboru musí být Setup.exe—for například MyMFCApplicationSetup.exe.  
  
    12. Na **konfigurace restartování** vyberte **bez restartování** a potom zvolte **Další**.  
  
    13. Na **Uložit směrnici extrakce** vyberte **soubor uložit samoobslužné extrakce – direktiva (MENŠIT)** a potom zvolte **Další**.  
  
    14. Na **vytvořit balíček** vyberte **Další**.  
  
4.  Testovací samorozbalovací instalační soubor v jiném počítači, který nemá knihovny jazyka Visual C++:  
  
    1.  V jiném počítači stáhněte si kopii souboru instalačního programu a poté jej nainstalujte spuštěním ho a následující kroky, které poskytuje.  
  
    2.  Spusťte aplikaci MFC.  
  
         Samorozbalovací soubor Instalační program nainstaluje aplikace MFC, která je ve složce, kterou jste zadali v kroku 2. Aplikace se úspěšně proběhne, protože instalační program Visual C++ Redistributable Package je obsažena v samorozbalovací instalační soubor.  
  
        > [!IMPORTANT]
        >  Pokud chcete zjistit, která verze modulu runtime je nainstalovaná, instalační program kontroluje \HKLM\SOFTWARE\Microsoft\VisualStudio\11.0\VC\Runtimes klíče registru\\[platformu]. Pokud aktuálně nainstalovaná verze je novější než verze, který instalační program se snaží nainstalovat, instalační program vrátí úspěch bez instalace starší verzi a nechá další záznam na stránce nainstalovaných programů v Ovládacích panelech.  
  
## <a name="see-also"></a>Viz také  
 [Příklady nasazení](../ide/deployment-examples.md)