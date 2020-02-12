---
title: Obecné osvědčené postupy v Concurrency Runtime
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
ms.openlocfilehash: 15bae5ba25da4987b076cf3de67cd8484fe47df8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141777"
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>Obecné osvědčené postupy v Concurrency Runtime

Tento dokument popisuje osvědčené postupy, které se vztahují na více oblastí Concurrency Runtime.

## <a name="top"></a>Řezů

Tento dokument obsahuje následující části:

- [Pokud je to možné, použijte konstruktory synchronizace spolupráce](#synchronization)

- [Vyhnout se zdlouhavým úlohám, které nepřinesí](#yield)

- [Použití předaného předplatného k posunování operací, které blokují nebo mají vysokou latenci](#oversubscription)

- [Pokud je to možné, používejte funkce souběžného řízení paměti.](#memory)

- [Použití RAII ke správě životnosti objektů souběžnosti](#raii)

- [Nevytvářejte objekty souběžnosti v globálním oboru](#global-scope)

- [Nepoužívejte objekty souběžnosti ve sdílených datových segmentech.](#shared-data)

## <a name="synchronization"></a>Pokud je to možné, použijte konstruktory synchronizace spolupráce

Concurrency Runtime poskytuje mnoho konstrukcí bezpečných pro souběžnost, které nevyžadují externí objekt synchronizace. Například třída [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) poskytuje operace připojení a přístupu k prvkům souběžného zpracování. V případě bezpečného zpracování v souběžnosti znamená, že ukazatele nebo iterátory jsou vždy platné. Není zárukou pro inicializaci elementu nebo z konkrétního pořadí procházení. Nicméně pro případy, kdy požadujete výhradní přístup k prostředku, modul runtime poskytuje třídy [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md), [concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)a [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) . Tyto typy se chovají v družstvu; Proto může Plánovač úloh znovu přidělit prostředky zpracování do jiného kontextu, protože první úkol čeká na data. Pokud je to možné, použijte tyto typy synchronizace místo jiných synchronizačních mechanismů, například těch, které poskytuje rozhraní API systému Windows, které se nechovají spolupracuje. Další informace o těchto typech synchronizace a příkladech kódu najdete v tématu [Synchronizace datových struktur](../../parallel/concrt/synchronization-data-structures.md) a [porovnání datových struktur synchronizace s rozhraním API systému Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[[Nahoře](#top)]

## <a name="yield"></a>Vyhnout se zdlouhavým úlohám, které nepřinesí

Vzhledem k tomu, že se Plánovač úloh chová v družstvu, neposkytuje nerovnost mezi úkoly. Proto může úkol zabránit spuštění jiných úloh. I když je to přijatelné v některých případech, může to způsobit zablokování nebo vyčerpání.

Následující příklad provádí více úloh než počet přidělených prostředků zpracování. První úkol nepřinese Plánovači úloh, a proto se druhý úkol nespustí až do dokončení prvního úkolu.

[!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]

Tento příklad vytvoří následující výstup:

1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000

Existuje několik způsobů, jak povolit spolupráci mezi těmito dvěma úkoly. Jednou z možností je občas vracet Plánovači úloh v dlouhodobé úloze. V následujícím příkladu je upravena funkce `task` pro volání metody [Concurrency:: Context:: yield](reference/context-class.md#yield) , která vykonává provádění plánovače úloh, aby bylo možné spustit jiný úkol.

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

Metoda `Context::Yield` poskytuje pouze další aktivní vlákno v plánovači, ke kterému patří aktuální vlákno, lehký úkol nebo jiné vlákno operačního systému. Tato metoda nepřinese práci, která je naplánována na spuštění v objektu [Concurrency:: task_group](reference/task-group-class.md) nebo [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) , ale ještě nebyla spuštěna.

Existují i jiné způsoby, jak povolit spolupráci mezi dlouhodobě běžícími úkoly. Velkou úlohu můžete rozdělit na menší dílčí úkoly. V průběhu zdlouhavé úlohy můžete také povolit přeregistraci. V rámci předplatného můžete vytvořit více vláken, než kolik jich je k dispozici. Přeplacení je zvlášť užitečné v případě, že úloha s délkou obsahuje vysoké množství latence, například čtení dat z disku nebo ze síťového připojení. Další informace o nenáročných úlohách a předaných předplatných najdete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Nahoře](#top)]

## <a name="oversubscription"></a>Použití předaného předplatného k posunování operací, které blokují nebo mají vysokou latenci

Concurrency Runtime poskytuje prvky synchronizace, jako je například [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md), které umožňují vzájemnou spolupráci a vzájemné navracení úkolů. Pokud jeden úkol pracuje v družstvu nebo jako důsledek, může Plánovač úloh znovu přidělit prostředky zpracování do jiného kontextu, protože první úkol čeká na data.

V některých případech nemůžete použít mechanizmus pro spolupráci, který je poskytován Concurrency Runtime. Například externí knihovna, kterou použijete, může používat jiný mechanismus synchronizace. Dalším příkladem je, že provedete operaci, která by mohla mít vysokou latenci, například když ke čtení dat ze síťového připojení použijete funkci Windows API `ReadFile`. V těchto případech může nadlimitní povolit spuštění jiných úloh, když je jiná úloha nečinná. V rámci předplatného můžete vytvořit více vláken, než kolik jich je k dispozici.

Vezměte v úvahu následující funkci, `download`, která stáhne soubor na dané adrese URL. Tento příklad používá metodu [Concurrency:: Context:: replacení odběru](reference/context-class.md#oversubscribe) k dočasnému zvýšení počtu aktivních vláken.

[!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]

Vzhledem k tomu, že funkce `GetHttpFile` provádí potenciálně latentní operaci, může přerušit předplatné povolit spuštění jiných úloh, protože aktuální úloha počká na data. Úplnou verzi tohoto příkladu naleznete v tématu [How to: use Replace (přepočet) k posunu latence](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

[[Nahoře](#top)]

## <a name="memory"></a>Pokud je to možné, používejte funkce souběžného řízení paměti.

Použijte funkce správy paměti, [Concurrency:: alokace](reference/concurrency-namespace-functions.md#alloc) a [Concurrency:: Free](reference/concurrency-namespace-functions.md#free), pokud máte jemné úlohy, které často přidělují malé objekty, které mají poměrně krátkou životnost. Concurrency Runtime obsahuje oddělenou paměťovou mezipaměť pro každé spuštěné vlákno. Funkce `Alloc` a `Free` přidělují a uvolňuje paměť z těchto mezipamětí bez použití zámků nebo bariéry paměti.

Další informace o těchto funkcích správy paměti najdete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Příklad, který používá tyto funkce, naleznete v tématu [How to: use realokace a Free ke zlepšení výkonu paměti](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).

[[Nahoře](#top)]

## <a name="raii"></a>Použití RAII ke správě životnosti objektů souběžnosti

Concurrency Runtime používá zpracování výjimek k implementaci funkcí, jako je například zrušení. Proto zapište kód bezpečný pro výjimky při volání do modulu runtime nebo zavolejte jinou knihovnu, která volá do modulu runtime.

Vzor *získání prostředku* (RAII) je jedním ze způsobů, jak bezpečně spravovat životnost objektu souběžnosti v daném oboru. V rámci vzoru RAII se datová struktura přiděluje v zásobníku. Tato struktura dat inicializuje nebo získá prostředek při jeho vytvoření a zničí nebo uvolní tento prostředek při zničení struktury dat. Vzor RAII zaručuje, že je destruktor volán před ukončením ohraničujícího oboru. Tento model je užitečný v případě, že funkce obsahuje více příkazů `return`. Tento model také pomáhá psát kód bezpečný pro výjimky. Když příkaz `throw` způsobí unwind zásobníku, je volán destruktor pro objekt RAII; Proto je prostředek vždy správně odstraněn nebo vydán.

Modul runtime definuje několik tříd, které používají vzor RAII, například [Concurrency:: critical_section:: scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class) a [concurrency:: reader_writer_lock:: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class). Tyto pomocné třídy se označují jako *zámky s oborem*. Tyto třídy poskytují několik výhod při práci s objekty [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) nebo [concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) . Konstruktor těchto tříd získá přístup k poskytnutému objektu `critical_section` nebo `reader_writer_lock`; destruktor uvolní přístup k tomuto objektu. Vzhledem k tomu, že uzamčený zámek uvolňuje k objektu vzájemného vyloučení automaticky, když je zničen, neodemknete tím základní objekt ručně.

Vezměte v úvahu následující třídu `account`, která je definována externí knihovnou, a proto ji nelze upravit.

[!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]

Následující příklad provádí paralelní více transakcí pro objekt `account`. V příkladu se používá objekt `critical_section` k synchronizaci přístupu k objektu `account`, protože třída `account` není bezpečná pro souběžnost. Každá paralelní operace používá objekt `critical_section::scoped_lock` k zajištění toho, aby byl objekt `critical_section` odemčený, když operace buď proběhne úspěšně, nebo selže. Pokud je zůstatek účtu záporný, operace `withdraw` se nezdařila vyvoláním výjimky.

[!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]

Tento příklad vytvoří následující vzorový výstup:

```Output
Balance before deposit: 1924
Balance after deposit: 2924
Balance before withdrawal: 2924
Balance after withdrawal: -76
Balance before withdrawal: -76
Error details:
    negative balance: -76
```

Další příklady, které používají vzor RAII ke správě životního cyklu objektů souběžnosti, naleznete v tématu [Návod: odebrání práce z vlákna uživatelského rozhraní](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md), [Postupy: použití třídy kontextu pro implementaci semaforu pro spolupráci](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)a [Postup: použití přeměny při posunu](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

[[Nahoře](#top)]

## <a name="global-scope"></a>Nevytvářejte objekty souběžnosti v globálním oboru

Když vytváříte objekt souběžnosti v globálním rozsahu, můžete způsobit problémy, jako je zablokování nebo narušení přístupu do paměti ve vaší aplikaci.

Když například vytvoříte objekt Concurrency Runtime, modul runtime vytvoří výchozí Plánovač, pokud ještě nebyl vytvořen. Běhový objekt, který je vytvořen během vytváření globálních objektů, způsobí, že modul runtime vytvoří tento výchozí Plánovač. Tento proces ale provede interní zámek, což může kolidovat s inicializací dalších objektů, které podporují infrastrukturu Concurrency Runtime. Tento interní zámek může být vyžadován jiným objektem infrastruktury, který ještě nebyl inicializován, a může tak způsobit zablokování ve vaší aplikaci.

Následující příklad ukazuje vytvoření globálního objektu [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) . Tento model se vztahuje nejen na třídu `Scheduler`, ale na všechny ostatní typy, které jsou k dispozici v Concurrency Runtime. Doporučujeme, abyste tento model nesledovali, protože to může způsobit neočekávané chování v aplikaci.

[!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]

Příklady správného způsobu vytváření `Scheduler` objektů naleznete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Nahoře](#top)]

## <a name="shared-data"></a>Nepoužívejte objekty souběžnosti ve sdílených datových segmentech.

Concurrency Runtime nepodporuje použití objektů souběžnosti v části sdílených dat, například datovou část vytvořenou direktivou [data_seg](../../preprocessor/data-seg.md)`#pragma`. Objekt souběžnosti, který je sdílen napříč hranicemi procesu, může přepnout modul runtime v nekonzistentním nebo neplatném stavu.

[[Nahoře](#top)]

## <a name="see-also"></a>Viz také

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
