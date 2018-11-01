---
title: 2.6.3 barrier – direktiva
ms.date: 11/04/2016
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
ms.openlocfilehash: 9079dce4b2a27e91e349fd0df8414d38cd245d2e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637018"
---
# <a name="263-barrier-directive"></a>2.6.3 barrier – direktiva

**Bariéry** – direktiva synchronizuje všechna vlákna v týmu. Vyskytne-li tuto možnost, každé vlákno v týmu čeká na všechny ostatní dosáhli tohoto bodu. Syntaxe **bariéry** direktivy je následující:

```
#pragma omp barrier new-line
```

Po všech vláken v týmu došlo k bariéry, začne každé vlákno v týmu, spouštět příkazy po barrier – direktiva paralelně. Upozorňujeme, že **bariéry** – direktiva nemá příkaz jazyka C jako součást syntaxe, platí určitá omezení na jeho umístění v rámci programu. Zobrazit [dodatku C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) pro formální gramatiku. Následující příklad znázorňuje tato omezení.

```
/* ERROR - The barrier directive cannot be the immediate
*          substatement of an if statement
*/
if (x!=0)
   #pragma omp barrier
...

/* OK - The barrier directive is enclosed in a
*      compound statement.
*/
if (x!=0) {
   #pragma omp barrier
}
```