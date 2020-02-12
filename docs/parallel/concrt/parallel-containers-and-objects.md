---
title: Paralelní kontejnery a objekty
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: 04b38fdc66a5c37a1780deaae4ae165f63238d93
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142908"
---
# <a name="parallel-containers-and-objects"></a>Paralelní kontejnery a objekty

Knihovna PPL (Parallel Patterns Library) obsahuje několik kontejnerů a objektů, které poskytují přístup pro přístup z více vláken ke svým prvkům.

*Souběžný kontejner* poskytuje přístup k nejdůležitějším operacím bez obav. V případě bezpečného zpracování v souběžnosti znamená, že ukazatele nebo iterátory jsou vždy platné. Není zárukou pro inicializaci elementu nebo z konkrétního pořadí procházení. Funkce těchto kontejnerů se podobá těm, které jsou k dispozici ve C++ standardní knihovně. Například třída [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) se podobá třídě [std:: Vector](../../standard-library/vector-class.md) s tím rozdílem, že třída `concurrent_vector` umožňuje připojit prvky paralelně. Pokud máte paralelní kód, který vyžaduje přístup pro čtení i zápis ke stejnému kontejneru, používejte Souběžné kontejnery.

*Souběžný objekt* se sdílí současně mezi komponentami. Proces, který vypočítá stav souběžného objektu paralelně vytvoří stejný výsledek jako jiný proces, který počítá stejný stav sériového stavu. Třída [Concurrency::](../../parallel/concrt/reference/combinable-class.md) kombinovat je jedním z příkladů souběžného typu objektu. Třída `combinable` umožňuje paralelní provádění výpočtů a pak tyto výpočty kombinovat do konečného výsledku. Souběžné objekty použijte, pokud byste jinak použili synchronizační mechanismus, například mutex, k synchronizaci přístupu ke sdílené proměnné nebo prostředku.

## <a name="top"></a>Řezů

V tomto tématu jsou podrobněji popsány následující paralelní kontejnery a objekty.

Souběžné kontejnery:

