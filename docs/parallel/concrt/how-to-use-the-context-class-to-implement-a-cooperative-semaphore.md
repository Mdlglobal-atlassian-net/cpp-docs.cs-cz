---
title: 'Postupy: použití třídy kontextu pro implementaci semaforu pro spolupráci | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 481c5f092becee7f455294437bdc695a6e1e4057
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693741"
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>Postupy: Použití třídy kontextu pro implementaci semaforu pro spolupráci
Toto téma ukazuje způsob použití třídy concurrency::Context pro implementaci semaforu pro spolupráci třídy.  
  
 `Context` Třída umožňuje blokovat nebo yield aktuálním kontextu spuštění. Blokování nebo je aktuální kontext je užitečné, když aktuální kontext nemůže pokračovat, protože prostředek není k dispozici. A *semaphore* je příkladem jeden situaci, kdy aktuální kontext spuštění musí čekat prostředek k dispozici. Semafor, jako je objekt kritická sekce je na synchronizační objekt, který umožňuje kód v jedné kontext, který má výhradní přístup k prostředku. Na rozdíl od objekt kritická sekce umožňuje semafor více než jeden kontext, který má přístup k prostředku současně. Pokud maximální počet kontexty obsahuje semafor zámku, musí každý další kontext čekat další kontext, který má uvolní zámek.  
  
### <a name="to-implement-the-semaphore-class"></a>Implementace třídy semaphore  
  
1.  Deklarování třídy s názvem `semaphore`. Přidat `public` a `private` oddíly pro tuto třídu.  
  
 [!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]  
  
2.  V `private` části `semaphore` třídy, deklarovat [std::atomic](../../standard-library/atomic-structure.md) proměnné, která obsahuje počet semafor a [concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) objekt, který obsahuje kontexty který čekat získat semaforu.  
  
 [!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]  
  
3.  V `public` části `semaphore` třídy, implementovat konstruktoru. Konstruktor přijímá `long long` hodnotu, která určuje maximální počet kontextů, které mohou být uloženy souběžně zámek.  
  
 [!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]  

4.  V `public` části `semaphore` třídy, implementovat `acquire` metoda. Tato metoda snižuje semaforu se počítají jako atomickou operaci. Pokud se počet semafor stane záporná, přidejte aktuální kontext konec čekání fronty a volání [concurrency::Context::Block](reference/context-class.md#block) metoda blokování aktuálního kontextu.  
  
 [!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]  
  
5.  V `public` části `semaphore` třídy, implementovat `release` metoda. Tato metoda zvětší počet semafor jako atomickou operaci. Pokud je tento počet semafor před provedením operace přírůstek záporná, není alespoň jeden kontext, který čeká na zámek. V takovém případě odblokujte kontext, který je na začátek fronty čekání.  
  
 [!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]  
  
## <a name="example"></a>Příklad  
 `semaphore` Třídy v tomto příkladu chová spolupráce při, protože `Context::Block` a `Context::Yield` metody yield provádění tak, aby modul runtime můžete provádět další úlohy.  
  
 `acquire` Metoda snižuje čítače, ale nemusí dokončit přidávání kontextu do fronty čekání před jiné volání kontextu `release` metoda. K účtu v takovém případě `release` metoda používá smyčku typu číselník, který volá [concurrency::Context::Yield](reference/context-class.md#yield) metoda čekat `acquire` metoda mohli dokončit přidávání člena kontextu.  
  
 `release` Můžete volat metodu `Context::Unblock` metody před `acquire` volání metod `Context::Block` metoda. Nemáte k ochraně proti tento spor, protože modul runtime umožňuje pro tyto metody, která se má volat v libovolném pořadí. Pokud `release` volání metod `Context::Unblock` před `acquire` volání metod `Context::Block` u stejného kontextu, zůstává odblokuje tohoto kontextu. Modul runtime vyžaduje pouze každé volání do `Context::Block` se najde shoda s odpovídající volání `Context::Unblock`.  
  
 Následující příklad ukazuje kompletní `semaphore` třídy. `wmain` Funkce zobrazuje základní informace o využití této třídy. `wmain` Využívá [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus vytvořit několik úloh, které vyžadují přístup k semaforu. Protože tři vlákna pojme zámek kdykoli, některé úlohy musí počkejte na dokončení a uvolní zámek jiné úlohy.  
  
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
  
 Další informace o `concurrent_queue` třídy najdete v tématu [paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md). Další informace o `parallel_for` algoritmus, najdete v části [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `cooperative-semaphore.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc spolupráce semaphore.cpp**  
  
## <a name="robust-programming"></a>Robustní programování  
 Můžete použít *prostředků pořízení je inicializace* (RAII) vzor omezit přístup k `semaphore` objekt do daného oboru. V části vzoru RAII je datová struktura přidělena v zásobníku. Aby datová struktura inicializuje nebo získá prostředek, pokud je vytvořen a ničí nebo uvolní prostředku, když je datová struktura zničen. Vzor RAII zaručuje, že destruktoru je volána před ukončí vymezeném oboru. Proto prostředek správně spravované když je vyvolána výjimka, nebo když funkce obsahuje více `return` příkazy.  
  
 Následující příklad definuje třídu, která je s názvem `scoped_lock`, která je definována v `public` části `semaphore` třídy. `scoped_lock` Vypadá takto: Třída [concurrency::critical_section::scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) a [concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) třídy. Konstruktoru `semaphore::scoped_lock` třída získá přístup k danou `semaphore` objekt a destruktoru uvolní přístup k objektu.  
  
 [!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]    
 Následující příklad změní obsah pracovní funkce, který je předán `parallel_for` algoritmus tak, aby používala RAII zajistit, že je semaforu vydané před funkce vrátí hodnotu. Tento postup zajišťuje, že pracovní funkce bezpečných výjimka.  
  
 [!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Kontexty](../../parallel/concrt/contexts.md)   
 [Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)

