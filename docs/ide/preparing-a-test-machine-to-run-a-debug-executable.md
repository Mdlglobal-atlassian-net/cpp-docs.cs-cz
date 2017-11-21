---
title: "Příprava testovacího počítače ke spuštění ladicího spustitelného souboru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: debug executable, preparing a test machine to run
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1b8b675f6125ce6449dc1627e8ba1f375f87aade
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="preparing-a-test-machine-to-run-a-debug-executable"></a>Příprava testovacího počítače ke spuštění ladicího spustitelného souboru
Chcete-li připravit počítač na testování ladicí verze aplikace sestavené aplikací Visual C++, je zapotřebí nasadit ladicí verze knihoven DLL jazyka Visual C++, na kterých aplikace závisí. Chcete-li zjistit, které mají být nasazeny knihovny DLL, postupujte podle kroků v [Principy závislostí aplikace Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Ladicí verze knihoven DLL jazyka Visual C++ mají obvykle názvy končící písmenem „d“. Například ladicí verze knihovny msvcr100.dll má název msvcr100d.dll.  
  
> [!NOTE]
>  Ladicí verze aplikace ani ladicí verze knihoven DLL jazyka Visual C++ nelze distribuovat. Tyto verze je povoleno nasazovat pouze na vlastní počítače, a to pouze za účelem ladění a testování aplikací na počítači, na němž není nainstalována sada Visual Studio. Další informace najdete v tématu [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
 Ladicí verze knihoven DLL jazyka Visual C++ lze spolu s ladicí verzí aplikace nasadit třemi různými způsoby.  
  
-   Pomocí centrálního nasazení nainstalujte ladicí verzi konkrétní knihovny DLL jazyka Visual C++ do adresáře %windir%\system32\ prostřednictvím Projektu instalace, který obsahuje slučovací moduly pro správnou verzi knihovny a architekturu aplikace. Slučovací moduly, které se nacházejí v Program Files nebo adresář Program Files (x86) v \Common Files\Merge moduly\\. Ladicí verze slučovacího modulu obsahuje ve svém názvu řetězec Debug, například Microsoft_VC110_DebugCRT_x86.msm. Příklad tohoto nasazení lze nalézt v [návod: nasazení Visual C++ aplikace pomocí projektu instalace](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).  
  
-   Použít místní nasazení k instalaci ladicí verze konkrétní knihovny DLL Visual C++ v adresáři aplikace instalace pomocí souborů, které jsou součástí Program Files nebo adresář Program Files (x86) v \Microsoft Visual Studio \<verze > \VC\redist\Debug_NonRedist\\.  
  
    > [!NOTE]
    >  Chcete-li vzdáleně ladit aplikaci sestavenou aplikací Visual C++ 2005 nebo Visual C++ 2008 na jiném počítači, je zapotřebí nasadit ladicí verze knihoven DLL jazyka Visual C++ jako sdílená sestavení vedle sebe. Odpovídající slučovací moduly lze nainstalovat pomocí Projektu instalace nebo pomocí Instalační služby systému Windows.  
  
-   Použít the_**nasadit** možnost **nástroje Configuration Manager** dialogové okno v sadě Visual Studio pro kopírování výstupu projektu @ a další soubory do vzdáleného počítače. 
  
 Po nainstalování knihoven DLL jazyka Visual C++ lze ve sdílené síťové složce spustit vzdálený ladicí program. Další informace o vzdáleném ladění najdete v tématu [vzdálené ladění](/visualstudio/debugger/remote-debugging.md).  
  
## <a name="see-also"></a>Viz také  
 
 [Nasazení v jazyce Visual C++](../ide/deployment-in-visual-cpp.md)   
 [Možnosti řádku příkaz Instalační služby systému Windows](http://msdn.microsoft.com/library/windows/desktop/aa367988.aspx)   
 [Příklady nasazení](../ide/deployment-examples.md) [vzdálené ladění](/visualstudio/debugger/remote-debugging.md)