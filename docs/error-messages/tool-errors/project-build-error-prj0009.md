---
title: Chyba sestavení projektu PRJ0009 | Dokumentace Microsoftu
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
ms.openlocfilehash: efeb110823e801dd86a503a7069c4898f400769e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057181"
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