---
title: 'Postupy: provádění mapování a redukční operace paralelně | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2eb7580b82d336e3a99d89f6bde6c2f8c950b6c3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411297"
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>Postupy: Paralelní provádění operací mapování a redukce

Tento příklad ukazuje způsob použití [concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) a [concurrency::parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) algoritmy a [concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)třídy počítání výskytů slova v souborech.

A *mapy* operace platí funkce pro každou hodnotu v pořadí. A *snížit* operace kombinuje elementy sekvence do jedné hodnoty. Můžete použít standardní knihovny C++ [std::transform](../../standard-library/algorithm-functions.md#transform) a [std::accumulate](../../standard-library/numeric-functions.md#accumulate) functions k provádění mapování a redukční operace. Kvůli zvýšení výkonu pro mnoho problémů se však můžete použít `parallel_transform` algoritmus paralelní provádění operací mapování a `parallel_reduce` algoritmus k provedení této operace zmenšení paralelně. V některých případech můžete použít `concurrent_unordered_map` provádět na mapě a snížit v rámci jedné operace.

## <a name="example"></a>Příklad

Následující příklad počítá výskyty slov v souborech. Používá [std::vector](../../standard-library/vector-class.md) představující obsah dva soubory. Operace mapy vypočítá výskyty jednotlivých slov v každé vektoru. Operace zmenšení nahromadí počty slov v obou vektorů.

[!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li kód zkompilovat, ho zkopírujte a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `parallel-map-reduce.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc paralelní map – reduce.cpp**

## <a name="robust-programming"></a>Robustní programování

V tomto příkladu můžete použít `concurrent_unordered_map` třída, která je definovaná v concurrent_unordered_map.h—to provádět mapy a omezení v rámci jedné operace.

[!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]

Obvykle paralelizovat zůstal jenom vnější nebo vnitřní smyčku. Paralelní zpracování vnitřní smyčky, pokud máte relativně malý počet souborů a každý soubor obsahuje mnoho slova. Paralelní zpracování vnější smyčky, pokud máte relativně velkým množstvím souborů a každý soubor obsahuje několik slov.

## <a name="see-also"></a>Viz také

[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_transform Function](reference/concurrency-namespace-functions.md#parallel_transform)<br/>
[parallel_reduce Function](reference/concurrency-namespace-functions.md#parallel_reduce)<br/>
[concurrent_unordered_map – třída](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
