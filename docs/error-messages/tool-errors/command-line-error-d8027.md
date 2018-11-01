---
title: Chyba příkazového řádku D8027
ms.date: 11/04/2016
f1_keywords:
- D8027
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
ms.openlocfilehash: d3a7908ec9e7e37d83fd7b928cad2ef256313c40
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526796"
---
# <a name="command-line-error-d8027"></a>Chyba příkazového řádku D8027

nelze spustit "součást"

Kompilátor nemůže spustit komponentu daného kompilátoru nebo linkeru.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Načíst součást není dostatek paměti. Pokud NMAKE vyvolá kompilátor spuštění kompilátoru mimo souboru pravidel.

1. Aktuální operační systém se nepovedlo spustit komponentu. Ujistěte se, že body cesty pro spustitelné soubory pro váš operační systém.

1. Komponenta byla poškozena. Překopírovat komponentu z disků distribuce pomocí instalačního programu.

1. Možnost byl nesprávně zadán. Příklad:

    ```
    cl /B1 file1.c
    ```