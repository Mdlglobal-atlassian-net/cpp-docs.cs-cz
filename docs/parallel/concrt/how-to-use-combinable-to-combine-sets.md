---
title: 'Postupy: Použití objektu combinable ke slučování množin'
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
ms.openlocfilehash: bf8a5bee65ea0ba1718c1d4d436b6af3e0b95961
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345575"
---
# <a name="how-to-use-combinable-to-combine-sets"></a>Postupy: Použití objektu combinable ke slučování množin

Toto téma ukazuje, jak používat [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třídy pro výpočet sadu prvočísel.

## <a name="example"></a>Příklad

Následující příklad vypočítá sadu prvočísel dvakrát. Každý výpočetní ukládá výsledek [std::bitset](../../standard-library/bitset-class.md) objektu. V příkladu nejdřív sériově vypočítá sadu a pak vypočítá sadě paralelně. V příkladu také tiskne na konzolu čas, který je potřeba provést i výpočty.

V tomto příkladu [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus a `combinable` objektu generuje sady místního vlákna. Poté použije [concurrency::combinable::combine_each](reference/combinable-class.md#combine_each) metoda kombinování sad místního vlákna do poslední sady.

[!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]

Následující ukázkový výstup je pro počítač, který má čtyři procesory.

```Output
serial time: 312 ms

parallel time: 78 ms
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `parallel-combine-primes.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe /EHsc parallel-combine-primes.cpp**

## <a name="see-also"></a>Viz také:

[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable – třída](../../parallel/concrt/reference/combinable-class.md)<br/>
[combinable::combine_each – metoda](reference/combinable-class.md#combine_each)
