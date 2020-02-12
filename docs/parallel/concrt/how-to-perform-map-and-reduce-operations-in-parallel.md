---
title: 'Postupy: Paralelní provádění operací mapování a redukce'
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
ms.openlocfilehash: 599e46c05a91a1f2ea6e317fe024d3c98a78977f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141712"
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>Postupy: Paralelní provádění operací mapování a redukce

Tento příklad ukazuje, jak použít algoritmus [Concurrency::p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) a [concurrency::p arallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) a třídu [Concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) k počítání výskytů slov v souborech.

Operace *mapování* aplikuje funkci na každou hodnotu v sekvenci. Operace *snížení* kombinuje prvky sekvence do jedné hodnoty. Pomocí C++ standardních knihoven funkce [std:: Transform](../../standard-library/algorithm-functions.md#transform) a [std:: Akumulovaná](../../standard-library/numeric-functions.md#accumulate) můžete provádět mapování a snižovat operace. Pro zlepšení výkonu mnoha problémů však můžete použít algoritmus `parallel_transform` k paralelnímu provedení operace mapování a algoritmus `parallel_reduce` k paralelnímu provedení operace zmenšení. V některých případech můžete použít `concurrent_unordered_map` k provedení mapy a zmenšení v jedné operaci.

## <a name="example"></a>Příklad

Následující příklad spočítá výskyt slov v souborech. Používá [std:: Vector](../../standard-library/vector-class.md) k reprezentaci obsahu dvou souborů. Operace map počítá výskyty každého slova v každém vektoru. Operace zmenšení nashromáždí počet slov v obou vektorech.

[!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li zkompilovat kód, zkopírujte jej a vložte jej do projektu aplikace Visual Studio nebo jej vložte do souboru s názvem `parallel-map-reduce.cpp` a poté spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Parallel-map-Reduce. cpp**

## <a name="robust-programming"></a>Robustní programování

V tomto příkladu můžete použít třídu `concurrent_unordered_map`, která je definována v concurrent_unordered_map. h – pro provedení mapy a zmenšení v jedné operaci.

[!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]

Obvykle se paralelizovat jenom vnější nebo vnitřní smyčka. Paralelizovat vnitřní smyčku, pokud máte relativně málo souborů a každý soubor obsahuje mnoho slov. Paralelizovat vnější smyčka, pokud máte relativně mnoho souborů a každý soubor obsahuje několik slov.

## <a name="see-also"></a>Viz také

[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_transform funkce](reference/concurrency-namespace-functions.md#parallel_transform)<br/>
[parallel_reduce funkce](reference/concurrency-namespace-functions.md#parallel_reduce)<br/>
[concurrent_unordered_map – třída](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
