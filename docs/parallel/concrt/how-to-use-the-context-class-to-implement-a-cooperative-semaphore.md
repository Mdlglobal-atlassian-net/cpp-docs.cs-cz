---
title: 'Postupy: Použití třídy kontextu pro implementaci semaforu pro spolupráci'
ms.date: 11/04/2016
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
ms.openlocfilehash: 460a1de03f34cb8ef9753e761aaef37470cd6d0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467756"
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>Postupy: Použití třídy kontextu pro implementaci semaforu pro spolupráci

Toto téma ukazuje, jak použít třídu concurrency::Context pro implementaci semaforu pro spolupráci třídy.

`Context` Třída umožňuje blokovat nebo pozastavit aktuální kontext spuštění. Blokování nebo získávání aktuální kontext je užitečné při aktuálním kontextu nemůže pokračovat, protože prostředek není k dispozici. A *semafor* je příkladem jedna situace, kdy musíte počkat, aktuálním kontextu spuštění pro prostředek k dispozici. Semafor, jako je objekt kritický oddíl je synchronizační objekt umožňující kód v jednom kontextu exkluzivní přístup k prostředku. Na rozdíl od objektu kritický oddíl umožňuje semafor více než jednom kontextu souběžně přístup k prostředku. Pokud se maximální počet kontextů drží zámek pro spolupráci, každý další kontext třeba vyčkat na dokončení jiného kontextu uvolnit zámek.

### <a name="to-implement-the-semaphore-class"></a>Implementace třídy semaphore

1. Deklarovat třídu s názvem `semaphore`. Přidat `public` a `private` části do této třídy.

[!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]

1. V `private` část `semaphore` třídy, deklarujte [std::atomic](../../standard-library/atomic-structure.md) proměnnou, která obsahuje počet pro semafor a [concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) objekt, který obsahuje kontexty který musíte počkat, k získání semafor.

[!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]

1. V `public` část `semaphore` třídy, implementaci konstruktoru. Konstruktor přijme `long long` hodnota, která určuje maximální počet kontextů, které lze souběžně držitelem zámku.

[!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]

1. V `public` část `semaphore` třídy, implementujte `acquire` metody. Tato metoda sníží semafor počet jako atomickou operaci. Pokud se počet pro semafor stane záporný, přidejte aktuálního kontextu konec čekací fronty a volání [concurrency::Context::Block](reference/context-class.md#block) metoda blokování aktuálního kontextu.

[!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]

1. V `public` část `semaphore` třídy, implementujte `release` metody. Tato metoda zvýší počet semafor jako atomickou operaci. Pokud je záporné před provedením operace Inkrementace počet pro spolupráci, existuje alespoň jeden kontext, který čeká na zámek. V takovém případě odblokujte kontext, který je na začátku čekací fronty.

[!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]

## <a name="example"></a>Příklad

`semaphore` Třídy v tomto příkladu se chová kooperativně vzhledem k tomu, `Context::Block` a `Context::Yield` metody pozastavit provádění tak, aby modul runtime můžete provádět další úlohy.

`acquire` Metoda dekrementuje čítače, ale nemusí být dokončeno přidání kontextu do fronty čekání před další kontext volání `release` metody. Na to, `release` metoda používá typu číselník smyčku, která volá [concurrency::Context::Yield](reference/context-class.md#yield) metoda čekat `acquire` metoda mohli dokončit přidávání kontextu.

`release` Můžete volat metodu `Context::Unblock` metody před `acquire` volání metod `Context::Block` metoda. Není potřeba chránit proti tento spor, protože modul runtime povoluje pro tyto metody volat v libovolném pořadí. Pokud `release` volání metody `Context::Unblock` před `acquire` volání metody `Context::Block` stejného kontextu, zůstane tento kontext odblokované. Modul runtime vyžaduje pouze, že každé volání `Context::Block` je nalezena shoda s odpovídající volání `Context::Unblock`.

Následující příklad ukazuje kompletní `semaphore` třídy. `wmain` Funkce ukazuje základní použití této třídy. `wmain` Funkce používá [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmů a vytvořit několik úloh, které vyžadují přístup pro semafor. Protože tři vlákna můžete kdykoli držitelem zámku, musíte počkat, některé úlohy pro jiný úkol k dokončení a uvolní zámek.

[!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]

Tento příklad vytvoří následující ukázkový výstup.

```Output
In loop iteration 5...
In loop iteration 0...
In loop iteration 6...
In loop iteration 1...
In loop iteration 2...
In loop iteration 7...
In loop iteration 3...
In loop iteration 8...
In loop iteration 9...
In loop iteration 4...
```

Další informace o `concurrent_queue` najdete v tématu [paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md). Další informace o `parallel_for` algoritmus, najdete v článku [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `cooperative-semaphore.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc kooperativní semaphore.cpp**

## <a name="robust-programming"></a>Robustní programování

Můžete použít *získání prostředků je inicializace* vzorek (RAII) k omezení přístupu k `semaphore` objekt do daného oboru. Podle vzoru RAII je datová struktura přidělené v zásobníku. Struktury dat inicializuje nebo získá prostředek, když se vytvoří a odstraní nebo vydání prostředku při zničení datová struktura. Vzorek RAII, aby zaručuje, že destruktoru je volána před ukončení nadřazeného oboru. Proto prostředku se správně spravuje při vyvolání výjimky, nebo když funkce obsahuje více `return` příkazy.

Následující příklad definuje třídu s názvem `scoped_lock`, který je definován v `public` část `semaphore` třídy. `scoped_lock` Třídy vypadá podobně jako [concurrency::critical_section::scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) a [concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) třídy. Konstruktor třídy `semaphore::scoped_lock` třídy získá přístup k daný `semaphore` objektu a destruktor uvolní přístup na tento objekt.

[!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]
Následující příklad upravuje text, který je předán do funkce práce `parallel_for` algoritmus tak, že používá k zajištění, že semafor je uvolněna dříve, než funkce vrátí RAII. Tento postup zajišťuje, že je pracovní funkce je bezpečnost výjimek.

[!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]

## <a name="see-also"></a>Viz také

[Kontexty](../../parallel/concrt/contexts.md)<br/>
[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)

