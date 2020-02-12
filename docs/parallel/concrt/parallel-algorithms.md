---
title: Paralelní algoritmy
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms [Concurrency Runtime]
ms.assetid: 045dca7b-4d73-4558-a44c-383b88a28473
ms.openlocfilehash: 3e9cce9af01ea108e6510d42e5eedba8ef05a7a4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142923"
---
# <a name="parallel-algorithms"></a>Paralelní algoritmy

Knihovna PPL (Parallel Patterns Library) poskytuje algoritmy, které souběžně provádějí práci na kolekcích dat. Tyto algoritmy připomínají ty, které poskytuje C++ standardní knihovna.

Paralelní algoritmy se skládají z existujících funkcí v Concurrency Runtime. Například algoritmus [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) používá k provádění iterací paralelní smyčky objekt [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) . Oddíly algoritmu `parallel_for` fungují optimálním způsobem s ohledem na dostupný počet výpočetních prostředků.

## <a name="top"></a>Řezů

- [Parallel_for algoritmus](#parallel_for)

- [Parallel_for_each algoritmus](#parallel_for_each)

- [Parallel_invoke algoritmus](#parallel_invoke)

- [Algoritmy parallel_transform a parallel_reduce](#parallel_transform_reduce)

    - [Parallel_transform algoritmus](#parallel_transform)

    - [Parallel_reduce algoritmus](#parallel_reduce)

    - [Příklad: paralelní provádění map a jejich zmenšení](#map_reduce_example)

- [Dělení práce](#partitions)

- [Paralelní řazení](#parallel_sorting)

    - [Výběr algoritmu řazení](#choose_sort)

## <a name="parallel_for"></a>Parallel_for algoritmus

Algoritmus [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) opakovaně provádí stejnou úlohu paralelně. Každý z těchto úloh je parametrizovaný hodnotou iterace. Tento algoritmus je užitečný v případě, že máte tělo smyčky, které nesdílí prostředky mezi iteracemi této smyčky.

U `parallel_for`ho algoritmu jsou úlohy v optimálním způsobu paralelního spouštění. Pro vyvážení těchto oddílů v době, kdy jsou nevyvážené úlohy, používá algoritmus, který pracuje na pracovišti, a krádež rozsahu. Když cyklus iterace v rámci jedné smyčky spolupracuje, modul runtime redistribuuje rozsah iterací, který je přiřazen aktuálnímu vláknu jiným vláknům nebo procesorům. Podobně, pokud vlákno dokončí rozsah iterací, modul runtime znovu distribuuje práci z jiných vláken do tohoto vlákna. Algoritmus `parallel_for` podporuje také *vnořené paralelismus*. Pokud jedna paralelní smyčka obsahuje další paralelní smyčka, modul runtime koordinuje zpracování prostředků mezi tělo smyčky účinným způsobem pro paralelní spuštění.

`parallel_for` algoritmus obsahuje několik přetížených verzí. První verze používá počáteční hodnotu, koncovou hodnotu a pracovní funkci (výraz lambda, objekt funkce nebo ukazatel na funkci). Druhá verze používá počáteční hodnotu, koncovou hodnotu, hodnotu, kterou chcete krokovat, a pracovní funkci. První verze této funkce používá jako hodnotu kroku 1. Zbývající verze převezmou objekty oddílů, které umožňují určit, jak `parallel_for` mají rozsahy oddílu mezi vlákny. Oddíly jsou podrobněji vysvětleny v části [práce s oddíly](#partitions) v tomto dokumentu.

Můžete převést mnoho smyček `for` pro použití `parallel_for`. Algoritmus `parallel_for` se však liší od příkazu `for` následujícím způsobem:

- `parallel_for` algoritmus `parallel_for` neprovede úlohy v předem určeném pořadí.

- Algoritmus `parallel_for` nepodporuje libovolné podmínky ukončení. Algoritmus `parallel_for` se zastaví, pokud je aktuální hodnota proměnné iterace jedna, která je menší než `last`.

- Parametr typu `_Index_type` musí být integrálního typu. Tento integrální typ může být podepsán nebo bez znaménka.

- Iterace smyčky musí být předána. Algoritmus `parallel_for` vyvolá výjimku typu [std:: invalid_argument](../../standard-library/invalid-argument-class.md) , pokud je parametr `_Step` menší než 1.

- Mechanismus zpracování výjimek pro `parallel_for` algoritmus se liší od `for` smyčky. Pokud k více výjimkám dochází současně v těle paralelní smyčky, modul runtime rozšíří pouze jednu výjimku do vlákna, které se nazývá `parallel_for`. Kromě toho, když iterace v rámci smyčky vyvolá výjimku, modul runtime nezastaví celkovou smyčku okamžitě. Místo toho je smyčka umístěna do stavu Canceled a modul runtime zahodí všechny úlohy, které ještě nebyly spuštěny. Další informace o zpracování výjimek a paralelních algoritmech naleznete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

I když `parallel_for` algoritmus nepodporuje libovolné podmínky ukončení, můžete použít zrušení pro zastavení všech úloh. Další informace o zrušení naleznete v tématu [zrušení v PPL](cancellation-in-the-ppl.md).

> [!NOTE]
> Náklady na plánování, které vychází z vyrovnávání zatížení a podpora funkcí, jako je například zrušení, nemusí překonat výhody vykonávání těla smyčky paralelně, zejména v případě, že tělo smyčky je relativně malé. Tuto režii můžete minimalizovat pomocí rozdělovače v paralelní smyčce. Další informace najdete v tématu [dělení práce](#partitions) dále v tomto dokumentu.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní strukturu `parallel_for`ho algoritmu. Tento příklad tiskne do konzoly každou hodnotu v rozsahu [1, 5] paralelně.

[!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_1.cpp)]

Tento příklad vytvoří následující vzorový výstup:

```Output
1 2 4 3 5
```

Vzhledem k tomu, že algoritmus `parallel_for` pracuje na jednotlivých položkách paralelně, pořadí, ve kterém se hodnoty tisknou do konzoly, se budou lišit.

Kompletní příklad, který používá algoritmus `parallel_for`, naleznete v tématu [How to: Write a Parallel_for Loop](../../parallel/concrt/how-to-write-a-parallel-for-loop.md).

[[Nahoře](#top)]

## <a name="parallel_for_each"></a>Parallel_for_each algoritmus

Algoritmus [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) provádí úlohy na iterativním kontejneru, jako jsou například ty, které poskytuje C++ standardní knihovna paralelně. Používá stejnou logiku dělení, kterou používá algoritmus `parallel_for`.

Algoritmus `parallel_for_each` se podobá C++ standardní knihovně [std:: for_each](../../standard-library/algorithm-functions.md#for_each) , s tím rozdílem, že `parallel_for_each` algoritmus spouští úlohy souběžně. Podobně jako u jiných paralelních algoritmů `parallel_for_each` neprovádí úlohy v určitém pořadí.

I když `parallel_for_each` algoritmus funguje na obou dopředných iterátorech i iterátorech náhodného přístupu, je lepší díky iterátorům s náhodným přístupem.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní strukturu `parallel_for_each`ho algoritmu. Tento příklad tiskne do konzoly každou hodnotu v objektu [std:: Array](../../standard-library/array-class-stl.md) paralelně.

[!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_2.cpp)]

Tento příklad vytvoří následující vzorový výstup:

```Output
4 5 1 2 3
```

Vzhledem k tomu, že algoritmus `parallel_for_each` pracuje na jednotlivých položkách paralelně, pořadí, ve kterém se hodnoty tisknou do konzoly, se budou lišit.

Kompletní příklad, který používá algoritmus `parallel_for_each`, naleznete v tématu [How to: Write a Parallel_for_each Loop](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md).

[[Nahoře](#top)]

## <a name="parallel_invoke"></a>Parallel_invoke algoritmus

Algoritmus [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) spustí paralelní sadu úkolů. Nevrátí se do doby, než se dokončí všechny úlohy. Tento algoritmus je užitečný, pokud máte několik nezávislých úloh, které chcete spustit současně.

`parallel_invoke` algoritmus přebírá jako svůj parametr řadu pracovních funkcí (funkce lambda, objekty funkcí nebo ukazatele na funkce). Algoritmus `parallel_invoke` je přetížený, aby bylo možné provést mezi dvěma a deseti parametry. Každá funkce, kterou předáte `parallel_invoke`, musí mít nulové parametry.

Podobně jako u jiných paralelních algoritmů `parallel_invoke` neprovádí úlohy v určitém pořadí. [Paralelní úkoly](../../parallel/concrt/task-parallelism-concurrency-runtime.md) v tématu popisují způsob, jakým `parallel_invoke` algoritmus souvisí s úlohami a skupinami úloh.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní strukturu `parallel_invoke`ho algoritmu. Tento příklad současně volá funkci `twice` na třech místních proměnných a výsledek vytiskne do konzoly.

[!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_3.cpp)]

Tento příklad vytvoří následující výstup:

```Output
108 11.2 HelloHello
```

Kompletní příklady, které používají algoritmus `parallel_invoke`, naleznete v tématu [How to: use parallel_invoke to Write The paralelní řazení](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) a [How to: použijte Parallel_invoke k provedení paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

[[Nahoře](#top)]

## <a name="parallel_transform_reduce"></a>Algoritmy parallel_transform a parallel_reduce

[Concurrency::p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) a [concurrency::p arallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) algoritmy jsou paralelní verze C++ standardních algoritmů knihovny [std:: Transforming](../../standard-library/algorithm-functions.md#transform) a [std:: akumulace](../../standard-library/numeric-functions.md#accumulate)v uvedeném pořadí. Verze Concurrency Runtime se chovají jako verze C++ Standard Library s tím rozdílem, že pořadí operací není určeno, protože jsou spouštěny paralelně. Tyto algoritmy použijte při práci se sadou, která je dostatečně velká, aby se výhody výkonu a škálovatelnosti zpracovaly paralelně.

> [!IMPORTANT]
> Algoritmy `parallel_transform` a `parallel_reduce` podporují jenom náhodný přístup, obousměrné a dopředné iterátory, protože tyto iterátory vytváří stabilní adresy paměti. Také tyto iterátory musí způsobit ne`const` l-Values.

### <a name="parallel_transform"></a>Parallel_transform algoritmus

Pomocí algoritmu `parallel transform` můžete provádět mnoho operací paralelního zpracování dat. Můžete například provést následující věci:

- Upravte jas obrázku a proveďte jiné operace zpracování imagí.

- Sečtěte nebo převezměte tečku mezi dva vektory a proveďte další číselné výpočty pro vektory.

- Proveďte trojrozměrné trasování, kde každá iterace odkazuje na jeden pixel, který musí být vykreslen.

Následující příklad ukazuje základní strukturu, která se používá k volání algoritmu `parallel_transform`. Tento příklad negace každého prvku objektu std::[Vector](../../standard-library/vector-class.md) dvěma způsoby. První způsob používá výraz lambda. Druhý způsob používá [std:: negaci](../../standard-library/negate-struct.md), který je odvozen z [std:: unary_function](../../standard-library/unary-function-struct.md).

[!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_4.cpp)]

> [!WARNING]
> Tento příklad ukazuje základní použití `parallel_transform`. Vzhledem k tomu, že pracovní funkce neprovádí významné množství práce, v tomto příkladu není očekáváno výrazné zvýšení výkonu.

`parallel_transform` algoritmus má dvě přetížení. První přetížení přebírá jeden vstupní rozsah a unární funkci. Unární funkce může být výraz lambda, který přebírá jeden argument, objekt funkce nebo typ, který je odvozen od `unary_function`. Druhé přetížení přebírá dva vstupní rozsahy a binární funkci. Binární funkce může být výraz lambda, který přebírá dva argumenty, objekt funkce nebo typ, který je odvozen z [std:: binary_function](../../standard-library/binary-function-struct.md). Následující příklad znázorňuje tyto rozdíly.

[!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_5.cpp)]

> [!IMPORTANT]
> Iterátor, který zadáte pro výstup `parallel_transform`, musí zcela překrývat vstupní iterátor nebo se nesmí překrývat. Chování tohoto algoritmu není určeno, pokud se vstupní a výstupní iterátory částečně překrývají.

### <a name="parallel_reduce"></a>Parallel_reduce algoritmus

`parallel_reduce` algoritmus je užitečný, pokud máte sekvenci operací, které odpovídají asociativní vlastnosti. (Tento algoritmus nevyžaduje vlastnost komutativní.) Tady je několik operací, které můžete provádět s `parallel_reduce`:

- Vynásobit sekvence matic pro vytvoření matice.

- Vynásobí vektor řadou matic pro vytvoření vektoru.

- Vypočítá délku posloupnosti řetězců.

- Zkombinujte seznam prvků, jako jsou například řetězce, do jednoho elementu.

Následující základní příklad ukazuje, jak použít algoritmus `parallel_reduce` pro kombinování posloupnosti řetězců do jednoho řetězce. Podobně jako u příkladů pro `parallel_transform`se v tomto základním příkladu neočekávají nárůst výkonu.

[!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_6.cpp)]

V mnoha případech si můžete `parallel_reduce` jako zkrácený pro použití `parallel_for_each` algoritmu spolu s třídou [Concurrency::](../../parallel/concrt/reference/combinable-class.md) kombinovat.

### <a name="map_reduce_example"></a>Příklad: paralelní provádění map a jejich zmenšení

Operace *mapování* aplikuje funkci na každou hodnotu v sekvenci. Operace *snížení* kombinuje prvky sekvence do jedné hodnoty. Pomocí C++ standardních knihoven funkce [std:: Transform](../../standard-library/algorithm-functions.md#transform) a [std:: Akumulovaná](../../standard-library/numeric-functions.md#accumulate) můžete provádět mapování a snižovat operace. U mnoha problémů však můžete použít algoritmus `parallel_transform` k paralelnímu provedení operace mapování a algoritmus `parallel_reduce` provede paralelní operaci zmenšení.

Následující příklad porovnává dobu potřebnou k výpočtu součtu primárních čísel v sériovém a paralelně. Fáze mapy transformuje hodnoty, které nejsou základní, na hodnotu 0 a fáze zmenšování sečte hodnoty.

[!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_7.cpp)]

Další příklad, který provádí mapu a zmenšuje paralelní operace, naleznete v tématu [How to: provádět mapování a snižovat paralelní operace](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

[[Nahoře](#top)]

## <a name="partitions"></a>Dělení práce

Aby se paralelizovat operace na zdroji dat, je důležitým krokem *rozdělit* zdroj do několika oddílů, ke kterým může mít Souběžný provoz více vláken. Dělicí metoda určuje, jak by měl paralelní algoritmus rozdělit rozsah mezi vlákny. Jak bylo vysvětleno dříve v tomto dokumentu, používá PPL výchozí mechanizmus pro dělení, který vytváří počáteční zatížení, a pak používá algoritmus, který je odcizen pro vyvážení těchto oddílů v případě nevyrovnaného zatížení. Například pokud iterace na jednom cyklu dokončí rozsah iterací, modul runtime znovu distribuuje práci z jiných vláken do tohoto vlákna. V některých scénářích ale můžete chtít zadat jiný mechanizmus dělení, který je vhodnější pro váš problém.

Algoritmy `parallel_for`, `parallel_for_each`a `parallel_transform` poskytují přetížené verze, které přijímají další parametr `_Partitioner`. Tento parametr definuje typ rozdělovače, který rozděluje práci. Tady jsou typy oddílů, které definuje PPL:

[Concurrency:: affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)<br/>
Rozdělí práci na pevný počet rozsahů (obvykle počet pracovních vláken, která jsou k dispozici pro práci na smyčce). Tento typ rozdělovače se podobá `static_partitioner`, ale vylepšuje spřažení mezipaměti tím, jak mapuje rozsahy na pracovní vlákna. Tento typ rozdělovače může zvýšit výkon, když se smyčka spouští přes stejnou datovou sadu několikrát (například smyčka v rámci smyčky) a data se vejdou do mezipaměti. Tento dělicí metoda není plně zapojená do zrušení. Nepoužívá taky sémantiku blokujícího blokování, takže se nedá použít s paralelními smyčkami, které mají dopřednou závislost.

[Concurrency:: auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)<br/>
Rozdělí práci do počátečního počtu rozsahů (obvykle se jedná o počet pracovních vláken, která jsou k dispozici pro práci na smyčce). Modul runtime používá tento typ ve výchozím nastavení, pokud nevoláte přetížený paralelní algoritmus, který přebírá `_Partitioner` parametr. Každý rozsah může být rozdělen do podrozsahů a tím umožňuje vyrovnávání zatížení. Po dokončení rozsahu práce modul runtime redistribuuje dílčí rozsahy práce z jiných vláken do tohoto vlákna. Tento dělicí metoda použijte v případě, že vaše úloha nepatří do jedné z ostatních kategorií, nebo pokud potřebujete plnou podporu pro zrušení nebo kooperativní blokování.

[Concurrency:: simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)<br/>
Rozdělí práci do rozsahů, aby měly všechny rozsahy alespoň počet iterací, které jsou určeny zadanou velikostí bloku. Tento typ rozdělovače se účastní vyrovnávání zatížení; modul runtime však nedělí rozsahy do dílčích rozsahů. Pro každý pracovní proces modul runtime kontroluje zrušení a provádí vyrovnávání zatížení po dokončení `_Chunk_size`ch iterací.

[Concurrency:: static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)<br/>
Rozdělí práci na pevný počet rozsahů (obvykle počet pracovních vláken, která jsou k dispozici pro práci na smyčce). Tento typ rozdělovače může zvýšit výkon, protože nepoužívá odcizení, a proto má méně režijních nákladů. Tento typ rozdělovače použijte, když Každá iterace paralelní smyčky provede pevný a jednotný objem práce a nepožadujete podporu pro zrušení nebo dopředné spolupráci.

> [!WARNING]
> Algoritmy `parallel_for_each` a `parallel_transform` podporují pouze kontejnery, které používají iterátory s náhodným přístupem (například std::[Vector](../../standard-library/vector-class.md)) pro oddíly statického, jednoduchého a spřažení. Použití kontejnerů, které používají obousměrné a dopředné iterátory, vytváří chybu při kompilaci. Výchozí dělicí metoda, `auto_partitioner`, podporuje všechny tři tyto typy iterátoru.

Tyto oddíly jsou obvykle používány stejným způsobem, s výjimkou `affinity_partitioner`. Většina typů oddílů neudržuje stav a modul runtime je nemění. Proto můžete vytvořit tyto objekty rozdělovače na webu volání, jak je znázorněno v následujícím příkladu.

[!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_8.cpp)]

Objekt `affinity_partitioner` však musíte předat jako ne`const`ný odkaz l-value, aby algoritmus mohl uložit stav pro budoucí opakované smyčky. Následující příklad ukazuje základní aplikaci, která provádí stejnou operaci na datové sadě paralelně více než jednou. Použití `affinity_partitioner` může zlepšit výkon, protože pole se pravděpodobně vejde do mezipaměti.

[!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_9.cpp)]

> [!CAUTION]
> Při úpravách stávajícího kódu, který spoléhá na sémantiku blokujícího blokování použití `static_partitioner` nebo `affinity_partitioner`, buďte opatrní. Tyto typy oddílů nevyužívají vyrovnávání zatížení nebo odcizení rozsahu, a proto mohou změnit chování aplikace.

Nejlepším způsobem, jak určit, jestli se má v kterémkoli scénáři použít dělicí metoda, je experimentovat a měřit, jak dlouho trvá operace v rámci reprezentativních zátěží a konfigurací počítačů. Statické dělení můžou například poskytovat významné zrychlení počítače, které mají jenom několik jader, ale můžou způsobit zpomalení v počítačích, které mají relativně mnoho jader.

[[Nahoře](#top)]

## <a name="parallel_sorting"></a>Paralelní řazení

PPL poskytuje tři algoritmy řazení: [Concurrency::p arallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::p arallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)a [Concurrency::p arallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Tyto algoritmy řazení jsou užitečné v případě, že máte datovou sadu, která je schopná využít paralelní řazení. Zejména řazení paralelně je užitečné, pokud máte velkou datovou sadu nebo pokud k řazení dat používáte výpočetní operaci porovnání. Každý z těchto algoritmů Seřadí prvky na místě.

Algoritmy `parallel_sort` a `parallel_buffered_sort` jsou algoritmy založené na porovnání. To znamená, že porovná prvky podle hodnoty. `parallel_sort` algoritmus nemá žádné další požadavky na paměť a je vhodný pro řazení pro obecné účely. `parallel_buffered_sort` algoritmus může poskytovat lepší výkon než `parallel_sort`, ale vyžaduje O (N) prostor.

`parallel_radixsort` algoritmus je založený na hodnotě hash. To znamená, že používá celočíselné klíče k řazení prvků. Pomocí klíčů může tento algoritmus přímo vypočítat cíl elementu namísto použití porovnání. Stejně jako u `parallel_buffered_sort`tento algoritmus vyžaduje O (N) místo.

Následující tabulka shrnuje důležité vlastnosti tří paralelních řadicích algoritmů.

|Algoritmus|Popis|Mechanismus řazení|Seřadit stabilitu|Požadavky na paměť|Složitost času|Přístup iterátoru|
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|
|`parallel_sort`|Řazení na základě porovnání obecného účelu.|Založený na porovnání (vzestupně)|Nestabilní|Žádné|O ((N/P) protokol (N/P) + 2N ((P-1)/P))|Náhodné|
|`parallel_buffered_sort`|Rychlejší řazení na základě porovnání obecných účelů, které vyžaduje O (N) prostor.|Založený na porovnání (vzestupně)|Nestabilní|Vyžaduje další znak O (N).|O ((N/P) protokol (N))|Náhodné|
|`parallel_radixsort`|Celočíselné řazení založené na klíčích, které vyžaduje O (N) prostor.|Založený na hodnotě hash|Stable|Vyžaduje další znak O (N).|O (N/P)|Náhodné|

Následující ilustrace znázorňuje důležité vlastnosti tří paralelních řadicích algoritmů.

![Porovnání algoritmů řazení](../../parallel/concrt/media/concrt_parallel_sorting.png "Porovnání algoritmů řazení")

Tyto algoritmy paralelního řazení dodržují pravidla zrušení a zpracování výjimek. Další informace o zrušení a zpracování výjimek v Concurrency Runtime naleznete v tématu [zrušení paralelních algoritmů](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms) a [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

> [!TIP]
> Tyto algoritmy paralelního řazení podporují sémantiku přesunutí. Můžete definovat operátor přiřazení přesunutí, aby bylo možné operace swapu provádět efektivněji. Další informace o tom, jak se sémantika přesunutí a operátor přiřazení přesunutí, naleznete v tématu [rvalue reference deklarátor: & &](../../cpp/rvalue-reference-declarator-amp-amp.md), [konstruktory přesunu aC++operátory přiřazení přesunu ()](../../cpp/move-constructors-and-move-assignment-operators-cpp.md). Pokud nezadáte operátor přiřazení přesunu nebo funkci swap, používají algoritmy pro řazení konstruktor kopie.

Následující základní příklad ukazuje, jak použít `parallel_sort` k řazení `vector` hodnot `int`. Ve výchozím nastavení používá `parallel_sort` k porovnání hodnot [std:: míň](../../standard-library/less-struct.md) .

[!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_10.cpp)]

Tento příklad ukazuje, jak poskytnout vlastní funkci Compare. Používá metodu [std:: Complex:: Real](../../standard-library/complex-class.md#real) pro řazení hodnot [std:: complex\<Double >](../../standard-library/complex-double.md) ve vzestupném pořadí.

[!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_11.cpp)]

Tento příklad ukazuje, jak poskytnout funkci hash `parallel_radixsort`mu algoritmu. V tomto příkladu se seřadí 3D body. Body jsou seřazené na základě jejich vzdálenosti od referenčního bodu.

[!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_12.cpp)]

Pro ilustraci tento příklad používá relativně malou datovou sadu. Můžete zvětšit počáteční velikost vektoru a experimentovat se zvýšením výkonu většího počtu datových sad.

Tento příklad používá výraz lambda jako funkci hash. Můžete také použít jednu z předdefinovaných implementací třídy std::[hash](../../standard-library/hash-class.md) nebo definovat vlastní specializaci. Můžete použít také vlastní objekt funkce hash, jak je znázorněno v následujícím příkladu:

[!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_13.cpp)]

[!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_14.cpp)]

Funkce hash musí vracet celočíselný typ ([std:: is_integral:: Value](../../standard-library/is-integral-class.md) musí mít **hodnotu true**). Tento integrálový typ musí být převoditelné na typ `size_t`.

### <a name="choose_sort"></a>Výběr algoritmu řazení

V mnoha případech `parallel_sort` poskytuje nejlepší rovnováhu mezi rychlostí a výkonem paměti. Když ale zvětšíte velikost sady dat, zvýší se počet dostupných procesorů nebo složitost funkce Compare, `parallel_buffered_sort` nebo `parallel_radixsort` může lépe dopracovat. Nejlepším způsobem, jak určit, který algoritmus řazení použít v kterémkoli daném scénáři, je experimentovat a měřit dobu potřebnou k řazení typických dat v rámci reprezentativních konfigurací počítačů. Při volbě strategie řazení mějte na paměti následující pokyny.

- Velikost sady dat. V tomto dokumentu *malá* datová sada obsahuje méně než 1 000 prvků, *střední* datová sada obsahuje mezi 10 000 a 100 000 elementy a *Velká* datová sada obsahuje více než 100 000 prvků.

- Množství práce, které provádí funkce Compare nebo funkce hash.

- Množství dostupných výpočetních prostředků.

- Charakteristiky vaší datové sady. Například jeden algoritmus může fungovat dobře pro data, která jsou už skoro seřazená, ale ne i pro data, která jsou zcela Neseřazená.

- Velikost bloku. Volitelný `_Chunk_size` argument určuje, kdy se algoritmus přepne z paralelního na implementaci sériového řazení, protože rozdělí celkové řazení na menší jednotky práce. Pokud například zadáte 512, algoritmus se přepne do sériové implementace, pokud pracovní jednotka obsahuje 512 nebo méně prvků. Sériová implementace může zvýšit celkový výkon, protože eliminuje režii, která je nutná k paralelnímu zpracování dat.

Je možné, že nebudete mít volnost v paralelním řazení malých datových sad, a to i v případě, že máte velký počet dostupných výpočetních prostředků nebo funkce Compare nebo hash, která provádí poměrně velký objem práce. Pomocí funkce [std:: Sort](../../standard-library/algorithm-functions.md#sort) můžete seřadit malé datové sady. (`parallel_sort` a `parallel_buffered_sort` volání `sort`, když zadáte velikost bloku, která je větší než datová sada, ale `parallel_buffered_sort` by musela přidělit (N) místo, což by mohlo trvat delší dobu, protože by došlo k kolizi uzamčení nebo přidělení paměti.)

Pokud je nutné ušetřit paměť nebo přiřadíte do svého přidělování paměti, použijte `parallel_sort` k seřazení datové sady střední velikosti. `parallel_sort` nevyžaduje žádné další místo. ostatní algoritmy vyžadují v (N) prostoru.

Použijte `parallel_buffered_sort` pro řazení středně velkých datových sad a v případě, že vaše aplikace splňuje další požadavky na místo (N). `parallel_buffered_sort` mohou být obzvláště užitečné, pokud máte velký počet výpočetních prostředků nebo funkci funkce Compare nebo funkci hash.

Použijte `parallel_radixsort` k řazení velkých datových sad a v případě, že vaše aplikace splňuje další požadavky na místo (N). `parallel_radixsort` může být obzvláště užitečná, pokud je ekvivalentní operace porovnání dražší, nebo když jsou obě operace nákladné.

> [!CAUTION]
> Implementace dobré funkce hash vyžaduje, abyste znali rozsah datové sady a jak jsou všechny prvky v datové sadě transformované na odpovídající hodnotu bez znaménka. Vzhledem k tomu, že operace hash funguje na hodnotách bez znaménka, zvažte jinou strategii řazení, pokud nelze vytvořit nepodepsané hodnoty hash.

Následující příklad porovnává výkon `sort`, `parallel_sort`, `parallel_buffered_sort`a `parallel_radixsort` se stejnou velkou sadou náhodných dat.

[!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_15.cpp)]

V tomto příkladu předpokládáme, že při seřazení je přijatelné přidělovat (N) prostor, `parallel_radixsort` pro tuto datovou sadu v této konfiguraci počítače nejlépe vyplní tuto datovou sadu.

[[Nahoře](#top)]

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Postupy: Programování smyčky parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|Ukazuje, jak použít algoritmus `parallel_for` k vynásobení matice.|
|[Postupy: Programování smyčky parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|Ukazuje, jak použít algoritmus `parallel_for_each` k výpočtu počtu primárních čísel v objektu [std:: Array](../../standard-library/array-class-stl.md) paralelně.|
|[Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Ukazuje, jak použít algoritmus `parallel_invoke` ke zlepšení výkonu bitonického algoritmu řazení.|
|[Postupy: Použití algoritmu parallel_invoke k provádění paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Ukazuje, jak použít algoritmus `parallel_invoke` ke zlepšení výkonu programu, který provádí více operací na sdíleném zdroji dat.|
|[Postupy: Paralelní provádění operací mapování a redukce](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Ukazuje, jak použít algoritmus `parallel_transform` a `parallel_reduce` k provedení mapy a snížení operace, která počítá výskyt slov v souborech.|
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Popisuje PPL, který poskytuje imperativní programovací model, který podporuje škálovatelnost a snadné použití při vývoji souběžných aplikací.|
|[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)|Vysvětluje roli zrušení v PPL, zrušení paralelní práce a určení, kdy se skupina úloh zruší.|
|[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Vysvětluje roli zpracování výjimek v Concurrency Runtime.|

## <a name="reference"></a>Referenční informace

[parallel_for funkce](reference/concurrency-namespace-functions.md#parallel_for)

[parallel_for_each funkce](reference/concurrency-namespace-functions.md#parallel_for_each)

[parallel_invoke funkce](reference/concurrency-namespace-functions.md#parallel_invoke)

[affinity_partitioner – třída](../../parallel/concrt/reference/affinity-partitioner-class.md)

[auto_partitioner – třída](../../parallel/concrt/reference/auto-partitioner-class.md)

[simple_partitioner – třída](../../parallel/concrt/reference/simple-partitioner-class.md)

[static_partitioner – třída](../../parallel/concrt/reference/static-partitioner-class.md)

[parallel_sort funkce](reference/concurrency-namespace-functions.md#parallel_sort)

[parallel_buffered_sort funkce](reference/concurrency-namespace-functions.md#parallel_buffered_sort)

[parallel_radixsort funkce](reference/concurrency-namespace-functions.md#parallel_radixsort)
