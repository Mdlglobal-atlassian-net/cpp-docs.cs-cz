---
title: Chyba sestavení projektu PRJ0009
ms.date: 11/04/2016
f1_keywords:
- PRJ0009
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
ms.openlocfilehash: 963b7c861f9e8ee7105ebdc23afff08c4be46465
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438092"
---
# <a name="project-build-error-prj0009"></a>Chyba sestavení projektu PRJ0009

Vytvoření protokolu nelze otevřít pro zápis.

**Ujistěte se, že soubor není otevřen jiným procesem a že není chráněn proti zápisu.**

Po nastavení **sestavení protokolování** vlastnost **Ano** a provádění sestavení nebo opětovné sestavení, Visual C++ se nepodařilo otevřít protokol sestavení ve výhradním režimu.

Zkontrolujte **sestavení protokolování** nastavení tak, že otevřete **možnosti** dialogové okno (na **nástroje** nabídky, klikněte na tlačítko **možnosti** příkaz) a pak Výběr **sestavení VC ++** v **projekty** složky. Soubor sestavení se nazývá BuildLog.htm a je zapsaný $ zprostředkující adresář (IntDir).

Možné důvody této chyby:

- Jsou spuštěné dva procesy jazyka Visual C++ a chcete současně vytvořit stejnou konfiguraci stejného projektu v obou.

- Soubor protokolu sestavení je otevřený v procesu, který uzamkne soubor.

- Uživatel nemá oprávnění k vytvoření souboru.

- Aktuální uživatel nemá oprávnění k zápisu do souboru BuildLog.htm.