---
title: Nasazení aplikace v jazyce Visual C++ pomocí projektu instalace | Dokumentace Microsoftu
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
ms.openlocfilehash: 36aad914fc9552cea06eabd0898fe33b9b09481e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605828"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Návod: Nasazení aplikace Visual C++ pomocí projektu instalace
Popisuje, jak nasadit aplikace v jazyce Visual C++ pomocí projektu instalace.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Počítače s Visual Studio 2012 nainstalovat.  
  
-   Další počítač, který nemá knihoven Visual C++.  
  
### <a name="to-deploy-an-application-by-using-a-setup-project"></a>K nasazení aplikace pomocí projektu instalace  
  
1.  Použití **MFC ApplicationWizard** vytvořit nové řešení sady Visual Studio. Najít průvodce, ze **nový projekt** dialogového okna rozbalte **Visual C++** uzlu, vyberte **MFC**vyberte **aplikace knihovny MFC**, zadejte název projektu a klikněte na **OK**.  
  
2.  Změňte konfiguraci aktivního řešení na **vydání**. Z **sestavení** nabídce vyberte možnost **Správce konfigurace**. Z **nástroje Configuration Manager** dialogu **vydání** z **konfigurace aktivního řešení** rozevíracího seznamu.  
  
3.  Stisknutím klávesy F7 k sestavení aplikace. Případně na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. To umožňuje nastavení projektu používají výstup tohoto projektu aplikace knihovny MFC.  
  
4.  Pokud jste tak již neučinili, stáhněte si InstallShield Limited Edition (ISLE), který je zdarma pro vývojáře v sadě Visual Studio a nahrazuje funkcionalitu šablon projektů v sadě Visual Studio pro instalaci a nasazení. Pokud jste připojeni k Internetu, otevřete **nový projekt** dialogové okno výběrem **souboru**, **nový**, **projektu** v nabídce panelu nebo pomocí pravým tlačítkem myši na řešení v **Průzkumníka řešení** a zvolíte **přidat**, **nový projekt**. Rozbalte **ostatní typy projektů** uzlu, vyberte **Povolit InstallShield Limited Edition** v **instalace a nasazení** uzel a postupujte podle pokynů na obrazovce. Po stažení, instalaci a aktivaci programu InstallShield Limited Edition, zavřete sadu Visual Studio a znovu ho otevřete.  
  
5.  Otevřít **nový projekt** dialogové okno znovu, rozbalte **ostatní typy projektů** uzel a zvolte **projektu InstallShield Limited Edition** v  **InstallShield Limited Edition** uzlu.  
  
6.  Postupujte podle pokynů **Začínáme** uzlu projektu instalace vytvořených šablonou InstallShield Limited Edition pro přidání odkazu na výstup do projektu knihovny MFC Visual Studio.  
  
7.  Sestavte projekt instalace k vytvoření souboru Instalační služby (setup.exe). Uděláte to tak, klikněte pravým tlačítkem myši na uzel projektu instalace v **Průzkumníka řešení** a vyberte **sestavení**.  
  
     InstallShield Limited Edition vytvoří instalační soubor ve stromu projektu instalace (ve výchozím nastavení, může být umístěn v podsložce Express\SingleImage\DiskImages\DISK1 v nastavení projektu).  
  
8.  Spusťte instalační program na druhém počítači, který nemá žádné knihovny Visual C++.  
  
## <a name="see-also"></a>Viz také  
 [Příklady nasazení](../ide/deployment-examples.md)