---
title: Paralelní kontejnery a objekty
ms.date: 11/04/2016
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: 0d3d883fa2199096d4dc880e2d8e78cff6d9830c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542555"
---
# <a name="parallel-containers-and-objects"></a>Paralelní kontejnery a objekty

Knihovna paralelních vzorů (PPL) zahrnuje několik kontejnery a objekty, které poskytují bezpečné pro vlákna přístup k jejich prvky.

A *souběžných kontejneru* poskytuje souběžnosti typově bezpečný přístup k nejdůležitějším operace. Funkce tyto kontejnery se podobá ty, které jsou k dispozici ve standardní knihovně jazyka C++. Například [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) třídy vypadá podobně jako [std::vector](../../standard-library/vector-class.md) třídy s výjimkou, že `concurrent_vector` třída umožňuje přidat prvky paralelně. Používejte souběžné kontejnery, pokud máte paralelní kód, který vyžaduje čtení a zápis do stejného kontejneru.

A *souběžných objekt* souběžně sdílen komponenty. Proces, který vypočítává stav souběžných objektu paralelně vytvoří stejný výsledek jako jiný proces, který vypočítává stejného stavu sériově. [Concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) je jedním z příkladů souběžných objektu typu třídy. `combinable` Třída umožňuje paralelní provádění výpočtů a pak sloučí těchto výpočtů do konečný výsledek. Souběžné objektů použijte, když používáte synchronizační mechanismus, například objekt mutex by jinak k synchronizaci přístupu ke sdílené proměnné nebo prostředku.

##  <a name="top"></a> Oddíly

Toto téma popisuje následující paralelní kontejnery a objekty v podrobností.

Souběžné kontejnery:

