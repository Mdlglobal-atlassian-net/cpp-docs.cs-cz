---
title: Chyba příkazového řádku D8027 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8027
dev_langs:
- C++
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8234835d3bb0545c8a72bf35cfb55b2e18bc7da2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070376"
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