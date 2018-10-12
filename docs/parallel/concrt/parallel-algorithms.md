---
title: Paralelní algoritmy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parallel algorithms [Concurrency Runtime]
ms.assetid: 045dca7b-4d73-4558-a44c-383b88a28473
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1eb46754f80bca89419e6c3c85db94ec802df2f
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163397"
---
# <a name="parallel-algorithms"></a>Paralelní algoritmy

Knihovna paralelních vzorů (PPL) poskytuje algoritmy, které provádějí práci současně na kolekce dat. Tyto algoritmy se podobají ve standardní knihovně jazyka C++.

Paralelní algoritmy se skládají z existující funkce v modulu Runtime souběžnosti. Například [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) používá algoritmus [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objekt pro provedení iteracích paralelní smyčky. `parallel_for` Algoritmus oddíly pracovat způsobem optimální zadaný počet dostupných výpočetních prostředků.

##  <a name="top"></a> Oddíly

- [Algoritmus parallel_for](#parallel_for)

- [Algoritmus parallel_for_each](#parallel_for_each)

- [Algoritmus parallel_invoke](#parallel_invoke)

- [Algoritmy parallel_transform a parallel_reduce](#parallel_transform_reduce)

    - [Algoritmus parallel_transform](#parallel_transform)

    - [Algoritmus parallel_reduce](#parallel_reduce)

    - [Příklad: Provádění mapování a redukce paralelní](#map_reduce_example)

- [Rozdělení práce](#partitions)

- [Paralelní řazení](#parallel_sorting)

    - [Volba řadicího algoritmu](#choose_sort)

##  <a name="parallel_for"></a> Algoritmus parallel_for

[Concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus opakovaně provádí stejnou úlohu současně. Každá z těchto úloh parametrizovanou hodnotu iterace. Tento algoritmus je užitečné v případě, že máte tělo smyčky, který nesdílí prostředky mezi iterací smyčky.

`parallel_for` Algoritmus rozděluje úlohy optimálně pro paralelní zpracování. Používá přebírající práci algoritmus a rozsah zcizování pro tyto oddíly po nevyváženou úlohy. Spolupráce při blokování jedné iterace smyčky, pokud modul runtime přerozděluje rozsah iterace, který je přiřazen k tomuto vláknu do jiných vláken nebo procesorů. Podobně po dokončení vlákna celou řadu iterací, modul runtime přerozděluje práce z jiných vláken pro toto vlákno. `parallel_for` Algoritmus také podporuje *vnořené paralelismu*. Když jeden paralelní smyčky obsahuje jiné paralelní smyčky, souřadnice modul runtime prostředků pro zpracování mezi smyček nejúčinnějším způsobem pro paralelní zpracování.

`parallel_for` Algoritmus využívající dlaždice má několik přetížených verzí. První verze trvá počáteční hodnotu, koncová hodnota a pracovní funkce (výraz lambda, objekt funkce nebo ukazatel na funkci). Druhá verze trvá počáteční hodnotu, koncová hodnota, hodnota podle kterého krok a pracovní funkce. První verze této funkce využívá jako hodnota kroku 1. Zbývající verze trvat rozdělovač objekty, které vám umožní určit jak `parallel_for` by měl oddíl rozsahy mezi vlákny. Dělicí metody jsou vysvětlené podrobněji v oddílu [rozdělení práce](#partitions) v tomto dokumentu.

Můžete převést mnoho `for` smyčky použít `parallel_for`. Ale `parallel_for` algoritmus se liší od `for` příkaz následujícími způsoby:

- `parallel_for` Algoritmus `parallel_for` nepracuje v předem určeném pořadí úkolů.

- `parallel_for` Algoritmus nepodporuje podmínky libovolného ukončení. `parallel_for` Algoritmus skončí aktuální hodnotu proměnné iterace je jeden menší než `last`.

- `_Index_type` Parametr typu musí být celočíselného typu. Tento celočíselný typ lze podepsané nebo nepodepsané.

- Iterace smyčky musí být vpřed. `parallel_for` Algoritmus vyvolá výjimku typu [std::invalid_argument](../../standard-library/invalid-argument-class.md) Pokud `_Step` parametru je menší než 1.

- Mechanismus zpracování výjimek `parallel_for` algoritmus se liší od `for` smyčky. Pokud více výjimek probíhají souběžně v těle paralelní smyčky, modul runtime rozšíří pouze jednu z výjimek na vlákno, které volá `parallel_for`. Kromě toho pokud jedné iterace smyčky vyvolá výjimku, modul runtime nezastaví okamžitě celkové smyčky. Místo toho smyčky se umístí do stavu zrušeno a modul runtime zahodí všechny úkoly, které ještě nebyly spuštěny. Další informace o zpracování výjimek a paralelní algoritmy, naleznete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

I když `parallel_for` algoritmus nepodporuje podmínky libovolného ukončení, vám pomůže zrušení zastavit všechny úlohy. Další informace o zrušení naleznete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).

> [!NOTE]
>  Plánování nákladů, že výsledky z vyrovnávání zatížení a podpora pro funkce, jako je zrušení nemusí překonat výhody paralelně prováděných do těla smyčky, zejména pokud tělo smyčky je poměrně malá. Tato dodatečná režie můžete minimalizovat pomocí rozdělovače v paralelní smyčce. Další informace najdete v tématu [rozdělení práce](#partitions) dále v tomto dokumentu.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní struktura `parallel_for` algoritmus. Tento příklad vytiskne do konzoly pro každou hodnotu v rozsahu [1, 5] paralelně.

[!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_1.cpp)]

Tento příklad vytvoří následující ukázkový výstup:

```Output
1 2 4 3 5
```

Vzhledem k tomu, `parallel_for` algoritmus funguje pro každou položku paralelně, pořadí, ve kterém jsou vypsány hodnoty do konzoly se bude lišit.

Úplný příklad používající `parallel_for` algoritmus, najdete v článku [jak: smyčky Parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md).

[[Horní](#top)]

##  <a name="parallel_for_each"></a> Algoritmus parallel_for_each

[: Concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus provádí úlohy na iterativní kontejneru, jako je například těch, které poskytuje standardní knihovnou jazyka C++, paralelně. Používá stejnou logiku dělení, který `parallel_for` algoritmus používá.

`parallel_for_each` Algoritmus vypadá podobně jako standardní knihovny C++ [std::for_each](../../standard-library/algorithm-functions.md#for_each) algoritmus, s výjimkou, že `parallel_for_each` algoritmus spustí úlohy současně. Další paralelní algoritmy, jako jsou `parallel_for_each` nepracuje v určitém pořadí úkolů.

I když `parallel_for_each` algoritmus funguje na dopředné iterátory a iterátory s náhodným přístupem, vrací lepší výsledky s iterátory s náhodným přístupem.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní struktura `parallel_for_each` algoritmus. Každé hodnoty v tomto příkladu tiskne na konzolu [std::array](../../standard-library/array-class-stl.md) objekt paralelně.

[!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_2.cpp)]

Tento příklad vytvoří následující ukázkový výstup:

```Output
4 5 1 2 3
```

Vzhledem k tomu, `parallel_for_each` algoritmus funguje pro každou položku paralelně, pořadí, ve kterém jsou vypsány hodnoty do konzoly se bude lišit.

Úplný příklad používající `parallel_for_each` algoritmus, najdete v článku [jak: smyčky Parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md).

[[Horní](#top)]

##  <a name="parallel_invoke"></a> Algoritmus parallel_invoke

[Concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus spustí sadu úloh paralelně. Nevrátí se až do dokončení každé úlohy. Tento algoritmus je užitečné v případě, že máte několik nezávislých úloh, které chcete spustit ve stejnou dobu.

`parallel_invoke` Algoritmus přijímá jako parametry řadu pracovní funkce (funkce lambda, objektů funkcí nebo ukazatele na funkce). `parallel_invoke` Algoritmus je přetížena pro převzetí mezi 2 až 10 parametry. Každá funkce, která můžete předat `parallel_invoke` nezbytné žádné parametry.

Další paralelní algoritmy, jako jsou `parallel_invoke` nepracuje v určitém pořadí úkolů. Téma [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md) vysvětluje, jak `parallel_invoke` algoritmus má vztah k úloh a skupin úloh.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní struktura `parallel_invoke` algoritmus. Tento příklad příkladu volá souběžně `twice` funkce na tři místní proměnné a vytiskne výsledek do konzoly.

[!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_3.cpp)]

Tento příklad vytvoří následující výstup:

```Output
108 11.2 HelloHello
```

Kompletní příklady, které používají `parallel_invoke` algoritmus, najdete v článku [postupy: použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) a [postupy: použití algoritmu parallel_invoke k provádění paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

[[Horní](#top)]

##  <a name="parallel_transform_reduce"></a> Algoritmy parallel_transform a parallel_reduce

[Concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) a [concurrency::parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) algoritmy jsou paralelní verze algoritmů standardní knihovny C++ [std::transform](../../standard-library/algorithm-functions.md#transform)a [std::accumulate](../../standard-library/numeric-functions.md#accumulate)v uvedeném pořadí. Verze modulu Runtime souběžnosti se chovají jako standardní knihovny C++ verze, s tím rozdílem, že pořadí operací není určit, protože paralelně spustit. Pomocí těchto algoritmů při práci se sadou, který je dostatečně velký, aby získáte výhody výkonu a škálovatelnosti pro paralelní zpracování.

> [!IMPORTANT]
>  `parallel_transform` a `parallel_reduce` algoritmy podporovat pouze náhodného přístupu, obousměrné a dopředné iterátory, protože tyto iterátory vytvořit stabilní paměti adresy. Také musíte vytvořit tyto iterátory jinou hodnotu než`const` l hodnoty.

###  <a name="parallel_transform"></a> Algoritmus parallel_transform

Můžete použít `parallel transform` algoritmus k provedení mnoha paralelizace operace s daty. Například můžete:

- Upravit jas bitovou kopii a provádění jiných operací zpracování obrazu.

- Součet nebo vzít součin mezi dvěma vektory a provádět další číselné výpočty vektorů.

- Proveďte trasování 3D ray, kde každé iteraci odkazuje na jeden pixel, který musí být vykreslen.

Následující příklad ukazuje základní struktura, která slouží k volání `parallel_transform` algoritmus. V tomto příkladu Neguje každý prvek std::[vektoru](../../standard-library/vector-class.md) objektu dvěma způsoby. První způsob využívá výraz lambda. Druhý způsob využívá [std::negate](../../standard-library/negate-struct.md), která je odvozena z [std::unary_function](../../standard-library/unary-function-struct.md).

[!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_4.cpp)]

> [!WARNING]
>  Tento příklad ukazuje základní použití `parallel_transform`. Protože je pracovní funkce neprovádí značné množství práce, velký nárůst výkon neočekává v tomto příkladu.

`parallel_transform` Algoritmus využívající dlaždice má dvě přetížení. První přetížení má jeden vstupní oblast a jednočlenné funkce. Jednočlenné funkce může být výraz lambda, který přebírá jeden argument, funkce objektu nebo typu, který je odvozen od `unary_function`. Druhé přetížení má dva vstupní rozsahy a binární funkce. Binární funkce může být výraz lambda, který přebírá dva argumenty, objekt funkce nebo typ, který je odvozen od [std::binary_function](../../standard-library/binary-function-struct.md). Následující příklad znázorňuje tyto rozdíly.

[!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_5.cpp)]

> [!IMPORTANT]
>  Iterátor, který zadáte pro výstup `parallel_transform` musí zcela překrývat vstupního iterátoru nebo nemusí být stejné. Chování tento algoritmus neurčená, pokud vstupní a výstupní iterátory se částečně překrývají.

###  <a name="parallel_reduce"></a> Algoritmus parallel_reduce

`parallel_reduce` Algoritmus je užitečné, když máte pořadí operací, které splňují asociativní vlastnost. (Tento algoritmus nevyžaduje, aby vlastnost komutativní.) Tady jsou některé operace, které můžete provádět pomocí `parallel_reduce`:

- Vynásobte pořadí matice pro vytvoření matice.

- Vektor vynásobte posloupnost matice pro vytvoření vektoru.

- Výpočetní délka posloupnost řetězců.

- Seznam prvků, jako jsou řetězce zkombinujte do jednoho elementu.

V následujícím základním příkladu ukazuje, jak používat `parallel_reduce` algoritmus zkombinovat posloupnost řetězců do jednoho řetězce. Stejně jako u příklady `parallel_transform`, zvýšení výkonu nejsou očekávány v tento základní příklad.

[!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_6.cpp)]

V mnoha případech si můžete představit `parallel_reduce` jako zkratka pro použití `parallel_for_each` algoritmus spolu s [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třídy.

###  <a name="map_reduce_example"></a> Příklad: Provádění mapování a redukce paralelní

A *mapy* operace platí funkce pro každou hodnotu v pořadí. A *snížit* operace kombinuje elementy sekvence do jedné hodnoty. Můžete použít standardní knihovny C++ [std::transform](../../standard-library/algorithm-functions.md#transform) a [std::accumulate](../../standard-library/numeric-functions.md#accumulate) functions k provádění mapování a redukční operace. Pro mnoho problémů, ale můžete použít `parallel_transform` algoritmus paralelní provádění operací mapování a `parallel_reduce` algoritmus paralelní provádění operace zmenšit.

Následující příklad porovnává času potřebného k nalezení součtu prvočísel sériově i paralelně. Fáze mapy transformuje bez primárního hodnoty 0 a snižte částky fáze hodnoty.

[!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_7.cpp)]

Další příklad, který provede mapování a snížit operace paralelně, naleznete v tématu [postupy: provádění mapování a snížit operace paralelně](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

[[Horní](#top)]

##  <a name="partitions"></a> Rozdělení práce

Pro paralelní zpracování operace na zdroji dat, je základním krokem *oddílu* zdroje do několika oddílů, které může přistupovat souběžně více vláken. Rozdělovače Určuje, jak by měl paralelního algoritmu oddílu rozsahy mezi vlákny. Jak bylo popsáno dříve v tomto dokumentu, PPL používá výchozí dělení mechanismus, který vytvoří počáteční úlohy a pak používá algoritmus a rozsah zcizování pro tyto oddíly po nevyváženou úlohy přebírající práci. Například po dokončení jedné iterace smyčky celou řadu iterací, modul runtime přerozděluje práce z jiných vláken pro toto vlákno. Pro některé scénáře, můžete ale zadat jiný mechanismus dělení, který se lépe hodí pro váš problém.

`parallel_for`, `parallel_for_each`, A `parallel_transform` algoritmy poskytuje přetížené verze, které může další parametr, `_Partitioner`. Tento parametr definuje typ dělicí metody, který rozděluje práci. Tady jsou typy dělicí metody, které definuje PPL:

[Concurrency::affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)<br/>
Rozdělí práce do pevný počet rozsahů (obvykle počet pracovních vláken, které jsou k dispozici pro práci na smyčky). Vypadá podobně jako tento typ rozdělovač `static_partitioner`, ale zlepší se tím, jak mapuje rozsahy pracovních vláken mezipaměti spřažení. Tento typ dělicí metody může zlepšit výkon, při smyčky je spouštěné přes stejné datové sady více než jednou (například smyčka v rámci smyčky) a vyhovuje data v mezipaměti. Tato dělicí metoda není součástí plně zrušení. Také nepoužívá sémantiku spolupráce blokování a proto jej nelze použít s paralelních smyček, které mají dopředné závislost.

[Concurrency::auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)<br/>
Rozdělí práce do počáteční počet rozsahů (obvykle počet pracovních vláken, které jsou k dispozici pro práci na smyčky). Modul runtime používá tento typ ve výchozím nastavení, když není volána přetížená paralelního algoritmu, který přijímá `_Partitioner` parametru. Každý rozsah je možné rozdělit do dílčí rozsahy a tím povolí Vyrovnávání zatížení na výskyt. Po dokončení se širokou škálou práce, modul runtime přerozděluje dílčí rozsahy práce z jiných vláken pro toto vlákno. Tato dělicí metoda použijte, pokud vaše úloha nespadá pod jednu z jiných kategorií nebo vyžadovat plnou podporu pro zrušení nebo spolupráce blokování.

[Concurrency::simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)<br/>
Rozdělí práce do oblasti tak, aby každá oblast má alespoň počet iterací, které jsou určeny velikost daného bloku. Tato dělicí metoda typ se účastní Vyrovnávání zatížení; modul runtime však nedělí rozsahů do dílčí rozsahy. Pro každý zaměstnanec, modul runtime vyhledává zrušení a provede Vyrovnávání zatížení po `_Chunk_size` dokončení iterace.

[Concurrency::static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)<br/>
Rozdělí práce do pevný počet rozsahů (obvykle počet pracovních vláken, které jsou k dispozici pro práci na smyčky). Tento typ dělicí metody může zlepšit výkon, protože nepoužívá přebírající práci a proto má nižší režijní náklady. Pomocí tohoto typu rozdělovač po jednotlivých iteracích paralelní smyčky provádí pevné a jednotné množství práce a nepožadujete podporu pro zrušení nebo z nich dál spolupráce blokování.

> [!WARNING]
>  `parallel_for_each` a `parallel_transform` algoritmy podporují pouze kontejnery, které používají iterátory s náhodným přístupem (například std::[vektoru](../../standard-library/vector-class.md)) pro dělicí metody statické, jednoduchý a vztahů. Použití kontejnerů, které používají obousměrné a dopředných iterátorů způsobí chybu kompilace. Rozdělovač výchozí `auto_partitioner`, podporuje všechny tři typy iterátoru.

Tato dělicí metody se obvykle používají stejným způsobem, s výjimkou `affinity_partitioner`. Většina typů dělicí metody nemají stav a nezmění modulem runtime. Proto můžete vytvořit tyto objekty dělicí metody v lokalitě volání, jak je znázorněno v následujícím příkladu.

[!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_8.cpp)]

Nicméně je nutné předat `affinity_partitioner` objektu jako non -`const`, l hodnota odkazovat tak, aby algoritmus může ukládání stavu pro budoucí cykly opakovaně používat. Následující příklad ukazuje základní aplikaci, která provede stejné operace na datové sadě paralelně více než jednou. Použití `affinity_partitioner` může zlepšit výkon, protože pole je pravděpodobné, aby se vešel do mezipaměti.

[!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_9.cpp)]

> [!CAUTION]
>  Buďte opatrní při úpravě existujícího kódu, která se spoléhá na spolupráce blokování sémantiku používat `static_partitioner` nebo `affinity_partitioner`. Tyto typy rozdělovač nepoužívejte Vyrovnávání zatížení nebo rozsah krádež a proto můžete změnit chování aplikace.

Nejlepší způsob, jak určit, jestli se má použít v jakékoli situaci rozdělovače je můžete experimentovat a změřit, jak dlouho trvá, než operace dokončete podle reprezentativní zatížením a konfigurací počítače. Například statické dělení může poskytnout výrazné zrychlení v počítači více jader, který má pouze několik jader, ale může způsobit zpomalení na počítačích, které mají relativně mnoha jádrech.

[[Horní](#top)]

##  <a name="parallel_sorting"></a> Paralelní řazení

PPL poskytuje tři algoritmy řazení: [concurrency::parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort), a [concurrency::parallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Tyto algoritmy řazení jsou užitečné v případě, že máte sadu dat, která může přinést seřazený paralelně. Zejména řazení paralelně je užitečné, pokud máte velkou datovou sadu nebo při použití operace výpočetně náročné porovnání řazení dat. Každá z těchto algoritmů Seřadí prvky na místě.

`parallel_sort` a `parallel_buffered_sort` algoritmy jsou algoritmy založené na porovnání. To znamená že porovnávat elementy podle hodnoty. `parallel_sort` Algoritmus nemá žádné požadavky na další paměť a je vhodný pro řazení pro obecné účely. `parallel_buffered_sort` Algoritmus můžete provádět lepší než `parallel_sort`, ale vyžaduje O(N) místa.

`parallel_radixsort` Algoritmus je založen na algoritmu hash. To znamená používá klíče celého čísla řadí prvky. Pomocí klíčů, můžete tento algoritmus přímo výpočetní cílového elementu namísto použití porovnávání. Stejně jako `parallel_buffered_sort`, tento algoritmus vyžaduje O(N) místa.

Následující tabulka shrnuje důležité vlastnosti tři paralelní algoritmy řazení.

|algoritmus|Popis|Mechanismus řazení|Řazení Stability|Požadavky na paměť|Čas složitost|Přístup k iterátoru|
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|
|`parallel_sort`|Pro obecné účely na základě porovnání řazení.|Na základě porovnání (vzestupně)|Nestabilní|Žádné|O((N/P)log(N/P) + 2N((P-1)/P))|náhodné|
|`parallel_buffered_sort`|Rychlejší pro obecné účely na základě porovnání řazení, která vyžaduje O(N) místa.|Na základě porovnání (vzestupně)|Nestabilní|Vyžaduje další prostor O(N)|O((N/P)log(N))|náhodné|
|`parallel_radixsort`|Celé číslo na základě klíčů řazení, která vyžaduje O(N) místa.|Na základě hodnoty hash|Stabilní verze|Vyžaduje další prostor O(N)|O(N/P)|náhodné|

Následující obrázek znázorňuje důležité vlastnosti tři paralelní algoritmy řazení více graficky.

![Porovnání řazení algoritmů](../../parallel/concrt/media/concrt_parallel_sorting.png "concrt_parallel_sorting")

Tyto paralelní algoritmy řazení podle pravidel zrušení a zpracování výjimek. Další informace o zrušení a zpracování výjimek v Concurrency Runtime naleznete v tématu [zrušení paralelních algoritmů](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms) a [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

> [!TIP]
>  Tyto paralelní algoritmy řazení podporují přesunutí sémantiky. Můžete definovat operátor přiřazení přesunutí umožňující operace prohození každý efektivněji. Další informace o sémantiku přesunu a operátor přiřazení přesunutí najdete v tématu [Rvalue Reference Declarator: & &](../../cpp/rvalue-reference-declarator-amp-amp.md), a [konstruktory přesunutí a operátory přiřazení přesunutí (C++)](../../cpp/move-constructors-and-move-assignment-operators-cpp.md). Pokud nezadáte swap – funkce a operátor přiřazení přesunutí, algoritmy řazení pomocí konstruktoru kopie.

V následujícím základním příkladu ukazuje, jak používat `parallel_sort` řazení `vector` z `int` hodnoty. Ve výchozím nastavení `parallel_sort` používá [std::less](../../standard-library/less-struct.md) k porovnání hodnoty.

[!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_10.cpp)]

Tento příklad ukazuje, jak poskytnout vlastní porovnání funkci. Používá [std::complex::real](../../standard-library/complex-class.md#real) metoda seřadíte [std::complex\<double >](../../standard-library/complex-double.md) hodnoty ve vzestupném pořadí.

[!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_11.cpp)]

Tento příklad ukazuje, jak poskytnout hashovací funkce, která se `parallel_radixsort` algoritmus. Tento příklad řadí 3D body. Body jsou seřazeny na základě jejich vzdálenost od referenčního bodu.

[!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_12.cpp)]

Tento příklad používá pro ilustraci, relativně malé datové sady. Můžete zvýšit počáteční velikost vektoru a experimentovat s vylepšení výkonu prostřednictvím větších datových sad.

Tento příklad používá výraz lambda jako funkce hash. Můžete také použít jednu z předdefinovaných implementací std::[hash – třída](../../standard-library/hash-class.md) nebo definovat vlastní specializace. Objekt vlastní hashovací funkce, můžete použít také, jak je znázorněno v tomto příkladu:

[!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_13.cpp)]

[!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_14.cpp)]

Funkce hash musí vrátit integrální typ ([std::is_integral::value](../../standard-library/is-integral-class.md) musí být **true**). Tento celočíselný typ musí být převoditelná na typ `size_t`.

###  <a name="choose_sort"></a> Volba řadicího algoritmu

V mnoha případech `parallel_sort` poskytuje optimální rovnováhu mezi výkonem rychlost a paměti. Ale při zvětšit velikost datové sady, počet dostupných procesorů a složitosti vaší funkce porovnání `parallel_buffered_sort` nebo `parallel_radixsort` můžete líp fungovat. Nejlepší způsob, jak určit, které algoritmus řazení pro použití v jakékoli situaci je můžete experimentovat a změřit, jak dlouho trvá řazení typické dat v rámci reprezentativní konfiguraci počítače. Tyto pokyny při mějte volba strategie řazení.

- Velikost datové sady. V tomto dokumentu *malé* datová sada obsahuje méně než 1 000 prvků *střední* datová sada obsahuje mezi elementy 10 000 a 100 000 a *velké* datová sada obsahuje více než 100 000 prvků.

- Množství práce, které provádí porovnání funkce nebo funkce hash.

- Množství dostupných výpočetních prostředcích.

- Vlastnosti datové sady. Například jeden algoritmus může provádět i pro data, která je už skoro seřazený, ale ne i pro data, která je zcela seřazená.

- Velikost bloku. Volitelný `_Chunk_size` argument určuje, kdy algoritmus přepne z paralelní provádění sériového portu řazení jako rozděluje celkové řazení do menších jednotek práce. Například když zadáte 512, algoritmus se přepne do sériové provádění, když pracovní jednotka obsahuje prvky 512 nebo méně. Sériové provádění může zvýšit celkový výkon, protože to eliminuje režijní náklady, které je nutné ke zpracování dat v paralelní.

Nemusí být vhodné si řazení na malou sadu dat současně, i když máte velký počet dostupných výpočetních prostředcích nebo relativně velké množství práce provádí porovnání funkce nebo funkce hash. Můžete použít [std::sort](../../standard-library/algorithm-functions.md#sort) funkce řazení malé datové sady. (`parallel_sort` a `parallel_buffered_sort` volání `sort` při zadávání velikost bloku dat, který je větší než datová sada; však `parallel_buffered_sort` by jste k přidělení místa O(N), což může trvat déle kvůli zámku kolize nebo paměť přidělení.)

Pokud musíte konzervaci paměti nebo váš přidělení paměti je v souladu s kolize zámků, použijte `parallel_sort` seřadíte středně velké datové sady. `parallel_sort` vyžaduje žádné další místo; jiné algoritmy vyžadují O(N) místa.

Použití `parallel_buffered_sort` seřadíte středně velké datové sady a pokud vaše aplikace splňovat další požadavek na prostor O(N). `parallel_buffered_sort` může být zvlášť užitečné, když máte velké množství výpočetních prostředků nebo nákladné porovnat funkce nebo funkce hash.

Použití `parallel_radixsort` seřadíte velkých datových sad a pokud vaše aplikace splňovat další požadavek na prostor O(N). `parallel_radixsort` může být zvlášť užitečné, pokud je operace porovnání ekvivalentní dražší, nebo když jsou nákladné operace.

> [!CAUTION]
>  Implementace dobré hashovací funkce vyžaduje, že znáte rozsah datové sady a jak je každý prvek v datové sadě transformuje na odpovídající hodnoty bez znaménka. Protože hodnota hash operace funguje u hodnot bez znaménka, zvažte různé strategie řazení Pokud hodnoty bez znaménka hash nelze vytvořil.

Následující příklad porovnává výkon `sort`, `parallel_sort`, `parallel_buffered_sort`, a `parallel_radixsort` stejné velké sady náhodná data.

[!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_15.cpp)]

V tomto příkladu se předpokládá, že je přijatelné k přidělení místa O(N) během řazení, `parallel_radixsort` provede nejlepší pro tuto datovou sadu v této konfiguraci počítače.

[[Horní](#top)]

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Postupy: Programování smyčky parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|Ukazuje způsob použití `parallel_for` algoritmus k provedení násobení matic.|
|[Postupy: Programování smyčky parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|Ukazuje způsob použití `parallel_for_each` algoritmus, který se Vypočítat hodnotu count prvočísel v [std::array](../../standard-library/array-class-stl.md) objekt paralelně.|
|[Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Ukazuje způsob použití `parallel_invoke` algoritmus pro zlepšení výkonu bitonického algoritmu řazení.|
|[Postupy: Použití algoritmu parallel_invoke k provádění paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Ukazuje způsob použití `parallel_invoke` algoritmus pro zlepšení výkonu programu, který provádí více operací na sdílený zdroj dat.|
|[Postupy: Paralelní provádění operací mapování a redukce](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Ukazuje způsob použití `parallel_transform` a `parallel_reduce` algoritmy s cílem provést mapy a omezit operace, která vypočítá počet výskytů slova v souborech.|
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Popisuje PPL, který poskytuje imperativní programovací model, který podporuje škálovatelnost a snadné použití pro vývoj souběžných aplikací.|
|[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)|Vysvětluje roli zrušení v knihovně PPL, jak zrušení paralelně prováděných úloh a jak určit, kdy je zrušena skupinu úloh.|
|[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Vysvětluje roli zpracování výjimek v Concurrency Runtime.|

## <a name="reference"></a>Odkaz

[parallel_for – funkce](reference/concurrency-namespace-functions.md#parallel_for)

[parallel_for_each Function](reference/concurrency-namespace-functions.md#parallel_for_each)

[parallel_invoke – funkce](reference/concurrency-namespace-functions.md#parallel_invoke)

[affinity_partitioner – třída](../../parallel/concrt/reference/affinity-partitioner-class.md)

[auto_partitioner – třída](../../parallel/concrt/reference/auto-partitioner-class.md)

[simple_partitioner – třída](../../parallel/concrt/reference/simple-partitioner-class.md)

[static_partitioner – třída](../../parallel/concrt/reference/static-partitioner-class.md)

[parallel_sort – funkce](reference/concurrency-namespace-functions.md#parallel_sort)

[parallel_buffered_sort – funkce](reference/concurrency-namespace-functions.md#parallel_buffered_sort)

[parallel_radixsort Function](reference/concurrency-namespace-functions.md#parallel_radixsort)

