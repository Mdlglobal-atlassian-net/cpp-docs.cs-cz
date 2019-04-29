---
title: Obecné osvědčené postupy v Concurrency Runtime
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
ms.openlocfilehash: e25011e2466d76c946cc55421ed228c8ea174161
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413915"
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>Obecné osvědčené postupy v Concurrency Runtime

Tento dokument popisuje osvědčené postupy, které se vztahují k více oblastem modulu Runtime souběžnosti.

##  <a name="top"></a> Oddíly

Tento dokument obsahuje následující části:

- [Použít kooperativní konstrukce synchronizace Pokud je to možné](#synchronization)

- [Vyhněte se zdlouhavým úlohám, které neposkytují](#yield)

- [Operace, která blokují nebo vysokou latencí a vytvořením nadbytečného](#oversubscription)

- [Pomocí funkce správy paměti s podporou souběžnosti, pokud je to možné](#memory)

- [Použijte vzor RAII pro správu životnosti objektů souběžnosti](#raii)

- [Nevytvářejte objekty souběžnosti v globálním oboru](#global-scope)

- [Nepoužívejte objekty souběžnosti ve sdílených datových segmentech](#shared-data)

##  <a name="synchronization"></a> Použít kooperativní konstrukce synchronizace Pokud je to možné

Modul Concurrency Runtime obsahuje mnoho bezpečná pro souběžnost konstrukce, které nevyžadují externí synchronizační objekt. Například [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) třída poskytuje bezpečné na souběžnosti připojit a operace přístup k elementu. Ale pro případy, které požadují výhradní přístup k prostředku, modul runtime poskytuje [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), [concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md), a [souběžnosti :: události](../../parallel/concrt/reference/event-class.md) třídy. Tyto typy se chovají kooperativně; proto plánovače úloh můžete přidělit jinému uživateli prostředků pro zpracování do jiného kontextu jako první úloha čeká na data. Pokud je to možné, použijte místo další synchronizace mechanismy, například těch, které poskytuje rozhraním Windows API, které nefungují tak kooperativně tyto typy synchronizace. Další informace o těchto typů synchronizace a příklady kódu naleznete v tématu [synchronizačních datových struktur](../../parallel/concrt/synchronization-data-structures.md) a [porovnávání synchronizačních datových struktur s rozhraním API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[[Horní](#top)]

##  <a name="yield"></a> Vyhněte se zdlouhavým úlohám, které neposkytují

Vzhledem k tomu, že Plánovač úloh se chová kooperativně, neposkytuje rovnost mezi úkoly. Proto úkol lze zabránit další úlohy spuštění. I když je to přijatelné, v některých případech, v ostatních případech to může způsobit zablokování nebo vyčerpání.

Následující příklad provádí více úloh než je počet elementů prostředky přidělené zpracování. První úkol nevydává pro Plánovač úloh, a proto druhá úloha nespustí až do dokončení první úlohy.

[!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]

Tento příklad vytvoří následující výstup:

1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000

Existuje několik způsobů umožňuje spolupráci mezi dvě úlohy. Jedním ze způsobů je někdy vést k plánovače úloh v rámci dlouhotrvající úlohy. Následující příklad upravuje `task` funkce má být volána [concurrency::Context::Yield](reference/context-class.md#yield) metodu tak, aby mohly běžet jinou úlohu pozastavit provádění pro Plánovač úloh.

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

`Context::Yield` Metoda vrací pouze jiné aktivní vlákno na plánovače, do kterého patří aktuální vlákno lehký úkol nebo jinému vláknu operačního systému. Tato metoda nevydává pracovat, který je naplánován ke spuštění v [concurrency::task_group](reference/task-group-class.md) nebo [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objektu, ale nebyla dosud spuštěna.

Existují jiné způsoby umožňuje spolupráci mezi dlouho běžících úloh. Velkých úloh můžete rozdělit na menší dílčí úkoly. Můžete také povolit překročení stanovených během dlouhých úloh. Kompenzujte umožňuje vytvořit další vlákna, než je k dispozici počet hardwarových vláken. Překryvný odběr je obzvláště užitečná při dlouhé úloha obsahuje vysoké množství latence, například čtení dat z disku nebo připojení k síti. Další informace o jednoduché úlohy a přepínacími najdete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Horní](#top)]

##  <a name="oversubscription"></a> Operace, která blokují nebo vysokou latencí a vytvořením nadbytečného

Modul Concurrency Runtime poskytuje synchronizací primitiv, například [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), umožňující úlohy kooperativně blokovat a vést k sobě navzájem. Když jeden úkol kooperativně blokuje nebo výnosy, Plánovač úloh můžete přidělit jinému uživateli prostředků pro zpracování do jiného kontextu jako první úloha čeká na data.

Existují případy, ve kterých nejde použít spolupráce blokování mechanismus, který je poskytován modulu Runtime souběžnosti. Vnější knihovny, který používáte například může pomocí různých synchronizační mechanismus. Dalším příkladem je při provádění operace, která by mohla mít vysokou velkou latenci, například při použití rozhraní API Windows `ReadFile` funkci na čtení dat z připojení k síti. V těchto případech můžete povolit překročení stanovených další úkoly spouštět, když jiná úloha je v nečinnosti. Kompenzujte umožňuje vytvořit další vlákna, než je k dispozici počet hardwarových vláken.

Vezměte v úvahu následující funkci `download`, která stáhne soubor na dané adrese URL. V tomto příkladu [concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe) metoda dočasně zvýšit počet aktivních podprocesů.

[!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]

Vzhledem k tomu, `GetHttpFile` funkce provede operaci potenciálně latentní, překryvného odběru můžete povolit další úlohy spustit, protože aktuální úloha čeká na data. Kompletní verze tohoto příkladu naleznete v tématu [jak: Latence vytvořením nadbytečného](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

[[Horní](#top)]

##  <a name="memory"></a> Pomocí funkce správy paměti s podporou souběžnosti, pokud je to možné

Pomocí funkce správy paměti [concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) a [concurrency::Free](reference/concurrency-namespace-functions.md#free), až budete mít podrobné úkoly, které často přidělovat malé objekty, které mají poměrně krátké doby života. Modul Concurrency Runtime obsahuje samostatný mezipaměti pro každé vlákno spuštěné. `Alloc` a `Free` funkce přidělují a uvolňují paměť z těchto mezipamětí bez použití zámků nebo překážky paměti.

Další informace o tyto funkce správy paměti naleznete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Příklad použití těchto funkcí, naleznete v tématu [jak: Použití funkcí Alloc a Free ke zlepšení výkonu paměti](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).

[[Horní](#top)]

##  <a name="raii"></a> Použijte vzor RAII pro správu životnosti objektů souběžnosti

Modul Concurrency Runtime používá k implementaci funkcí, jako je například zrušení zpracování výjimek. Proto napište kód bezpečným pro výjimky při volání do modulu runtime nebo volat jiné knihovny, která volá do modulu runtime.

*Získání prostředků je inicializace* vzor (RAII) je jedním ze způsobů pro bezpečnou správu životnosti objektů souběžnosti v daném oboru. Podle vzoru RAII je datová struktura přidělené v zásobníku. Struktury dat inicializuje nebo získá prostředek, když se vytvoří a odstraní nebo vydání prostředku při zničení datová struktura. Vzorek RAII, aby zaručuje, že destruktoru je volána před ukončení nadřazeného oboru. Tento model je vhodný, když funkce obsahuje více `return` příkazy. Tento model také pomáhá psát kód bezpečnost výjimek. Když `throw` příkaz způsobí, že zásobník k provedení operace unwind, destruktor pro objekt vzoru RAII, se nazývá; proto se odstraní nebo vydání prostředku vždy správně.

Modul runtime definuje několik tříd, které používají vzor RAII, například [concurrency::critical_section::scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class) a [concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class). Tyto pomocné rutiny třídy jsou označovány jako *obor zámků*. Tyto třídy nabízejí několik výhod při práci s [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) nebo [concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) objekty. Konstruktor tyto třídy získá přístup k zadané `critical_section` nebo `reader_writer_lock` objekt; přístup verze destruktor na tento objekt. Protože vymezené zámek uvolní přístup k jeho vzájemné vyloučení objektu automaticky při je zničen, ne odemknutí ručně základní objekt.

Vezměte v úvahu následující třídy `account`, který je definován pomocí externí knihovny a proto jej nelze změnit.

[!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]

Následující příklad provádí více transakcí `account` objekt paralelně. V příkladu se používá `critical_section` k synchronizaci přístupu k objektu `account` objektu, protože `account` třída není bezpečná pro souběžnost. Každý paralelní operace používá `critical_section::scoped_lock` objekt zaručit, že `critical_section` je odemknuté objekt, když operace úspěšná nebo neúspěšná. Když zůstatek na účtu je záporný, `withdraw` selže operace vyvoláním výjimky.

[!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]

Tento příklad vytvoří následující ukázkový výstup:

```Output
Balance before deposit: 1924
Balance after deposit: 2924
Balance before withdrawal: 2924
Balance after withdrawal: -76
Balance before withdrawal: -76
Error details:
    negative balance: -76
```

Další příklady, které používají vzor RAII pro správu životnosti objektů souběžnosti, najdete v článku [názorný postup: Odstranění práce z vlákna uživatelského rozhraní](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md), [jak: Použití třídy kontextu pro implementaci semaforu pro spolupráci](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md), a [jak: Latence vytvořením nadbytečného](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

[[Horní](#top)]

##  <a name="global-scope"></a> Nevytvářejte objekty souběžnosti v globálním oboru

Při vytváření objektu souběžnosti v globálním oboru může způsobit problémy, jako je paměť nebo zablokování porušení přístupu v aplikaci.

Například při vytváření objektu modulu Runtime souběžnosti, vytvoří modul runtime výchozí plánovače za vás, pokud dosud nebyla vytvořena. Objekt modulu runtime, který se vytvoří během konstrukce globální objekt odpovídajícím způsobem způsobí, že modul runtime k vytvoření této výchozí plánovače. Nicméně tento proces trvá interní zámek, což může vést k potížím s inicializací jiné objekty, které podporují infrastrukturu Concurrency Runtime. Toto interní zámku může být vyžadováno jiným objektem infrastrukturu, která dosud nebyla inicializována a proto způsobit zablokování aplikace.

Následující příklad ukazuje vytvoření globální [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) objektu. Tento model se týká není pouze `Scheduler` třídy, ale všechny ostatní typy, které jsou k dispozici v modulu Runtime souběžnosti. Doporučujeme, protože to může způsobit neočekávané chování ve vaší aplikaci není podle tohoto vzoru.

[!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]

Příklady správný způsob, jak vytvořit `Scheduler` objekty, najdete [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Horní](#top)]

##  <a name="shared-data"></a> Nepoužívejte objekty souběžnosti ve sdílených datových segmentech

Modulu Runtime souběžnosti nepodporuje použití objekty souběžnosti v části sdílených dat, například data oddíl, který je vytvořen [data_seg](../../preprocessor/data-seg.md) `#pragma` směrnice. Objekt souběžnosti, který se sdílí přes hranice procesu umístit modulu runtime v nekonzistentní nebo neplatném stavu.

[[Horní](#top)]

## <a name="see-also"></a>Viz také:

[Osvědčené postupy v Concurrency Runtime](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Porovnávání synchronizačních datových struktur s rozhraním API systému Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
[Postupy: Použití funkcí Alloc a Free ke zlepšení výkonu paměti](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)<br/>
[Postupy: Kompenzace latence vytvořením nadbytečného počtu vláken](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)<br/>
[Postupy: Použití třídy kontextu pro implementaci semaforu pro spolupráci](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[Návod: Odebrání práce z vlákna uživatelského rozhraní](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
[Osvědčené postupy v knihovně PPL (Parallel Patterns Library)](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[Osvědčené postupy v knihovně asynchronních agentů](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
