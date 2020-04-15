---
title: Paralelní kontejnery a objekty
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: f3fb2bb57c8bcf65de0a7f74f2992050d8257429
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363047"
---
# <a name="parallel-containers-and-objects"></a>Paralelní kontejnery a objekty

Knihovna paralelních vzorů (PPL) obsahuje několik kontejnerů a objektů, které poskytují přístup k jejich prvkům bezpečnýpro přístup zvícen.

*Souběžný kontejner* poskytuje bezpečný přístup k nejdůležitějším operacím. Zde jsou vždy platné ukazatele bezpečné pro souběžnost nebo iterátory. Není to záruka inicializace prvku nebo konkrétního pořadí průchodu. Funkce těchto kontejnerů se podobá těm, které jsou k dispozici standardní knihovny C++. Například [třída concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) připomíná třídu [std::vector](../../standard-library/vector-class.md) s `concurrent_vector` tím rozdílem, že třída umožňuje paralelní připojovat prvky. Souběžné kontejnery použijte, pokud máte paralelní kód, který vyžaduje přístup pro čtení i zápis do stejného kontejneru.

*Souběžný objekt* je sdílen souběžně mezi součástmi. Proces, který vypočítá stav souběžného objektu paralelně vytváří stejný výsledek jako jiný proces, který vypočítá stejný stav sériově. [Souběžnost::kombinovatelná](../../parallel/concrt/reference/combinable-class.md) třída je jedním z příkladů typu souběžného objektu. Třída `combinable` umožňuje provádět výpočty paralelně a pak kombinovat tyto výpočty do konečného výsledku. Souběžné objekty použijte v případě, že byste jinak použili mechanismus synchronizace, například mutex, k synchronizaci přístupu ke sdílené proměnné nebo prostředku.

## <a name="sections"></a><a name="top"></a>Oddíly

Toto téma podrobně popisuje následující paralelní kontejnery a objekty.

Souběžné kontejnery:

