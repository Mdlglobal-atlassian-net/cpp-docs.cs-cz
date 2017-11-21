---
title: "Postupy: použití funkcí Alloc a Free ke zlepšení výkonu paměti | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b375c5b3ec9f35050d7da4ae03139f6e809172cd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>Postupy: Použití funkcí Alloc a Free ke zlepšení výkonu paměti

Tento dokument ukazuje, jak používat [concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) a [concurrency::Free](reference/concurrency-namespace-functions.md#free) funkce ke zlepšení výkonu paměti. Porovná čas, který je potřeba obrátit prvků pole paralelně pro tři různé typy, zadejte každou `new` a `delete` operátory.  

  
 `Alloc` a `Free` funkce jsou velmi užitečné při volání i více vláken často `Alloc` a `Free`. Modul runtime obsahuje samostatné mezipaměť pro každé vlákno; modul runtime tedy spravuje paměti bez použití zámky nebo překážek paměti.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje tři typy, zadejte každou `new` a `delete` operátory. `new_delete` Třída používá na globální `new` a `delete` operátory, `malloc_free` třída používá C Runtime [malloc –](../../c-runtime-library/reference/malloc.md) a [volné](../../c-runtime-library/reference/free.md) funkce a `Alloc_Free` třída používá Concurrency Runtime `Alloc` a `Free` funkce.  
  
 [!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `swap` a `reverse_array` funkce. `swap` Funkce výměny obsah pole na zadané indexy. Přidělí paměť z haldy pro dočasné proměnné. `reverse_array` Funkce vytvoří velké pole a vypočítá čas, který je potřeba obrátit tohoto pole několikrát paralelně.  
  
 [!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `wmain` funkci, která vypočítá dobu, která je požadována pro `reverse_array` funkce tak, aby fungoval na `new_delete`, `malloc_free`, a `Alloc_Free` typy, z nichž každá používá jiné paměti přidělení schéma.  
  
 [!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]  
  
## <a name="example"></a>Příklad  
 Úplný příklad následuje.  
  
 [!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]  
  
 Tento příklad vytvoří následující ukázkový výstup pro počítač, který se čtyřmi procesory.  
  
```Output  
Took 2031 ms with new/delete.  
Took 1672 ms with malloc/free.  
Took 656 ms with Alloc/Free.  
```  
  
 V tomto příkladu typ, který používá `Alloc` a `Free` funkce poskytuje nejlepší výkon paměti, protože `Alloc` a `Free` funkce jsou optimalizované pro často přidělování a uvolnění bloky paměti z více vláken.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `allocators.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc allocators.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Funkce správy paměti](../../parallel/concrt/memory-management-functions.md)   
 [ALLOC – funkce](reference/concurrency-namespace-functions.md#alloc)   
 [Free – funkce](reference/concurrency-namespace-functions.md#free)

