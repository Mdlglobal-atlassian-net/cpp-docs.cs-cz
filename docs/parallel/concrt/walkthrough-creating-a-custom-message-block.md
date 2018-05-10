---
title: 'Návod: Vytvoření vlastního bloku zpráv | Microsoft Docs'
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
ms.openlocfilehash: fa70cf40851815ff92f01405d47015afd2e3e444
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-creating-a-custom-message-block"></a>Návod: Vytvoření vlastního bloku zpráv
Tento dokument popisuje, jak vytvořit vlastní zprávu typ bloku, jemuž příchozí zprávy pořadí podle priority.  
  
 I když typy bloku předdefinované zpráv poskytovat celou řadu funkcí, můžete vytvořit vlastní typ bloku zpráv a přizpůsobit podle požadavků vaší aplikace. Popis typy bloku předdefinované zpráv, které jsou poskytovány knihovna asynchronních agentů najdete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="prerequisites"></a>Požadavky  
 Přečtěte si následující dokumenty, než začnete Tento názorný postup:  
  
- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)  
  
- [Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)  
  
##  <a name="top"></a> Oddíly  
 Tento názorný postup obsahuje následující části:  
  
- [Navrhování vlastního bloku zpráv](#design)  
  
- [Definování priority_buffer – třída](#class)  
  
- [Úplný příklad](#complete)  
  
##  <a name="design"></a> Navrhování vlastního bloku zpráv  
 Bloky zpráv účastnit operace odesílání a přijímání zpráv. Blok zpráva, která odesílá zprávy se označuje jako *zdrojového bloku*. Blok zpráv, která přijímá zprávy se označuje jako *cílový blok*. Blok zpráv, který odesílá i přijímá zprávy, se označuje jako *Šiřitel bloku*. Knihovna agentů používá abstraktní třídu [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) k reprezentaci zdroj bloky a abstraktní třída [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) představují cíl bloky. Blok zpráv typy které působí jako zdroje jsou odvozeny od `ISource`; bloku zpráv typy které působí jako cíle odvozena od `ITarget`.  
  
 I když můžete odvodit typ bloku vaše zprávy přímo z `ISource` a `ITarget`, knihovna agentů definuje tři základní třídy, které provádějí většinu funkce, které jsou společné pro všechny typy bloku zpráv, například zpracování chyb a připojení bloky zpráv společně způsobem bezpečných souběžnosti. [Concurrency::source_block](../../parallel/concrt/reference/source-block-class.md) třída odvozená z `ISource` a odešle zprávy do jiné bloky. [Concurrency::target_block](../../parallel/concrt/reference/target-block-class.md) třída odvozená z `ITarget` a přijímá zprávy od jiných bloky. [Concurrency::propagator_block](../../parallel/concrt/reference/propagator-block-class.md) třída odvozená z `ISource` a `ITarget` a odesílá zprávy do jiné bloky a přijímá zprávy od jiných bloky. Doporučujeme použít tyto tři základní třídy pro zpracování podrobnosti infrastruktury tak, aby se můžete soustředit na chování vaší bloku zpráv.  
  
 `source_block`, `target_block`, A `propagator_block` třídy jsou šablony, které jsou parametry na typ, který spravuje připojení nebo odkazy, mezi zdrojem a cílem bloky a na typ, který spravuje zpracování zpráv. Knihovna agentů definuje dva typy, které provádět správu odkaz [concurrency::single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) a [concurrency::multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md). `single_link_registry` Třída umožňuje blok zpráv propojení jeden zdroj nebo jeden cíl. `multi_link_registry` Třída umožňuje blok zpráv propojení více zdrojů nebo více cílů. Knihovna agentů definuje jednu třídu, která provádí správu zpráva [concurrency::ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md). `ordered_message_processor` Třída umožňuje bloky zpráv ke zpracování zpráv v pořadí, ve kterém je obdrží.  
  
 Abyste lépe pochopili, jak bloky zpráv vztahují k jejich zdroje a cíle, podívejte se na následující příklad. Tento příklad ukazuje deklaraci [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) třídy.  
  
 [!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]  
  
 `transformer` Třída odvozená z `propagator_block`a proto funguje jako blok zdrojový i cílový blok. Přijímá zprávy typu `_Input` a odesílá zprávy typu `_Output`. `transformer` Určuje třídu `single_link_registry` jako správce odkaz pro všechny cílové bloky a `multi_link_registry` jako správce odkaz pro všechny zdroje bloky. Proto `transformer` objekt může obsahovat maximálně jeden cíl a neomezený počet zdrojů.  
  

 Třída odvozená z `source_block` musí implementovat šesti metody: [propagate_to_any_targets –](reference/source-block-class.md#propagate_to_any_targets), [accept_message –](reference/source-block-class.md#accept_message), [reserve_message –](reference/source-block-class.md#reserve_message), [ consume_message –](reference/source-block-class.md#consume_message), [release_message –](reference/source-block-class.md#release_message), a [resume_propagation –](reference/source-block-class.md#resume_propagation). Třída odvozená z `target_block` musí implementovat [propagate_message –](reference/propagator-block-class.md#propagate_message) metoda a volitelně můžete implementovat [send_message –](reference/propagator-block-class.md#send_message) metoda. Odvozování z `propagator_block` je funkčně srovnatelný odvozování z obou `source_block` a `target_block`.  


  
 `propagate_to_any_targets` Metoda je volána modulu runtime synchronně nebo asynchronně zpracovat žádné příchozí zprávy a šířit se všechny odchozí zprávy. `accept_message` Metoda je volána metodou cíl bloky přijímat zprávy. Mnoho zprávy typy bloku, například `unbounded_buffer`, odesílat zprávy pouze první cíl, který by ji přijmou. Proto přenos vlastnictví zprávy k cíli. Další bloku zpráv typy, jako například [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md), nabízejí zprávy pro každý z jeho cíl bloků. Proto `overwrite_buffer` vytvoří kopii zprávu pro každý z jeho cíle.  
  
 `reserve_message`, `consume_message`, `release_message`, A `resume_propagation` metody povolit bloky zpráv se účastnit rezervace zprávy. Cíl blokuje volání `reserve_message` metoda po jejich nabízí zprávu a mít tak, aby vyhradil zprávu pro pozdější použití. Po cílový blok si vyhrazuje zprávu, může zavolat `consume_message` metoda využívat zprávy nebo `release_message` metoda zrušení rezervace. Stejně jako u `accept_message` metoda, provádění `consume_message` můžete převést vlastnictví zprávy nebo vrátit kopii zprávy. Poté, co cílový blok využívá nebo uvolní vyhrazených zpráv, volá modul runtime `resume_propagation` metoda. Obvykle tuto metodu pokračuje šíření zpráv, počínaje na další zprávu ve frontě.  
  
 Modul runtime volání `propagate_message` metoda asynchronně posílat zprávy z jiného bloku do aktuální. `send_message` Vypadá takto: metoda `propagate_message`kromě toho, že ho synchronně, místo asynchronně, odešle zprávu do cílové bloky. Výchozí implementaci `send_message` odmítne všechny příchozí zprávy. Modul runtime nevyvolá žádnou z těchto metod Pokud zpráva neprojde funkce volitelný filtr, který je přidružen cílový blok. Další informace o filtry zpráv najdete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).  
  
 [[Horní](#top)]  
  
##  <a name="class"></a> Definování priority_buffer – třída  
 `priority_buffer` Třída je typ bloku vlastní zprávy, který řadí příchozí zprávy nejprve podle priority a poté podle pořadí, ve kterém jsou přijaty zprávy. `priority_buffer` Vypadá takto: Třída [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) třídy, protože drží frontu zprávy a také protože funguje jako zdroj a cíl bloku zpráv a může mít více zdrojů a více cíle. Ale `unbounded_buffer` základů zprávy šíření pouze v pořadí, ve kterém přijímá zprávy od její zdroje.  
  
 `priority_buffer` Třída přijímá zprávy typu – std::[řazené kolekce členů](../../standard-library/tuple-class.md) obsahující `PriorityType` a `Type` elementy. `PriorityType` odkazuje na typ, který obsahuje prioritu všech zpráv; `Type` odkazuje na datové části zprávy. `priority_buffer` Třída odesílající zprávy typu `Type`. `priority_buffer` Třída také spravuje dva fronty zpráv: [std::priority_queue](../../standard-library/priority-queue-class.md) objekt pro příchozí zprávy a – std::[fronty](../../standard-library/queue-class.md) objekt odesílaných zpráv. Řazení zpráv podle priority je užitečné, když `priority_buffer` objektu současně přijímá více zprávy nebo při přijetí více zpráv předtím, než jsou příjemci číst všechny zprávy.  
  
 Kromě sedm metod, třída odvozená z `propagator_block` musí implementovat `priority_buffer` třídy také přepsání `link_target_notification` a `send_message` metody. `priority_buffer` Třída také definuje dvě veřejné pomocné metody `enqueue` a `dequeue`a privátní Pomocná metoda, `propagate_priority_order`.  
  
 Následující postup popisuje, jak implementovat `priority_buffer` třídy.  
  
#### <a name="to-define-the-prioritybuffer-class"></a>Definice třídy priority_buffer  
  
1.  Vytvořte soubor hlaviček C++ a pojmenujte ji `priority_buffer.h`. Alternativně můžete použít existující soubor hlaviček, který je součástí projektu.  
  
2.  V `priority_buffer.h`, přidejte následující kód.  
  
 [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]  
  
3.  V `std` obor názvů, definujte specializací [std::less](../../standard-library/less-struct.md) a [std::greater](../../standard-library/greater-struct.md) , fungují v concurrency::[zpráva](../../parallel/concrt/reference/message-class.md) objekty.  
  
 [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]  
  
     `priority_buffer` Třídy úložiště `message` objekty v `priority_queue` objektu. Tyto typ specializací povolit priority fronty seřadit podle jejich prioritu zprávy. Priorita je první prvek `tuple` objektu.  
  
4.  V `concurrencyex` obor názvů, deklarovat `priority_buffer` třídy.  
  
 [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]  
  
     `priority_buffer` Třída odvozená z `propagator_block`. Proto se může odesílat i přijímat zprávy. `priority_buffer` Třída může mít více cílů, které přijímají zprávy typu `Type`. Může také obsahovat více zdrojů, které odesílají zprávy typu `tuple<PriorityType, Type>`.  
  
5.  V `private` části `priority_buffer` třídy, přidejte následující proměnné členů.  
  
 [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]  
  
     `priority_queue` Má objekt příchozí zprávy; `queue` má objekt odchozích zpráv. A `priority_buffer` objekt může být současně více zpráv; `critical_section` objekt synchronizuje přístup do fronty vstupní zpráv.  
  
6.  V `private` část, definování konstruktor copy a operátor přiřazení. Zabrání se tak `priority_queue` objekty z se přiřadit.  
  
 [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]  
  
7.  V `public` část, definování konstruktory, které jsou společné pro mnoho typů bloku zpráv. Také definujte destruktoru.  
  
 [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]  
  
8.  V `public` část, definování metody `enqueue` a `dequeue`. Tyto metody helper poskytnout alternativní způsob zprávy odesílat a přijímat zprávy z `priority_buffer` objektu.  
  
 [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]  
  
9. V `protected` části, zadejte `propagate_to_any_targets` metoda.  
  
 [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]  
  
     `propagate_to_any_targets` Metoda přenáší zprávu, která je na začátku vstupní fronty pro výstupní fronty a rozšíří na všechny zprávy ve výstupní fronty.  
  
10. V `protected` části, zadejte `accept_message` metoda.  
  
 [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]  
  
     Pokud cílový blok volá `accept_message` metoda, `priority_buffer` třída přenáší vlastnictví zprávy do první cílový blok, který přijímá ho. (To se podobá chování `unbounded_buffer`.)  
  
11. V `protected` části, zadejte `reserve_message` metoda.  
  
 [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]  
  
     `priority_buffer` Třída umožňuje cílový blok tak, aby vyhradil zprávu, když identifikátor zadaná zpráva odpovídá identifikátor zprávy, která se nachází na začátek fronty. Jinými slovy, cíl můžete vyhradit zprávu, pokud `priority_buffer` objekt neobdržel ještě další zprávu a ještě nebyl rozšířen na aktuální.  
  
12. V `protected` části, zadejte `consume_message` metoda.  
  
 [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]  
  
     Cílový blok volá `consume_message` přenos vlastnictví zprávu, která je vyhrazena.  
  
13. V `protected` části, zadejte `release_message` metoda.  
  
 [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]  
  
     Cílový blok volá `release_message` zrušit jeho rezervaci na zprávy.  
  
14. V `protected` části, zadejte `resume_propagation` metoda.  
  
 [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]  
  
     Volání modulu runtime `resume_propagation` po cílový blok využívá nebo uvolní vyhrazených zpráv. Tato metoda se rozšíří na všechny zprávy, které jsou v výstupní fronty.  
  
15. V `protected` části, zadejte `link_target_notification` metoda.  
  
 [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]  
  
     `_M_pReservedFor` Členské proměnné je definována v základní třídě `source_block`. Tato proměnná člen odkazuje na cílový blok, pokud existuje, která drží rezervace na zprávu, která se nachází na začátku výstupní fronty. Volání modulu runtime `link_target_notification` kdy je nový cíl propojený s `priority_buffer` objektu. Tato metoda se rozšíří na všechny zprávy, které se nacházejí v výstupní fronty, pokud žádný cíl drží rezervace.  
  
16. V `private` části, zadejte `propagate_priority_order` metoda.  
  
 [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]  
  
     Tato metoda se rozšíří na všechny zprávy z výstupní fronty. Každou zprávu ve frontě se nabízí na každý cílový blok, dokud jeden cíl bloků přijímá zprávy. `priority_buffer` Třída zachovává pořadí odchozích zpráv. Proto první zprávu ve výstupní fronty musí přijmout cílový blok před jakoukoli jinou zprávu na bloky target nabízí tuto metodu.  
  
17. V `protected` části, zadejte `propagate_message` metoda.  
  
 [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]  
  
     `propagate_message` Metoda umožňuje `priority_buffer` třídy tak, aby fungoval jako příjemce zprávy, nebo nastavte jako cíl. Tato metoda obdrží zprávu, která nabízí blok zadaný zdroj a vloží zprávy do fronty s prioritou. `propagate_message` Metoda poté asynchronně odešle všechny výstup zpráv do cílového bloky.  
  

     Modul runtime volá tuto metodu při volání [concurrency::asend](reference/concurrency-namespace-functions.md#asend) funkce nebo pokud je bloku zpráv připojené k jiné bloky zpráv.  

  
18. V `protected` části, zadejte `send_message` metoda.  
  
 [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]  
  
     `send_message` Vypadá takto: metoda `propagate_message`. Ale odešle zprávy výstup synchronně místo asynchronně.  
  

     Modul runtime volá tuto metodu během odesílání synchronní operace, jako je například při volání [concurrency::send](reference/concurrency-namespace-functions.md#send) funkce.  
  
 `priority_buffer` Třída obsahuje konstruktor přetížení, která jsou typická ve mnoho typů bloku zpráv. Některé konstruktor přetížení proveďte [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) nebo [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objekty, které umožňují bloku zpráv lze spravovat pomocí plánovače úloh konkrétní. Dalšími přetíženími konstruktor trvat funkce filtru. Funkce filtru povolit bloky zpráv k přijetí nebo odmítnutí zprávu na základě jeho datové části. Další informace o filtry zpráv najdete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md). Další informace o plánovače úloh najdete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
 Protože `priority_buffer` třída pořadí podle priority zprávy a pak podle pořadí, ve kterém jsou přijaty zprávy, tato třída se používá při přijetí zprávy asynchronně, například při volání [concurrency::asend](reference/concurrency-namespace-functions.md#asend)funkce nebo pokud je bloku zpráv připojené k jiné bloky zpráv.  
  
 [[Horní](#top)]  
  
##  <a name="complete"></a> Úplný příklad  
 Následující příklad ukazuje definici dokončení `priority_buffer` třídy.  
  
 [!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]  
  
 Následující příklad souběžně provede několik `asend` a [concurrency::receive](reference/concurrency-namespace-functions.md#receive) operací na `priority_buffer` objektu.  

  
 [!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]  
  
 Tento příklad vytvoří následující ukázkový výstup.  
  
```Output  
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36  
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24  
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12  
```  
  
 `priority_buffer` Třída řadí zprávy nejprve podle priority a poté podle pořadí, ve kterém se přijímá zprávy. V tomto příkladu jsou vloženy zprávy s vyšší prioritou číselné směrem dopředu fronty.  
  
 [[Horní](#top)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kopírování ukázkový kód a vložte ji do projektu sady Visual Studio nebo vložit definici `priority_buffer` – třída v souboru, který je pojmenován `priority_buffer.h` a program test v souboru, který je pojmenován `priority_buffer.cpp` a poté spusťte následující příkaz v sadě Visual Studio Okno příkazového řádku.  
  
 **cl.exe /EHsc priority_buffer.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Návody k Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)
