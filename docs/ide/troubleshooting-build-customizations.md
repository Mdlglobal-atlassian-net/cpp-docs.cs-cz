---
title: Řešení potíží s vlastní nastavení sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2821c851c5b4498250a78f33eb111dd5f20ae272
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895146"
---
# <a name="troubleshooting-build-customizations"></a>Řešení potíží s přizpůsobením sestavení

Pokud vaše vlastní kroky sestavení nebo události se nechová podle očekávání, existuje několik věcí, které vám pomůžou se pokouší o vysvětlení, co je špatně.

- Ujistěte se, že soubory, které vaše vlastní kroky sestavení generovat odpovídaly souborům, který deklarujete jako výstup.

- Pokud vaše vlastní kroky sestavení vygenerovat žádné soubory, které jsou vstupy nebo kroky (vlastní nebo jinak) závislosti jiných sestavení, ujistěte se, že tyto soubory jsou přidány do projektu. A ujistěte se, že spuštění nástroje, které využívají tyto soubory po vlastní krok sestavení.

- K zobrazení vlastního kroku sestavení je ve skutečnosti činnosti, přidejte `@echo on` jako první příkaz. Události sestavení a kroků sestavení jsou vložit do souboru dočasné .bat a spustit při sestavení projektu. Proto můžete přidat Chyba při ověřování k události sestavení nebo sestavení krokových příkazů.

- Vyhledejte v protokolu sestavení v adresáři zprostředkujících souborů chcete zobrazit, co skutečně proveden. Cesta a název protokolu sestavení je reprezentována **MSBuild** – makro výraz **$(IntDir)\\$(MSBuildProjectName) .log**.

- Upravte nastavení projektu shromažďovat více než výchozí množství informací protokolu sestavení. Na **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogové okno, klikněte na tlačítko **projekty a řešení** uzlu a pak klikněte na tlačítko **sestavíte a spustíte** uzlu. Potom v **podrobnost soubor MSBuild projekt sestavení protokolu** klikněte **podrobné**.

- Ověřte, že hodnoty libovolného souboru makra název nebo adresář, který používáte. Makra můžete vypsat jednotlivě, nebo můžete přidat `copy %0 command.bat` pro spuštění vlastního kroku sestavení, která zkopíruje kroku vlastního sestavení příkazy do souboru command.bat se všechna makra rozšířit.

- Spuštění vlastní kroky sestavení a události jednotlivě a zkontrolovat jejich chování sestavení.

## <a name="see-also"></a>Viz také

[Seznámení s kroky vlastního sestavení a s událostmi sestavení](../ide/understanding-custom-build-steps-and-build-events.md)