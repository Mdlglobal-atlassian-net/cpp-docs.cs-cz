---
title: 'Postupy: Použití třídy kontextu pro implementaci semaforu pro spolupráci'
ms.date: 11/04/2016
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
ms.openlocfilehash: 5075052592993f413290242e70206b1e227064aa
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141902"
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>Postupy: Použití třídy kontextu pro implementaci semaforu pro spolupráci

Toto téma ukazuje, jak použít třídu concurrency:: Context k implementaci třídy "kooperativního semaforu".

## <a name="remarks"></a>Poznámky

Třída `Context` umožňuje blokovat nebo vracet aktuální kontext spuštění. Blokování nebo převracení aktuálního kontextu je užitečné, pokud aktuální kontext nemůže pokračovat, protože prostředek není k dispozici. *Semafor* je příklad jedné situace, kdy aktuální kontext spuštění musí čekat, až bude zdroj k dispozici. Semafor, podobně jako objekt kritického oddílu, je objekt synchronizace, který umožňuje kódu v jednom kontextu mít výhradní přístup k prostředku. Nicméně na rozdíl od kritického objektu oddílu, semafor umožňuje více než jeden kontext pro přístup k prostředku souběžně. Pokud maximální počet kontextů obsahuje zámek semaforu, musí každý další kontext počkat na jiný kontext, aby zámek uvolnil.

### <a name="to-implement-the-semaphore-class"></a>Implementace třídy semaphore

1. Deklarujte třídu s názvem `semaphore`. Přidejte do této třídy oddíly `public` a `private`.

[!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]

1. V sekci `private` třídy `semaphore` deklarujte proměnnou [std:: Atomic](../../standard-library/atomic-structure.md) , která obsahuje počet semaforu a objekt [concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) , který obsahuje kontexty, které musí čekat na získání semaforu.

[!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]

1. V sekci `public` třídy `semaphore` implementujte konstruktor. Konstruktor přebírá `long long` hodnotu, která určuje maximální počet kontextů, které mohou být souběžně uloženy.

[!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]

1. V sekci `public` třídy `semaphore` Implementujte metodu `acquire`. Tato metoda sníží počet semaforu jako atomickou operaci. Pokud je počet semaforů záporný, přidejte aktuální kontext na konec fronty čekání a zavolejte metodu [Concurrency:: Context:: Block](reference/context-class.md#block) pro blokování aktuálního kontextu.

[!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]

1. V sekci `public` třídy `semaphore` Implementujte metodu `release`. Tato metoda zvýší počet semaforu jako atomickou operaci. Pokud je počet semaforů záporný před operací zvýšení, existuje alespoň jeden kontext, který čeká na zámek. V takovém případě odblokujte kontext, který je na začátku fronty čekání.

[!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]

## <a name="example"></a>Příklad

Třída `semaphore` v tomto příkladu se chová spolupracuje, protože metody `Context::Block` a `Context::Yield` mají za následek provedení jiných úloh.

Metoda `acquire` snižuje čítač, ale nemusí dokončit přidání kontextu do fronty čekání před tím, než jiný kontext zavolá metodu `release`. Pro účely tohoto účtu metoda `release` používá smyčku, která volá metodu [Concurrency:: Context:: yield](reference/context-class.md#yield) , aby čekala na dokončení přidávání kontextu metodou `acquire`.

Metoda `release` může volat metodu `Context::Unblock` předtím, než metoda `acquire` zavolá metodu `Context::Block`. Nemusíte se chránit proti tomuto konfliktu, protože modul runtime umožňuje volání těchto metod v libovolném pořadí. Pokud metoda `release` volá `Context::Unblock` předtím, než metoda `acquire` volá `Context::Block` pro stejný kontext, zůstane tento kontext odblokované. Modul runtime vyžaduje pouze, aby každé volání `Context::Block` bylo spárováno s odpovídajícím voláním `Context::Unblock`.

Následující příklad ukazuje kompletní třídu `semaphore`. Funkce `wmain` ukazuje základní použití této třídy. Funkce `wmain` používá algoritmus [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) k vytvoření několika úloh, které vyžadují přístup k semaforu. Vzhledem k tomu, že tři vlákna můžou zámek kdykoli uchovávat, některé úlohy musí počkat na dokončení jiné úlohy a uvolnit zámek.

[!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]

Tento příklad vytvoří následující vzorový výstup.

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

Další informace o třídě `concurrent_queue` naleznete v tématu [Parallel Containers and Objects](../../parallel/concrt/parallel-containers-and-objects.md). Další informace o algoritmu `parallel_for` najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `cooperative-semaphore.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Cooperative-Semaphore. cpp**

## <a name="robust-programming"></a>Robustní programování

Můžete použít vzor pro *získání prostředku* (RAII), který omezí přístup k objektu `semaphore` na daný obor. V rámci vzoru RAII se datová struktura přiděluje v zásobníku. Tato struktura dat inicializuje nebo získá prostředek při jeho vytvoření a zničí nebo uvolní tento prostředek při zničení struktury dat. Vzor RAII zaručuje, že je destruktor volán před ukončením ohraničujícího oboru. Proto je prostředek správně spravován, pokud je vyvolána výjimka nebo když funkce obsahuje více příkazů `return`.

Následující příklad definuje třídu s názvem `scoped_lock`, která je definována v oddílu `public` třídy `semaphore`. Třída `scoped_lock` se podobá třídám [Concurrency:: critical_section:: scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) a [concurrency:: reader_writer_lock:: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) . Konstruktor třídy `semaphore::scoped_lock` získává přístup k danému objektu `semaphore` a destruktor uvolní přístup k tomuto objektu.

[!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]
Následující příklad upravuje tělo pracovní funkce, která je předána algoritmu `parallel_for`, aby používala RAII k zajištění toho, aby byl Semafor uvolněn před vrácením funkce. Tato technika zajišťuje, že pracovní funkce je bezpečná pro výjimky.

[!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]

## <a name="see-also"></a>Viz také

[Kontexty](../../parallel/concrt/contexts.md)<br/>
[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)