- [concurrent_vector třída](#vector)

  - [Rozdíly mezi concurrent_vector a vektorem](#vector-differences)

  - [Provoz bezpečný pro souběžnost](#vector-safety)

  - [Bezpečnost výjimek](#vector-exceptions)

- [concurrent_queue – třída](#queue)

  - [Rozdíly mezi concurrent_queue a frontou](#queue-differences)

  - [Provoz bezpečný pro souběžnost](#queue-safety)

  - [Podpora iterátoru](#queue-iterators)

- [concurrent_unordered_map třída](#unordered_map)

  - [Rozdíly mezi concurrent_unordered_map a unordered_map](#map-differences)

  - [Provoz bezpečný pro souběžnost](#map-safety)

- [concurrent_unordered_multimap – třída](#unordered_multimap)

- [concurrent_unordered_set – třída](#unordered_set)

- [concurrent_unordered_multiset třída](#unordered_multiset)

Souběžné objekty:

- [combinable – třída](#combinable)

  - [Metody a funkce](#combinable-features)

  - [Příklady](#combinable-examples)

## <a name="concurrent_vector-class"></a><a name="vector"></a>concurrent_vector třída

[Souběžnost::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) třída je třída kontejneru sekvence, která, stejně jako [třída std::vector,](../../standard-library/vector-class.md) umožňuje náhodný přístup k jejím prvkům. Třída `concurrent_vector` umožňuje souběžnost bezpečné připojení a operace přístupu k elementu. Připojit operace nezneplatňují existující ukazatele nebo iterátory. Iterator přístup a traversal operace jsou také bezpečné souběžnosti. Zde jsou vždy platné ukazatele bezpečné pro souběžnost nebo iterátory. Není to záruka inicializace prvku nebo konkrétního pořadí průchodu.

### <a name="differences-between-concurrent_vector-and-vector"></a><a name="vector-differences"></a>Rozdíly mezi concurrent_vector a vektorem

Třída `concurrent_vector` se velmi `vector` podobá třídě. Složitost připojení, přístup k prvku a iterátor přístup `concurrent_vector` operace na objekt jsou `vector` stejné jako pro objekt. Následující body ilustrují, kde `concurrent_vector` se liší od `vector`:

- Připojit, přístup k prvku, iterátor přístup a iterátor `concurrent_vector` traversal operace na objektu jsou bezpečné souběžnosti.

- Prvky můžete přidat pouze na `concurrent_vector` konec objektu. Třída `concurrent_vector` neposkytuje metodu. `insert`

- Objekt `concurrent_vector` nepoužívá [přesunout sémantiku](../../cpp/rvalue-reference-declarator-amp-amp.md) při připojení k němu.

- Třída `concurrent_vector` neposkytuje metody `erase` `pop_back` or. Stejně `vector`jako v případě , použijte `concurrent_vector` [metodu clear](reference/concurrent-vector-class.md#clear) k odstranění všech prvků z objektu.

- Třída `concurrent_vector` neukládá své prvky souvisle v paměti. Proto nelze použít `concurrent_vector` třídu ve všech způsobech, které můžete použít pole. Například pro proměnnou `v` pojmenovanou `concurrent_vector` `&v[0]+2` typu výraz vytváří nedefinované chování.

- Třída `concurrent_vector` definuje [metody grow_by](reference/concurrent-vector-class.md#grow_by) a [grow_to_at_least.](reference/concurrent-vector-class.md#grow_to_at_least) Tyto metody se podobají metodě [změny velikosti](reference/concurrent-vector-class.md#resize) s tím rozdílem, že jsou bezpečné pro souběžnost.

- Objekt `concurrent_vector` nepřemístí jeho prvky, když k němu připojíte nebo změníte jeho velikost. To umožňuje existující ukazatele a iterátory zůstat v platnosti během souběžných operací.

- Runtime nedefinuje specializovanou verzi `concurrent_vector` pro `bool`typ .

### <a name="concurrency-safe-operations"></a><a name="vector-safety"></a>Provoz bezpečný pro souběžnost

Všechny metody, které se připojují nebo zvětšit velikost objektu `concurrent_vector` nebo přístup k prvku v objektu, `concurrent_vector` jsou bezpečné souběžnosti. Zde jsou vždy platné ukazatele bezpečné pro souběžnost nebo iterátory. Není to záruka inicializace prvku nebo konkrétního pořadí průchodu. Výjimkou z tohoto pravidla `resize` je metoda.

V následující tabulce `concurrent_vector` jsou uvedeny běžné metody a operátory, které jsou bezpečné pro souběžnost.

||||
|-|-|-|
|[Na](reference/concurrent-vector-class.md#at)|[Konec](reference/concurrent-vector-class.md#end)|[operátor&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|
|[Začít](reference/concurrent-vector-class.md#begin)|[Přední](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[Zpět](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|
|[capacity](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|
|[empty](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[Velikost](reference/concurrent-vector-class.md#size)|

Operace, které runtime poskytuje kompatibilitu s c++ `reserve`standardní knihovny, například , nejsou bezpečné souběžnosti. V následující tabulce jsou uvedeny běžné metody a operátory, které nejsou bezpečné pro souběžnost.

|||
|-|-|
|[Přiřadit](reference/concurrent-vector-class.md#assign)|[Rezervy](reference/concurrent-vector-class.md#reserve)|
|[Jasné](reference/concurrent-vector-class.md#clear)|[Změnit velikost](reference/concurrent-vector-class.md#resize)|
|[operátor =](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

Operace, které mění hodnotu existujících prvků, nejsou bezpečné pro souběžnost. Pomocí objektu synchronizace, například [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) objektu, synchronizujte souběžné operace čtení a zápisu se stejným datovým prvkem. Další informace o objektech synchronizace naleznete v [tématu Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md).

Při převodu existující `vector` kód, `concurrent_vector`který používá k použití , souběžné operace může způsobit chování aplikace změnit. Zvažte například následující program, který současně provádí `concurrent_vector` dva úkoly na objektu. První úkol připojí další prvky k objektu. `concurrent_vector` Druhý úkol vypočítá součet všech prvků ve stejném objektu.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

Přestože `end` metoda je bezpečné souběžnosti, souběžné volání [push_back](reference/concurrent-vector-class.md#push_back) metoda způsobí, `end` že hodnota, která je vrácena změnit. Počet prvků, které iterátor prochází je neurčitý. Proto tento program může produkovat jiný výsledek při každém spuštění. Pokud je typ prvku netriviální, je možné, že mezi `push_back` `end` nimi existuje spor a volání. Metoda `end` může vrátit prvek, který je přidělen, ale není plně inicializován.

### <a name="exception-safety"></a><a name="vector-exceptions"></a>Bezpečnost výjimek

Pokud operace růstu nebo přiřazení vyvolá výjimku, stav objektu `concurrent_vector` se stane neplatným. Chování objektu, `concurrent_vector` který je v neplatném stavu, není definováno, pokud není uvedeno jinak. Destruktor však vždy uvolní paměť, kterou objekt přiděluje, i když je objekt v neplatném stavu.

Datový typ vektorových prvků `T`, musí splňovat následující požadavky. V opačném případě `concurrent_vector` chování třídy není definováno.

- Destruktor nesmí házet.

- Pokud výchozí nebo copy konstruktor vyvolá, destruktor nesmí `virtual` být deklarován pomocí klíčového slova a musí pracovat správně s nulovou inicializovanou pamětí.

[[Nahoře]](#top)

## <a name="concurrent_queue-class"></a><a name="queue"></a>concurrent_queue třída

[Souběžnost::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) třídy, stejně jako [std::queue](../../standard-library/queue-class.md) třídy, umožňuje přístup k jeho přední a zadní prvky. Třída `concurrent_queue` umožňuje souběžnost bezpečné fronty a dequeue operace. Zde jsou vždy platné ukazatele bezpečné pro souběžnost nebo iterátory. Není to záruka inicializace prvku nebo konkrétního pořadí průchodu. Třída `concurrent_queue` také poskytuje podporu iterátoru, který není bezpečné souběžnosti.

### <a name="differences-between-concurrent_queue-and-queue"></a><a name="queue-differences"></a>Rozdíly mezi concurrent_queue a frontou

Třída `concurrent_queue` se velmi `queue` podobá třídě. Následující body ilustrují, kde `concurrent_queue` se liší od `queue`:

- Operace zařazení do fronty `concurrent_queue` a vyřazení objektu do fronty jsou bezpečné pro souběžnost.

- Třída `concurrent_queue` poskytuje iterator podporu, která není bezpečné souběžnosti.

- Třída `concurrent_queue` neposkytuje metody `front` `pop` or. Třída `concurrent_queue` nahrazuje tyto metody definováním [try_pop](reference/concurrent-queue-class.md#try_pop) metody.

- Třída `concurrent_queue` neposkytuje metodu. `back` Proto nelze odkazovat na konec fronty.

- Třída `concurrent_queue` poskytuje [metodu unsafe_size](reference/concurrent-queue-class.md#unsafe_size) `size` namísto metody. Metoda `unsafe_size` není bezpečné souběžnosti.

### <a name="concurrency-safe-operations"></a><a name="queue-safety"></a>Provoz bezpečný pro souběžnost

Všechny metody, které zařazují nebo dequeue z objektu `concurrent_queue` jsou bezpečné souběžnosti. Zde jsou vždy platné ukazatele bezpečné pro souběžnost nebo iterátory. Není to záruka inicializace prvku nebo konkrétního pořadí průchodu.

V následující tabulce `concurrent_queue` jsou uvedeny běžné metody a operátory, které jsou bezpečné pro souběžnost.

|||
|-|-|
|[empty](reference/concurrent-queue-class.md#empty)|[Push](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

Přestože `empty` metoda je bezpečné souběžnosti, souběžná operace může způsobit fronty `empty` zvětšit nebo zmenšit před vrátí metoda.

V následující tabulce jsou uvedeny běžné metody a operátory, které nejsou bezpečné pro souběžnost.

|||
|-|-|
|[Jasné](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

### <a name="iterator-support"></a><a name="queue-iterators"></a>Podpora iterátoru

Poskytuje `concurrent_queue` iterátory, které nejsou bezpečné souběžnosti. Doporučujeme použít tyto iterátory pouze pro ladění.

Iterátor `concurrent_queue` prochází prvky pouze ve směru dopředu. V následující tabulce jsou uvedeny operátory, které každý iterátor podporuje.

|Operátor|Popis|
|--------------|-----------------|
|`operator++`|Přejde na další položku ve frontě. Tento operátor je přetížena poskytnout sémantiku před přírůstkem i po přírůstku.|
|`operator*`|Načte odkaz na aktuální položku.|
|`operator->`|Načte ukazatel na aktuální položku.|

[[Nahoře]](#top)

## <a name="concurrent_unordered_map-class"></a><a name="unordered_map"></a>concurrent_unordered_map třída

[Souběžnost::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) třída je asociativní třída kontejneru, která, stejně jako [std::unordered_map](../../standard-library/unordered-map-class.md) třídy, řídí posloupnost různých délek prvků typu [std::pair\<const Key, Ty>](../../standard-library/pair-structure.md). Neuspořádanou mapu si můžete zamyslet jako slovník, do kterého můžete přidat dvojici klíčů a hodnot nebo vyhledat hodnotu podle klíče. Tato třída je užitečná, pokud máte více vláken nebo úkolů, které mají současně přístup ke sdílenému kontejneru, vložit do něj nebo aktualizovat.

Následující příklad ukazuje základní strukturu `concurrent_unordered_map`pro použití . Tento příklad vloží klíče znaků do rozsahu ['a', 'i']. Vzhledem k tomu, že pořadí operací není určeno, konečná hodnota pro každý klíč je také neurčena. Je však bezpečné provádět vložení paralelně.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

Příklad, který `concurrent_unordered_map` se používá k provedení mapy a snížit operace paralelně, naleznete v [tématu How to: Perform Map and Reduce Operations in Parallel](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

### <a name="differences-between-concurrent_unordered_map-and-unordered_map"></a><a name="map-differences"></a>Rozdíly mezi concurrent_unordered_map a unordered_map

Třída `concurrent_unordered_map` se velmi `unordered_map` podobá třídě. Následující body ilustrují, kde `concurrent_unordered_map` se liší od `unordered_map`:

- Metody `erase` `bucket`, `bucket_count`, `bucket_size` , `unsafe_erase`a `unsafe_bucket` `unsafe_bucket_count`jsou `unsafe_bucket_size`pojmenovány , , a , v uvedeném pořadí. Konvence `unsafe_` pojmenování označuje, že tyto metody nejsou bezpečné souběžnosti. Další informace o bezpečnosti souběžnosti naleznete v [tématu Operace bezpečné pro souběžnost](#map-safety).

- Operace vložení neruší existující ukazatele nebo iterátory, ani nemění pořadí položek, které již existují v mapě. Operace vložení a procházení mohou nastat souběžně.

- `concurrent_unordered_map`podporuje pouze předsunutou iteraci.

- Vložení nezruší platnost nebo aktualizovat iterátory, které `equal_range`jsou vráceny . Vložení může připojit nerovné položky na konec rozsahu. Počáteční iterátor odkazuje na stejnou položku.

Chcete-li se vyhnout zablokování, žádná metoda drží `concurrent_unordered_map` zámek při volání přidělování paměti, hash funkce nebo jiný kód definovaný uživatelem. Také je nutné zajistit, aby funkce hash vždy vyhodnocuje stejné klíče na stejnou hodnotu. Nejlepší funkce hash distribuují klíče rovnoměrně v prostoru kódu hash.

### <a name="concurrency-safe-operations"></a><a name="map-safety"></a>Provoz bezpečný pro souběžnost

Třída `concurrent_unordered_map` umožňuje operace vkládání a přístupu k prvku bezpečné souběžnosti. Vložení operace nezneplatňují existující ukazatele nebo iterátory. Iterator přístup a traversal operace jsou také bezpečné souběžnosti. Zde jsou vždy platné ukazatele bezpečné pro souběžnost nebo iterátory. Není to záruka inicializace prvku nebo konkrétního pořadí průchodu. V následující tabulce jsou `concurrent_unordered_map` uvedeny běžně používané metody a operátory, které jsou bezpečné pro souběžnost.

|||||
|-|-|-|-|
|[Na](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[operátor&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[Vložit](reference/concurrent-unordered-map-class.md#insert)|`size`|

Přestože `count` metoda může být volána bezpečně ze souběžně spuštěných vláken, různá vlákna mohou přijímat různé výsledky, pokud je současně vložena nová hodnota do kontejneru.

V následující tabulce jsou uvedeny běžně používané metody a operátory, které nejsou bezpečné pro souběžnost.

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[operátor =](reference/concurrent-unordered-map-class.md#operator_eq)

Kromě těchto metod není žádná metoda, `unsafe_` která začíná, také bezpečná pro souběžnost.

[[Nahoře]](#top)

## <a name="concurrent_unordered_multimap-class"></a><a name="unordered_multimap"></a>concurrent_unordered_multimap třída

[Souběžnost::concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) třída se velmi `concurrent_unordered_map` podobá třídě s tím rozdílem, že umožňuje více hodnot mapovat na stejný klíč. To se také `concurrent_unordered_map` liší od následujících způsobů:

- Metoda [concurrent_unordered_multimap::insert](reference/concurrent-unordered-multimap-class.md#insert) vrátí místo `std::pair<iterator, bool>`.

- Třída `concurrent_unordered_multimap` neposkytuje `operator[]` ani `at` metodu.

Následující příklad ukazuje základní strukturu `concurrent_unordered_multimap`pro použití . Tento příklad vloží klíče znaků do rozsahu ['a', 'i']. `concurrent_unordered_multimap`umožňuje klíčmít více hodnot.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[Nahoře]](#top)

## <a name="concurrent_unordered_set-class"></a><a name="unordered_set"></a>concurrent_unordered_set třída

[Souběžnost::concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) třída se velmi `concurrent_unordered_map` podobá třídě s tím rozdílem, že spravuje hodnoty namísto párů klíčů a hodnot. Třída `concurrent_unordered_set` neposkytuje `operator[]` ani `at` metodu.

Následující příklad ukazuje základní strukturu `concurrent_unordered_set`pro použití . Tento příklad vloží hodnoty znaků do rozsahu ['a', 'i']. Je bezpečné provádět vkládání paralelně.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[Nahoře]](#top)

## <a name="concurrent_unordered_multiset-class"></a><a name="unordered_multiset"></a>concurrent_unordered_multiset třída

[Souběžnost::concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) třída se velmi `concurrent_unordered_set` podobá třídě s tím rozdílem, že umožňuje duplicitní hodnoty. To se také `concurrent_unordered_set` liší od následujících způsobů:

- Metoda [concurrent_unordered_multiset::insert](reference/concurrent-unordered-multiset-class.md#insert) vrátí místo `std::pair<iterator, bool>`.

- Třída `concurrent_unordered_multiset` neposkytuje `operator[]` ani `at` metodu.

Následující příklad ukazuje základní strukturu `concurrent_unordered_multiset`pro použití . Tento příklad vloží hodnoty znaků do rozsahu ['a', 'i']. `concurrent_unordered_multiset`umožňuje hodnotu dojít vícekrát.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[Nahoře]](#top)

## <a name="combinable-class"></a><a name="combinable"></a>kombinovatelná třída

[Souběžnost::kombinovatelná](../../parallel/concrt/reference/combinable-class.md) třída poskytuje opakovaně použitelné úložiště místní vlákno, které umožňuje provádět jemně odstupňované výpočty a pak sloučit tyto výpočty do konečného výsledku. `combinable` Objekt si můžete myslet jako proměnnou redukce.

Třída `combinable` je užitečná, pokud máte prostředek, který je sdílen mezi několika vlákny nebo úkoly. Třída `combinable` vám pomůže eliminovat sdílený stav tím, že poskytuje přístup ke sdíleným prostředkům způsobem bez zámku. Proto tato třída poskytuje alternativu k použití mechanismu synchronizace, například mutex, pro synchronizaci přístupu ke sdíleným datům z více vláken.

### <a name="methods-and-features"></a><a name="combinable-features"></a>Metody a funkce

V následující tabulce jsou uvedeny `combinable` některé důležité metody třídy. Další informace o `combinable` všech metodách třídy naleznete v [tématu kombinovatelné Class](../../parallel/concrt/reference/combinable-class.md).

|Metoda|Popis|
|------------|-----------------|
|[Místní](reference/combinable-class.md#local)|Načte odkaz na místní proměnnou, která je přidružena k aktuálnímu kontextu vlákna.|
|[Jasné](reference/combinable-class.md#clear)|Odebere z objektu všechny `combinable` místní proměnné podprocesu.|
|[combine](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Používá zapředpokladu nouzi funkce generovat konečnou hodnotu ze sady všech výpočtů místní vlákno.|

Třída `combinable` je třída šablony, která je parametrizována na konečný sloučený výsledek. Pokud voláte výchozí konstruktor, typ parametru `T` šablony musí mít výchozí konstruktor a konstruktor kopie. Pokud `T` typ parametru šablony nemá výchozí konstruktor, volání přetížené verze konstruktoru, který má funkci inicializace jako jeho parametr.

Další data můžete uložit `combinable` do objektu po volání [metody kombinovat](reference/combinable-class.md#combine) nebo [combine_each.](reference/combinable-class.md#combine_each) Můžete také volat `combine` `combine_each` a metody vícekrát. Pokud se nezmění `combinable` žádná místní `combine` hodnota `combine_each` v objektu, metody a vytvoří stejný výsledek pokaždé, když jsou volány.

### <a name="examples"></a><a name="combinable-examples"></a>Příklady

Příklady použití třídy `combinable` naleznete v následujících tématech:

- [Postupy: Použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [Postupy: Použití objektu combinable ke slučování množin](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[Nahoře]](#top)

## <a name="related-topics"></a>Související témata

[Postupy: Použití paralelních kontejnerů ke zvýšení účinnosti](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
Ukazuje, jak používat paralelní kontejnery efektivně ukládat a přistupovat k datům paralelně.

[Postupy: Použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
Ukazuje, jak `combinable` pomocí třídy eliminovat sdílený stav a tím zlepšit výkon.

[Postupy: Použití objektu combinable ke slučování množin](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
Ukazuje, jak `combine` pomocí funkce sloučit místní sady dat podprocesu.

[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Popisuje PPL, který poskytuje imperativní programovací model, který podporuje škálovatelnost a snadnost použití pro vývoj souběžných aplikací.

## <a name="reference"></a>Referenční informace

[concurrent_vector třída](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue – třída](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map třída](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap – třída](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set – třída](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset třída](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[combinable – třída](../../parallel/concrt/reference/combinable-class.md)
