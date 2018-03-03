---
title: "Řešení potíží s přizpůsobení sestavení | Microsoft Docs"
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
- build events [C++], troubleshooting
- builds [C++], build events
- troubleshooting [C++], builds
- build steps [C++], troubleshooting
- events [C++], build
- builds [C++], troubleshooting
- custom build steps [C++], troubleshooting
ms.assetid: e4ceb177-fbee-4ed3-a7d7-80f0d78c1d07
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5fa3b2d3910a71d189f5177e13fbd91930e15ee8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="troubleshooting-build-customizations"></a>Řešení potíží s přizpůsobením sestavení
Pokud vaše vlastní kroky sestavení nebo události nejsou chovají podle očekávání, existuje několik věcí, které můžete provést zkuste zjistit příčinu problému.  
  
-   Ujistěte se, že soubory, které vlastní kroky generovat odpovídat soubory, které je deklarovat jako výstup.  
  
-   Pokud vaše vlastní kroky sestavení generovat všechny soubory, které jsou vstupy nebo závislosti jiných sestavení kroky (vlastní nebo jiných), ujistěte se, že tyto soubory jsou přidány do projektu. A ujistěte se, že spuštění nástroje, které využívají tyto soubory po vlastní krok sestavení.  
  
-   Chcete-li zobrazit vlastního kroku sestavení je ve skutečnosti činnosti, přidejte `@echo on` jako první příkaz. Události sestavení a kroků sestavení jsou vložte do souboru dočasný .bat a spustit, když sestavení projektu. Proto můžete přidat Chyba při ověřování k události sestavení nebo sestavení krok příkazy.  
  
-   Vyhledejte v protokolu sestavení v adresáři zprostředkující soubory zobrazíte co skutečně proveden. Cesta a název protokolu sestavení je reprezentována **MSBuild** makro výraz **$(IntDir)\\$(MSBuildProjectName) .log**.  
  
-   Upravte nastavení projektu shromažďovat více než výchozí množství informací v protokolu sestavení. Na **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogové okno, klikněte na tlačítko **projekty a řešení** uzel a pak klikněte na tlačítko **sestavit a spustit** uzlu. Potom v **podrobnosti souboru MSBuild projektu sestavení protokolu** pole, klikněte na tlačítko **podrobné**.  
  
-   Ověřte, že hodnoty libovolného souboru, adresáře nebo název makra, kterou používáte. Můžete vypsat makra jednotlivě, nebo můžete přidat `copy %0 command.bat` na začátek vlastního kroku sestavení, který zkopíruje příkazy vašeho vlastního kroku sestavení do souboru command.bat se všemi makry rozbaleny.  
  
-   Spusťte vlastní kroky sestavení a události jednotlivě, abyste zkontrolujte jejich chování sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Seznámení s kroky vlastního sestavení a s událostmi sestavení](../ide/understanding-custom-build-steps-and-build-events.md)