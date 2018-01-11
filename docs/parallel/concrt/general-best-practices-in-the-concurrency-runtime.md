---
title: "Obecné osvědčené postupy v Concurrency Runtime | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d5c2c626ceb0243e91e56d70f0d8ae71208b157f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>Obecné osvědčené postupy v Concurrency Runtime
Tento dokument popisuje osvědčené postupy, které se vztahují k několika oblastem Concurrency Runtime.  
  
##  <a name="top"></a>Oddíly  
 Tento dokument obsahuje následující části:  
  
- [Použít konstrukce spolupráci synchronizace, pokud je to možné](#synchronization)  
  
- [Vyhněte se zdlouhavé úlohy, které není Yield](#yield)  
  
- [Vytvořením nadbytečného na posunu operace, která blokují nebo mají vysoké latenci](#oversubscription)  
  
- [Pomocí funkce správy souběžných paměti, pokud je to možné](#memory)  
  
- [Použití RAII dobu trvání objektů souběžnosti](#raii)  
  
- [Nevytvářejte souběžnosti objekty v globálním oboru](#global-scope)  
  
- [Nepoužívejte souběžnosti objekty ve sdílených datových segmentů](#shared-data)  
  
##  <a name="synchronization"></a>Použít konstrukce spolupráci synchronizace, pokud je to možné  
 Concurrency Runtime poskytuje mnoho souběžnosti bezpečných konstrukce, které nevyžadují objekt externí synchronizace. Například [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) třída poskytuje souběžnosti bezpečných připojit a element přístup operace. Ale pro případy, ve kterém vyžaduje výhradní přístup k prostředku, poskytuje modul runtime [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), [concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md), a [souběžnosti :: událostí](../../parallel/concrt/reference/event-class.md) třídy. Tyto typy chovat spolupráce při; proto plánovače úloh můžete znovu přidělte zdroje zpracování na jiný kontext jako první úloha čeká na data. Pokud je to možné, používejte tyto typy synchronizace místo jiné synchronizace mechanismy, jako třeba rozhraním API systému Windows, které nefungují spolupráce při tak. Další informace o těchto typů synchronizace a příklad kódu najdete v tématu [synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md) a [porovnávání synchronizačních datových struktur rozhraní API systému Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).  
  
 [[Horní](#top)]  
  
##  <a name="yield"></a>Vyhněte se zdlouhavé úlohy, které není Yield  
 Protože Plánovač úloh se chová spolupráce při, neposkytuje rovné zacházení s úlohy. Proto úlohu můžete zabránit další úlohy spuštění. To je přijatelné v některých případech, v ostatních případech to může způsobit zablokování nebo nedostatku prostředků.  
  
 Následující příklad provede další informace o úlohách než počet prostředky přidělené zpracování. První úlohou nepřinese pro Plánovač úloh, a proto v druhé úloze nespustí, dokud nebude dokončeno první úlohou.  
  
 [!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
 1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000  
  

 Existuje několik způsobů, jak povolit spolupráci mezi dvě úlohy. Jedním ze způsobů je občas yield plánovačem úloh v dlouho běžící úlohy. Následující příklad změní `task` funkce k volání [concurrency::Context::Yield](reference/context-class.md#yield) metoda na základě výnosu spouštění plánovače úloh tak, aby jiná úloha.  

  
 [!code-cpp[concrt-cooperative-tasks#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_2.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
1: 250000000  
2: 250000000  
1: 500000000  
2: 500000000  
1: 750000000  
2: 750000000  
1: 1000000000  
2: 1000000000  
```  
  
 `Context::Yield` Metoda poskytuje jenom jiné vlákno active pro Plánovač, do které patří aktuální vlákno prosté úlohy nebo jiné vlákno operačního systému. Tato metoda není yield pracovat, je naplánované spuštění v [concurrency::task_group](reference/task-group-class.md) nebo [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objektu, ale ještě nezačala.  
  
 Chcete-li povolit spolupráci mezi dlouhotrvající úlohy i jinými způsoby. Velkých úloh můžete rozdělit na menší dílčí úkoly. Můžete také povolit Překryvný odběr během dlouhou úlohu. Překryvný odběr umožňuje vytvářet další podprocesy než dostupný počet vláken hardwaru. Překryvný odběr je obzvláště užitečná při dlouhou úlohu obsahuje vysoký objem latence, například čtení dat z disku nebo připojení k síti. Další informace o prosté úlohy a Překryvný odběr najdete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
 [[Horní](#top)]  
  
##  <a name="oversubscription"></a>Vytvořením nadbytečného na posunu operace, která blokují nebo mají vysoké latenci  
 Concurrency Runtime poskytuje synchronizace primitiv, například [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), které umožňují úlohy spolupráce při blokování a poskytne k sobě navzájem. Pokud jeden úkol spolupráce při blokování nebo vypočítá, plánovače úloh můžete přidělit jinému uživateli zdroje zpracování na jiný kontext jako první úloha čeká na data.  
  
 Existují případy, ve kterých se nedá použít spolupráci blokování mechanismus, který zajišťuje Concurrency Runtime. Například vnější knihovny, který používáte, může použít jiný synchronizační mechanismus. Dalším příkladem je při provádění operace, která může mít vysoký objem latence, například při použití rozhraní API systému Windows `ReadFile` funkce Číst data z připojení k síti. V těchto případech můžete povolit Překryvný odběr další úlohy ke spuštění při nečinnosti jiná úloha. Překryvný odběr umožňuje vytvářet další podprocesy než dostupný počet vláken hardwaru.  
  
 Vezměte v úvahu následující funkce `download`, čímž stáhnete soubor v dané adrese URL. Tento příklad používá [concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe) metody dočasně zvýšit počet aktivních podprocesů.  

 [!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]  
  
 Protože `GetHttpFile` funkce provádí operaci potenciálně latentní, Překryvný odběr můžete povolit další úlohy ke spuštění jako aktuální úloha čeká na data. Dokončení verzi v tomto příkladu, naleznete v části [postupy: použití Překryvný odběr k posunu latence](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).  
  
 [[Horní](#top)]  
  
##  <a name="memory"></a>Pomocí funkce správy souběžných paměti, pokud je to možné  

 Pomocí funkce správy paměti [concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) a [concurrency::Free](reference/concurrency-namespace-functions.md#free), až budete mít podrobné úlohy, které často přidělit malé objekty, které mají poměrně krátké doby platnosti. Concurrency Runtime obsahuje samostatné mezipaměť pro každý spuštěných vláken. `Alloc` a `Free` funkce přidělit a volné paměti z těchto mezipamětí bez použití zámky nebo překážek paměti.  
  
 Další informace o tyto funkce správy paměti najdete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Příklad, který používá tyto funkce, naleznete v části [postupy: použití Alloc a Free ke zlepšení výkonu paměti](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).  
  
 [[Horní](#top)]  
  
##  <a name="raii"></a>Použití RAII dobu trvání objektů souběžnosti  
 Concurrency Runtime používá implementovat funkce, jako je například zrušení zpracování výjimek. Proto napište kód bezpečných výjimky při volání do modulu runtime nebo volat jiné knihovny, která volá do modulu runtime.  
  
 *Prostředků pořízení je inicializace* (RAII) vzor je jedním ze způsobů pro bezpečnou správu životnosti objektu souběžnosti v daném oboru. V části vzoru RAII je datová struktura přidělena v zásobníku. Aby datová struktura inicializuje nebo získá prostředek, pokud je vytvořen a ničí nebo uvolní prostředku, když je datová struktura zničen. Vzor RAII zaručuje, že destruktoru je volána před ukončí vymezeném oboru. Tento vzor je užitečné, když funkce obsahuje více `return` příkazy. Tento vzor také umožňuje napsat kód výjimky bezpečné. Když `throw` příkaz způsobuje zásobníku unwind, destruktoru pro objekt RAII se nazývá; proto je odstranit nebo vydání prostředku vždy správně.  
  
 Modul runtime definuje několik tříd, které používají vzorec RAII, například [concurrency::critical_section::scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class) a [concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class). Tyto pomocné třídy se označují jako *obor zámků*. Tyto třídy poskytují několik výhod při práci s [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) nebo [concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) objekty. V konstruktoru tyto třídy získá přístup k zadanému `critical_section` nebo `reader_writer_lock` objekt; destruktor verzích přístup k objektu. Protože vymezená zámku uvolní přístup k jeho vzájemné vyloučení objekt automaticky, když byla, není odemknutí ručně podkladových objektů.  
  
 Vezměte v úvahu následující třídy, `account`, které je určené vnější knihovny a proto nemůže být upraven.  
  
 [!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]  
  
 Následující příklad více transakcí provádí `account` objekt paralelně. V příkladu se používá `critical_section` objekt, který chcete synchronizovat přístup k `account` objekt, protože `account` třída není bezpečná souběžnosti. Každý paralelní operace používá `critical_section::scoped_lock` objekt, který chcete-li zaručit, že `critical_section` objektu je odemčený při operaci buď úspěšná nebo neúspěšná. Když zůstatek účtu je záporná, `withdraw` dojde k selhání operace podle došlo k výjimce.  
  
 [!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
Balance before deposit: 1924  
Balance after deposit: 2924  
Balance before withdrawal: 2924  
Balance after withdrawal: -76  
Balance before withdrawal: -76  
Error details:  
    negative balance: -76  
```  
  
 Další příklady, které používají vzorec RAII dobu trvání souběžnosti objektů najdete v tématu [návod: odstranění práce z uživatelského rozhraní vláken](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md), [postupy: použití třídy kontextu pro implementaci spolupráce Semafor](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md), a [postupy: kompenzace latence vytvořením nadbytečného](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).  
  
 [[Horní](#top)]  
  
##  <a name="global-scope"></a>Nevytvářejte souběžnosti objekty v globálním oboru  
 Když vytvoříte objekt souběžnosti v globálním oboru může způsobit problémy, jako je zablokování nebo paměti porušení přístupu nastat ve vaší aplikaci.  
  
 Například při vytváření objektu Concurrency Runtime vytvoří modulu runtime výchozí plánovače za vás, pokud dosud nebyl vytvořen. Runtime objektu, který je vytvořen během vytváření globální objekt odpovídajícím způsobem způsobí modulu runtime pro vytvoření této výchozí plánovače. Tento proces však trvá zámek interní, která může narušovat inicializaci jiné objekty, které podporují infrastrukturu Concurrency Runtime. Tato interní zámku může být vyžadován jiný objekt infrastrukturu, která dosud nebyla inicializována a proto může způsobit zablokování vaší aplikace.  
  
 Následující příklad ukazuje vytvoření globální konfiguraci [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) objektu. Tento vzor se týkají není pouze `Scheduler` třídy, ale všechny ostatní typy, které jsou poskytovány Concurrency Runtime. Doporučujeme, protože ho může způsobit neočekávané chování vaší aplikace není podle tohoto vzoru.  
  
 [!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]  
  
 Příklady správný způsob, jak vytvořit `Scheduler` objekty, najdete v části [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
 [[Horní](#top)]  
  
##  <a name="shared-data"></a>Nepoužívejte souběžnosti objekty ve sdílených datových segmentů  
 Concurrency Runtime nepodporuje použití concurrency objekty v části sdílených dat, například oddíl dat, který byl vytvořený [data_seg](../../preprocessor/data-seg.md) `#pragma` – direktiva. Objekt souběžnosti, který je sdílen mezi hranice procesu by mohlo modulu runtime v nekonzistentním nebo neplatném stavu.  
  
 [[Horní](#top)]  
  
## <a name="see-also"></a>Viz také  
 [Osvědčené postupy Concurrency Runtime](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [Knihovna Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)   
 [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)   
 [Porovnávání synchronizačních datových struktur rozhraním API systému Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)   
 [Postupy: použití funkcí Alloc a Free ke zlepšení výkonu paměti](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)   
 [Postupy: kompenzace latence vytvořením nadbytečného](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)   
 [Postupy: použití třídy kontextu pro implementaci semaforu pro spolupráci](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)   
 [Návod: Odstranění práce z vlákna uživatelského rozhraní](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)   
 [Osvědčené postupy v Parallel Patterns Library](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [Osvědčené postupy v knihovně asynchronních agentů](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
