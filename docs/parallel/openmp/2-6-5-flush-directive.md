---
title: 2.6.5 flush – direktiva | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a2ec5f74-9c37-424a-8376-47ab4a5829a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d67453b636d50fcb78092318ebb76f5192817548
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442731"
---
# <a name="265-flush-directive"></a>2.6.5 flush – direktiva

**Vyprázdnění** směrnice, zda explicitní nebo implicitní, určuje, ve kterém implementace je potřeba k tomu, že všechna vlákna v týmu mají konzistentní zobrazení určité objekty (uvedené níže) v bodu sekvence "mezi vlákny" paměť. To znamená, že předchozí vyhodnocení výrazů, které odkazují na tyto objekty jsou dokončeny, a ještě nezačali následné hodnocení. Například kompilátory musíte obnovit hodnoty objekty z registrů na paměť a hardware mohou potřebovat k vyprázdnění vyrovnávacích pamětí zápisu na paměť a znovu načíst hodnoty objekty z paměti.

Syntaxe **vyprázdnění** direktivy je následující:

```
#pragma omp flush [(variable-list)]  new-line
```

Pokud objekty, které vyžadují synchronizaci můžete všechny označeny proměnné a pak tyto proměnné lze zadat volitelný *seznamu proměnné*. Pokud je k dispozici v ukazatel *seznamu proměnné*, vyprázdní ukazatel sám, nikoli objekt ukazatel odkazuje na.

A **vyprázdnění** direktiv bez *seznamu proměnné* synchronizuje všechny sdílené objekty s výjimkou v případě nepřístupných objektů s automatickým trváním úložiště. (To je pravděpodobně mají další režii než kolekce **vyprázdnění** s *seznamu proměnné*.) A **vyprázdnění** direktiv bez *seznamu proměnné* implicitní pro následující direktivy:

- `barrier`

- Na vstupu a výstupu z **kritické**

- Na vstupu a výstupu z `ordered`

- Na vstupu a výstupu z **paralelní**

- Opuštění at **pro**

- Opuštění at **oddíly**

- Opuštění at **jeden**

- Na vstupu a výstupu z **paralelní pro**

- Na vstupu a výstupu z **parallel sections –**

Direktiva není zahrnuta, pokud `nowait` je přítomna klauzule. Je třeba poznamenat, který **vyprázdnění** – direktiva není určen pro některý z následujících akcí:

- Vstup **pro**

- Položky nebo opuštění **hlavní**

- Vstup **oddíly**

- Vstup **jeden**

Odkaz, který přistupuje k hodnotě objektu s typem přechodný se chová jako by byly **vyprázdnění** směrnice zadání tohoto objektu na předchozí bod sekvence. Odkaz, který změní hodnotu objektu s typem přechodný se chová jako by byly **vyprázdnění** směrnice zadání tohoto objektu v okamžiku, následné pořadí.

Upozorňujeme, že **vyprázdnění** – direktiva nemá příkaz jazyka C jako součást syntaxe, platí určitá omezení na jeho umístění v rámci programu. Zobrazit [dodatku C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) pro formální gramatiku. Následující příklad znázorňuje tato omezení.

```
/* ERROR - The flush directive cannot be the immediate
*          substatement of an if statement.
*/
if (x!=0)
   #pragma omp flush (x)
...

/* OK - The flush directive is enclosed in a
*      compound statement
*/
if (x!=0) {
   #pragma omp flush (x)
}
```

Omezení **vyprázdnění** směrnice jsou následující:

- Zadané v proměnné **vyprázdnění** direktiva nesmí mít typ odkazu.