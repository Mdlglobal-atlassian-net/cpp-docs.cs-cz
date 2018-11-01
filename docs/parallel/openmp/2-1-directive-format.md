---
title: 2.1 Formát direktivy
ms.date: 11/04/2016
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
ms.openlocfilehash: 6ee977005d421a59e71f852be3d78a2caad9b45b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629486"
---
# <a name="21-directive-format"></a>2.1 Formát direktivy

Syntaxe direktivy OpenMP formálně určené gramatiku v [dodatku C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)a neformálně následujícím způsobem:

```
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

Jednotlivé direktivy začíná **#pragma omp**, abyste snížili riziko je v konfliktu s další direktivy pragma (-OpenMP – nebo dodavatele rozšíření OpenMP) se stejnými názvy. Zbývající část direktiva dodržovat konvence standardů C a C++ pro direktivy kompilátoru. Zejména prázdné místo je možné před a po **#**, a v některých případech prázdné místo musí použít k oddělení slov v direktivě. Následující tokeny předzpracování **#pragma omp** se vztahují nahrazení makra.

Direktivy jsou malá a velká písmena. Pořadí, v jakém klauzule uvedeny ve směrnicích není důležité. Klauzule direktivami může opakovat podle potřeby vztahují omezení uvedená v popisu jednotlivým klauzulím. Pokud *seznamu proměnné* se zobrazí v klauzuli, musí určovat pouze proměnné. Pouze jeden *název směrnice* jednu direktivu lze určit.  Například následující direktiva není dovolená:

```
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

Direktivě OpenMP se vztahuje na maximálně jeden následující příkaz, který musí být strukturovaný blok.