---
title: 'Návod: Vytvoření vlastního bloku zpráv | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9391d99f75bdb5ac2191a65e525ce989aefcd6b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421281"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>Návod: Vytvoření vlastního bloku zpráv

Tento dokument popisuje, jak vytvořit typ bloku vlastní zprávy, který řadí příchozích zprávy podle priority.

Přestože typy bloků předdefinovaných zpráv poskytují celou řadu funkcí, můžete vytvořit vlastní typ bloku zprávy a přizpůsobit tak, aby vyhovovala požadavkům vaší aplikace. Popis typů bloků vestavěné zprávy, které jsou poskytovány asynchronní knihovnou agentů najdete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="prerequisites"></a>Požadavky

Před zahájením tohoto návodu, přečtěte si následující dokumenty:

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)

##  <a name="top"></a> Oddíly

Tento návod obsahuje následující části:

- [Návrh vlastního bloku zpráv](#design)

- [Definice třídy priority_buffer](#class)

- [Kompletní příklad](#complete)

##  <a name="design"></a> Návrh vlastního bloku zpráv

Bloky zpráv se účastní aktu odesílání a příjem zpráv. Blok zpráv, který odesílá zprávy se označuje jako *zdrojovým blokem*. Blok zpráv, který přijímá zprávy, se nazývá *cílový blok*. Blok zpráv, který odesílá a přijímá zprávy, se nazývá *propagátor*. Knihovna agentů používá abstraktní třídu [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) pro reprezentaci zdrojových bloků a abstraktní třídu [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) pro reprezentaci cílových bloků. Typy bloků zpráv, které se chovají jako zdroje, jsou odvozeny z `ISource`; typy bloků zpráv, které se chovají jako cíle, jsou odvozeny z `ITarget`.

Ačkoli lze odvodit váš typ bloku zprávy přímo z `ISource` a `ITarget`, knihovna agentů definuje tři základní třídy, které provádějí většinu funkcí, které jsou společné pro všechny typy bloků zpráv, například zpracování chyb a propojení blokům zpráv v souběžným bezpečným způsobem. [Concurrency::source_block](../../parallel/concrt/reference/source-block-class.md) třída odvozena z `ISource` a odesílá zprávy jiným blokům. [Concurrency::target_block](../../parallel/concrt/reference/target-block-class.md) třída odvozena z `ITarget` a přijímá zprávy z jiných bloků. [Concurrency::propagator_block](../../parallel/concrt/reference/propagator-block-class.md) třída odvozena z `ISource` a `ITarget` a odesílá zprávy jiným blokům a přijímá zprávy z jiných bloků. Doporučujeme používat tyto tři základní třídy pro zpracování podrobností infrastrukturu tak, aby se mohli soustředit na chování vašeho bloku zpráv.

`source_block`, `target_block`, A `propagator_block` třídy jsou šablony, které jsou parametrizovány na typ, který spravuje připojení nebo propojení mezi zdrojovými a cílovými bloky a typ, který spravuje zpracování zpráv. Knihovna agentů definuje dva typy, které provádějí správu odkazů, [concurrency::single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) a [concurrency::multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md). `single_link_registry` Třída umožňuje bloku zprávy být spojen s jedním zdrojem nebo jedním cílem. `multi_link_registry` Třída umožňuje bloku zprávy být spojen s více zdroji nebo více cílů. Knihovna agentů definuje jednu třídu, která provádí správu zprávy, [concurrency::ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md). `ordered_message_processor` Třída umožňuje blokům zpráv zpracovávat zprávy v pořadí, ve kterém je obdrží.

Abyste lépe pochopili vztah bloků zpráv a jejich zdrojů a cílů, podívejte se na následující příklad. Tento příklad ukazuje deklaraci třídy [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) třídy.

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

`transformer` Třída odvozena z `propagator_block`a proto se chová jako blok zdrojový a cílový blok. Přijímá zprávy typu `_Input` a odesílá zprávy typu `_Output`. `transformer` Určuje třída `single_link_registry` jako správce odkazu pro všechny cílové bloky a `multi_link_registry` jako správce odkazu pro všechny zdrojové bloky. Proto `transformer` objekt může mít až jeden cíl a neomezený počet zdrojů.

Třída, která je odvozena z `source_block` musí implementovat šest metod: [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets), [accept_message](reference/source-block-class.md#accept_message), [reserve_message](reference/source-block-class.md#reserve_message), [ consume_message](reference/source-block-class.md#consume_message), [release_message](reference/source-block-class.md#release_message), a [resume_propagation](reference/source-block-class.md#resume_propagation). Třídu, která je odvozena z `target_block` musí implementovat [propagate_message](reference/propagator-block-class.md#propagate_message) metody a může volitelně implementovat [send_message](reference/propagator-block-class.md#send_message) metoda. Odvozování z `propagator_block` je funkčně ekvivalentní odvození z `source_block` a `target_block`.

`propagate_to_any_targets` Metoda je volána modulem runtime pro synchronní nebo asynchronní zpracování všech příchozích zpráv a propagaci všech odchozích zpráv. `accept_message` Metoda je volána cílovými bloky pro příjem zpráv. Mnoho typů bloků zpráv, jako `unbounded_buffer`, odesílá zprávy pouze prvnímu cíli, který přijme. Proto převede vlastnictví zprávy na cíl. Další typy bloků zpráv, jako například [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md), nabízejí zprávy každému svému cílovému bloku. Proto `overwrite_buffer` vytvoří kopii zprávy pro každý svůj cíl.

`reserve_message`, `consume_message`, `release_message`, A `resume_propagation` metody umožňují blokům zpráv účastnit se rezervace zpráv. Cílové bloky volají `reserve_message` metoda při nabídnuta zpráva a máte ji rezervovat pro pozdější použití. Poté, co cílový blok vyhradí zprávu, může zavolat `consume_message` metodu ke zpracování zprávy nebo `release_message` metoda ke zrušení rezervace. Stejně jako u `accept_message` metoda, provádění `consume_message` můžete převést vlastnictví zprávy nebo vrátit kopii zprávy. Poté, co cílový blok spotřebuje nebo uvolní vyhrazenou zprávu, modul runtime volá `resume_propagation` metody. Tato metoda obvykle pokračuje v šíření zpráv, počínaje další zprávou ve frontě.

Modul runtime zavolá `propagate_message` metody pro asynchronní přenos zprávy z jiného bloku do aktuálního. `send_message` Způsob se podobá `propagate_message`, s tím rozdílem, že ho synchronně, místo asynchronně, odesílá zprávu cílovým blokům. Výchozí implementace `send_message` odmítne všechny příchozí zprávy. Modul runtime nevolá ani jednu z těchto metod Pokud zpráva neprojde funkcí volitelného filtru, který je přidružený k cílovému bloku. Další informace o filtrech zpráv naleznete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).

[[Horní](#top)]

##  <a name="class"></a> Definice třídy priority_buffer

`priority_buffer` Třída je typu blok vlastní zprávy, která řadí příchozí zprávy nejprve podle priority a pak podle pořadí, ve kterém jsou zprávy přijímány. `priority_buffer` Třídy vypadá podobně jako [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) třídy, protože obsahuje frontu zpráv a také protože funguje jako zdrojový i cílový blok zpráv a může mít více zdrojů i více cíle. Ale `unbounded_buffer` zakládá šíření jenom na pořadí, ve kterém přijímá zprávy ze zdrojů zprávy.

`priority_buffer` Třídy přijímá zprávy typu std::[řazené kolekce členů](../../standard-library/tuple-class.md) , které obsahují `PriorityType` a `Type` elementy. `PriorityType` odkazuje na typ, který má prioritu každé zprávy; `Type` odkazuje na datovou část zprávy. `priority_buffer` Třídy odesílá zprávy typu `Type`. `priority_buffer` Třídy také spravuje dvě fronty zpráv: [std::priority_queue](../../standard-library/priority-queue-class.md) pro příchozí zprávy a std::[fronty](../../standard-library/queue-class.md) pro odchozí zprávy. Řazení zpráv podle priority je užitečné, když `priority_buffer` objektu přijímá více zpráv najednou nebo když přijímá více zpráv předtím, než jsou nějaké zprávy přečteny spotřebitelem.

Kromě sedmi metod, že třída odvozená z `propagator_block` musí implementovat, `priority_buffer` třídy také přepsání `link_target_notification` a `send_message` metody. `priority_buffer` Třída definuje také dvě veřejné pomocné metody `enqueue` a `dequeue`a soukromou pomocnou metodu `propagate_priority_order`.

Následující postup popisuje, jak implementovat `priority_buffer` třídy.

#### <a name="to-define-the-prioritybuffer-class"></a>Definice třídy priority_buffer

1. Vytvořte soubor hlaviček jazyka C++ a pojmenujte ho `priority_buffer.h`. Alternativně můžete použít existující hlavičkový soubor, který je součástí projektu.

1. V `priority_buffer.h`, přidejte následující kód.

[!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. V `std` obor názvů, definujte specializace z [std::less](../../standard-library/less-struct.md) a [std::greater](../../standard-library/greater-struct.md) , které působí na souběžnost::[zpráva](../../parallel/concrt/reference/message-class.md) objekty.

[!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

     The `priority_buffer` class stores `message` objects in a `priority_queue` object. These type specializations enable the priority queue to sort messages according to their priority. The priority is the first element of the `tuple` object.

1. V `concurrencyex` oboru názvů deklarovat `priority_buffer` třídy.

[!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

     The `priority_buffer` class derives from `propagator_block`. Therefore, it can both send and receive messages. The `priority_buffer` class can have multiple targets that receive messages of type `Type`. It can also have multiple sources that send messages of type `tuple<PriorityType, Type>`.

1. V `private` část `priority_buffer` třídy, přidejte následující proměnné členů.

[!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

     The `priority_queue` object holds incoming messages; the `queue` object holds outgoing messages. A `priority_buffer` object can receive multiple messages simultaneously; the `critical_section` object synchronizes access to the queue of input messages.

1. V `private` části, definujte konstruktor kopie a operátor přiřazení. To zabraňuje `priority_queue` objekty v přiřaditelnosti.

[!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. V `public` části, definujte konstruktory, které jsou společné pro mnoho typů bloků zprávy. Také definujte destruktor.

[!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. V `public` části, definovat metody `enqueue` a `dequeue`. Tyto pomocné metody poskytují alternativní způsob odesílání a příjem zpráv `priority_buffer` objektu.

[!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

9. V `protected` části, definujte `propagate_to_any_targets` metody.

[!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

     The `propagate_to_any_targets` method transfers the message that is at the front of the input queue to the output queue and propagates out all messages in the output queue.

10. V `protected` části, definujte `accept_message` metody.

[!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

     When a target block calls the `accept_message` method, the `priority_buffer` class transfers ownership of the message to the first target block that accepts it. (This resembles the behavior of `unbounded_buffer`.)

11. V `protected` části, definujte `reserve_message` metody.

[!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

     The `priority_buffer` class permits a target block to reserve a message when the provided message identifier matches the identifier of the message that is at the front of the queue. In other words, a target can reserve the message if the `priority_buffer` object has not yet received an additional message and has not yet  propagated out the current one.

12. V `protected` části, definujte `consume_message` metody.

[!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

     A target block calls `consume_message` to transfer ownership of the message that it reserved.

13. V `protected` části, definujte `release_message` metody.

[!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

     A target block calls `release_message` to cancel its reservation to a message.

14. V `protected` části, definujte `resume_propagation` metody.

[!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

     The runtime calls `resume_propagation` after a target block either consumes or releases a reserved message. This method propagates out any messages that are in the output queue.

15. V `protected` části, definujte `link_target_notification` metody.

[!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

     The `_M_pReservedFor` member variable is defined by the base class, `source_block`. This member variable points to the target block, if any, that is holding a reservation to the message that is at the front of the output queue. The runtime calls `link_target_notification` when a new target is linked to the `priority_buffer` object. This method propagates out any messages that are in the output queue if no target is holding a reservation.

16. V `private` části, definujte `propagate_priority_order` metody.

[!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

     This method propagates out all messages from the output queue. Every message in the queue is offered to every target block until one of the target blocks accepts the message. The `priority_buffer` class preserves the order of the outgoing messages. Therefore, the first message in the output queue must be accepted by a target block before this method offers any other message to the target blocks.

17. V `protected` části, definujte `propagate_message` metody.

[!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

     The `propagate_message` method enables the `priority_buffer` class to act as a message receiver, or target. This method receives the message that is offered by the provided source block and inserts that message into the priority queue. The `propagate_message` method then asynchronously sends all output messages to the target blocks.

     The runtime calls this method when you call the [concurrency::asend](reference/concurrency-namespace-functions.md#asend) function or when the message block is connected to other message blocks.

18. V `protected` části, definujte `send_message` metody.

[!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

     The `send_message` method resembles `propagate_message`. However it sends the output messages synchronously instead of asynchronously.

     The runtime calls this method during a synchronous send operation, such as when you call the [concurrency::send](reference/concurrency-namespace-functions.md#send) function.

`priority_buffer` Třída obsahuje přetížení konstruktoru, která jsou běžná v mnoha typech bloku zprávy. Některá přetížení konstruktoru přijímají [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) nebo [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objekty, které umožňují bloku zprávy být spravován určitým plánovačem úloh. Další přetížení konstruktoru přebírají funkci filtru. Funkce filtru povolují blokům zpráv přijmout nebo odmítnout zprávu na základě její datové části. Další informace o filtrech zpráv naleznete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md). Další informace o plánovačích úkolů naleznete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Vzhledem k tomu, `priority_buffer` třídy seřadí zprávy podle priority a pak podle pořadí, ve kterém jsou zprávy přijímány, tato třída je nejužitečnější, když obdrží zprávy asynchronně, například při volání [concurrency::asend](reference/concurrency-namespace-functions.md#asend)funkce nebo když je blok zpráv připojen k jinému bloku zpráv.

[[Horní](#top)]

##  <a name="complete"></a> Kompletní příklad

Následující příklad ukazuje úplnou definici `priority_buffer` třídy.

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

Následující příklad provádí souběžně několik `asend` a [concurrency::receive](reference/concurrency-namespace-functions.md#receive) operace `priority_buffer` objektu.

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

Tento příklad vytvoří následující ukázkový výstup.

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

`priority_buffer` Třídy seřadí zprávy nejprve podle priority a pak podle pořadí, ve kterém zprávy příjme. V tomto příkladu jsou zprávy s vyšší číselnou prioritou vloženy směrem k začátku fronty.

[[Horní](#top)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit definici třídy `priority_buffer` třída v souboru s názvem `priority_buffer.h` a testovací program do souboru s názvem `priority_buffer.cpp` a pak spusťte následující příkaz v sadě Visual Studio Okno příkazového řádku.

**cl.exe/EHsc priority_buffer.cpp**

## <a name="see-also"></a>Viz také

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)
