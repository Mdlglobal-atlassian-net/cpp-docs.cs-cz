---
title: 2.6.3 barrier – direktiva | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8654534143e6feed06e93406c8fe03983ee9c2fc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429146"
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