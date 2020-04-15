---
title: 'Návod: Vytvoření vlastního bloku zpráv'
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: 3386994dce68812cf3ed0852a24d8910cb903acf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368561"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>Návod: Vytvoření vlastního bloku zpráv

Tento dokument popisuje, jak vytvořit vlastní typ bloku zprávy, který seřídí příchozí zprávy podle priority.

Přestože předdefinované typy bloků zpráv poskytují širokou škálu funkcí, můžete vytvořit vlastní typ bloku zprávy a přizpůsobit jej tak, aby splňoval požadavky vaší aplikace. Popis předdefinovaných typů bloků zpráv, které poskytuje knihovna asynchronních agentů, naleznete [v tématu Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="prerequisites"></a>Požadavky

Před zahájením tohoto návodu si přečtěte následující dokumenty:

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkce předávání zpráv](../../parallel/concrt/message-passing-functions.md)

## <a name="sections"></a><a name="top"></a>Oddíly

Tento návod obsahuje následující části:

- [Návrh vlastního bloku zpráv](#design)

- [Definování třídy priority_buffer](#class)

- [Kompletní příklad](#complete)

## <a name="designing-a-custom-message-block"></a><a name="design"></a>Návrh vlastního bloku zpráv

Bloky zpráv se účastní odesílání a přijímání zpráv. Blok zpráv, který odesílá zprávy, se označuje jako *zdrojový blok*. Blok zpráv, který přijímá zprávy, se označuje jako *cílový blok*. Blok zprávy, který odesílá i přijímá zprávy, se označuje jako *blok propagátoru*. Knihovna agentů používá [souběžnost abstraktní třídy::ISource](../../parallel/concrt/reference/isource-class.md) k reprezentaci zdrojových bloků a souběžnosti abstraktní třídy::ITarget k reprezentaci cílových bloků. [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) Typy bloků zpráv, které `ISource`fungují jako zdroje odvozené z ; typy bloků zpráv, které `ITarget`fungují jako cíle odvozené z .

Přestože můžete odvodit `ISource` typ `ITarget`bloku zprávy přímo z a , knihovna agentů definuje tři základní třídy, které provádějí většinu funkcí, které jsou společné pro všechny typy bloků zpráv, například zpracování chyb a spojování bloků zpráv společně způsobem bezpečným souběžnosti. [Souběžnost::source_block](../../parallel/concrt/reference/source-block-class.md) třída je `ISource` odvozena od a odesílá zprávy do jiných bloků. [Souběžnost::target_block](../../parallel/concrt/reference/target-block-class.md) třída je `ITarget` odvozena od a přijímá zprávy z jiných bloků. [Souběžnost::propagator_block](../../parallel/concrt/reference/propagator-block-class.md) třída je `ISource` odvozena od a `ITarget` odesílá zprávy do jiných bloků a přijímá zprávy z jiných bloků. Doporučujeme použít tyto tři základní třídy ke zpracování podrobností infrastruktury, takže se můžete zaměřit na chování bloku zpráv.

Aplikace `source_block` `target_block`, `propagator_block` a třídy jsou šablony, které jsou parametrizovány na typu, který spravuje připojení nebo propojení mezi zdrojovými a cílovými bloky a na typu, který spravuje způsob zpracování zpráv. Knihovna agentů definuje dva typy, které provádějí správu propojení, [souběžnost::single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) a [souběžnost::multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md). Třída `single_link_registry` umožňuje blok zpráv, které mají být propojeny s jedním zdrojem nebo na jeden cíl. Třída `multi_link_registry` umožňuje bloku zpráv, které mají být propojeny s více zdrojů nebo více cílů. Knihovna agentů definuje jednu třídu, která provádí správu zpráv, [souběžnost::ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md). Třída `ordered_message_processor` umožňuje bloky zpráv ke zpracování zpráv v pořadí, ve kterém je přijímá.

Chcete-li lépe pochopit, jak bloky zpráv souvisejí s jejich zdroji a cíli, zvažte následující příklad. Tento příklad ukazuje deklaraci [třídy souběžnosti:transformer.](../../parallel/concrt/reference/transformer-class.md)

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

Třída `transformer` je odvozena od `propagator_block`, a proto funguje jako zdrojový blok a jako cílový blok. Přijímá zprávy typu `_Input` a odesílá `_Output`zprávy typu . Třída `transformer` určuje `single_link_registry` jako správce odkazů pro všechny `multi_link_registry` cílové bloky a jako správce odkazů pro všechny zdrojové bloky. Proto `transformer` objekt může mít až jeden cíl a neomezený počet zdrojů.

Třída, která je `source_block` odvozena od musí implementovat šest metod: [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets), [accept_message](reference/source-block-class.md#accept_message), [reserve_message](reference/source-block-class.md#reserve_message), [consume_message](reference/source-block-class.md#consume_message), [release_message](reference/source-block-class.md#release_message)a [resume_propagation](reference/source-block-class.md#resume_propagation). Třída, která je `target_block` odvozena od musí implementovat [metodu propagate_message](reference/propagator-block-class.md#propagate_message) a volitelně můžete implementovat [metodu send_message.](reference/propagator-block-class.md#send_message) Odvození z `propagator_block` je funkčně ekvivalentní odvození `source_block` z `target_block`obou a .

Metoda `propagate_to_any_targets` je volána modulem runtime asynchronně nebo synchronně zpracovat všechny příchozí zprávy a šířit všechny odchozí zprávy. Metoda `accept_message` je volána cílovými bloky pro přijímání zpráv. Mnoho typů bloků zpráv, například `unbounded_buffer`, odesílá zprávy pouze prvnímu cíli, který by je obdržel. Proto přenese vlastnictví zprávy do cíle. Jiné typy bloků zpráv, například [souběžnost::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md), nabízejí zprávy pro každý z jeho cílových bloků. Proto `overwrite_buffer` vytvoří kopii zprávy pro každý z jeho cílů.

V `reserve_message` `consume_message`, `release_message`, `resume_propagation` a metody umožňují bloky zpráv k účasti v rezervaci zprávy. Cílové bloky `reserve_message` volání metody, když jsou nabízeny zprávy a musí rezervovat zprávu pro pozdější použití. Poté, co cílový blok rezervuje `consume_message` zprávu, může volat `release_message` metodu využívat tuto zprávu nebo metodu pro zrušení rezervace. Stejně `accept_message` jako u metody `consume_message` může implementace buď převést vlastnictví zprávy nebo vrátit kopii zprávy. Poté, co cílový blok spotřebovává nebo vydává vyhrazenou zprávu, runtime volá metodu. `resume_propagation` Tato metoda obvykle pokračuje šíření zpráv, počínaje další zprávy ve frontě.

Modul runtime `propagate_message` volá metodu asynchronně přenést zprávu z jiného bloku do aktuálního. Metoda `send_message` se `propagate_message`podobá , s tím rozdílem, že synchronně, namísto asynchronně, odešle zprávu do cílových bloků. Výchozí implementace `send_message` odmítne všechny příchozí zprávy. Runtime nevolá ani jednu z těchto metod, pokud zpráva neprojde volitelnou funkci filtru, která je přidružena k cílovému bloku. Další informace o filtrech zpráv naleznete [v tématu Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).

[[Nahoře]](#top)

## <a name="defining-the-priority_buffer-class"></a><a name="class"></a>Definování třídy priority_buffer

Třída `priority_buffer` je vlastní typ bloku zprávy, který objednává příchozí zprávy nejprve podle priority a potom podle pořadí, ve kterém jsou zprávy přijímány. Třída `priority_buffer` se podobá [souběžnosti::unbounded_buffer](reference/unbounded-buffer-class.md) třídy, protože obsahuje frontu zpráv a také proto, že funguje jako zdroj ový a cílový blok zpráv a může mít více zdrojů a více cílů. Však `unbounded_buffer` základy šíření zpráv pouze na pořadí, ve kterém přijímá zprávy ze svých zdrojů.

Třída `priority_buffer` přijímá zprávy typu std::[řazená kolekce členů,](../../standard-library/tuple-class.md) které obsahují `PriorityType` a `Type` prvky. `PriorityType`odkazuje na typ, který má prioritu každé zprávy; `Type` odkazuje na datovou část zprávy. Třída `priority_buffer` odesílá zprávy `Type`typu . Třída `priority_buffer` také spravuje dvě fronty zpráv: [std::priority_queue](../../standard-library/priority-queue-class.md) objekt pro příchozí zprávy a std::[objekt fronty](../../standard-library/queue-class.md) pro odchozí zprávy. Řazení zpráv podle priority `priority_buffer` je užitečné, pokud objekt přijímá více zpráv současně nebo pokud přijímá více zpráv před čtením všech zpráv spotřebiteli.

Kromě sedmi metod, které třída, která `propagator_block` je odvozena z musí implementovat, `priority_buffer` třída také přepíše `link_target_notification` a `send_message` metody. Třída `priority_buffer` také definuje dvě veřejné pomocné metody `enqueue` a `dequeue`, a `propagate_priority_order`soukromou pomocnou metodu .

Následující postup popisuje, jak `priority_buffer` implementovat třídu.

#### <a name="to-define-the-priority_buffer-class"></a>Definice třídy priority_buffer

1. Vytvořte soubor záhlaví c++ `priority_buffer.h`a pojmenujte jej . Případně můžete použít existující soubor záhlaví, který je součástí projektu.

1. V `priority_buffer.h`přidejte následující kód.

    [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. V `std` oboru názvů definujte specializace [std::less](../../standard-library/less-struct.md) a [std::greater,](../../standard-library/greater-struct.md) které působí na souběžnost:: objekty[zpráv.](../../parallel/concrt/reference/message-class.md)

    [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   Třída `priority_buffer` ukládá `message` objekty `priority_queue` v objektu. Tyto specializace typu umožňují fronty priorit řazení zpráv podle jejich priority. Priorita je první prvek `tuple` objektu.

1. V `concurrencyex` oboru názvů deklarujte třídu. `priority_buffer`

    [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   Třída `priority_buffer` je odvozena od `propagator_block`. Proto může odesílat i přijímat zprávy. Třída `priority_buffer` může mít více cílů, `Type`které přijímají zprávy typu . Může mít také více zdrojů, `tuple<PriorityType, Type>`které odesílají zprávy typu .

1. V `private` části třídy `priority_buffer` přidejte následující členské proměnné.

    [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   Objekt `priority_queue` obsahuje příchozí zprávy; objekt `queue` obsahuje odchozí zprávy. Objekt `priority_buffer` může přijímat více zpráv současně; `critical_section` objekt synchronizuje přístup k frontě vstupních zpráv.

1. V `private` části definujte konstruktor kopie a operátor přiřazení. Tím zabráníte `priority_queue` přiřaditelné objekty.

    [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. V `public` části definujte konstruktory, které jsou společné pro mnoho typů bloků zpráv. Také definujte destruktor.

    [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. V `public` části definujte `enqueue` metody `dequeue`a . Tyto pomocné metody poskytují alternativní způsob odesílání zpráv `priority_buffer` a přijímání zpráv z objektu.

    [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

1. V `protected` části definujte `propagate_to_any_targets` metodu.

    [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   Metoda `propagate_to_any_targets` přenese zprávu, která je na přední straně vstupní fronty do výstupní fronty a rozšíří všechny zprávy ve výstupní frontě.

1. V `protected` části definujte `accept_message` metodu.

    [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   Když cílový blok `accept_message` volá metodu, `priority_buffer` třída převede vlastnictví zprávy na první cílový blok, který ji přijímá. (To se podobá `unbounded_buffer`chování .)

1. V `protected` části definujte `reserve_message` metodu.

    [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   Třída `priority_buffer` umožňuje cílový blok rezervovat zprávu, pokud zadaný identifikátor zprávy odpovídá identifikátoru zprávy, která je na přední straně fronty. Jinými slovy cíl můžete rezervovat zprávu, `priority_buffer` pokud objekt ještě neobdržel další zprávu a dosud šířeny aktuální.

1. V `protected` části definujte `consume_message` metodu.

    [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   Cílový blok `consume_message` volá k převodu vlastnictví zprávy, kterou rezervoval.

1. V `protected` části definujte `release_message` metodu.

    [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   Cílový blok `release_message` volá zrušit svou rezervaci na zprávu.

1. V `protected` části definujte `resume_propagation` metodu.

    [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   Runtime volání `resume_propagation` po cílový blok spotřebovává nebo uvolní vyhrazené zprávy. Tato metoda rozšíří všechny zprávy, které jsou ve výstupní frontě.

1. V `protected` části definujte `link_target_notification` metodu.

    [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   Členská `_M_pReservedFor` proměnná je definována `source_block`základní třídou . Tato členská proměnná odkazuje na cílový blok, pokud existuje, který drží rezervaci na zprávu, která je na přední straně výstupní fronty. Runtime volá, `link_target_notification` když je nový `priority_buffer` cíl propojen s objektem. Tato metoda rozšíří všechny zprávy, které jsou ve výstupní frontě, pokud žádný cíl drží rezervaci.

1. V `private` části definujte `propagate_priority_order` metodu.

    [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   Tato metoda rozšíří všechny zprávy z výstupní fronty. Každá zpráva ve frontě je nabízena každému cílovému bloku, dokud jeden z cílových bloků zprávu nepřijme. Třída `priority_buffer` zachová pořadí odchozích zpráv. Proto první zpráva ve výstupní frontě musí být přijatcílový blok před tato metoda nabízí jakékoli jiné zprávy do cílových bloků.

1. V `protected` části definujte `propagate_message` metodu.

    [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   Metoda `propagate_message` umožňuje `priority_buffer` třídy fungovat jako příjemce zprávy nebo cíl. Tato metoda obdrží zprávu, která je nabízena zadaný zdrojový blok a vloží tuto zprávu do fronty priorit. Metoda `propagate_message` pak asynchronně odešle všechny výstupní zprávy do cílových bloků.

   Runtime volá tuto metodu při volání [funkce concurrency::asend](reference/concurrency-namespace-functions.md#asend) nebo když je blok zpráv připojen k jiným blokům zpráv.

1. V `protected` části definujte `send_message` metodu.

    [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   Metoda `send_message` se `propagate_message`podobá . Však odesílá výstupní zprávy synchronně namísto asynchronně.

   Modul runtime volá tuto metodu během operace synchronního odesílání, například při volání funkce [concurrency::send.](reference/concurrency-namespace-functions.md#send)

Třída `priority_buffer` obsahuje přetížení konstruktoru, které jsou typické pro mnoho typů bloků zpráv. Některá přetížení konstruktoru přebírají [souběžnost::Plánovač](../../parallel/concrt/reference/scheduler-class.md) nebo [souběžnost::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objekty, které umožňují spravovat blok zpráv určitým plánovačem úloh. Ostatní přetížení konstruktoru trvat funkce filtru. Funkce filtru umožňují blokům zpráv přijmout nebo odmítnout zprávu na základě její datové části. Další informace o filtrech zpráv naleznete [v tématu Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md). Další informace o plánovačích úloh naleznete v [tématu Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Vzhledem `priority_buffer` k tomu, že třída objednávky zpráv podle priority a potom podle pořadí, ve kterém jsou přijímány zprávy, tato třída je nejužitečnější, když přijímá zprávy asynchronně, například při volání [souběžnosti::asend](reference/concurrency-namespace-functions.md#asend) funkce nebo při bloku zpráv je připojen k jiné bloky zpráv.

[[Nahoře]](#top)

## <a name="the-complete-example"></a><a name="complete"></a>Kompletní příklad

Následující příklad ukazuje úplnou `priority_buffer` definici třídy.

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

Následující příklad současně provádí řadu `asend` operací a [souběžnost::receive](reference/concurrency-namespace-functions.md#receive) na objektu. `priority_buffer`

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

Tento příklad vytvoří následující ukázkový výstup.

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

Třída `priority_buffer` objednává zprávy nejprve podle priority a potom podle pořadí, ve kterém přijímá zprávy. V tomto příkladu jsou zprávy s větší číselnou prioritou vloženy směrem k přední části fronty.

[[Nahoře]](#top)

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte jej do projektu `priority_buffer` sady Visual Studio nebo `priority_buffer.h` vložte definici třídy `priority_buffer.cpp` do souboru s názvem a testovacího programu do souboru s názvem a spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

**cl.exe /EHsc priority_buffer.cpp**

## <a name="see-also"></a>Viz také

[Návody runtime souběžnosti](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce předávání zpráv](../../parallel/concrt/message-passing-functions.md)
