---
title: 'Postupy: Použití funkcí Alloc a Free ke zlepšení výkonu paměti'
ms.date: 11/04/2016
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
ms.openlocfilehash: 8438e833262d42c6083f48f759501c573a35c772
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142789"
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>Postupy: Použití funkcí Alloc a Free ke zlepšení výkonu paměti

Tento dokument ukazuje, jak používat funkce [Concurrency:: alokace](reference/concurrency-namespace-functions.md#alloc) a [Concurrency:: Free](reference/concurrency-namespace-functions.md#free) ke zlepšení výkonu paměti. Porovnává čas, který je potřeba k tomu, aby bylo možné obrátit prvky pole paralelně pro tři různé typy, které určují operátory `new` a `delete`.

Funkce `Alloc` a `Free` jsou nejužitečnější, pokud více vláken často volá `Alloc` i `Free`. Modul runtime obsahuje samostatnou paměťovou mezipaměť pro každé vlákno; modul runtime proto spravuje paměť bez použití zámků nebo bariéry paměti.

## <a name="example"></a>Příklad

Následující příklad ukazuje tři typy, které určují operátory `new` a `delete`. Třída `new_delete` používá globální operátory `new` a `delete`, třída `malloc_free` používá funkce C Runtime \ a [bezplatné](../../c-runtime-library/reference/free.md) [funkce a třída](../../c-runtime-library/reference/malloc.md) `Alloc_Free` používá Concurrency Runtime `Alloc` a `Free` funkce.

[!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]

## <a name="example"></a>Příklad

Následující příklad ukazuje funkce `swap` a `reverse_array`. Funkce `swap` vyměňuje obsah pole se zadanými indexy. Přiděluje paměť z haldy pro dočasnou proměnnou. Funkce `reverse_array` vytvoří velké pole a vypočítá čas, který je požadován k navrácení tohoto pole několikrát.

[!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]

## <a name="example"></a>Příklad

Následující příklad ukazuje funkci `wmain`, která vypočítá čas potřebný k tomu, aby funkce `reverse_array` pracovala s typy `new_delete`, `malloc_free`a `Alloc_Free`, z nichž každá používá jiné schéma přidělování paměti.

[!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]

## <a name="example"></a>Příklad

Následující příklad následuje.

[!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]

Tento příklad vytvoří následující vzorový výstup pro počítač se čtyřmi procesory.

```Output
Took 2031 ms with new/delete.
Took 1672 ms with malloc/free.
Took 656 ms with Alloc/Free.
```

V tomto příkladu typ, který používá funkce `Alloc` a `Free`, poskytuje nejlepší výkon paměti, protože `Alloc` a `Free` funkce jsou optimalizované pro často přidělující a uvolňování bloků paměti z více vláken.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `allocators.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc přidělování. cpp**

## <a name="see-also"></a>Viz také

[Funkce správy paměti](../../parallel/concrt/memory-management-functions.md)<br/>
[Funkce alokace](reference/concurrency-namespace-functions.md#alloc)<br/>
[Free – funkce](reference/concurrency-namespace-functions.md#free)
