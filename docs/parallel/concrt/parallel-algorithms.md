---
title: Paralelní algoritmy
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms [Concurrency Runtime]
ms.assetid: 045dca7b-4d73-4558-a44c-383b88a28473
ms.openlocfilehash: a31787172c89e23e5eb32aa203b9f541584c0f68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363210"
---
# <a name="parallel-algorithms"></a>Paralelní algoritmy

Knihovna paralelních vzorů (PPL) poskytuje algoritmy, které současně provádějí práci na kolekcích dat. Tyto algoritmy se podobají těm, které poskytuje standardní knihovna C++.

Paralelní algoritmy se skládají z existujících funkcí v souběžnosti Runtime. Například [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus používá [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objekt k provedení iterací paralelní smyčky. Algoritmové `parallel_for` oddíly fungují optimálním způsobem vzhledem k dostupnému počtu výpočetních prostředků.

## <a name="sections"></a><a name="top"></a>Oddíly

- [Algoritmus parallel_for](#parallel_for)

- [Algoritmus parallel_for_each](#parallel_for_each)

- [Algoritmus parallel_invoke](#parallel_invoke)

- [Algoritmy parallel_transform a parallel_reduce](#parallel_transform_reduce)

  - [Algoritmus parallel_transform](#parallel_transform)

  - [Algoritmus parallel_reduce](#parallel_reduce)

  - [Příklad: Provádění mapy a paralelní redukce](#map_reduce_example)

- [Rozdělení práce](#partitions)

- [Paralelní řazení](#parallel_sorting)

  - [Výběr algoritmu řazení](#choose_sort)

## <a name="the-parallel_for-algorithm"></a><a name="parallel_for"></a>Algoritmus parallel_for

[Souběžnost::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus opakovaně provádí stejný úkol paralelně. Každý z těchto úkolů je parametrizován hodnotou iterace. Tento algoritmus je užitečné, pokud máte tělo smyčky, která nesdílí prostředky mezi iterací této smyčky.

Algoritmus `parallel_for` oddíly úkoly optimálním způsobem pro paralelní provádění. Používá algoritmus krádeže práce a rozsah krádeže vyvážit tyto oddíly, když jsou nevyvážené úlohy. Když jedna iterace smyčky blokuje kooperativně, runtime redistribuuje rozsah iterací, který je přiřazen k aktuálnímu vláknu do jiných vláken nebo procesorů. Podobně když vlákno dokončí rozsah iterací, runtime redistribuuje práci z jiných vláken do tohoto vlákna. Algoritmus `parallel_for` také podporuje *vnořený paralelismus*. Pokud jedna paralelní smyčka obsahuje jinou paralelní smyčku, runtime souřadnice zpracování prostředků mezi tělesy smyčky efektivním způsobem pro paralelní spuštění.

Algoritmus `parallel_for` má několik přetížených verzí. První verze přebírá počáteční hodnotu, koncovou hodnotu a pracovní funkci (výraz lambda, objekt funkce nebo ukazatel funkce). Druhá verze má počáteční hodnotu, koncovou hodnotu, hodnotu, kterou chcete krok a pracovní funkci. První verze této funkce používá hodnotu 1 jako hodnotu kroku. Zbývající verze přebírají objekty partitioner, které `parallel_for` umožňují určit, jak by měl oddíl rozsahy mezi podprocesy. Rozdělovače jsou podrobněji vysvětleny v části [Dělení práce](#partitions) v tomto dokumentu.

Můžete převést `for` mnoho smyček `parallel_for`k použití . Algoritmus `parallel_for` se však `for` liší od příkazu následujícími způsoby:

- `parallel_for` Algoritmus `parallel_for` neprovádí úkoly v předem určeném pořadí.

- Algoritmus `parallel_for` nepodporuje podmínky libovolného ukončení. Algoritmus se `parallel_for` zastaví, když je aktuální hodnota `last`iterace o jednu menší než .

- Parametr `_Index_type` typu musí být integrální typ. Tento integrální typ může být podepsán nebo nepodepsaný.

- Opakování smyčky musí být vpřed. Algoritmus `parallel_for` vyvolá výjimku typu [std::invalid_argument](../../standard-library/invalid-argument-class.md) Pokud je `_Step` parametr menší než 1.

- Mechanismus zpracování výjimek `parallel_for` pro algoritmus se `for` liší od smyčky. Pokud více výjimek dojít současně v těle paralelní smyčky, runtime rozšíří pouze jednu `parallel_for`z výjimek z podprocesu, který volal . Kromě toho při jedné opakování smyčky vyvolá výjimku, runtime okamžitě nezastaví celkovou smyčku. Místo toho smyčky je umístěn ve stavu zrušena a zahodí všechny úkoly, které ještě nebyly spuštěny. Další informace o zpracování výjimek a paralelní algoritmy naleznete v [tématu zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Přestože `parallel_for` algoritmus nepodporuje podmínky libovolného ukončení, můžete použít zrušení zastavit všechny úkoly. Další informace o zrušení naleznete [v tématu Zrušení v PPL](cancellation-in-the-ppl.md).

> [!NOTE]
> Náklady na plánování, které jsou výsledkem vyrovnávání zatížení a podpory funkcí, jako je zrušení, nemusí překonat výhody paralelního provádění těla smyčky, zejména pokud je tělo smyčky relativně malé. Tuto režii můžete minimalizovat pomocí rozdělovače v paralelní smyčce. Další informace naleznete v [tématu Dělení práce](#partitions) dále v tomto dokumentu.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní strukturu `parallel_for` algoritmu. Tento příklad vytiskne do konzoly každou hodnotu v rozsahu [1, 5] paralelně.

[!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_1.cpp)]

Tento příklad vytvoří následující ukázkový výstup:

```Output
1 2 4 3 5
```

Vzhledem `parallel_for` k tomu, že algoritmus pracuje na každé položce paralelně, pořadí, ve kterém jsou hodnoty vytištěny do konzoly se bude lišit.

Úplný příklad, který `parallel_for` používá algoritmus, najdete v tématu [Jak: Napsat parallel_for smyčky](../../parallel/concrt/how-to-write-a-parallel-for-loop.md).

[[Nahoře]](#top)

## <a name="the-parallel_for_each-algorithm"></a><a name="parallel_for_each"></a>Algoritmus parallel_for_each

[Souběžnost::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus provádí úlohy na iterativní kontejner, jako jsou poskytované c++ standardní knihovny, paralelně. Používá stejnou logiku dělení, `parallel_for` která používá algoritmus.

Algoritmus `parallel_for_each` se podobá C++ Standardní knihovna [std::for_each](../../standard-library/algorithm-functions.md#for_each) algoritmus, s tím rozdílem, `parallel_for_each` že algoritmus provádí úkoly souběžně. Stejně jako ostatní `parallel_for_each` paralelní algoritmy neprovádí úlohy v určitém pořadí.

Přestože `parallel_for_each` algoritmus pracuje na obou dopředu iterátory a náhodný přístup iterátory, funguje lépe s náhodným přístupem iterátory.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní strukturu `parallel_for_each` algoritmu. Tento příklad vytiskne do konzoly každou hodnotu v [std::array](../../standard-library/array-class-stl.md) objektu paralelně.

[!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_2.cpp)]

Tento příklad vytvoří následující ukázkový výstup:

```Output
4 5 1 2 3
```

Vzhledem `parallel_for_each` k tomu, že algoritmus pracuje na každé položce paralelně, pořadí, ve kterém jsou hodnoty vytištěny do konzoly se bude lišit.

Úplný příklad, který `parallel_for_each` používá algoritmus, najdete v tématu [Jak: Napsat parallel_for_each smyčky](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md).

[[Nahoře]](#top)

## <a name="the-parallel_invoke-algorithm"></a><a name="parallel_invoke"></a>Algoritmus parallel_invoke

[Souběžnost::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus provede sadu úloh paralelně. Nevrátí se, dokud nebude dokončen každý úkol. Tento algoritmus je užitečné, pokud máte několik nezávislých úloh, které chcete spustit současně.

Algoritmus `parallel_invoke` bere jako své parametry řadu pracovních funkcí (lambda funkce, objekty funkce nebo ukazatele funkce). Algoritmus `parallel_invoke` je přetížena trvat mezi dvěma a deseti parametry. Každá funkce, kterou `parallel_invoke` předáte, musí mít nulové parametry.

Stejně jako ostatní `parallel_invoke` paralelní algoritmy neprovádí úlohy v určitém pořadí. Téma [Paralelismus úlohvysvětluje,](../../parallel/concrt/task-parallelism-concurrency-runtime.md) `parallel_invoke` jak algoritmus souvisí s úkoly a skupinami úkolů.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní strukturu `parallel_invoke` algoritmu. Tento příklad současně volá `twice` funkci na tři místní proměnné a vytiskne výsledek do konzoly.

[!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_3.cpp)]

Tento příklad vytváří následující výstup:

```Output
108 11.2 HelloHello
```

Úplné příklady, které `parallel_invoke` používají algoritmus, naleznete v [tématu Postup: Použití parallel_invoke k napsání rutiny paralelního řazení](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) a [Jak: Použití parallel_invoke k provedení paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

[[Nahoře]](#top)

## <a name="the-parallel_transform-and-parallel_reduce-algorithms"></a><a name="parallel_transform_reduce"></a>Algoritmy parallel_transform a parallel_reduce

[Souběžnost::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) a [concurrency::parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) algoritmy jsou paralelní verze algoritmů standardní knihovny C++std::transform a [std::accumulate](../../standard-library/numeric-functions.md#accumulate). [std::transform](../../standard-library/algorithm-functions.md#transform) Souběžné runtime verze se chovají jako verze standardní knihovny C++ s tím rozdílem, že pořadí operací není určeno, protože se spouští paralelně. Tyto algoritmy použijte při práci se sadou, která je dostatečně velká, aby získala výhody výkonu a škálovatelnosti z paralelního zpracování.

> [!IMPORTANT]
> A `parallel_transform` `parallel_reduce` algoritmy podporují pouze náhodný přístup, obousměrný a dopředu iterátory, protože tyto iterátory produkují stabilní paměťové adresy. Tyto iterátory musí také vytvářet hodnoty ne-l.`const`

### <a name="the-parallel_transform-algorithm"></a><a name="parallel_transform"></a>Algoritmus parallel_transform

`parallel transform` Algoritmus můžete použít k provedení mnoha operací paralelizace dat. Můžete například provést následující věci:

- Upravte jas obrazu a proveďte další operace zpracování obrazu.

- Součet nebo vzít tečka produkt mezi dvěma vektory a provádět další číselné výpočty na vektory.

- Proveďte 3D ray trasování, kde každá iterace odkazuje na jeden obrazový bod, který musí být vykreslen.

Následující příklad ukazuje základní strukturu, která `parallel_transform` se používá k volání algoritmu. Tento příklad neguje každý prvek std::[vektorový](../../standard-library/vector-class.md) objekt dvěma způsoby. První způsob používá lambda výraz. Druhý způsob používá [std::negate](../../standard-library/negate-struct.md), který je odvozen od [std::unary_function](../../standard-library/unary-function-struct.md).

[!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_4.cpp)]

> [!WARNING]
> Tento příklad ukazuje základní `parallel_transform`použití . Vzhledem k tomu, že pracovní funkce neprovádí významné množství práce, v tomto příkladu se neočekává významné zvýšení výkonu.

Algoritmus `parallel_transform` má dvě přetížení. První přetížení trvá jeden vstupní rozsah a unární funkce. Unární funkce může být lambda výraz, který trvá jeden argument, objekt `unary_function`funkce nebo typ, který je odvozen z . Druhé přetížení trvá dva vstupní rozsahy a binární funkce. Binární funkce může být lambda výraz, který trvá dva argumenty, objekt funkce nebo typ, který je odvozen od [std::binary_function](../../standard-library/binary-function-struct.md). Následující příklad ilustruje tyto rozdíly.

[!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_5.cpp)]

> [!IMPORTANT]
> Iterátor, který zadáte pro výstup `parallel_transform` musí zcela překrývat vstupní iterátor nebo se nepřekrývají vůbec. Chování tohoto algoritmu není specifikováno, pokud se vstupní a výstupní iterátory částečně překrývají.

### <a name="the-parallel_reduce-algorithm"></a><a name="parallel_reduce"></a>Algoritmus parallel_reduce

Algoritmus `parallel_reduce` je užitečné, pokud máte posloupnost operací, které splňují asociativní vlastnost. (Tento algoritmus nevyžaduje komutativní vlastnost.) Zde jsou některé operace, které `parallel_reduce`můžete provádět s :

- Násobit sekvence matice k vytvoření matice.

- Vynásobte vektor posloupností matic a vyhotovte vektor.

- Vypočítat délku posloupnosti řetězců.

- Zkombinujte seznam prvků, jako jsou řetězce, do jednoho prvku.

Následující základní příklad ukazuje, `parallel_reduce` jak pomocí algoritmu kombinovat posloupnost řetězců do jednoho řetězce. Stejně jako u `parallel_transform`příkladů pro , zvýšení výkonu se neočekává v tomto základním příkladu.

[!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_6.cpp)]

V mnoha případech si `parallel_reduce` můžete myslet jako zkratka `parallel_for_each` pro použití algoritmu spolu s [souběžnost::kombinovatelné](../../parallel/concrt/reference/combinable-class.md) třídy.

### <a name="example-performing-map-and-reduce-in-parallel"></a><a name="map_reduce_example"></a>Příklad: Provádění mapy a paralelní redukce

Operace *mapy* použije funkci pro každou hodnotu v sekvenci. Operace *snížení* kombinuje prvky sekvence do jedné hodnoty. Můžete použít C++ Standardní knihovna [std::transform](../../standard-library/algorithm-functions.md#transform) a [std::accumulate](../../standard-library/numeric-functions.md#accumulate) funkce k provedení mapy a snížení operací. Však pro mnoho problémů můžete `parallel_transform` použít algoritmus k paralelnímu `parallel_reduce` provedení operace mapy a algoritmus provést operaci snížit paralelně.

Následující příklad porovnává čas potřebný k výpočtu součtu prvočísel sériově a paralelně. Fáze mapy transformuje hodnoty bez základní hodnoty na 0 a fáze snížení shrnuje hodnoty.

[!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_7.cpp)]

Další příklad, který provádí mapu a snížit operace paralelně, naleznete v [tématu How to: Provést mapování a snížit operace paralelně](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

[[Nahoře]](#top)

## <a name="partitioning-work"></a><a name="partitions"></a>Rozdělení práce

Chcete-li paralelizovat operaci na zdroj dat, základním krokem je *rozdělení* zdroje do více oddílů, které lze přistupovat souběžně více vláken. Rozdělovač určuje, jak paralelní algoritmus by měl rozdělit rozsahy mezi podprocesy. Jak je vysvětleno dříve v tomto dokumentu, PPL používá výchozí mechanismus dělení, který vytvoří počáteční zatížení a pak používá algoritmus krádeže práce a rozsah krádeže k vyrovnání těchto oddílů, když jsou nevyvážené úlohy. Například když jedna iterace smyčky dokončí rozsah iterací, runtime redistribuuje práci z jiných vláken do tohoto vlákna. V některých scénářích však můžete chtít zadat jiný mechanismus dělení, který je vhodnější pro váš problém.

Aplikace `parallel_for` `parallel_for_each`, `parallel_transform` a algoritmy poskytují přetížené verze, `_Partitioner`které zabírají další parametr . Tento parametr definuje typ rozdělovače, který rozděluje práci. Zde jsou druhy rozdělovačů, které Definuje PPL:

[souběžnost::affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)<br/>
Rozdělí práci do pevného počtu rozsahů (obvykle počet pracovních podprocesů, které jsou k dispozici pro práci na smyčce). Tento typ rozdělovače se podobá `static_partitioner`, ale zlepšuje spřažení mezipaměti podle způsobu, jakým mapuje rozsahy pracovních podprocesů. Tento typ rozdělovače může zlepšit výkon při smyčku je spuštěn a přes stejnou sadu dat vícekrát (například smyčky v rámci smyčky) a data se vejde do mezipaměti. Tento partitioner se plně neúčastní zrušení. Také nepoužívá kooperativní blokování sémantiku a proto nelze použít s paralelní smyčky, které mají dopředné závislosti.

[souběžnost::auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)<br/>
Rozdělí práci do počátečního počtu rozsahů (obvykle počet pracovních podprocesů, které jsou k dispozici pro práci na smyčce). Runtime používá tento typ ve výchozím nastavení, pokud nevoláte `_Partitioner` přetížený paralelní algoritmus, který přebírá parametr. Každý rozsah lze rozdělit do dílčích rozsahů a tím umožňuje vyrovnávání zatížení. Po dokončení rozsahu práce, runtime redistribuuje dílčí rozsahy práce z jiných vláken do tohoto vlákna. Tento rozdělovač použijte, pokud vaše úloha nespadá do jedné z dalších kategorií nebo vyžadujete plnou podporu pro zrušení nebo kooperativní blokování.

[souběžnost::simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)<br/>
Rozdělí práci do rozsahů tak, aby každý rozsah má alespoň počet iterací, které jsou určeny danou velikostí bloku. Tento typ rozdělovače se podílí na vyrovnávání zatížení; však runtime nerozdělí rozsahy do dílčích rozsahů. Pro každého pracovníka za běhu zkontroluje zrušení a `_Chunk_size` provede vyrovnávání zatížení po dokončení iterací.

[souběžnost::static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)<br/>
Rozdělí práci do pevného počtu rozsahů (obvykle počet pracovních podprocesů, které jsou k dispozici pro práci na smyčce). Tento typ partitioner může zlepšit výkon, protože nepoužívá práci krást a proto má menší režii. Tento typ rozdělovače použijte, když každá iterace paralelní smyčky provádí pevné a jednotné množství práce a nepotřebujete podporu pro zrušení nebo předávání kooperativní blokování.

> [!WARNING]
> A `parallel_for_each` `parallel_transform` algoritmy podporují pouze kontejnery, které používají iterátory náhodného přístupu (například std::[vector)](../../standard-library/vector-class.md)pro statické, jednoduché a spřažení partitionery. Použití kontejnerů, které používají obousměrné a dopředu iterátory vytváří chybu kompilace. Výchozí rozdělovač `auto_partitioner`, podporuje všechny tři tyto typy iterátoru.

Obvykle se tyto rozdělovače používají stejným způsobem, s výjimkou `affinity_partitioner`. Většina typů rozdělovače neudržuje stav a nejsou změněny za běhu. Proto můžete vytvořit tyto objekty partitioner na webu volání, jak je znázorněno v následujícím příkladu.

[!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_8.cpp)]

Je však nutné `affinity_partitioner` předat objekt`const`jako odkaz na hodnotu l, aby algoritmus mohl uložit stav pro budoucí smyčky, které mají být znovu použít. Následující příklad ukazuje základní aplikaci, která provádí stejnou operaci na datové sadě paralelně vícekrát. Použití `affinity_partitioner` může zlepšit výkon, protože pole je pravděpodobně vejde do mezipaměti.

[!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_9.cpp)]

> [!CAUTION]
> Buďte opatrní při úpravě existující kód, který závisí na `static_partitioner` `affinity_partitioner`kooperativní blokování sémantiku použít nebo . Tyto typy rozdělovač nepoužívají vyrovnávání zatížení nebo rozsah krádeže, a proto může změnit chování vaší aplikace.

Nejlepší způsob, jak zjistit, zda použít rozdělovač v daném scénáři je experimentovat a měřit, jak dlouho trvá operace k dokončení pod reprezentativní zatížení a konfigurace počítače. Statické dělení může například poskytnout významné zrychlení v počítači s více jádry, který má pouze několik jader, ale může mít za následek zpomalení v počítačích, které mají relativně mnoho jader.

[[Nahoře]](#top)

## <a name="parallel-sorting"></a><a name="parallel_sorting"></a>Paralelní řazení

PPL poskytuje tři třídící algoritmy: [concurrency::parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)a [concurrency::parallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Tyto algoritmy řazení jsou užitečné, pokud máte sadu dat, která může mít prospěch z řazení paralelně. Zejména třídění paralelně je užitečné, pokud máte velkou datovou sadu nebo při použití výpočtově nákladné operace porovnání k řazení dat. Každý z těchto algoritmů seřadí prvky na místě.

A `parallel_sort` `parallel_buffered_sort` algoritmy jsou oba algoritmy založené na porovnání. To znamená, že porovnávají prvky podle hodnoty. Algoritmus `parallel_sort` nemá žádné další požadavky na paměť a je vhodný pro obecné účely řazení. Algoritmus `parallel_buffered_sort` může pracovat `parallel_sort`lépe než , ale vyžaduje o(N) prostor.

Algoritmus `parallel_radixsort` je založen na algoritmu hash. To znamená, že používá celé klíče k řazení prvků. Pomocí klíčů tento algoritmus můžete přímo vypočítat cíl prvku namísto použití porovnání. Stejně jako `parallel_buffered_sort`tento algoritmus vyžaduje O(N) prostor.

Následující tabulka shrnuje důležité vlastnosti tří algoritmů paralelního řazení.

|Algoritmus|Popis|Třídící mechanismus|Stabilita řazení|Požadavky na paměť|Časová složitost|Přístup k iterátoru|
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|
|`parallel_sort`|Obecné řazení založené na porovnání.|Na základě porovnání (vzestupně)|Nestabilní|Žádný|O(((N/P)log(N/P) + 2N((P-1)/P))|Náhodné|
|`parallel_buffered_sort`|Rychlejší obecné porovnání založené řazení, které vyžaduje O(N) prostor.|Na základě porovnání (vzestupně)|Nestabilní|Vyžaduje další prostor O(N)|O(((N/P)log(N))|Náhodné|
|`parallel_radixsort`|Celočíselné řazení založené na klíči, které vyžaduje prostor O(N).|Na základě hash|Stable|Vyžaduje další prostor O(N)|O(N/P)|Náhodné|

Následující obrázek znázorňuje důležité vlastnosti tří algoritmů paralelního řazení více graficky.

![Porovnání třídících algoritmů](../../parallel/concrt/media/concrt_parallel_sorting.png "Porovnání třídících algoritmů")

Tyto algoritmy paralelní řazení dodržovat pravidla zrušení a zpracování výjimek. Další informace o zrušení a zpracování výjimek v runtime souběžnosti naleznete v [tématu Zrušení paralelních algoritmů](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms) a [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

> [!TIP]
> Tyto paralelní řazení algoritmy podporují přesunout sémantiku. Můžete definovat operátor přiřazení přesunutí, který umožní efektivnější odkládací operace. Další informace o sémantice přesunutí a operátoru přiřazení přesunutí naleznete v tématech [Deklarátor odkazu Rvalue: &&](../../cpp/rvalue-reference-declarator-amp-amp.md)a [Přesunout konstruktory a operátory přiřazení přesunutí (C++).](../../cpp/move-constructors-and-move-assignment-operators-cpp.md) Pokud nezadáte operátor přiřazení přesunutí nebo funkci odkládacího přiřazení, algoritmy řazení použijí konstruktor kopie.

Následující základní příklad ukazuje, `parallel_sort` jak `vector` použít `int` k řazení hodnot. Ve výchozím `parallel_sort` nastavení používá [std::less](../../standard-library/less-struct.md) k porovnání hodnot.

[!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_10.cpp)]

Tento příklad ukazuje, jak poskytnout vlastní funkci porovnání. Používá [std:::complex::real](../../standard-library/complex-class.md#real) metodu k řazení [std::complex\<double>](../../standard-library/complex-double.md) hodnoty ve vzestupném pořadí.

[!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_11.cpp)]

Tento příklad ukazuje, jak poskytnout `parallel_radixsort` funkci hash algoritmu. Tento příklad seřadí 3D body. Body jsou seřazeny podle jejich vzdálenosti od referenčního bodu.

[!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_12.cpp)]

Pro ilustraci tento příklad používá relativně malou sadu dat. Můžete zvětšit počáteční velikost vektoru experimentovat s vylepšení výkonu přes větší sady dat.

Tento příklad používá výraz lambda jako funkci hash. Můžete také použít jednu z předdefinovaných implementací třídy std::[hash](../../standard-library/hash-class.md) nebo definovat vlastní specializaci. Můžete také použít vlastní objekt funkce hash, jak je znázorněno v tomto příkladu:

[!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_13.cpp)]

[!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_14.cpp)]

Funkce hash musí vrátit integrální typ ([std::is_integral:value](../../standard-library/is-integral-class.md) musí být **true**). Tento integrální typ `size_t`musí být převoditelný k typu .

### <a name="choosing-a-sorting-algorithm"></a><a name="choose_sort"></a>Výběr algoritmu řazení

V mnoha `parallel_sort` případech poskytuje nejlepší rovnováhu rychlosti a výkonu paměti. Při zvětšení velikosti sady dat však počet dostupných procesorů nebo složitost funkce `parallel_buffered_sort` `parallel_radixsort` porovnání nebo může fungovat lépe. Nejlepší způsob, jak určit, který algoritmus třídění použít v daném scénáři je experimentovat a měřit, jak dlouho trvá řazení typických dat v rámci konfigurace reprezentativní počítače. Při výběru strategie řazení mějte na paměti následující pokyny.

- Velikost datové sady. V tomto dokumentu *obsahuje malá* datová sada méně než 1 000 prvků, *střední* datová sada obsahuje 10 000 až 100 000 prvků a *velká* datová sada obsahuje více než 100 000 prvků.

- Množství práce, které provádí funkce porovnání nebo funkce hash.

- Množství dostupných výpočetních prostředků.

- Charakteristiky vaší datové sady. Jeden algoritmus může například fungovat dobře pro data, která je již téměř seřazena, ale ne tak dobře pro data, která je zcela neseřazená.

- Velikost bloku. Volitelný `_Chunk_size` argument určuje, kdy algoritmus přepne z paralelní na sériovou implementaci řazení, protože rozděluje celkové řazení na menší jednotky práce. Například pokud zadáte 512, algoritmus přepne na sériovou implementaci, pokud jednotka práce obsahuje 512 nebo méně prvků. Sériová implementace může zlepšit celkový výkon, protože eliminuje režii, která je vyžadována pro paralelní zpracování dat.

Nemusí být vhodné třídit malou datovou sadu paralelně, i když máte velký počet dostupných výpočetních prostředků nebo funkce porovnání nebo funkce hash provádí relativně velké množství práce. Pomocí funkce [std::sort](../../standard-library/algorithm-functions.md#sort) můžete řadit malé datové sady. `parallel_sort` (a `parallel_buffered_sort` `sort` volání při zadání velikosti bloku, který je `parallel_buffered_sort` větší než datová sada; však bude muset přidělit O(N) místo, což může trvat další čas z důvodu uzamčení kolize nebo přidělení paměti.)

Pokud je nutné ušetřit paměť nebo přidělování paměti je předmětem `parallel_sort` konflikty zámku, použijte k řazení středně velké datové sady. `parallel_sort`nevyžaduje žádný další prostor; ostatní algoritmy vyžadují O(N) prostor.

Slouží `parallel_buffered_sort` k řazení středně velkých datových sad a když aplikace splňuje další požadavky na místo O(N). `parallel_buffered_sort`může být užitečné zejména v případě, že máte velký počet výpočetních prostředků nebo nákladné porovnat funkce nebo hash funkce.

Slouží `parallel_radixsort` k řazení velkých datových sad a když vaše aplikace splňuje další O(N) požadavek na místo. `parallel_radixsort`může být užitečné zejména v případě, že ekvivalentní porovnání operace je dražší nebo pokud obě operace jsou drahé.

> [!CAUTION]
> Implementace funkce dobré hodnoty hash vyžaduje, abyste znali rozsah datové sady a jak je každý prvek v datové sadě transformován na odpovídající nepodepsanou hodnotu. Vzhledem k tomu, že operace hash funguje na nepodepsaných hodnotách, zvažte jinou strategii řazení, pokud nelze vytvořit nepodepsané hodnoty hash.

Následující příklad porovnává výkon `sort`, `parallel_sort` `parallel_buffered_sort`, `parallel_radixsort` a proti stejné velké sadě náhodných dat.

[!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_15.cpp)]

V tomto příkladu, který předpokládá, že je přijatelné přidělit O(N) prostor během řazení, `parallel_radixsort` provádí nejlepší na této datové sady v této konfiguraci počítače.

[[Nahoře]](#top)

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Postupy: Programování smyčky parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|Ukazuje, jak `parallel_for` pomocí algoritmu provádět násobení matice.|
|[Postupy: Programování smyčky parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|Ukazuje, jak `parallel_for_each` použít algoritmus k výpočtu počtu prvočísel v [objektu std::array](../../standard-library/array-class-stl.md) paralelně.|
|[Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Ukazuje, jak `parallel_invoke` pomocí algoritmu ke zlepšení výkonu bitonic algoritmu řazení.|
|[Postup: Použití parallel_invoke k provádění paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Ukazuje, jak `parallel_invoke` pomocí algoritmu zlepšit výkon programu, který provádí více operací na sdíleném zdroji dat.|
|[Postupy: Paralelní provádění operací mapování a redukce](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Ukazuje, jak `parallel_transform` pomocí `parallel_reduce` algoritmů a provést mapu a snížit operaci, která počítá výskyty slov v souborech.|
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Popisuje PPL, který poskytuje imperativní programovací model, který podporuje škálovatelnost a snadnost použití pro vývoj souběžných aplikací.|
|[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)|Vysvětluje roli zrušení v PPL, jak zrušit paralelní práci a jak určit, kdy je skupina úloh zrušena.|
|[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Vysvětluje roli zpracování výjimek v souběžnosti Runtime.|

## <a name="reference"></a>Referenční informace

[funkce parallel_for](reference/concurrency-namespace-functions.md#parallel_for)

[parallel_for_each funkce](reference/concurrency-namespace-functions.md#parallel_for_each)

[parallel_invoke funkce](reference/concurrency-namespace-functions.md#parallel_invoke)

[affinity_partitioner – třída](../../parallel/concrt/reference/affinity-partitioner-class.md)

[auto_partitioner – třída](../../parallel/concrt/reference/auto-partitioner-class.md)

[simple_partitioner – třída](../../parallel/concrt/reference/simple-partitioner-class.md)

[static_partitioner – třída](../../parallel/concrt/reference/static-partitioner-class.md)

[parallel_sort funkce](reference/concurrency-namespace-functions.md#parallel_sort)

[parallel_buffered_sort funkce](reference/concurrency-namespace-functions.md#parallel_buffered_sort)

[parallel_radixsort funkce](reference/concurrency-namespace-functions.md#parallel_radixsort)