- [concurrent_vector – třída](#vector)

   - [Rozdíly mezi concurrent_vector a vektorem](#vector-differences)

   - [Operace bezpečné pro souběžnost](#vector-safety)

   - [Zabezpečení výjimek](#vector-exceptions)

- [concurrent_queue – třída](#queue)

   - [Rozdíly mezi concurrent_queue a frontou](#queue-differences)

   - [Operace bezpečné pro souběžnost](#queue-safety)

   - [Podpora iterátoru](#queue-iterators)

- [concurrent_unordered_map – třída](#unordered_map)

   - [Rozdíly mezi concurrent_unordered_map a unordered_map](#map-differences)

   - [Operace bezpečné pro souběžnost](#map-safety)

- [concurrent_unordered_multimap – třída](#unordered_multimap)

- [concurrent_unordered_set – třída](#unordered_set)

- [concurrent_unordered_multiset – třída](#unordered_multiset)

Souběžné objekty:

- [combinable – třída](#combinable)

   - [Metody a funkce](#combinable-features)

   - [Příklady](#combinable-examples)

## <a name="vector"></a>concurrent_vector – třída

Třída [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) je třída kontejneru sekvence, která, stejně jako třída [std:: Vector](../../standard-library/vector-class.md) , umožňuje náhodný přístup k jeho prvkům. Třída `concurrent_vector` povoluje operace připojení v rámci souběžného zpracování a operace přístupu k prvkům. Operace připojení neověřuje existující ukazatele nebo iterátory. Přístup iterátoru a operace procházení také jsou bezpečné pro souběžnost. V případě bezpečného zpracování v souběžnosti znamená, že ukazatele nebo iterátory jsou vždy platné. Není zárukou pro inicializaci elementu nebo z konkrétního pořadí procházení.

### <a name="vector-differences"></a>Rozdíly mezi concurrent_vector a vektorem

Třída `concurrent_vector` úzce připomíná třídu `vector`. Složitost připojení, přístupu k prvkům a operace přístupu iterátoru na objekt `concurrent_vector` jsou stejné jako u objektu `vector`. Následující body znázorňují, kde se `concurrent_vector` liší od `vector`:

- Připojení, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru u objektu `concurrent_vector` jsou bezpečné pro souběžnost.

- Prvky lze přidat pouze na konec objektu `concurrent_vector`. Třída `concurrent_vector` neposkytuje metodu `insert`.

- Objekt `concurrent_vector` nepoužívá [sémantiku přesunutí](../../cpp/rvalue-reference-declarator-amp-amp.md) při připojení k objektu.

- Třída `concurrent_vector` neposkytuje metody `erase` nebo `pop_back`. Stejně jako u `vector`použijte metodu [clear](reference/concurrent-vector-class.md#clear) k odebrání všech prvků z objektu `concurrent_vector`.

- Třída `concurrent_vector` neukládá své prvky souvisle do paměti. Proto nemůžete použít třídu `concurrent_vector` ve všech způsobech, jak lze použít pole. Například pro proměnnou s názvem `v` typu `concurrent_vector`, výraz `&v[0]+2` vytvoří nedefinované chování.

- Třída `concurrent_vector` definuje metody [grow_by](reference/concurrent-vector-class.md#grow_by) a [grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least) . Tyto metody připomínají metodu [změny](reference/concurrent-vector-class.md#resize) , s tím rozdílem, že jsou bezpečné pro souběžnost.

- Objekt `concurrent_vector` nenalezne své prvky při připojení nebo změně velikosti. Díky tomu mohou existující ukazatele a iterátory zůstat platné během souběžných operací.

- Modul runtime nedefinuje specializovanou verzi `concurrent_vector` pro typ `bool`.

### <a name="vector-safety"></a>Operace bezpečné pro souběžnost

Všechny metody, které připojují nebo zvyšují velikost objektu `concurrent_vector` nebo mají přístup k elementu v objektu `concurrent_vector`, jsou bezpečné pro souběžnost. V případě bezpečného zpracování v souběžnosti znamená, že ukazatele nebo iterátory jsou vždy platné. Není zárukou pro inicializaci elementu nebo z konkrétního pořadí procházení. Výjimkou z tohoto pravidla je metoda `resize`.

V následující tabulce jsou uvedeny běžné metody `concurrent_vector` a operátory, které jsou bezpečné pro souběžnost.

||||
|-|-|-|
|[Počínaje](reference/concurrent-vector-class.md#at)|[účelu](reference/concurrent-vector-class.md#end)|[podnikatel&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|
|[ifunctiondiscovery](reference/concurrent-vector-class.md#begin)|[dopředu](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[návrat](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|
|[klíčivost](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|
|[obsahovat](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[hodnota](reference/concurrent-vector-class.md#size)|

Operace, které modul runtime poskytuje pro kompatibilitu se C++ standardní knihovnou, například `reserve`, nejsou bezpečné pro souběžnost. V následující tabulce jsou uvedeny běžné metody a operátory, které nejsou bezpečné pro souběžnost.

|||
|-|-|
|[řadit](reference/concurrent-vector-class.md#assign)|[rezervační](reference/concurrent-vector-class.md#reserve)|
|[jejich](reference/concurrent-vector-class.md#clear)|[velikost](reference/concurrent-vector-class.md#resize)|
|[operátor =](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

Operace, které upravují hodnotu stávajících prvků, nejsou bezpečné pro souběžnost. K synchronizaci souběžných operací čtení a zápisu se stejným datovým prvkem použijte objekt synchronizace, například objekt [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) . Další informace o synchronizačních objektech najdete v tématu [Synchronizace datových struktur](../../parallel/concrt/synchronization-data-structures.md).

Při převodu stávajícího kódu, který používá `vector` k použití `concurrent_vector`, můžou souběžné operace způsobit změnu chování aplikace. Zvažte například následující program, který souběžně provede dvě úlohy na objekt `concurrent_vector`. První úkol připojí další prvky k objektu `concurrent_vector`. Druhý úkol vypočítá součet všech prvků ve stejném objektu.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

I když je metoda `end` bezpečná pro souběžnost, souběžné volání metody [push_back](reference/concurrent-vector-class.md#push_back) způsobí, že hodnota vrácená `end`, která se má změnit. Počet elementů, jejichž průchod iterátorem je neurčitý Proto může tento program při každém spuštění vytvořit jiný výsledek. Pokud je typ elementu netriviální, je možné, že existuje podmínka časování mezi `push_back` a `end` volání. Metoda `end` může vracet prvek, který je přidělen, ale není zcela inicializován.

### <a name="vector-exceptions"></a>Zabezpečení výjimek

Pokud operace růstu nebo přiřazení vyvolá výjimku, stav objektu `concurrent_vector` bude neplatný. Chování objektu `concurrent_vector`, který je v neplatném stavu, není definováno, pokud není uvedeno jinak. Destruktor však vždy uvolňuje paměť, kterou objekt přiděluje, i v případě, že je objekt v neplatném stavu.

Datový typ prvků Vector, `T`musí splňovat následující požadavky. V opačném případě chování třídy `concurrent_vector` není definováno.

- Destruktor nesmí být throw.

- Pokud konstruktor default nebo Copy vyvolá, nesmí být destruktor deklarovaný pomocí klíčového slova `virtual` a musí správně fungovat s nulovou inicializovaný pamětí.

[[Nahoře](#top)]

## <a name="queue"></a>concurrent_queue – Třída

Třída [Concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) , stejně jako třída [std:: Queue](../../standard-library/queue-class.md) , umožňuje přístup ke svým předním a zadním prvkům. Třída `concurrent_queue` povoluje operace zařazování do fronty a dequeued pro souběžnost. V případě bezpečného zpracování v souběžnosti znamená, že ukazatele nebo iterátory jsou vždy platné. Není zárukou pro inicializaci elementu nebo z konkrétního pořadí procházení. Třída `concurrent_queue` také poskytuje podporu iterátoru, která není bezpečná pro souběžnost.

### <a name="queue-differences"></a>Rozdíly mezi concurrent_queue a frontou

Třída `concurrent_queue` úzce připomíná třídu `queue`. Následující body znázorňují, kde se `concurrent_queue` liší od `queue`:

- Operace zařazování a odstranění fronty u objektu `concurrent_queue` jsou bezpečné pro souběžnost.

- Třída `concurrent_queue` poskytuje podporu iterátoru, která není bezpečná pro souběžnost.

- Třída `concurrent_queue` neposkytuje metody `front` nebo `pop`. Třída `concurrent_queue` nahrazuje tyto metody definováním metody [try_pop](reference/concurrent-queue-class.md#try_pop) .

- Třída `concurrent_queue` neposkytuje metodu `back`. Proto nemůžete odkazovat na konec fronty.

- Třída `concurrent_queue` poskytuje metodu [unsafe_size](reference/concurrent-queue-class.md#unsafe_size) namísto metody `size`. Metoda `unsafe_size` není bezpečná pro souběžnost.

### <a name="queue-safety"></a>Operace bezpečné pro souběžnost

Všechny metody, které jsou zařazené do fronty nebo z něj z objektu `concurrent_queue`, jsou bezpečné pro souběžnost. V případě bezpečného zpracování v souběžnosti znamená, že ukazatele nebo iterátory jsou vždy platné. Není zárukou pro inicializaci elementu nebo z konkrétního pořadí procházení.

V následující tabulce jsou uvedeny běžné metody `concurrent_queue` a operátory, které jsou bezpečné pro souběžnost.

|||
|-|-|
|[obsahovat](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

I když je metoda `empty` bezpečná pro souběžnost, souběžná operace může způsobit, že se fronta zvětšuje nebo zmenšuje předtím, než se vrátí metoda `empty`.

V následující tabulce jsou uvedeny běžné metody a operátory, které nejsou bezpečné pro souběžnost.

|||
|-|-|
|[jejich](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

### <a name="queue-iterators"></a>Podpora iterátoru

`concurrent_queue` poskytuje iterátory, které nejsou bezpečné pro souběžnost. Doporučujeme použít tyto iterátory pouze pro ladění.

Iterátor `concurrent_queue` projde prvky pouze ve směru před směrem. V následující tabulce jsou uvedeny operátory, které každý iterátor podporuje.

|Operátor|Popis|
|--------------|-----------------|
|`operator++`|Přejde na další položku ve frontě. Tento operátor je přetížen, aby poskytoval sémantiku před přírůstku i po přírůstcích.|
|`operator*`|Načte odkaz na aktuální položku.|
|`operator->`|Načte ukazatel na aktuální položku.|

[[Nahoře](#top)]

## <a name="unordered_map"></a>concurrent_unordered_map – třída

Třída [Concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) je asociativní třída kontejneru, která stejně jako třída [std:: unordered_map](../../standard-library/unordered-map-class.md) řídí proměnlivou posloupnost prvků typu [std::P air\<const Key >](../../standard-library/pair-structure.md). Neuspořádané mapování se považuje za slovník, ke kterému můžete přidat dvojici klíč-hodnota nebo vyhledat hodnotu podle klíče. Tato třída je užitečná v případě, že máte více vláken nebo úloh, které mají souběžný přístup ke sdílenému kontejneru, vložení do něj nebo ho aktualizovat.

Následující příklad ukazuje základní strukturu pro použití `concurrent_unordered_map`. Tento příklad vloží znakové klíče v rozsahu [' a ', ' i ']. Vzhledem k tomu, že pořadí operací není určeno, je také neurčená koncová hodnota pro každý klíč. Paralelní provádění vkládání je ale bezpečné.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

Příklad, který používá `concurrent_unordered_map` k provedení mapy a zkrácení operace paralelně, naleznete v tématu [How to: provádět mapování a zmenšování operací paralelně](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

### <a name="map-differences"></a>Rozdíly mezi concurrent_unordered_map a unordered_map

Třída `concurrent_unordered_map` úzce připomíná třídu `unordered_map`. Následující body znázorňují, kde se `concurrent_unordered_map` liší od `unordered_map`:

- Metody `erase`, `bucket`, `bucket_count`a `bucket_size` jsou pojmenovány `unsafe_erase`, `unsafe_bucket`, `unsafe_bucket_count`a `unsafe_bucket_size`v uvedeném pořadí. `unsafe_` konvence pojmenování označuje, že tyto metody nejsou bezpečné pro souběžnost. Další informace o zabezpečení souběžnosti najdete v tématu [operace bezpečné pro souběžné zpracování](#map-safety).

- Operace INSERT neověřuje existující ukazatele nebo iterátory, ani nemění pořadí položek, které již existují v mapě. Operace vkládání a procházení mohou probíhat současně.

- `concurrent_unordered_map` podporuje pouze předávací iteraci.

- Vložení neověřuje ani neaktualizuje iterátory, které jsou vráceny `equal_range`. Vložení může na konec rozsahu připojit nerovné položky. Iterátor zahájení odkazuje na shodnou položku.

Aby se zabránilo zablokování, žádná metoda `concurrent_unordered_map` nedrží zámek při volání přidělování paměti, funkce hash nebo jiného uživatelsky definovaného kódu. Také je nutné zajistit, aby funkce hash vždy vyhodnotila stejné klíče na stejnou hodnotu. Nejlepší funkce hash rozdělují klíče stejnoměrně napříč prostorem kódu hash.

### <a name="map-safety"></a>Operace bezpečné pro souběžnost

Třída `concurrent_unordered_map` umožňuje bezpečné vkládání a operace přístupu k prvkům souběžné souběžnosti. Operace INSERT neověřuje existující ukazatele nebo iterátory. Přístup iterátoru a operace procházení také jsou bezpečné pro souběžnost. V případě bezpečného zpracování v souběžnosti znamená, že ukazatele nebo iterátory jsou vždy platné. Není zárukou pro inicializaci elementu nebo z konkrétního pořadí procházení. V následující tabulce jsou uvedeny běžně používané `concurrent_unordered_map` metody a operátory, které jsou bezpečné pro souběžnost.

|||||
|-|-|-|-|
|[Počínaje](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[podnikatel&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[zadat](reference/concurrent-unordered-map-class.md#insert)|`size`|

I když lze metodu `count` vyvolat bezpečně z souběžně běžících vláken, různá vlákna mohou získat různé výsledky, pokud je nová hodnota vložena do kontejneru.

V následující tabulce jsou uvedeny běžně používané metody a operátory, které nejsou bezpečné pro souběžnost.

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[operátor =](reference/concurrent-unordered-map-class.md#operator_eq)

Kromě těchto metod jakákoli metoda, která začíná na `unsafe_`, není také souběžná s souběžnou souběžnou.

[[Nahoře](#top)]

## <a name="unordered_multimap"></a>concurrent_unordered_multimap – třída

Třída [Concurrency:: concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) se těsně podobá třídě `concurrent_unordered_map` s tím rozdílem, že umožňuje mapovat více hodnot na stejný klíč. Také se liší od `concurrent_unordered_map` následujícími způsoby:

- Metoda [concurrent_unordered_multimap:: INSERT](reference/concurrent-unordered-multimap-class.md#insert) vrací iterátor místo `std::pair<iterator, bool>`.

- Třída `concurrent_unordered_multimap` neposkytuje `operator[]` ani metodu `at`.

Následující příklad ukazuje základní strukturu pro použití `concurrent_unordered_multimap`. Tento příklad vloží znakové klíče v rozsahu [' a ', ' i ']. `concurrent_unordered_multimap` umožňuje, aby klíč měl více hodnot.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[Nahoře](#top)]

## <a name="unordered_set"></a>concurrent_unordered_set – třída

Třída [Concurrency:: concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) se těsně podobá třídě `concurrent_unordered_map` s tím rozdílem, že spravuje hodnoty namísto párů klíč a hodnota. Třída `concurrent_unordered_set` neposkytuje `operator[]` ani metodu `at`.

Následující příklad ukazuje základní strukturu pro použití `concurrent_unordered_set`. Tento příklad vloží znakové hodnoty do rozsahu [' a ', ' i ']. Paralelní provádění vkládání je bezpečné.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[Nahoře](#top)]

## <a name="unordered_multiset"></a>concurrent_unordered_multiset – třída

Třída [Concurrency:: concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) se těsně podobá třídě `concurrent_unordered_set` s tím rozdílem, že umožňuje duplicitní hodnoty. Také se liší od `concurrent_unordered_set` následujícími způsoby:

- Metoda [concurrent_unordered_multiset:: INSERT](reference/concurrent-unordered-multiset-class.md#insert) vrací iterátor místo `std::pair<iterator, bool>`.

- Třída `concurrent_unordered_multiset` neposkytuje `operator[]` ani metodu `at`.

Následující příklad ukazuje základní strukturu pro použití `concurrent_unordered_multiset`. Tento příklad vloží znakové hodnoty do rozsahu [' a ', ' i ']. `concurrent_unordered_multiset` umožňuje, aby k hodnotě docházelo víckrát.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[Nahoře](#top)]

## <a name="combinable"></a>kombinace třídy

Třída [Concurrency::](../../parallel/concrt/reference/combinable-class.md) Merged poskytuje opakované použití, místní úložiště vlákna, které umožňuje provádět jemně odstupňované výpočty a pak tyto výpočty sloučit do konečného výsledku. Objekt `combinable` lze představit jako redukční proměnnou.

Třída `combinable` je užitečná v případě, že máte prostředek, který je sdílen mezi několika vlákny nebo úkoly. Třída `combinable` pomáhá eliminovat sdílený stav tím, že poskytuje přístup ke sdíleným prostředkům způsobem bez zámku. Proto tato třída poskytuje alternativu k použití synchronizačního mechanismu, například mutex, k synchronizaci přístupu ke sdíleným datům z více vláken.

### <a name="combinable-features"></a>Metody a funkce

V následující tabulce jsou uvedeny některé důležité metody třídy `combinable`. Další informace o všech metodách `combinable` třídy naleznete v tématu [kombinace třídy](../../parallel/concrt/reference/combinable-class.md).

|Metoda|Popis|
|------------|-----------------|
|[local](reference/combinable-class.md#local)|Načte odkaz na místní proměnnou, která je přidružena k aktuálnímu kontextu vlákna.|
|[jejich](reference/combinable-class.md#clear)|Odebere všechny proměnné místního vlákna z objektu `combinable`.|
|[spojen](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Používá poskytnutou funkci kombinovat k vygenerování konečné hodnoty ze sady všech výpočtů místních vláken.|

Třída `combinable` je třída šablony, která je parametrizovaná na finálním sloučeném výsledku. Pokud zavoláte výchozí konstruktor, typ parametru šablony `T` musí mít výchozí konstruktor a kopírovací konstruktor. Pokud typ parametru šablony `T` nemá výchozí konstruktor, zavolejte přetíženou verzi konstruktoru, který jako svůj parametr přijímá inicializační funkci.

Po volání metod [kombinace](reference/combinable-class.md#combine) nebo [combine_each](reference/combinable-class.md#combine_each) můžete do objektu `combinable` uložit další data. Můžete také volat `combine` a `combine_each` metody několikrát. Pokud se v objektu `combinable` nemění žádná místní hodnota, metody `combine` a `combine_each` vytvoří stejný výsledek pokaždé, když jsou voláni.

### <a name="combinable-examples"></a>4.6

Příklady použití třídy `combinable` naleznete v následujících tématech:

- [Postupy: Použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [Postupy: Použití objektu combinable ke slučování množin](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[Nahoře](#top)]

## <a name="related-topics"></a>Související témata

[Postupy: Použití paralelních kontejnerů ke zvýšení účinnosti](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
Ukazuje, jak použít paralelní kontejnery pro efektivní ukládání a přístup k datům paralelně.

[Postupy: Použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
Ukazuje, jak použít třídu `combinable` k odstranění sdíleného stavu, a tím ke zvýšení výkonu.

[Postupy: Použití objektu combinable ke slučování množin](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
Ukazuje, jak použít funkci `combine` pro sloučení místních sad dat vlákna.

[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Popisuje PPL, který poskytuje imperativní programovací model, který podporuje škálovatelnost a snadné použití při vývoji souběžných aplikací.

## <a name="reference"></a>Referenční informace

[concurrent_vector – třída](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue – třída](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map – třída](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap – třída](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set – třída](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset – třída](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[combinable – třída](../../parallel/concrt/reference/combinable-class.md)
