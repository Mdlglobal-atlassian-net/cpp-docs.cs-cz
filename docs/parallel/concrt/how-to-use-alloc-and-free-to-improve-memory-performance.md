---
title: 'Postupy: Použití funkcí Alloc a Free ke zlepšení výkonu paměti'
ms.date: 11/04/2016
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
ms.openlocfilehash: d91734859cd7d3499979566f427c10a0f026941b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467816"
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>Postupy: Použití funkcí Alloc a Free ke zlepšení výkonu paměti

Tento dokument ukazuje způsob použití [concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) a [concurrency::Free](reference/concurrency-namespace-functions.md#free) funkce ke zlepšení výkonu paměti. Porovnává čas, který se vyžaduje zpětná prvky pole paralelně pro tři různé typy, které každý určuje `new` a `delete` operátory.

`Alloc` a `Free` funkce jsou nejužitečnější tehdy, když často volat více vláken, obě `Alloc` a `Free`. Modul runtime obsahuje samostatný mezipaměti pro každé vlákno; Proto se modul runtime spravuje paměť bez použití zámků nebo překážky paměti.

## <a name="example"></a>Příklad

Následující příklad ukazuje tři typy nichž každý určuje `new` a `delete` operátory. `new_delete` Třída používá globální `new` a `delete` operátory, `malloc_free` třída používá modul Runtime jazyka C [malloc](../../c-runtime-library/reference/malloc.md) a [bezplatné](../../c-runtime-library/reference/free.md) funkce a `Alloc_Free` třída používá modulu Runtime souběžnosti `Alloc` a `Free` funkce.

[!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]

## <a name="example"></a>Příklad

Následující příklad ukazuje `swap` a `reverse_array` funkce. `swap` Funkce vymění obsah pole na zadané indexy. Přidělí paměť ze haldy pro dočasné proměnné. `reverse_array` Funkce vytvoří velkého pole a vypočítá čas, který je potřeba reverse takové pole několikrát paralelně.

[!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]

## <a name="example"></a>Příklad

Následující příklad ukazuje `wmain` funkce, která vypočítá čas, který je třeba použít `reverse_array` funkce tak, aby fungoval na `new_delete`, `malloc_free`, a `Alloc_Free` typy, z nichž každá používá jiné paměťové přidělení schéma.

[!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]

## <a name="example"></a>Příklad

Následuje Úplný příklad.

[!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]

Tento příklad vytvoří následující ukázkový výstup pro počítač, který má čtyři procesory.

```Output
Took 2031 ms with new/delete.
Took 1672 ms with malloc/free.
Took 656 ms with Alloc/Free.
```

V tomto příkladu typ, který používá `Alloc` a `Free` functions poskytuje nejlepší výkon, protože `Alloc` a `Free` funkce jsou optimalizované pro často přidělení a uvolnění bloky paměti z několika vlákna.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `allocators.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc allocators.cpp**

## <a name="see-also"></a>Viz také

[Funkce správy paměti](../../parallel/concrt/memory-management-functions.md)<br/>
[ALLOC – funkce](reference/concurrency-namespace-functions.md#alloc)<br/>
[Free – funkce](reference/concurrency-namespace-functions.md#free)