- [concurrent_vector – třída](#ctor)

   - [Rozdíly mezi concurrent_vector – a vektoru](#ctor)

   - [Operace bezpečné na souběžnosti](#ctor)

   - [Bezpečnost výjimek](#ctor)

- [concurrent_queue – třída](#queue)

   - [Rozdíly mezi concurrent_queue – a fronty](#queue-differences)

   - [Operace bezpečné na souběžnosti](#queue-safety)

   - [Iterator Support](#queue-iterators)

- [concurrent_unordered_map – třída](#unordered_map)

   - [Rozdíly mezi concurrent_unordered_map – a unordered_map](#map-differences)

   - [Operace bezpečné na souběžnosti](#map-safety)

- [concurrent_unordered_multimap – třída](#unordered_multimap)

- [concurrent_unordered_set – třída](#unordered_set)

- [concurrent_unordered_multiset – třída](#unordered_multiset)

Souběžné objekty:

- [combinable – třída](#combinable)

   - [Metody a funkce](#combinable-features)

   - [Příklady](#combinable-examples)

##  <a name="vector"></a> concurrent_vector – třída

[Concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) třída je třídou kontejneru sekvence, která, stejně jako [std::vector](../../standard-library/vector-class.md) třídy, umožňuje náhodně přístup k jeho prvkům. `concurrent_vector` Třída umožňuje připojení bezpečné na souběžnosti a element přístup operace. Doplňovací operace k zneplatnění stávajících ukazatele nebo iterátory. Operace přístupu a procházení iterátoru jsou také bezpečná pro souběžnost.

###  <a name="vector-differences"></a> Rozdíly mezi concurrent_vector – a vektoru

`concurrent_vector` Třídy připomíná `vector` třídy. Složitost připojení, přístup k prvkům a operací přístupu k iterátoru ve `concurrent_vector` objektu jsou stejné jako v případě `vector` objektu. Následující body znázorňují, kde `concurrent_vector` se liší od `vector`:

- Přidat přístup k prvkům, přístup k iterátoru a operace procházení iterátoru na `concurrent_vector` objektu jsou bezpečné na souběžnosti.

- Elementy můžete přidat pouze do konce `concurrent_vector` objektu. `concurrent_vector` Třída neposkytuje `insert` metody.

- A `concurrent_vector` objekt nepoužíval [sémantiky přesunutí](../../cpp/rvalue-reference-declarator-amp-amp.md) při připojení k němu.

- `concurrent_vector` Třída neposkytuje `erase` nebo `pop_back` metody. Stejně jako u `vector`, použijte [vymazat](reference/concurrent-vector-class.md#clear) metoda odebrat všechny prvky z `concurrent_vector` objektu.

- `concurrent_vector` Třídy neukládá jeho prvky souvisle v paměti. Proto je nelze použít `concurrent_vector` třídy všechny způsoby, které můžete použít pole. Například pro proměnnou s názvem `v` typu `concurrent_vector`, výraz `&v[0]+2` vytvoří nedefinované chování.

- `concurrent_vector` Třída definuje [grow_by –](reference/concurrent-vector-class.md#grow_by) a [grow_to_at_least –](reference/concurrent-vector-class.md#grow_to_at_least) metody. Tyto metody vypadat podobně jako [změnit velikost](reference/concurrent-vector-class.md#resize) metody, s tím rozdílem, že jsou bezpečné na souběžnosti.

- A `concurrent_vector` objektu není přemístit jeho prvky při připojení k němu nebo změňte jeho velikost. Díky tomu existující ukazatele a iterátory jsou dál platné při souběžných operací.

- Modul runtime nedefinuje specializované verze `concurrent_vector` pro typ `bool`.

###  <a name="vector-safety"></a> Operace bezpečné na souběžnosti

Všechny metody, které se připojí k nebo zvětšete velikost `concurrent_vector` objektu nebo přístup k prvku v `concurrent_vector` objektu, jsou bezpečná pro souběžnost. Výjimkou z tohoto pravidla je `resize` metody.

V následující tabulce jsou uvedeny běžné `concurrent_vector` metody a operátory, které jsou bezpečné na souběžnosti.

||||
|-|-|-|

|[na](reference/concurrent-vector-class.md#at)|[end](reference/concurrent-vector-class.md#end)|[operátor&#91;&#93;](reference/concurrent-vector-class.md#operator_at)||[ Začněte](reference/concurrent-vector-class.md#begin)|[přední](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)||[ zpět](reference/concurrent-vector-class.md#back)|[grow_by –](reference/concurrent-vector-class.md#grow_by)|[rbegin –](reference/concurrent-vector-class.md#rbegin)||[ kapacita](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least –](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)||[ prázdný](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[velikost](reference/concurrent-vector-class.md#size)|

Operace, které poskytuje modul runtime pro kompatibilitu s standardní knihovny C++, například `reserve`, nejsou bezpečná pro souběžnost. V následující tabulce jsou uvedeny běžné metody a operátory, které nejsou bezpečná pro souběžnost.

|||
|-|-|

|[přiřadit](reference/concurrent-vector-class.md#assign)|[rezervovat](reference/concurrent-vector-class.md#reserve)||[ Vymazat](reference/concurrent-vector-class.md#clear)|[změnit velikost](reference/concurrent-vector-class.md#resize)||[ operátor =](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit –](reference/concurrent-vector-class.md#shrink_to_fit)|

Operace, které mění hodnotu prvků existující nejsou bezpečná pro souběžnost. Například použít objekt synchronizace [reader_writer_lock –](../../parallel/concrt/reference/reader-writer-lock-class.md) objektu, který chcete synchronizovat souběžné čtení a operací zápisu na stejný datový element. Další informace o synchronizaci objektů najdete v tématu [synchronizačních datových struktur](../../parallel/concrt/synchronization-data-structures.md).

Při převádění existujícího kódu, který používá `vector` používat `concurrent_vector`, souběžné operace může způsobit chování vaší aplikace, chcete-li změnit. Představte si třeba následující program, který současně provádí dva úkoly `concurrent_vector` objektu. První úkol přidá další prvky k `concurrent_vector` objektu. Druhá úloha kód vypočítá součet všech prvků ve stejném objektu.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

I když `end` metoda je bezpečná pro souběžnost, souběžných volání [push_back](reference/concurrent-vector-class.md#push_back) metoda způsobí, že hodnota, která je vrácena `end` změnit. Je neurčitý počet prvků, které překračují iterátor. Tento program tedy může vytvořit jiný výsledek pokaždé, když jej spustíte.

###  <a name="vector-exceptions"></a> Bezpečnost výjimek

Pokud operace růstu nebo přiřazení vyvolá výjimku, stav `concurrent_vector` se objekt stane neplatným. Chování `concurrent_vector` objekt, který je v neplatném stavu, není definováno, pokud není uvedeno jinak. Destruktor uvolní však vždy přidělí objektu paměť, i v případě, že objekt je v neplatném stavu.

Datový typ elementů vektorové `T`, musí splňovat následující požadavky. V opačném případě chování `concurrent_vector` třída není definován.

- Destruktor musí vyvolávat.

- Pokud vyvolá výchozího nebo kopírovacího konstruktoru, destruktoru nesmí být deklarován s použitím `virtual` – klíčové slovo a musí fungovat správně s pamětí inicializována nulou.

[[Horní](#top)]

##  <a name="queue"></a> concurrent_queue – třída

[Concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) třídy, podobně jako [std::queue](../../standard-library/queue-class.md) třídy, vám umožní přístup k jeho front a zpět elementy. `concurrent_queue` Třída umožňuje bezpečné na souběžnosti zařadit do fronty a operace odstranění z fronty. `concurrent_queue` Třída rovněž poskytuje iterátor podporu, která není bezpečná pro souběžnost.

###  <a name="queue-differences"></a> Rozdíly mezi concurrent_queue – a fronty

`concurrent_queue` Třídy připomíná `queue` třídy. Následující body znázorňují, kde `concurrent_queue` se liší od `queue`:

- Zařazení do fronty a vyřazovat je z ní operací na `concurrent_queue` objektu jsou bezpečné na souběžnosti.

- `concurrent_queue` Třída poskytuje iterátor podporu, která není bezpečná pro souběžnost.

- `concurrent_queue` Třída neposkytuje `front` nebo `pop` metody. `concurrent_queue` Třídy nahradí tyto metody tak, že definujete [try_pop –](reference/concurrent-queue-class.md#try_pop) metody.

- `concurrent_queue` Třída neposkytuje `back` metody. Proto nemůže odkazovat na konec fronty.

- `concurrent_queue` Třída poskytuje [unsafe_size –](reference/concurrent-queue-class.md#unsafe_size) metoda místo `size` metody. `unsafe_size` Metoda není bezpečná pro souběžnost.

###  <a name="queue-safety"></a> Operace bezpečné na souběžnosti

Všechny metody tohoto zařadit do fronty k nebo odstranění z fronty z `concurrent_queue` objektu jsou bezpečné na souběžnosti.

V následující tabulce jsou uvedeny běžné `concurrent_queue` metody a operátory, které jsou bezpečné na souběžnosti.

|||
|-|-|
|[prázdný](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

I když `empty` metoda je bezpečná pro souběžnost, souběžná operace může způsobit fronty zvětšit nebo zmenšit před `empty` metoda vrátí hodnotu.

V následující tabulce jsou uvedeny běžné metody a operátory, které nejsou bezpečná pro souběžnost.

|||
|-|-|
|[Vymazat](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

###  <a name="queue-iterators"></a> Iterator Support

`concurrent_queue` Poskytuje iterátorů, které nejsou bezpečná pro souběžnost. Doporučujeme používat tyto iterátory pouze pro ladění.

A `concurrent_queue` iterátoru prochází přes prvky ve směru dopředu pouze. Následující tabulka ukazuje operátory, podporuje každý iterátoru.

|Operátor|Popis|
|--------------|-----------------|
|`operator++`|Přejde k další položky ve frontě. Tento operátor je přetížena pro poskytují sémantiku přírůstek před a po přírůstku.|
|`operator*`|Získá odkaz na aktuální položku.|
|`operator->`|Načte ukazatel na aktuální položku.|

[[Horní](#top)]

##  <a name="unordered_map"></a> concurrent_unordered_map – třída

[Concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) třídy je třída asociativní kontejner, který, stejně jako [std::unordered_map](../../standard-library/unordered-map-class.md) třídy, řídí různé délky sekvence elementů typu [std::pair\<const Key, Ty >](../../standard-library/pair-structure.md). Neuspořádanou mapu můžete představit jako slovník, který můžete přidat dvojici klíče a hodnoty do nebo vyhledat hodnotu podle klíče. Tato třída je užitečná, když máte více vláken nebo úloh, které mají přístup k sdílené kontejner souběžně, vložte do ní nebo ji aktualizovat.

Následující příklad ukazuje základní strukturu pro používání `concurrent_unordered_map`. V tomto příkladu vloží klávesy znaku v rozsahu ["a", "i"]. Protože neurčená pořadí operací, je také neurčeném konečnou hodnotu pro každý klíč. Je však bezpečné paralelní provádění vložení.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

Příklad, který používá `concurrent_unordered_map` provádění mapování a snížit operace paralelně najdete v tématu [jak: snížit operace paralelně a provádět mapování](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

###  <a name="map-differences"></a> Rozdíly mezi concurrent_unordered_map – a unordered_map

`concurrent_unordered_map` Třídy připomíná `unordered_map` třídy. Následující body znázorňují, kde `concurrent_unordered_map` se liší od `unordered_map`:

- `erase`, `bucket`, `bucket_count`, A `bucket_size` metody jsou pojmenovány `unsafe_erase`, `unsafe_bucket`, `unsafe_bucket_count`, a `unsafe_bucket_size`v uvedeném pořadí. `unsafe_` Zásady vytváření názvů značí, že tyto metody nejsou bezpečná pro souběžnost. Další informace o bezpečnosti souběžnosti, naleznete v tématu [bezpečná pro souběžnost operace](#map-safety).

- Operace vložení zneplatnění stávajících ukazatele nebo iterátory, ani mění pořadí položek, které již existují v objektu map. Vložit a procházení operace můžou probíhat souběžně.

- `concurrent_unordered_map` podporuje předávání pouze iterace.

- Vložení zrušení platnosti nebo aktualizace iterátory, které jsou vráceny pomocí `equal_range`. Vložení můžete připojit nerovnost položky na konec rozsahu. Počáteční iterátor odkazuje na stejné položky.

Chcete-li zablokování, žádná metoda `concurrent_unordered_map` drží zámek při volání přidělení paměti, funkce hash nebo jiný uživatelský kód. Musí také se ujistěte, že funkce hash vždy vyhodnotí rovná klíči na stejnou hodnotu. Nejlepší funkce hash rovnoměrně distribuovat klíče mezi prostor kódu hash.

###  <a name="map-safety"></a> Operace bezpečné na souběžnosti

`concurrent_unordered_map` Třída umožňuje operace insert a přístup k prvkům bezpečná pro souběžnost. Operace vložení zneplatnění stávajících ukazatele nebo iterátory. Operace přístupu a procházení iterátoru jsou také bezpečná pro souběžnost. V následující tabulce jsou uvedeny běžně používané `concurrent_unordered_map` metody a operátory, které jsou bezpečné na souběžnosti.

|||||
|-|-|-|-|
|[at](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[– operátor&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[Vložit](reference/concurrent-unordered-map-class.md#insert)|`size`|

I když `count` metodu lze volat bez obav z souběžně spuštěných vláken, různých vláken může přijímat odlišné výsledky, pokud je nová hodnota současně vložen do kontejneru.

V následující tabulce jsou uvedeny běžně používané metody a operátory, které nejsou bezpečná pro souběžnost.

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[operátor =](reference/concurrent-unordered-map-class.md#operator_eq)

Kromě těchto metod jakoukoli metodu, která začíná `unsafe_` není bezpečná pro souběžnost.

[[Horní](#top)]

##  <a name="unordered_multimap"></a> concurrent_unordered_multimap – třída

[Concurrency::concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) třídy připomíná `concurrent_unordered_map` třídy s tím rozdílem, že umožňuje více hodnot pro mapování na stejný klíč. Se také liší od `concurrent_unordered_map` následujícími způsoby:

- [Concurrent_unordered_multimap::Insert –](reference/concurrent-unordered-multimap-class.md#insert) metoda vrátí iterátor místo `std::pair<iterator, bool>`.

- `concurrent_unordered_multimap` Třída neposkytuje `operator[]` ani `at` metody.

Následující příklad ukazuje základní strukturu pro používání `concurrent_unordered_multimap`. V tomto příkladu vloží klávesy znaku v rozsahu ["a", "i"]. `concurrent_unordered_multimap` umožňuje mít více hodnot klíče.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[Horní](#top)]

##  <a name="unordered_set"></a> concurrent_unordered_set – třída

[Concurrency::concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) třídy připomíná `concurrent_unordered_map` třídy s tím rozdílem, že spravuje hodnot namísto páry klíč-hodnota. `concurrent_unordered_set` Třída neposkytuje `operator[]` ani `at` metody.

Následující příklad ukazuje základní strukturu pro používání `concurrent_unordered_set`. V tomto příkladu vloží znak hodnoty v rozsahu ["a", "i"]. Je bezpečné paralelní provádění vložení.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[Horní](#top)]

##  <a name="unordered_multiset"></a> concurrent_unordered_multiset – třída

[Concurrency::concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) třídy připomíná `concurrent_unordered_set` třídy s tím rozdílem, že umožňuje duplicitní hodnoty. Se také liší od `concurrent_unordered_set` následujícími způsoby:

- [Concurrent_unordered_multiset::Insert –](reference/concurrent-unordered-multiset-class.md#insert) metoda vrátí iterátor místo `std::pair<iterator, bool>`.

- `concurrent_unordered_multiset` Třída neposkytuje `operator[]` ani `at` metody.

Následující příklad ukazuje základní strukturu pro používání `concurrent_unordered_multiset`. V tomto příkladu vloží znak hodnoty v rozsahu ["a", "i"]. `concurrent_unordered_multiset` umožňuje hodnotu dojde k více než jednou.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[Horní](#top)]

##  <a name="combinable"></a> combinable – třída

[Concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třída obsahuje opakovaně použitelné, místní úložiště, které vám umožní provádět podrobné výpočtů a pak těchto výpočtů sloučit do konečný výsledek. Můžete si představit `combinable` objektu jako redukční proměnná.

`combinable` Třída je užitečná v případě, že máte prostředek, který je sdílen mezi několik vláken nebo úloh. `combinable` Třídy pomáhá eliminovat tím, že poskytuje přístup ke sdíleným prostředkům v podobě bez zámku sdíleného stavu. Proto se tato třída poskytuje alternativu k použití mechanismu synchronizace, například objekt mutex k synchronizaci přístupu ke sdíleným datům z více vláken.

###  <a name="combinable-features"></a> Metody a funkce

V následující tabulce jsou uvedeny některé důležité metody `combinable` třídy. Další informace o všech `combinable` metod najdete v tématu [combinable – třída](../../parallel/concrt/reference/combinable-class.md).

|Metoda|Popis|
|------------|-----------------|
|[local](reference/combinable-class.md#local)|Získá odkaz na místní proměnnou, která je přidružena aktuální kontext vlákna.|
|[Vymazat](reference/combinable-class.md#clear)|Odebere všechny místní proměnné vlákna z `combinable` objektu.|
|[kombinování](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Zadané kombinační funkcí používá ke generování konečnou hodnotu ze sady všechny výpočty místního vlákna.|

`combinable` Třídy je třída šablony, která je na konečný výsledek sloučení s parametry. Při volání výchozího konstruktoru `T` typ parametru šablony musí mít výchozí konstruktor a kopírovací konstruktor. Pokud `T` typ šablony parametr nemá výchozí konstruktor, volání přetížené verze konstruktoru, který přijímá jako svůj parametr inicializační funkce.

Další data v můžete ukládat `combinable` objektu po volání [kombinovat](reference/combinable-class.md#combine) nebo [combine_each –](reference/combinable-class.md#combine_each) metody. Můžete také volat `combine` a `combine_each` metody více než jednou. Pokud žádná místní hodnota v `combinable` objektem, `combine` a `combine_each` metody pokaždé, když jsou volány přinesou stejný výsledek.

###  <a name="combinable-examples"></a> Příklady

Příklady o tom, jak používat `combinable` naleznete v následujících tématech:

- [Postupy: Použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [Postupy: Použití objektu combinable ke slučování množin](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[Horní](#top)]

## <a name="related-topics"></a>Související témata

[Postupy: Použití paralelních kontejnerů ke zvýšení účinnosti](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
Ukazuje, jak efektivně ukládat a přistupovat k datům v paralelní použití paralelních kontejnerů.

[Postupy: Použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
Ukazuje způsob použití `combinable` třídy eliminovat sdílený stav a tím zlepšit výkon.

[Postupy: Použití objektu combinable ke slučování množin](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
Ukazuje, jak používat `combine` funkce Sloučit místních datových sad.

[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Popisuje PPL, který poskytuje imperativní programovací model, který podporuje škálovatelnost a snadné použití pro vývoj souběžných aplikací.

## <a name="reference"></a>Odkaz

[concurrent_vector – třída](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue – třída](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map – třída](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap – třída](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set – třída](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset – třída](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[combinable – třída](../../parallel/concrt/reference/combinable-class.md)
