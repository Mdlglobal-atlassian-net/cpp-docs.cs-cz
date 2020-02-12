---
title: 'Postupy: Použití objektu combinable ke zlepšení výkonu'
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
ms.openlocfilehash: db27a791b2b92102118606712db4cbd2920f9619
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142431"
---
# <a name="how-to-use-combinable-to-improve-performance"></a>Postupy: Použití objektu combinable ke zlepšení výkonu

Tento příklad ukazuje, jak použít třídu [Concurrency::](../../parallel/concrt/reference/combinable-class.md) asociativní k výpočtu součtu čísel v objektu [std:: Array](../../standard-library/array-class-stl.md) , který je primární. Třída `combinable` vylepšuje výkon odstraněním sdíleného stavu.

> [!TIP]
> V některých případech může paralelní mapa ([Concurrency::p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)) a snižování ([concurrency:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)) poskytovat zlepšení výkonu oproti `combinable`. Příklad použití map a omezení operací k vytváření stejných výsledků jako v tomto příkladu naleznete v tématu Parallel Algorithms ( [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)).

## <a name="example---accumulate"></a>Příklad – akumulace

V následujícím příkladu je použita funkce [std:: Akumulovaná](../../standard-library/numeric-functions.md#accumulate) pro výpočet součtu prvků v poli, které jsou ve formátu základny. V tomto příkladu je `a` objektem `array` a funkce `is_prime` určuje, zda je jeho vstupní hodnota primární.

[!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]

## <a name="example---parallel_for_each"></a>Příklad – parallel_for_each

Následující příklad ukazuje Naive způsob, jak paralelizovat předchozí příklad. V tomto příkladu se používá algoritmus [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) pro zpracování pole paralelně a objekt [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) pro synchronizaci přístupu k proměnné `prime_sum`. Tento příklad není škálovatelný, protože každé vlákno musí čekat, než se sdílený prostředek zpřístupní.

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]

## <a name="example---combinable"></a>Příklad – kombinace

V následujícím příkladu je použit objekt `combinable` pro zlepšení výkonu předchozího příkladu. Tento příklad eliminuje potřebu synchronizačních objektů; Škáluje se, protože objekt `combinable` umožňuje každému vláknu provádět nezávislé úkoly.

Objekt `combinable` se obvykle používá ve dvou krocích. Nejdřív vytvořte řadu jemně odstupňovaných výpočtů tím, že provedete paralelní práci. Potom v konečném výsledku Zkombinujte (nebo snižte) výpočty. Tento příklad používá metodu [Concurrency:: kombinovatelné:: Local](reference/combinable-class.md#local) pro získání odkazu na místní součet. Potom používá metodu [Concurrency:: kombinovatelné:: kombinovat](reference/combinable-class.md#combine) a objekt [std::p Lu](../../standard-library/plus-struct.md) ke kombinování místních výpočtů do konečného výsledku.

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]

## <a name="example---serial-and-parallel"></a>Příklad – sériové a paralelní

Následující kompletní příklad vypočítá součet primárních čísel, a to jak sériové, tak i paralelně. V příkladu se v konzole vytiskne čas potřebný k provedení výpočtů.

[!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_4.cpp)]

Následující vzorový výstup je určen pro počítač se čtyřmi procesory.

```Output
1709600813
serial time: 6178 ms

1709600813
parallel time: 1638 ms
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li zkompilovat kód, zkopírujte jej a vložte jej do projektu aplikace Visual Studio nebo jej vložte do souboru s názvem `parallel-sum-of-primes.cpp` a poté spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Parallel-Sum-of-PRIMES. cpp**

## <a name="robust-programming"></a>Robustní programování

Příklad použití map a omezení operací k vytváření stejných výsledků naleznete v tématu Parallel Algorithms ( [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)).

## <a name="see-also"></a>Viz také

[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable – třída](../../parallel/concrt/reference/combinable-class.md)<br/>
[critical_section – třída](../../parallel/concrt/reference/critical-section-class.md)
