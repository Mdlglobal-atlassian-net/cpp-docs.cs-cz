---
title: "Paralelní kontejnery a objekty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
caps.latest.revision: "34"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9159b9c8170ee73afd8bee5305506a842368a231
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="parallel-containers-and-objects"></a>Paralelní kontejnery a objekty
Paralelní vzory knihovny (PPL) obsahuje několik kontejnery a objekty, které poskytují přístup z více vláken bezpečný přístup k jejich elementů.  
  
 A *souběžných kontejneru* poskytuje souběžnosti bezpečný přístup k nejdůležitější operace. Funkce těchto kontejnerů se podobá ty, které jsou dostupné ve standardní knihovně C++. Například [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) vypadá takto: Třída [std::vector](../../standard-library/vector-class.md) třídy, vyjma toho, že `concurrent_vector` třída umožňuje připojit elementy paralelně. Souběžné kontejnery použijte, když máte paralelní kód, který vyžaduje oprávnění čtení a zápis do kontejneru.  
  
 A *souběžných objekt* souběžně sdílí součásti. Proces, který vypočítává stav souběžných objektu paralelně vytváří stejný výsledek jako jiný proces, který vypočítá stejného stavu sériově. [Concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třída je příkladem typu souběžných objektu. `combinable` Třída umožňuje provádět paralelní výpočty a pak tyto výpočty do konečný výsledek. Používejte souběžné objekty, když používáte synchronizační mechanismus, například mutex by jinak synchronizovat přístup ke sdílené proměnné nebo prostředků.  
  
##  <a name="top"></a>Oddíly  
 Toto téma popisuje následující paralelní kontejnery a objekty podrobně.  
  
 Souběžné kontejnery:  
  
-   [concurrent_vector – třída](#ctor)  
  
    -   [Rozdíly mezi concurrent_vector a vektoru](#ctor)  
  
    -   [Operace bezpečné souběžnosti](#ctor)  
  
    -   [Bezpečnost výjimek](#ctor)  
  
-   [concurrent_queue – třída](#queue)  
  
    -   [Rozdíly mezi concurrent_queue a fronty](#queue-differences)  
  
    -   [Operace bezpečné souběžnosti](#queue-safety)  
  
    -   [Podpora iterátorů](#queue-iterators)  
  
-   [concurrent_unordered_map – třída](#unordered_map)  
  
    -   [Rozdíly mezi concurrent_unordered_map a unordered_map](#map-differences)  
  
    -   [Operace bezpečné souběžnosti](#map-safety)  
  
-   [concurrent_unordered_multimap – třída](#unordered_multimap)  
  
-   [concurrent_unordered_set – třída](#unordered_set)  
  
-   [concurrent_unordered_multiset – třída](#unordered_multiset)  
  
 Souběžné objekty:  
  
-   [combinable – třída](#combinable)  
  
    -   [Metody a funkce](#combinable-features)  
  
    -   [Příklady](#combinable-examples)  
  
##  <a name="vector"></a>concurrent_vector – třída  
 [Concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) třídy je třída pořadí kontejneru, která, stejně jako [std::vector](../../standard-library/vector-class.md) třídy, vám umožní náhodně přístup k jeho elementy. `concurrent_vector` Elementu a třída umožňuje připojit souběžnosti bezpečné pro přístup k operace. Připojit operace zneplatnění existující ukazatele nebo iterátory. Iterator přístup a traversal operace jsou také bezpečných souběžnosti.  
  
###  <a name="vector-differences"></a>Rozdíly mezi concurrent_vector a vektoru  
 `concurrent_vector` Třída podobá `vector` třídy. Složitost připojení, element přístup a operace přístupu iterator na `concurrent_vector` objekt jsou stejné jako u `vector` objektu. Následující body ilustrují, kde `concurrent_vector` se liší od `vector`:  
  
-   Připojit iterator traversal operace, iterator přístup a přístup k elementu na `concurrent_vector` objekt jsou bezpečné souběžnosti.  
  
-   Prvky můžete přidat pouze na konci `concurrent_vector` objektu. `concurrent_vector` Třída neposkytuje `insert` metoda.  
  
-   A `concurrent_vector` objekt nepoužíval [přesunout sémantiku](../../cpp/rvalue-reference-declarator-amp-amp.md) při připojení k němu.  
  

-   `concurrent_vector` Třída neposkytuje `erase` nebo `pop_back` metody. Stejně jako u `vector`, použijte [vymazat](reference/concurrent-vector-class.md#clear) metoda odebrat všechny elementy z `concurrent_vector` objektu.  
  
-   `concurrent_vector` Třída neukládá jeho elementy souvisle v paměti. Proto nelze použít `concurrent_vector` třída všechny způsoby, které můžete použít pole. Například pro proměnné s názvem `v` typu `concurrent_vector`, výraz `&v[0]+2` vytváří nedefinované chování.  
  
-   `concurrent_vector` Třída definuje [grow_by –](reference/concurrent-vector-class.md#grow_by) a [grow_to_at_least –](reference/concurrent-vector-class.md#grow_to_at_least) metody. Tyto metody vypadat [změnit velikost](reference/concurrent-vector-class.md#resize) metoda, s tím rozdílem, že jsou bezpečné pro souběžnosti.  
  
-   A `concurrent_vector` objekt není přemístit jeho prvky, pokud k němu připojí nebo jeho velikost. To umožňuje existující ukazatelů a iterátory zůstává v platnosti během souběžných operací.  
  
-   Modul runtime nedefinuje specializovanou verzi `concurrent_vector` pro typ `bool`.  
  
###  <a name="vector-safety"></a>Operace bezpečné souběžnosti  
 Všechny metody, které se připojí k nebo zvětšete velikost `concurrent_vector` objektu nebo přístup k elementu v `concurrent_vector` objektu, jsou bezpečné souběžnosti. Výjimka, která má toto pravidlo je `resize` metoda.  
  
 Následující tabulka uvádí nejběžnější `concurrent_vector` metody a operátory, které jsou bezpečné pro souběžnosti.  
  
||||  
|-|-|-|  

|[v](reference/concurrent-vector-class.md#at)|[end](reference/concurrent-vector-class.md#end)|[operátor &#91; &#93;](reference/concurrent-vector-class.md#operator_at)|  
|[Začněte](reference/concurrent-vector-class.md#begin)|[přední](reference/concurrent-vector-class.md#front)|[push_back –](reference/concurrent-vector-class.md#push_back)|  
|[zpět](reference/concurrent-vector-class.md#back)|[grow_by –](reference/concurrent-vector-class.md#grow_by)|[rbegin –](reference/concurrent-vector-class.md#rbegin)|  
|[kapacita](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least –](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|  
|[prázdný](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[velikost](reference/concurrent-vector-class.md#size)|  

  
 Operace, které poskytuje modul runtime pro kompatibilitu s standardní knihovny C++, například `reserve`, nejsou bezpečné souběžnosti. V následující tabulce jsou uvedeny běžné metody a operátory, které nejsou bezpečné souběžnosti.  
  
|||  
|-|-|  

|[přiřadit](reference/concurrent-vector-class.md#assign)|[rezervovat](reference/concurrent-vector-class.md#reserve)|  
|[Vymazat](reference/concurrent-vector-class.md#clear)|[Změna velikosti](reference/concurrent-vector-class.md#resize)|  
|[operátor =](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit –](reference/concurrent-vector-class.md#shrink_to_fit)|  
  
 Operace, které změňte hodnotu stávající elementy nejsou bezpečné souběžnosti. Například použít objekt synchronizace [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) objekt, který chcete synchronizovat souběžných pro čtení a operací zápisu na stejný datový prvek. Další informace o objektech synchronizace najdete v tématu [synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md).  
  
 Při převodu existující kód, který používá `vector` používat `concurrent_vector`, souběžných operací může způsobit chování vaší aplikace, chcete-li změnit. Zvažte například následující program, který současně provádí dvě úlohy `concurrent_vector` objektu. První úlohou připojí další prvky k `concurrent_vector` objektu. V druhé úloze vypočítá součet všech elementů ve stejném objektu.  
  
 [!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]  
  

 I když `end` metoda je souběžnosti bezpečných souběžných volání [push_back –](reference/concurrent-vector-class.md#push_back) metoda způsobí, že hodnota, kterou vrátí `end` změnit. Počet elementů, které překračují iteraci je neurčitou. Tento program proto může vytvářet různé výsledek pokaždé, když ji spustit.  
  
###  <a name="vector-exceptions"></a>Bezpečnost výjimek  
 Pokud operace růstu nebo přiřazení vyvolá výjimku, stav `concurrent_vector` se objekt stane neplatným. Chování `concurrent_vector` není definován objekt, který je v neplatném stavu, pokud není uvedeno jinak. Však destruktoru vždycky uvolní paměť, která objekt přiděluje, i v případě, že objekt je v neplatném stavu.  
  
 Datový typ elementů vektorové `T`, musí splňovat následující požadavky. V opačném chování `concurrent_vector` třída není definován.  
  
-   Destruktoru nesmí výjimku.  
  
-   Pokud výchozí nebo kopírování konstruktoru vyvolá, nesmí deklarovat destruktoru pomocí `virtual` – klíčové slovo a musí fungovat správně s pamětí inicializovat nula.  
  
 [[Horní](#top)]  
  
##  <a name="queue"></a>concurrent_queue – třída  
 [Concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) třídy, podobně jako [std::queue](../../standard-library/queue-class.md) třídy, vám umožní přístup k jeho dopředu a zpět elementy. `concurrent_queue` Třída umožňuje bezpečné souběžnosti zařazování a dequeue – operace. `concurrent_queue` Třída rovněž poskytuje podporu iterator, která není bezpečná souběžnosti.  
  
###  <a name="queue-differences"></a>Rozdíly mezi concurrent_queue a fronty  
 `concurrent_queue` Třída podobá `queue` třídy. Následující body ilustrují, kde `concurrent_queue` se liší od `queue`:  
  
-   Zařazování a dequeue – operací na `concurrent_queue` objekt jsou bezpečné souběžnosti.  
  
-   `concurrent_queue` Třída poskytuje podporu iterator, která není bezpečná souběžnosti.  
  

-   `concurrent_queue` Třída neposkytuje `front` nebo `pop` metody. `concurrent_queue` Třída nahradí tyto metody definováním [try_pop –](reference/concurrent-queue-class.md#try_pop) metoda.  
  
-   `concurrent_queue` Třída neposkytuje `back` metoda. Proto nemůže odkazovat na konec fronty.  
  
-   `concurrent_queue` Třída poskytuje [unsafe_size –](reference/concurrent-queue-class.md#unsafe_size) metoda místo `size` metoda. `unsafe_size` Metoda není bezpečná souběžnosti.  

  
###  <a name="queue-safety"></a>Operace bezpečné souběžnosti  
 Všechny metody této zařadit do nebo dequeue – z `concurrent_queue` objekt jsou bezpečné souběžnosti.  
  
 Následující tabulka uvádí nejběžnější `concurrent_queue` metody a operátory, které jsou bezpečné pro souběžnosti.  
  
|||  
|-|-|  
|[prázdný](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|  
|[get_allocator –](reference/concurrent-queue-class.md#get_allocator)|[try_pop –](reference/concurrent-queue-class.md#try_pop)|  


  
 I když `empty` metoda je souběžnosti bezpečný, souběžná operace může způsobit fronty zvětšení nebo zmenšení před `empty` metoda vrátí.  
  
 V následující tabulce jsou uvedeny běžné metody a operátory, které nejsou bezpečné souběžnosti.  
  
|||  
|-|-|  
|[Vymazat](reference/concurrent-queue-class.md#clear)|[unsafe_end –](reference/concurrent-queue-class.md#unsafe_end)|  
|[unsafe_begin –](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size –](reference/concurrent-queue-class.md#unsafe_size)|  


  
###  <a name="queue-iterators"></a>Podpora iterátorů  
 `concurrent_queue` Poskytuje iterátory, které nejsou bezpečné souběžnosti. Doporučujeme použít tyto iterátory pouze pro ladění.  
  
 A `concurrent_queue` iterator prochází směrem dopředu pouze elementy. Následující tabulka uvádí operátory, že každý iterator podporuje.  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[Operator ++](http://msdn.microsoft.com/en-us/4cfdd07e-927a-42f8-aaa0-d6881687f413)|Přejde k další položky ve frontě. Tento operátor. je přetížena zajistit sémantiku přírůstek před a po přírůstku.|  
|[operátor *](http://msdn.microsoft.com/en-us/a0e671fc-76e6-4fb4-b95c-ced4dd2b2017)|Načte odkaz s aktuální položkou.|  
|[-> – operátor](http://msdn.microsoft.com/en-us/41fa393d-ae1e-4a38-bb4b-19e8df709ca9)|Načte ukazatel s aktuální položkou.|  
  
 [[Horní](#top)]  
  
##  <a name="unordered_map"></a>concurrent_unordered_map – třída  
 [HYPERLINK "file:///C:\\\Users\\\thompet\\\AppData\\\Local\\\Temp\\\DxEditor\\\DduePreview\\\Default \\\798d7037-df37-4310-858b-6f590bbf6ebf\\\HTM\\\html\\\a217b4ac-af2b-4d41-94eb-09a75ee28622 "concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) třída je Třída asociativní kontejneru, který stejně jako [std::unordered_map](../../standard-library/unordered-map-class.md) třídy, ovládací prvky různých délka posloupnost elementy typu [std::pair\<const klíč, Ty >](../../standard-library/pair-structure.md). Neseřazený mapy si můžete představit jako slovník, který můžete přidat dvojici klíč a hodnotu do nebo najít hodnotu podle klíče. Tato třída je užitečná, když máte více vláken nebo úlohy, které mají přístup k kontejner sdílené souběžně, vložte do něj nebo jej aktualizovat.  
  
 Následující příklad ukazuje, využít základní strukturu pro používání `concurrent_unordered_map`. Tento příklad vloží znak klíče v rozsahu ['a', ' i']. Protože neurčená pořadí operací, je také neurčená konečná hodnota pro každý klíč. Je však bezpečné provést vložení paralelně.  
  
 [!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]  
  
 Pro příklad, který používá `concurrent_unordered_map` provést mapu a snížit operace paralelně najdete v tématu [postup: provedení mapy a snížit operace paralelně](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).  
  
###  <a name="map-differences"></a>Rozdíly mezi concurrent_unordered_map a unordered_map  
 `concurrent_unordered_map` Třída podobá `unordered_map` třídy. Následující body ilustrují, kde `concurrent_unordered_map` se liší od `unordered_map`:  
  
-   `erase`, `bucket`, `bucket_count`, A `bucket_size` metody jsou pojmenované `unsafe_erase`, `unsafe_bucket`, `unsafe_bucket_count`, a `unsafe_bucket_size`, v uvedeném pořadí. `unsafe_` Zásady vytváření názvů označuje, že tyto metody není bezpečné souběžnosti. Další informace o zabezpečení souběžného zpracování najdete v tématu [operace souběžnosti bezpečné](#map-safety).  
  
-   Operace INSERT není zneplatnit existující ukazatele nebo iterátory, ani se změnit pořadí položek, které již existují v mapě. Vložení a procházení operations dochází současně.  
  
-   `concurrent_unordered_map`podporuje předávání pouze iterací.  
  
-   Vložení zneplatnit nebo aktualizovat iterátory, které se vrátí pomocí `equal_range`. Vložení můžete připojit nerovné položky na konec rozsahu. Begin iterator odkazuje na položku stejné.  
  
 Abyste se vyhnuli zablokování, žádná metoda `concurrent_unordered_map` obsahuje zámek při volání přidělení paměti, funkce hash nebo jiný kód, uživatelem definované. Navíc je nutné zajistit, že funkce hash vždy vyhodnotí rovna klíči na stejnou hodnotu. Nejlepší funkce hash distribuci klíčů jednotně prostoru kód hash.  
  
###  <a name="map-safety"></a>Operace bezpečné souběžnosti  
 `concurrent_unordered_map` Třída umožňuje operace insert a element přístup bezpečných souběžnosti. Operace INSERT není zneplatnit existující ukazatele nebo iterátory. Iterator přístup a traversal operace jsou také bezpečných souběžnosti. V následující tabulce jsou běžně používané `concurrent_unordered_map` metody a operátory, které jsou bezpečné pro souběžnosti.  
  
|||||  
|-|-|-|-|  
|[v](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq –](reference/concurrent-unordered-map-class.md#key_eq)|  
|`begin`|`empty`|`get_allocator`|`max_size`|  
|`cbegin`|`end`|`hash_function`|[operátor &#91; &#93;](reference/concurrent-unordered-map-class.md#operator_at)|  
|`cend`|`equal_range`|[Vložení](reference/concurrent-unordered-map-class.md#insert)|`size`|  
  
 I když `count` nelze volat metodu bezpečně z souběžně běžících vláken, různých vláknech může přijímat odlišné výsledky, pokud nová hodnota je současně vloženy do kontejneru.  
  
 V následující tabulce jsou běžně používané metody a operátory, které nejsou bezpečné souběžnosti.  
  
||||  
|-|-|-|  
|`clear`|`max_load_factor`|`rehash`|  
|`load_factor`|[operátor =](reference/concurrent-unordered-map-class.md#operator_eq) 


  
 Kromě těchto metod libovolné metody, začíná `unsafe_` není také bezpečných souběžnosti.  
  
 [[Horní](#top)]  
  
##  <a name="unordered_multimap"></a>concurrent_unordered_multimap – třída  
 [Concurrency::concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) třída podobá `concurrent_unordered_map` třídy s tím rozdílem, že umožňuje pro více hodnot pro mapování na stejný klíč. Se také liší od `concurrent_unordered_map` následujícími způsoby:  
  
-   [Concurrent_unordered_multimap::Insert –](reference/concurrent-unordered-multimap-class.md#insert) metoda vrátí iterovat místo `std::pair<iterator, bool>`.  

  
-   `concurrent_unordered_multimap` Třída neposkytuje `operator[]` ani `at` metoda.  
  
 Následující příklad ukazuje, využít základní strukturu pro používání `concurrent_unordered_multimap`. Tento příklad vloží znak klíče v rozsahu ['a', ' i']. `concurrent_unordered_multimap`umožňuje klíč do mají více hodnot.  
  
 [!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]  
  
 [[Horní](#top)]  
  
##  <a name="unordered_set"></a>concurrent_unordered_set – třída  
 [Concurrency::concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) třída podobá `concurrent_unordered_map` třídy s tím rozdílem, že spravuje hodnoty místo páry klíč-hodnota. `concurrent_unordered_set` Třída neposkytuje `operator[]` ani `at` metoda.  
  
 Následující příklad ukazuje, využít základní strukturu pro používání `concurrent_unordered_set`. Tento příklad vloží znak hodnoty v rozsahu ['a', ' i']. Je bezpečné provést vložení paralelně.  
  
 [!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]  
  
 [[Horní](#top)]  
  
##  <a name="unordered_multiset"></a>concurrent_unordered_multiset – třída  
 [Concurrency::concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) třída podobá `concurrent_unordered_set` třídy s tím rozdílem, že umožňuje duplicitní hodnoty. Se také liší od `concurrent_unordered_set` následujícími způsoby:  
  

-   [Concurrent_unordered_multiset::Insert –](reference/concurrent-unordered-multiset-class.md#insert) metoda vrátí iterovat místo `std::pair<iterator, bool>`.  

  
-   `concurrent_unordered_multiset` Třída neposkytuje `operator[]` ani `at` metoda.  
  
 Následující příklad ukazuje, využít základní strukturu pro používání `concurrent_unordered_multiset`. Tento příklad vloží znak hodnoty v rozsahu ['a', ' i']. `concurrent_unordered_multiset`umožňuje hodnotu do více než jednou.  
  
 [!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]  
  
 [[Horní](#top)]  
  
##  <a name="combinable"></a>combinable – třída  
 [Concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třída poskytuje opakovaně použitelný, místní úložiště, které vám umožní provádět podrobné výpočty a pak sloučit těchto výpočtů do konečný výsledek. Si můžete představit `combinable` objektu jako redukční proměnnou.  
  
 `combinable` Třída je užitečná v případě, že máte na prostředek, který sdílí několik vláken nebo úlohy. `combinable` Třída pomáhá eliminovat sdíleného stavu tím, že poskytuje přístup ke sdíleným prostředkům způsobem uvolnění zámku. Proto tato třída poskytuje alternativu k použití synchronizační mechanismus, například mutex synchronizovat přístup ke sdíleným datům z více vláken.  
  
###  <a name="combinable-features"></a>Metody a funkce  
 V následující tabulce jsou uvedeny některé důležité metody `combinable` třídy. Další informace o všech `combinable` metody třídy najdete v tématu [combinable – třída](../../parallel/concrt/reference/combinable-class.md).  
  
|Metoda|Popis|  
|------------|-----------------|  
|[místní](reference/combinable-class.md#local)|Získá odkaz na místní proměnné, která souvisí s aktuálním kontextu přístup z více vláken.|  
|[Vymazat](reference/combinable-class.md#clear)|Odebere všechny lokální proměnné vláken z `combinable` objektu.|  
|[kombinování](reference/combinable-class.md#combine)<br /><br /> [combine_each –](reference/combinable-class.md#combine_each)|Zadané kombinační funkcí používá ke generování konečná hodnota ze sady všechny místní výpočty.|  
  
 `combinable` Třída je šablona třídu, která je na konečný výsledek sloučené s parametry. Pokud volat výchozí konstruktor `T` typ parametru šablony musí mít výchozí konstruktor a kopírovacího konstruktoru. Pokud `T` typ šablony parametr nemá výchozí konstruktor, volání přetížené verzi konstruktor, který přebírá inicializační funkce jako jeho parametr.  
  
 Další data v můžete uložit `combinable` objektu po zavolání metody [kombinovat](reference/combinable-class.md#combine) nebo [combine_each –](reference/combinable-class.md#combine_each) metody. Můžete také zavolat `combine` a `combine_each` metody vícekrát. Pokud žádná místní hodnota v `combinable` objektu změny, `combine` a `combine_each` metody pokaždé, když jsou volány vytvořila stejný výsledek.  
  
###  <a name="combinable-examples"></a>Příklady  
 Příklady týkající se použití `combinable` třídy, najdete v následujících tématech:  
  
-   [Postupy: Použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
  
-   [Postupy: Použití objektu combinable ke slučování množin](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
  
 [[Horní](#top)]  
  
## <a name="related-topics"></a>Související témata  
 [Postupy: Použití paralelních kontejnerů ke zvýšení účinnosti](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)  
 Ukazuje způsob použití paralelních kontejnerů ke efektivně ukládat a přistupovat k datům paralelně.  
  
 [Postupy: Použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
 Ukazuje, jak používat `combinable` třídy eliminovat sdíleného stavu a tak zlepšit výkon.  
  
 [Postupy: Použití objektu combinable ke slučování množin](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
 Ukazuje, jak používat `combine` funkce Sloučit místní datových sad.  
  
 [Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)  
 Popisuje PPL, která poskytuje imperativní programovací model, který zvýší úroveň škálovatelnost a snadné použití pro vývoj souběžných aplikací.  
  
## <a name="reference"></a>Odkaz  
 [concurrent_vector – třída](../../parallel/concrt/reference/concurrent-vector-class.md)  
  
 [concurrent_queue – třída](../../parallel/concrt/reference/concurrent-queue-class.md)  
  
 [concurrent_unordered_map – třída](../../parallel/concrt/reference/concurrent-unordered-map-class.md)  
  
 [concurrent_unordered_multimap – třída](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)  
  
 [concurrent_unordered_set – třída](../../parallel/concrt/reference/concurrent-unordered-set-class.md)  
  
 [concurrent_unordered_multiset – třída](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)  
  
 [combinable – třída](../../parallel/concrt/reference/combinable-class.md)
