---
title: Chyba sestavení projektu PRJ0009 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0009
dev_langs:
- C++
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5692ec643f5e3fe1adebf68048a6c435ab05d6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0009"></a>Chyba sestavení projektu PRJ0009
Sestavení protokolu nelze otevřít pro zápis.  
  
 **Ujistěte se, zda soubor není otevřen jiným procesem a není chráněna proti zápisu.**  
  
 Po nastavení **sestavení protokolování** vlastnost **Ano** a provádění sestavení nebo opětovném sestavení, Visual C++ se nepodařilo otevřít protokolu sestavení ve výhradním režimu.  
  
 Zkontrolujte **sestavení protokolování** nastavení otevřením **možnosti** dialogové okno (na **nástroje** nabídky, klikněte na tlačítko **možnosti** příkaz) a potom Výběr **VC ++ sestavení** v **projekty** složky. Soubor sestavení je volána BuildLog.htm a je zapsán do zprostředkující directory $(IntDir).  
  
 Možné důvody této chyby:  
  
-   Jsou spuštěné dva procesy Visual c++ a pokusu o vytvoření stejnou konfiguraci stejného projektu v obou současně.  
  
-   Soubor protokolu sestavení je otevřen v procesu, který uzamkne soubor.  
  
-   Uživatel nemá oprávnění k vytvoření souboru.  
  
-   Aktuální uživatel nemá oprávnění k zápisu do souboru BuildLog.htm.