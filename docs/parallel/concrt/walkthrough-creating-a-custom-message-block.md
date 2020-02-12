---
title: 'Návod: Vytvoření vlastního bloku zpráv'
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: a29ed382d67b91443bd13e029af2a37c42ee834d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142831"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>Návod: Vytvoření vlastního bloku zpráv

Tento dokument popisuje, jak vytvořit vlastní typ bloku zpráv, který vyřadí příchozí zprávy podle priority.

I když integrované typy bloků zpráv poskytují široké spektrum funkcí, můžete vytvořit vlastní typ bloku zpráv a přizpůsobit ho tak, aby splňoval požadavky vaší aplikace. Popis integrovaných typů bloků zpráv, které jsou k dispozici v knihovně asynchronních agentů, naleznete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="prerequisites"></a>Požadavky

Než začnete tento návod, přečtěte si následující dokumenty:

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)

## <a name="top"></a>Řezů

Tento návod obsahuje následující oddíly:

- [Návrh vlastního bloku zpráv](#design)

- [Definování třídy priority_buffer](#class)

- [Úplný příklad](#complete)

## <a name="design"></a>Návrh vlastního bloku zpráv

Bloky zpráv se účastní jednání o posílání a přijímání zpráv. Blok zpráv, který odesílá zprávy, se označuje jako *Zdrojový blok*. Blok zpráv, který přijímá zprávy, se označuje jako *cílový blok*. Blok zpráv, který odesílá i přijímá zprávy, se označuje jako *blok šíření*. Knihovna agentů používá abstraktní třídu [Concurrency:: ISource](../../parallel/concrt/reference/isource-class.md) , která představuje zdrojové bloky a abstraktní třídu [Concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md) , která představuje cílové bloky. Typy bloků zpráv, které fungují jako zdroje odvozené od `ISource`; typy bloků zpráv, které fungují jako cíle, jsou odvozeny od `ITarget`.

I když můžete odvodit typ bloku zprávy přímo z `ISource` a `ITarget`, knihovna agentů definuje tři základní třídy, které provádějí většinu funkcí, které jsou společné pro všechny typy bloků zpráv, například zpracování chyb a spojování bloků zpráv v rámci zajištění bezpečného souběžnosti. Třída [Concurrency:: source_block](../../parallel/concrt/reference/source-block-class.md) je odvozena z `ISource` a odesílá zprávy do jiných bloků. Třída [Concurrency:: target_block](../../parallel/concrt/reference/target-block-class.md) je odvozena z `ITarget` a přijímá zprávy z jiných bloků. Třída [Concurrency::p ropagator_block](../../parallel/concrt/reference/propagator-block-class.md) je odvozena z `ISource` a `ITarget` a odesílá zprávy jiným blokům a přijímá zprávy z jiných bloků. Doporučujeme používat tyto tři základní třídy pro zpracování podrobností infrastruktury, abyste se mohli zaměřit na chování vašeho bloku zpráv.

Třídy `source_block`, `target_block`a `propagator_block` jsou šablony, které jsou parametrizované na typu, který spravuje připojení, nebo propojení mezi zdrojovými a cílovými bloky a na typu, který spravuje zpracování zpráv. Knihovna agentů definuje dva typy, které provádějí správu odkazů, [Concurrency:: single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) a [concurrency:: multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md). Třída `single_link_registry` umožňuje, aby byl blok zprávy propojen s jedním zdrojem nebo na jednom cíli. Třída `multi_link_registry` umožňuje, aby byl blok zprávy propojen s více zdroji nebo více cíli. Knihovna agentů definuje jednu třídu, která provádí správu zpráv, [Concurrency:: ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md). Třída `ordered_message_processor` umožňuje blokům zpráv zpracovávat zprávy v pořadí, ve kterém je přijímá.

Chcete-li lépe pochopit, jak bloky zpráv souvisejí s jejich zdroji a cíli, vezměte v úvahu následující příklad. Tento příklad ukazuje deklaraci třídy [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) .

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

Třída `transformer` je odvozena z `propagator_block`a proto funguje jako zdrojový blok i jako cílový blok. Přijímá zprávy typu `_Input` a odesílá zprávy typu `_Output`. Třída `transformer` určuje `single_link_registry` jako správce odkazů pro všechny cílové bloky a `multi_link_registry` jako správce odkazů pro všechny zdrojové bloky. Proto objekt `transformer` může mít až jeden cíl a neomezený počet zdrojů.

Třída, která je odvozena z `source_block` musí implementovat šest metod: [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets), [accept_message](reference/source-block-class.md#accept_message), [reserve_message](reference/source-block-class.md#reserve_message), [consume_message](reference/source-block-class.md#consume_message), [release_message](reference/source-block-class.md#release_message)a [resume_propagation](reference/source-block-class.md#resume_propagation). Třída, která je odvozena z `target_block` musí implementovat metodu [propagate_message](reference/propagator-block-class.md#propagate_message) a může volitelně implementovat metodu [send_message](reference/propagator-block-class.md#send_message) . Odvození od `propagator_block` je funkčně ekvivalentní k odvození z `source_block` a `target_block`.

Metoda `propagate_to_any_targets` je volána modulem runtime k asynchronnímu nebo synchronnímu zpracování všech příchozích zpráv a šíření všech odchozích zpráv. Metoda `accept_message` je volána cílovými bloky pro příjem zpráv. Mnoho typů bloků zpráv, například `unbounded_buffer`, odesílá zprávy pouze do prvního cíle, který je obdrží. Proto přenáší vlastnictví zprávy na cíl. Jiné typy bloků zpráv, například [Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md), nabízejí zprávy každému z jeho cílových bloků. Proto `overwrite_buffer` vytvoří kopii zprávy pro každý z jejích cílů.

Metody `reserve_message`, `consume_message`, `release_message`a `resume_propagation` umožňují, aby se bloky zpráv účastnily rezervace zpráv. Cílové bloky volají metodu `reserve_message`, když jsou nabízena zpráva a musí ji rezervovat pro pozdější použití. Po tom, co cílový blok rezervuje zprávu, může zavolat metodu `consume_message` pro využití této zprávy nebo metody `release_message` pro zrušení rezervace. Stejně jako u metody `accept_message` může implementace `consume_message` buď přenést vlastnictví zprávy, nebo vracet kopii zprávy. Poté, co cílový blok spotřebuje nebo uvolní vyhrazenou zprávu, modul runtime zavolá metodu `resume_propagation`. Tato metoda obvykle pokračuje v šíření zpráv, počínaje další zprávou ve frontě.

Modul runtime volá metodu `propagate_message` k asynchronnímu přenosu zprávy z jiného bloku do aktuálního. Metoda `send_message` se podobá `propagate_message`, s tím rozdílem, že synchronně místo asynchronně odesílá zprávu do cílových bloků. Výchozí implementace `send_message` odmítne všechny příchozí zprávy. Modul runtime nevolá žádnou z těchto metod, pokud zpráva neprojde volitelnou funkcí filtru, která je přidružena k cílovému bloku. Další informace o filtrech zpráv naleznete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).

[[Nahoře](#top)]

## <a name="class"></a>Definování třídy priority_buffer

Třída `priority_buffer` je vlastní typ bloku zprávy, který nejprve vyřadí příchozí zprávy podle priority a pak podle pořadí, ve kterém jsou zprávy přijímány. Třída `priority_buffer` se podobá třídě [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) , protože obsahuje frontu zpráv a také proto, že funguje jako zdrojový i cílový blok zprávy a může mít jak více zdrojů, tak i více cílů. Nicméně `unbounded_buffer` základy šíření zpráv pouze v pořadí, ve kterém přijímá zprávy ze svých zdrojů.

Třída `priority_buffer` přijímá zprávy typu std::[Tuple](../../standard-library/tuple-class.md) , které obsahují prvky `PriorityType` a `Type`. `PriorityType` odkazuje na typ, který má prioritu každé zprávy; `Type` odkazuje na datovou část zprávy. Třída `priority_buffer` odesílá zprávy typu `Type`. Třída `priority_buffer` také spravuje dvě fronty zpráv: objekt [riority_queue std::p](../../standard-library/priority-queue-class.md) pro příchozí zprávy a objekt std::[Queue](../../standard-library/queue-class.md) pro odchozí zprávy. Řazení zpráv podle priority je užitečné v případě, že objekt `priority_buffer` obdrží více zpráv současně nebo když obdrží více zpráv, než je uživatelé přečtou.

Kromě sedmi metod, které třída odvozená z `propagator_block` musí implementovat, třída `priority_buffer` také přepisuje metody `link_target_notification` a `send_message`. Třída `priority_buffer` také definuje dvě veřejné pomocné metody, `enqueue` a `dequeue`a soukromou pomocnou metodu, `propagate_priority_order`.

Následující postup popisuje, jak implementovat třídu `priority_buffer`.

#### <a name="to-define-the-priority_buffer-class"></a>Definice třídy priority_buffer

1. Vytvořte C++ hlavičkový soubor a pojmenujte ho `priority_buffer.h`. Alternativně můžete použít existující hlavičkový soubor, který je součástí projektu.

1. V `priority_buffer.h`přidejte následující kód.

[!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. V oboru názvů `std` definujte specializace [std:: minus](../../standard-library/less-struct.md) a [std:: vyšší](../../standard-library/greater-struct.md) , které fungují v objektech concurrency::[Message](../../parallel/concrt/reference/message-class.md) .

[!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   Třída `priority_buffer` ukládá `message` objektů do objektu `priority_queue`. Tyto specializace typu umožňují, aby fronta priorit seřadila zprávy podle jejich priority. Priorita je prvním prvkem objektu `tuple`.

1. V oboru názvů `concurrencyex` Deklarujte třídu `priority_buffer`.

[!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   Třída `priority_buffer` je odvozena z `propagator_block`. Proto může odesílat i přijímat zprávy. Třída `priority_buffer` může mít více cílů, které přijímají zprávy typu `Type`. Může mít také více zdrojů, které odesílají zprávy typu `tuple<PriorityType, Type>`.

1. V části `private` `priority_buffer` třídy přidejte následující proměnné členů.

[!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   Objekt `priority_queue` obsahuje příchozí zprávy; objekt `queue` obsahuje odchozí zprávy. Objekt `priority_buffer` může přijímat více zpráv současně. objekt `critical_section` synchronizuje přístup do fronty vstupních zpráv.

1. V části `private` definujte kopírovací konstruktor a operátor přiřazení. Tím se zabrání přiřazení objektů `priority_queue`.

[!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. V části `public` definujte konstruktory, které jsou společné pro mnoho typů bloků zpráv. Také definujte destruktor.

[!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. V části `public` definujte metody `enqueue` a `dequeue`. Tyto pomocné metody poskytují alternativní způsob, jak odesílat zprávy do a přijímat zprávy z objektu `priority_buffer`.

[!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

9. V části `protected` Definujte metodu `propagate_to_any_targets`.

[!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   Metoda `propagate_to_any_targets` přenáší zprávu, která je na začátku vstupní fronty, do výstupní fronty a šíří všechny zprávy ve výstupní frontě.

10. V části `protected` Definujte metodu `accept_message`.

[!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   Když cílový blok volá metodu `accept_message`, třída `priority_buffer` přenáší vlastnictví zprávy na první cílový blok, který je přijímá. (To se podobá chování `unbounded_buffer`.)

11. V části `protected` Definujte metodu `reserve_message`.

[!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   Třída `priority_buffer` umožňuje cílovému bloku rezervovat zprávu, pokud zadaný identifikátor zprávy odpovídá identifikátoru zprávy, která je na začátku fronty. Jinými slovy cíl může rezervovat zprávu, pokud objekt `priority_buffer` ještě nedostal další zprávu a ještě nerozšířila aktuální.

12. V části `protected` Definujte metodu `consume_message`.

[!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   Cílový blok volá `consume_message` pro přenos vlastnictví zprávy, kterou rezervoval.

13. V části `protected` Definujte metodu `release_message`.

[!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   Cílový blok volá `release_message` pro zrušení jeho rezervace na zprávu.

14. V části `protected` Definujte metodu `resume_propagation`.

[!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   Volání za běhu `resume_propagation` po cílovém bloku buď spotřebují, nebo uvolní rezervovanou zprávu. Tato metoda šíří všechny zprávy, které jsou ve výstupní frontě.

15. V části `protected` Definujte metodu `link_target_notification`.

[!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   Členská proměnná `_M_pReservedFor` je definována základní třídou `source_block`. Tato členská proměnná odkazuje na cílový blok (pokud existuje), který drží rezervaci na zprávu, která je na začátku výstupní fronty. Běhové volání `link_target_notification`, když je nový cíl propojen s objektem `priority_buffer`. Tato metoda šíří všechny zprávy, které jsou ve výstupní frontě, pokud žádný cíl nedrží rezervaci.

16. V části `private` Definujte metodu `propagate_priority_order`.

[!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   Tato metoda šíří všechny zprávy z výstupní fronty. Všechny zprávy ve frontě jsou nabízeny každému cílovému bloku, dokud některý z cílových bloků zprávu nepřijme. Třída `priority_buffer` zachovává pořadí odchozích zpráv. Proto musí být první zpráva ve frontě výstupu přijata cílovým blokem před tím, než tato metoda nabídne jakékoli jiné zprávě cílovým blokům.

17. V části `protected` Definujte metodu `propagate_message`.

[!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   Metoda `propagate_message` umožňuje, aby třída `priority_buffer` pracovala jako příjemce zprávy nebo cíl. Tato metoda obdrží zprávu, kterou nabízí poskytnutý zdrojový blok, a vloží tuto zprávu do fronty priorit. Metoda `propagate_message` pak asynchronně pošle všechny výstupní zprávy do cílových bloků.

   Modul runtime volá tuto metodu při volání funkce [Concurrency:: asend](reference/concurrency-namespace-functions.md#asend) nebo v případě, že je blok zpráv připojen k jiným blokům zpráv.

18. V části `protected` Definujte metodu `send_message`.

[!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   Metoda `send_message` se podobá `propagate_message`. Ale odešle výstupní zprávy synchronně namísto asynchronního.

   Modul runtime volá tuto metodu během operace synchronního odeslání, například při volání funkce [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) .

Třída `priority_buffer` obsahuje přetížení konstruktoru, která jsou typická v mnoha typech bloků zpráv. Některá přetížení konstruktoru přijímají objekty [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) nebo [Concurrency:: Schedule](../../parallel/concrt/reference/schedulegroup-class.md) , které umožňují spravovat blok zpráv konkrétním plánovačem úloh. Další přetížení konstruktoru přebírají funkci filtru. Funkce filtru umožňují blokům zpráv přijmout nebo odmítnout zprávu na základě její datové části. Další informace o filtrech zpráv naleznete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md). Další informace o Plánovači úloh naleznete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Vzhledem k tomu, že třída `priority_buffer` řadí zprávy podle priority a pak podle pořadí, ve kterém jsou zprávy přijímány, je tato třída nejužitečnější, když přijímá zprávy asynchronně, například při volání funkce [Concurrency:: asend](reference/concurrency-namespace-functions.md#asend) nebo při připojení bloku zpráv k jiným blokům zpráv.

[[Nahoře](#top)]

## <a name="complete"></a>Úplný příklad

Následující příklad ukazuje úplnou definici třídy `priority_buffer`.

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

Následující příklad současně provádí několik `asend` a [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) pro objekt `priority_buffer`.

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

Tento příklad vytvoří následující vzorový výstup.

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

Třída `priority_buffer` řadí zprávy nejprve podle priority a pak podle pořadí, ve kterém přijímá zprávy. V tomto příkladu se do přední části fronty vloží zprávy s větší číselnou prioritou.

[[Nahoře](#top)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte vzorový kód a vložte ho do projektu sady Visual Studio nebo vložte definici třídy `priority_buffer` do souboru s názvem `priority_buffer.h` a testovací program v souboru s názvem `priority_buffer.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

**CL. exe/EHsc priority_buffer. cpp**

## <a name="see-also"></a>Viz také

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)
