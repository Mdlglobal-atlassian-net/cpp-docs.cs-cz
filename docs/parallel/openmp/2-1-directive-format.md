---
title: 2.1 formát direktivy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b2f2d2f5742dbc4faa1d8386e935c9d4ccc8049
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424648"
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