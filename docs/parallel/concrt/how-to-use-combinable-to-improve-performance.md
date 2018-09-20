---
title: 'Postupy: použití objektu combinable ke zlepšení výkonu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 22425ac212ee2bfb52354044b1a6193b6a9cd11a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432085"
---
# <a name="how-to-use-combinable-to-improve-performance"></a>Postupy: Použití objektu combinable ke zlepšení výkonu

Tento příklad ukazuje způsob použití [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třídy vypočítat součet čísel v [std::array](../../standard-library/array-class-stl.md) objekt, který se primární. `combinable` Třídy zlepšuje výkon odstraněním sdílený stav.

> [!TIP]
>  V některých případech paralelní mapování ([concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)) a snížení ([souběžnosti:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)) mohou poskytnout zvýšení výkonu přes `combinable`. Například, že používá mapovací a redukční operace, které vytvářejí stejné výsledky jako v tomto příkladu najdete v části [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

## <a name="example"></a>Příklad

V následujícím příkladu [std::accumulate](../../standard-library/numeric-functions.md#accumulate) funkcí pro výpočet součtu prvky v poli, které jsou primární. V tomto příkladu `a` je `array` objektu a `is_prime` funkce určuje, zda je jeho vstupní hodnotu šířky.

[!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob naivní paralelizovat z předchozího příkladu. V tomto příkladu [: concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus pole paralelní zpracování a [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) objektu k synchronizaci přístupu k `prime_sum` proměnné . V tomto příkladu škálování, protože každé vlákno musí čekat na zpřístupnění sdíleného prostředku.

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]

## <a name="example"></a>Příklad

Následující příklad používá `combinable` objekt ke zlepšení výkonu v předchozím příkladu. V tomto příkladu se eliminuje potřeba synchronizace objektů Škáluje, protože `combinable` objektu umožňuje každé vlákno k provedení svých úkolů nezávisle na sobě.

A `combinable` objekt se obvykle používá ve dvou krocích. Nejprve vytvořit řadu podrobných výpočty pomocí provádí práci paralelně. V dalším kroku zkombinovat (nebo snížit) výpočtů do konečný výsledek. V tomto příkladu [concurrency::combinable::local](reference/combinable-class.md#local) metodu k získání odkazu na místní součet. Poté použije [concurrency::combinable::combine](reference/combinable-class.md#combine) metoda a [std::plus](../../standard-library/plus-struct.md) objekt kombinovat místní výpočty na konečný výsledek.

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]

## <a name="example"></a>Příklad

Následující kompletní příklad vypočítá součet prvků prvočísel obou sériově i paralelně. V příkladu tiskne na konzolu čas, který je potřeba provést i výpočty.

[!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_4.cpp)]

Následující ukázkový výstup je pro počítač, který má čtyři procesory.

```Output
1709600813
serial time: 6178 ms

1709600813
parallel time: 1638 ms
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li kód zkompilovat, ho zkopírujte a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `parallel-sum-of-primes.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc paralelní – součet sady primes.cpp**

## <a name="robust-programming"></a>Robustní programování

Například, že používá mapovací a redukční operace, které vytvářejí stejné výsledky, naleznete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

## <a name="see-also"></a>Viz také

[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable – třída](../../parallel/concrt/reference/combinable-class.md)<br/>
[critical_section – třída](../../parallel/concrt/reference/critical-section-class.md)
