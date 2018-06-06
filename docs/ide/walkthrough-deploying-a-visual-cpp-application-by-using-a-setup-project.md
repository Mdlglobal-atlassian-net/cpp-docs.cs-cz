---
title: Nasazení aplikace Visual C++ pomocí projektu instalace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 454507a3a3f33b43af0e50c25dab6703aa75a56b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33332777"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Návod: Nasazení aplikace Visual C++ pomocí projektu instalace
Popisuje postup nasazení aplikace Visual C++ pomocí projektu instalace.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Počítač s [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] nainstalována.  
  
-   Další počítač, který nemá knihovny jazyka Visual C++.  
  
### <a name="to-deploy-an-application-by-using-a-setup-project"></a>Nasazení aplikace pomocí projektu instalace  
  
1.  Použití **MFC ApplicationWizard** k vytvoření nové řešení sady Visual Studio. Najít v Průvodci z **nový projekt** dialogové okno rozbalte položku **Visual C++** uzlu, vyberte **MFC**, vyberte **aplikace knihovny MFC**, zadejte pro projekt a potom klikněte na **OK**.  
  
2.  Změňte konfiguraci aktivním řešení, aby **verze**. Z **sestavení** nabídce vyberte možnost **Configuration Manager**. Z **nástroje Configuration Manager** dialogové okno, vyberte **verze** z **aktivní konfigurace řešení** rozevíracího seznamu.  
  
3.  Stisknutím klávesy F7 sestavení aplikace. Nebo na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. To umožňuje projektu instalace použít výstup tohoto projektu aplikace MFC.  
  
4.  Pokud jste tak již neučinili, stáhněte si InstallShield Limited Edition (MANSKÁ), který je zdarma pro vývojáře v sadě Visual Studio a nahrazuje funkci šablony projektů v sadě Visual Studio pro instalaci a nasazení. Pokud jste připojeni k Internetu, otevřete **nový projekt** dialogové okno a vybrat **soubor**, **nový**, **projektu** v nabídce panelu nebo pomocí pravým tlačítkem myši na řešení v **Průzkumníku řešení** a výběr **přidat**, **nový projekt**. Rozbalte **jiné typy projektů** uzlu, zvolte **Povolit InstallShield Limited Edition** v **instalace a nasazení** uzel a postupujte podle pokynů na obrazovce. Po stáhnout, nainstalovat a aktivovat InstallShield Limited Edition, zavřete Visual Studio a znovu ho otevřete.  
  
5.  Otevřete **nový projekt** dialogové okno znovu, rozbalte **jiné typy projektů** uzel a zvolte **projekt InstallShield Limited Edition** v  **InstallShield Limited Edition** uzlu.  
  
6.  Postupujte podle pokynů v **Začínáme** uzlu projektu instalace vytvořených šablonou InstallShield Limited Edition přidat odkaz na výstup do projektu Visual Studio MFC.  
  
7.  Sestavení projektu instalace k vytvoření souboru instalačního programu (setup.exe). Uděláte to tak, klikněte pravým tlačítkem na uzel projektu Instalační program v **Průzkumníku řešení** a vyberte **sestavení**.  
  
     InstallShield Limited Edition ve stromu projektu Instalační program vytvoří instalační soubor (ve výchozím nastavení, může být umístěn v podsložce Express\SingleImage\DiskImages\DISK1 projektu instalace).  
  
8.  Spusťte instalační program na druhém počítači, který nemá knihovny jazyka Visual C++.  
  
## <a name="see-also"></a>Viz také  
 [Příklady nasazení](../ide/deployment-examples.md)