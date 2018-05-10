---
title: Paralelní algoritmy | Microsoft Docs
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
ms.openlocfilehash: 365acd15c61b52631fc75018ab4c3a017d3eed8f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="parallel-algorithms"></a>Paralelní algoritmy
Paralelní vzory knihovny (PPL) poskytuje algoritmy, které současně u kolekcí dat v práci. Tyto algoritmy vypadat jako standardní knihovna C++ u.  
  

 Paralelní algoritmy se skládají ze stávajících funkcí v Concurrency Runtime. Například [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus používá [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objekt, který chcete provést paralelní smyčky iterací. `parallel_for` Algoritmus oddíly pracovat s optimálně zadané dostupný počet výpočetních prostředků.  

  
##  <a name="top"></a> Oddíly  
  
- [Parallel_for – algoritmus](#parallel_for)  
  
- [Parallel_for_each – algoritmus](#parallel_for_each)  
  
- [Parallel_invoke – algoritmus](#parallel_invoke)  
  
- [Parallel_transform – a parallel_reduce – algoritmy](#parallel_transform_reduce)  
  
    - [Parallel_transform – algoritmus](#parallel_transform)  
  
    - [Parallel_reduce – algoritmus](#parallel_reduce)  
  
    - [Příklad: Provádění mapování a snížit paralelně](#map_reduce_example)  
  
- [Vytváření oddílů pracovní](#partitions)  
  
- [Paralelní řazení](#parallel_sorting)  
  
    - [Výběr řazení algoritmus](#choose_sort)  
  
##  <a name="parallel_for"></a> Parallel_for – algoritmus  

 [Concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus opakovaně provede stejnou úlohu současně. Každý z těchto úloh je parametry podle hodnotou iterací. Tento algoritmus je užitečné, když máte těla smyčky, který není sdílet prostředky opakování tohoto smyčky.  
  
 `parallel_for` Algoritmus oddíly optimálně pro paralelní provádění úlohy. Používá pracovní krádež algoritmus a rozsah krádež vyvážit tyto oddíly po nevyváženou úlohy. Když jedna iterace smyčky blokuje spolupráce při, modul runtime znovu distribuuje oblast iterací, která je přiřazena k aktuálnímu vláknu další vlákna nebo procesory. Podobně po dokončení řadu iterací vlákna provede modulu runtime redistribuci pracovní z jiná vlákna na daném vláknu. `parallel_for` Algoritmus také podporuje *vnořené paralelismus*. Když jedna paralelní smyčky obsahuje jiné paralelní smyčky, modul runtime koordinuje zpracování prostředků mezi smyček efektivním způsobem pro paralelní zpracování.  
  
 `parallel_for` Algoritmus má několik přetížené verzí. První verze má počáteční hodnotu, koncová hodnota a pracovní funkci (výrazu lambda, objekt funkce nebo ukazatel na funkci). Druhá verze trvá počáteční hodnotu, koncovou hodnotu, hodnotu podle kterého kroku a pracovní funkci. První verze součásti tato funkce používá jako hodnota kroku 1. Zbývající verze trvat dělicí metody objekty, které vám umožní určit, jak `parallel_for` by měl oddílu rozsahy mezi vláken. Dělicí metody jsou vysvětlené podrobněji v části [dělení pracovní](#partitions) v tomto dokumentu.  
  
 Můžete převést mnoho `for` smyčky používat `parallel_for`. Ale `parallel_for` algoritmus se liší od `for` příkaz následujícími způsoby:  
  
-   `parallel_for` Algoritmus `parallel_for` nepracuje v předem určené pořadí úloh.  
  
-   `parallel_for` Algoritmus nepodporuje libovolný ukončení podmínky. `parallel_for` Algoritmus zastaví, pokud je aktuální hodnota proměnné iterace jeden menší než `last`.  
  
-   `_Index_type` Parametr typu musí být celočíselné typu. Tento typ integrální můžete podepsané nebo bez znaménka.  
  
-   Dál musí být iteraci smyčky. `parallel_for` Algoritmus vyvolá výjimku typu [std::invalid_argument](../../standard-library/invalid-argument-class.md) Pokud `_Step` parametru je menší než 1.  
  
-   Zpracování výjimek mechanismus pro `parallel_for` algoritmus se liší od `for` smyčky. Dojde-li několik výjimek současně v textu paralelní smyčky, modul runtime rozšíří pouze jeden z výjimky na vlákno, které volá `parallel_for`. Kromě toho pokud jeden iteraci smyčky vyvolá výjimku, modul runtime nezastaví okamžitě celkové smyčky. Místo toho smyčky je umístěn ve zrušeném stavu a modul runtime, zahodí se všechny úlohy, které nebyly ještě nezačala. Další informace o zpracování výjimek a paralelní algoritmy najdete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 I když `parallel_for` algoritmus nepodporuje libovolný ukončení podmínky, můžete použít zrušení zastavit všechny úlohy. Další informace o zrušení najdete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).  
  
> [!NOTE]
>  Plánování náklady, že výsledky z vyrovnávání zatížení a podpora pro funkce, jako je zrušení nemusí překonat výhody paralelní provádění těla smyčky, zejména pokud těla smyčky je poměrně malý. Tato dodatečná režie můžete minimalizovat pomocí rozdělovače v paralelní smyčky. Další informace najdete v tématu [dělení pracovní](#partitions) dále v tomto dokumentu.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje základní strukturu `parallel_for` algoritmus. Tento příklad zobrazí ke konzole každou hodnotu v rozsahu [1, 5] paralelně.  
  
 [!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_1.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
1 2 4 3 5  
```  
  
 Protože `parallel_for` algoritmus funguje na každou položku v paralelní, pořadí, ve kterém hodnoty vytištěny ke konzole se bude lišit.  
  
 Úplný příklad používající `parallel_for` algoritmus, najdete v části [postup: smyčky Parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md).  
  
 [[Horní](#top)]  
  
##  <a name="parallel_for_each"></a> Parallel_for_each – algoritmus  

 [Concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus provádí iterativní kontejneru, jako třeba standardní knihovny C++, paralelní úlohy. Používá stejné logiky, která rozdělení oddílů, `parallel_for` algoritmus používá.  
  
 `parallel_for_each` Algoritmus vypadá takto: standardní knihovna C++ [std::for_each](../../standard-library/algorithm-functions.md#for_each) algoritmus, vyjma toho, že `parallel_for_each` algoritmus provádí úkoly současně. Jako další paralelní algoritmy `parallel_for_each` nepracuje úloh v určitém pořadí.  
  
 I když `parallel_for_each` algoritmus na dopředného iterátory a iterátory náhodný přístup funguje, provede lépe s náhodným přístupem iterátory.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje základní strukturu `parallel_for_each` algoritmus. Tento příklad zobrazí ke konzole každé hodnoty v [std::array](../../standard-library/array-class-stl.md) objekt paralelně.  
  
 [!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_2.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
4 5 1 2 3  
```  
  
 Protože `parallel_for_each` algoritmus funguje na každou položku v paralelní, pořadí, ve kterém hodnoty vytištěny ke konzole se bude lišit.  
  
 Úplný příklad používající `parallel_for_each` algoritmus, najdete v části [postup: smyčky Parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md).  
  
 [[Horní](#top)]  
  
##  <a name="parallel_invoke"></a> Parallel_invoke – algoritmus  

 [Concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus provede sadu úloh paralelně. Nevrací se dokud každý úkol dokončí. Tento algoritmus je užitečné, když máte několik nezávislých úkolů, které chcete provést ve stejnou dobu.  
  
 `parallel_invoke` Algoritmus jako jeho parametry obsahuje řadu pracovních funkcí (lambda funkce, funkce objekty nebo ukazatelů na funkce). `parallel_invoke` Algoritmus je přetížena provést mezi dvěma a deset parametry. Každá funkce, která je předat do `parallel_invoke` musí mít žádné parametry.  
  
 Jako další paralelní algoritmy `parallel_invoke` nepracuje úloh v určitém pořadí. Téma [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md) vysvětluje, jak `parallel_invoke` algoritmus má vztah k úlohy a skupiny úloh.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje základní strukturu `parallel_invoke` algoritmus. Tento příklad souběžně volá `twice` funkce na tři místní proměnné a vytiskne výsledek do konzoly.  
  
 [!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_3.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
108 11.2 HelloHello  
```  
  
 Pro dokončení příklady, které používají `parallel_invoke` algoritmus, najdete v části [postupy: použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) a [postupy: použití algoritmu parallel_invoke k provádění paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md).  
  
 [[Horní](#top)]  
  
##  <a name="parallel_transform_reduce"></a> Parallel_transform – a parallel_reduce – algoritmy  

 [Concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) a [concurrency::parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) algoritmy jsou paralelní verze algoritmů standardní knihovna C++ [std::transform](../../standard-library/algorithm-functions.md#transform)a [std::accumulate](../../standard-library/numeric-functions.md#accumulate), v uvedeném pořadí. Verze Concurrency Runtime chovat jako verze standardní knihovny C++ s tím rozdílem, že operace pořadí není určit, protože paralelně provádět. Použijte tyto algoritmy při práci s sadu dostatečně velký, aby se sám výkon a výhody škálování se zpracovávají paralelně.  
  
> [!IMPORTANT]
>  `parallel_transform` a `parallel_reduce` algoritmy podporovat pouze náhodný přístup obousměrný a předat dál iterátory, protože tyto iterátory vytvořit stabilní paměti adresy. Také musíte vytvořit tyto iterátory jinou hodnotu než`const` hodnoty l.  
  
###  <a name="parallel_transform"></a> Parallel_transform – algoritmus  
 Můžete použít `parallel transform` algoritmus k provedení mnoha operací paralelizace data. Například můžete:  
  
-   Upravte také průraznost bitové kopie a provádění dalších operací zpracování bitové kopie.  
  
-   Součet nebo trvat produktu tečkou mezi dvěma vektory a na vektory jiné číselné a výpočty.  
  
-   Proveďte trasování 3D ray, kde každé iteraci odkazuje jeden pixel, kterou je nutné vykreslit.  
  
 Následující příklad ukazuje základní struktura, která se používá k volání `parallel_transform` algoritmus. Tento příklad Neguje každý prvek std::[vektoru](../../standard-library/vector-class.md) objekt dvěma způsoby. První způsob využívá výrazu lambda. Druhý způsob využívá [std::negate](../../standard-library/negate-struct.md), která je odvozena z [std::unary_function](../../standard-library/unary-function-struct.md).  
  
 [!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_4.cpp)]  
  
> [!WARNING]
>  Tento příklad ukazuje základní použití `parallel_transform`. Protože funkce pracovní neprovede významné množství práce, není v tomto příkladu očekáván výrazné zvýšení výkonu.  
  
 `parallel_transform` Algoritmus má dva přetížení. První přetížení trvá jeden vstupní rozsah a unární funkce. Funkce unární může být výraz lambda, která přijímá jeden argument, funkce objekt nebo typ, který je odvozen od `unary_function`. Druhý přetížení přebírá dva vstupní rozsahy a binární funkce. Binární funkce může být výraz lambda, která přebírá dva argumenty, funkce objekt nebo typ, který je odvozen od [std::binary_function](../../standard-library/binary-function-struct.md). Následující příklad znázorňuje tyto rozdíly.  
  
 [!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_5.cpp)]  
  
> [!IMPORTANT]
>  Iterator, kterou zadáte jako výstup `parallel_transform` musí zcela překrývat vstupní iterator nebo nepřekrývají vůbec. Chování tento algoritmus neurčené, pokud vstupní a výstupní iterátory částečně překrývají.  
  
###  <a name="parallel_reduce"></a> Parallel_reduce – algoritmus  
 `parallel_reduce` Algoritmus je užitečné, když máte pořadí operací, které odpovídají asociativní vlastnost. (Tento algoritmus se nevyžaduje vlastnost komutativní). Zde jsou některé operace, které můžete provádět s `parallel_reduce`:  
  
-   Vynásobte pořadí matice k vytvoření matice.  
  
-   Vektor vynásobte posloupnost matice k vytvoření vektor.  
  
-   Výpočetní délka posloupnosti řetězců.  
  
-   Seznam prvků, jako jsou třeba řetězce, zkombinovat do jednoho elementu.  
  
 Následující základní příklad ukazuje, jak používat `parallel_reduce` algoritmus kombinovat posloupnost řetězce do jednoho řetězce. Stejně jako u příklady pro `parallel_transform`, nejsou v tomto příkladu základní očekávané zvýšení výkonu.  
  
 [!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_6.cpp)]  
  
 V mnoha případech si můžete představit `parallel_reduce` jako sdružená vlastnost pro použití `parallel_for_each` algoritmus společně s [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třídy.  
  
###  <a name="map_reduce_example"></a> Příklad: Provádění mapování a snížit paralelně  

 A *mapy* operace platí pro každou hodnotu v pořadí funkce. A *snížit* operace kombinuje elementy sekvence do jednu hodnotu. Můžete použít standardní knihovna C++ [std::transform](../../standard-library/algorithm-functions.md#transform) a [std::accumulate](../../standard-library/numeric-functions.md#accumulate) funkce k provedení mapy a snížení operací. Mnohé problémy, ale můžete použít `parallel_transform` algoritmus k provedení operace mapy paralelně a `parallel_reduce` algoritmus provést operaci snižte paralelně.  

  
 Následující příklad porovnává čas potřebný k výpočtu součet prvočísel sériově a paralelně. Fáze mapy transformuje než prvotřídní hodnoty 0 a součtů fáze snižte hodnoty.  
  
 [!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_7.cpp)]  
  
 Další příklad, který provede mapu a snížit operace paralelně, najdete v části [postup: provedení mapy a snížit operace paralelně](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).  
  
 [[Horní](#top)]  
  
##  <a name="partitions"></a> Vytváření oddílů pracovní  
 Učinit paralelní operace pro zdroj dat, je základním krokem *oddílu* zdroje do více oddílů, které dostanete souběžně několik vláken. Rozdělovače Určuje, jak by měla paralelní algoritmus oddílu rozsahy mezi vláken. Jak je popsáno dříve v tomto dokumentu, knihovně PPL používá výchozí dělení mechanismus, který vytvoří počáteční úlohu a potom pomocí krádež pracovní algoritmus a rozsah krádež vyvážit tyto oddíly po nevyváženou úlohy. Například po dokončení řadu iterací jeden iteraci smyčky provede modulu runtime redistribuci práce z jiná vlákna tento přístup z více vláken. V některých případech, můžete však zadat jiný rozdělení mechanismus, který je lepší hodí pro váš problém.  
  
 `parallel_for`, `parallel_for_each`, A `parallel_transform` algoritmy poskytují přetížené verze, která přebírají další parametr, `_Partitioner`. Tento parametr definuje dělicí metody typ, který rozděluje práci. Zde jsou druhy dělicí metody, které definuje knihovně PPL:  
  
 [Concurrency::affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)  
 Vydělí fungovat do pevný počet rozsahů (obvykle počet pracovních vláken, které jsou k dispozici pro práci na smyčky). Tento typ dělicí metody se podobá `static_partitioner`, ale zvyšuje mezipaměti spřažení tím, jak mapuje rozsahy do pracovních vláken. Tento typ dělicí metody lze vylepšit výkon, když se spustí smyčku přes sadu dat několikrát (například smyčku v rámci smyčku) a vyhovuje data v mezipaměti. Tato dělicí metody zrušení plně neúčastní. Je také nepoužívá spolupráci blokování sémantiku a proto jej nelze použít s paralelní smyčky, které jsou závislé předat dál.  
  
 [Concurrency::auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)  
 Vydělí fungovat do počáteční počet rozsahů (obvykle počet pracovních vláken, které jsou k dispozici pro práci na smyčky). Modul runtime tento typ používá ve výchozím nastavení při Nevolejte přetížené paralelní algoritmu, který přebírá `_Partitioner` parametr. Každý rozsah je možné rozdělit do dílčí rozsahy a tím umožňuje načíst vyrovnávání proběhnout. Po dokončení rozsah práce modulu runtime znovu distribuuje dílčí rozsahy práce z jiná vlákna na daném vláknu. Použijte tento dělicí metody, pokud vaše úlohy nespadá do jedné z jiných kategorií nebo vyžadovat plnou podporu pro zrušení nebo spolupráci blokování.  
  
 [Concurrency::simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)  
 Vydělí fungovat do rozsahů tak, aby měl každý rozsah alespoň počet iterací, které jsou určené velikost daného bloku. Tento typ dělicí metody účastní Vyrovnávání zatížení; ale modulu runtime není rozdělení rozsahy na dílčí rozsahy. Pro každý pracovní běhové prostředí vyhledává zrušení a provede Vyrovnávání zatížení po `_Chunk_size` dokončení iterací.  
  
 [Concurrency::static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)  
 Vydělí fungovat do pevný počet rozsahů (obvykle počet pracovních vláken, které jsou k dispozici pro práci na smyčky). Tento typ dělicí metody lze vylepšit výkon, protože nepoužívá pracovní krádež a proto má nižší režijní náklady. Pomocí tohoto typu dělicí metody při každé iteraci paralelní smyčky provede pevných a uniform množství práce, a nemáte vyžaduje podporu pro zrušení nebo předávat spolupráci blokování.  
  
> [!WARNING]
>  `parallel_for_each` a `parallel_transform` algoritmy podporují pouze kontejnery, které iterátory náhodným přístupem (například – std::[vektoru](../../standard-library/vector-class.md)) pro dělicí metody statické, jednoduchý a spřažení. Použití kontejnery, které obousměrného a předat dál iterátory vytvoří chyby kompilace. Dělicí metody výchozí, `auto_partitioner`, podporuje všechny tři z těchto typů iterator.  
  
 Obvykle se používají tyto dělicí metody stejným způsobem, s výjimkou `affinity_partitioner`. Většina typů dělicí metody neudržují stavu a se nemění modulem runtime. Proto můžete vytvořit tyto objekty dělicí metody v lokalitě volání, jak je znázorněno v následujícím příkladu.  
  
 [!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_8.cpp)]  
  
 Je však nutné předat `affinity_partitioner` objektu jako jinou hodnotu než`const`, l-value odkazovat tak, aby algoritmus můžete uložit stav pro budoucí smyčky znovu použít. Následující příklad ukazuje základní aplikaci, která provede stejnou operaci pro datové sady paralelně vícekrát. Použití `affinity_partitioner` může zlepšit výkon, protože pole je pravděpodobné, aby se vešla do mezipaměti.  
  
 [!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_9.cpp)]  
  
> [!CAUTION]
>  Buďte opatrní při úpravě existující kód, který závisí na spolupráci blokování sémantiku používat `static_partitioner` nebo `affinity_partitioner`. Tyto typy dělicí metody nepoužívejte Vyrovnávání zatížení nebo krádež rozsahu a proto můžete změnit chování vaší aplikace.  
  
 Nejlepší způsob, jak určit, zda se v jakékoli dané scénáři používat rozdělovače je experiment a vyhodnocovat, jak dlouho trvalo na dokončení pod reprezentativní zatížení a konfiguracích počítačů operací. Například statické dělení může poskytovat významné zrychlení vícejádrové počítače, který má jenom několik jader, ale může způsobit zpomalení na počítačích, které mají relativně velký počet jader.  
  
 [[Horní](#top)]  
  
##  <a name="parallel_sorting"></a> Paralelní řazení  

 Knihovně PPL poskytuje tři řazení algoritmy: [concurrency::parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort), a [concurrency::parallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Toto řazení algoritmy jsou užitečné v případě, že máte datové sady, které můžete využít řazen paralelně. Konkrétně řazení paralelně je užitečné, když máte velké datové sady nebo při použití operace výpočetně náročné porovnání řadit data. Všechny tyto algoritmy Seřadí prvky na místě.  

  
 `parallel_sort` a `parallel_buffered_sort` algoritmy jsou obou algoritmů na základě porovnání. To znamená že porovnávat elementy hodnotou. `parallel_sort` Algoritmus nemá žádné požadavky na další paměť a je vhodný pro řazení pro obecné účely. `parallel_buffered_sort` Algoritmus můžete provádět lepší, než `parallel_sort`, ale vyžaduje to O(N) místa.  
  
 `parallel_radixsort` Algoritmus je založen na algoritmu hash. To znamená používá celé číslo klíče seřadit elementy. S využitím klíčů, můžete tento algoritmus přímo výpočetní cílového elementu místo použití porovnávání. Jako `parallel_buffered_sort`, tento algoritmus vyžaduje O(N) místa.  
  
 Následující tabulka shrnuje důležité vlastnosti tři paralelní algoritmy řazení.  
  
|Algoritmus|Popis|Řazení mechanismus|Řazení Stability|Požadavky na paměť|Složitost čas|Iterator přístup|  
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|  
|`parallel_sort`|Pro obecné účely na základě porovnání řazení.|Na základě porovnání (vzestupně)|Nestabilním|Žádné|O((N/P)log(N/P) + 2N((P-1)/P))|Náhodné|  
|`parallel_buffered_sort`|Rychlejší pro obecné účely na základě porovnání řazení, které vyžaduje O(N) místa.|Na základě porovnání (vzestupně)|Nestabilním|Vyžaduje další prostor O(N)|O((N/P)log(N))|Náhodné|  
|`parallel_radixsort`|Celé číslo na základě klíčů řazení, které vyžaduje O(N) místa.|Na základě hodnoty hash|Stabilní|Vyžaduje další prostor O(N)|O(N/P)|Náhodné|  
  
 Následující obrázek znázorňuje více graficky důležité vlastnosti tři paralelní algoritmy řazení.  
  
 ![Porovnání řazení algoritmů](../../parallel/concrt/media/concrt_parallel_sorting.png "concrt_parallel_sorting")  
  
 Tyto algoritmy paralelní řazení podle pravidla zrušení a výjimek. Další informace o zrušení a zpracování výjimek v Concurrency Runtime najdete v tématu [zrušení paralelních algoritmů](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms) a [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
> [!TIP]
>  Tyto algoritmy paralelní řazení podporovat sémantiku move. Můžete definovat operátor přiřazení přesunutí pro povolení operací swap proběhnout efektivněji. Další informace o sémantiku move a operátor move přiřazení najdete v tématu [Rvalue – deklarátor odkazu: & &](../../cpp/rvalue-reference-declarator-amp-amp.md), a [přesunout konstruktory a operátory přesunout přiřazení (C++)](../../cpp/move-constructors-and-move-assignment-operators-cpp.md). Pokud nezadáte operátor přiřazení přesunutí nebo funkce odkládacího souboru, použijte řazení algoritmy konstruktor copy.  
  
 Následující základní příklad ukazuje, jak používat `parallel_sort` řadit `vector` z `int` hodnoty. Ve výchozím nastavení `parallel_sort` používá [std::less](../../standard-library/less-struct.md) pro porovnání hodnot.  
  
 [!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_10.cpp)]  
  
 Tento příklad ukazuje, jak poskytnout vlastní porovnat funkce. Použije [std::complex::real](../../standard-library/complex-class.md#real) metoda seřadit [std::complex\<dvojité >](../../standard-library/complex-double.md) hodnoty ve vzestupném pořadí.  
  
 [!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_11.cpp)]  
  
 Tento příklad ukazuje, jak poskytnout funkce hash, která se `parallel_radixsort` algoritmus. Tento příklad seřadí 3D body. Body jsou seřazené podle jejich vzdálenost od referenční bod.  
  
 [!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_12.cpp)]  
  
 Pro ilustraci tento příklad používá relativně malé datové sady. Můžete zvýšit počáteční velikost vektoru a experimentovat s vylepšení výkonu přes větších datových sad.  
  
 Tento příklad používá výrazu lambda jako funkce hash. Můžete také použít jeden z předdefinovaných implementace – std::[hash – třída](../../standard-library/hash-class.md) nebo definovat vlastní specializace. Také můžete objekt funkce vlastní algoritmu hash, jak je uvedeno v následujícím příkladu:  
  
 [!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_13.cpp)]  
  
 [!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_14.cpp)]  
  
 Funkce hash musí vracet typ integrální ([std::is_integral::value](../../standard-library/is-integral-class.md) musí být `true`). Tento typ integrální musí být převoditelná na typ `size_t`.  
  
###  <a name="choose_sort"></a> Výběr řazení algoritmus  
 V mnoha případech `parallel_sort` poskytuje optimální rovnováhu mezi rychlostí a paměti na výkon. Však jako můžete zvětšit velikost datové sady, počet dostupných procesorů nebo složitost funkce porovnání `parallel_buffered_sort` nebo `parallel_radixsort` můžete lépe provádět. Nejlepší způsob, jak určit, který algoritmus řazení pro použití v jakékoli této situaci je experiment a vyhodnocovat, jak dlouho trvá řazení typické dat v rámci reprezentativní konfiguraci počítače. Když zvolíte strategie řazení, mít na paměti následující pokyny.  
  
-   Velikost datové sady. V tomto dokumentu *malé* datová sada obsahuje méně než 1 000 elementy *střední* datová sada obsahuje mezi elementy 10 000 a 100 000 a *velké* datová sada obsahuje více než 100 000 prvků.  
  
-   Množství práce, který provádí porovnání funkce nebo funkce hash.  
  
-   Množství dostupné výpočetní prostředky.  
  
-   Vlastnosti datové sady. Například jeden algoritmus může provést i pro data, která je již téměř seřadit, ale není i pro data, která je zcela seřazená.  
  
-   Velikost bloku. Volitelné `_Chunk_size` argument určuje, kdy algoritmus přepíná z paralelní implementaci sériové řazení jako se dále dělí celkové řazení do menších jednotek práce. Například pokud zadáte 512, algoritmus se přepne do sériového portu implementace při pracovní jednotka obsahuje prvky 512 nebo méně. Sériové implementace může zvýšit celkový výkon, protože eliminuje režijní náklady, které jsou potřeba ke zpracování dat paralelně.  
  
 Nemusí být smysl seřadit na malou datovou sadu paralelně, i v případě, že máte velký počet dostupných výpočetních prostředcích nebo porovnat funkce nebo funkce hash provede relativně velké množství práce. Můžete použít [std::sort](../../standard-library/algorithm-functions.md#sort) funkce seřadit malé datové sady. (`parallel_sort` a `parallel_buffered_sort` volání `sort` při zadávání velikost bloku, která je větší než datovou sadu; však `parallel_buffered_sort` se přidělit O(N) místa, což může trvat déle kvůli přidělení zámku kolizí nebo paměti.)  
  
 Pokud musí konzervaci paměti nebo váš přidělení paměti podléhá spory uzamčení, použijte `parallel_sort` seřadit střední datové sady. `parallel_sort` vyžaduje žádný další prostor; jiné algoritmy vyžadují O(N) místa.  
  
 Použití `parallel_buffered_sort` seřadit středně velkých datových sad a když aplikace splňuje požadavek na místo další O(N). `parallel_buffered_sort` může být obzvláště užitečný, když máte velký počet výpočetních prostředků nebo nákladné porovnat funkce nebo funkce hash.  
  
 Použití `parallel_radixsort` seřadit rozsáhlých datových sad a když aplikace splňuje požadavek na další místa O(N). `parallel_radixsort` může být obzvláště užitečné, když je operace porovnání ekvivalentní dražší, nebo pokud jsou obě operace nákladné.  
  
> [!CAUTION]
>  Implementace funkce dobrý hash je nutné znát rozsah datové sady, a jak je každý prvek v datové sadě transformován na odpovídající hodnotu bez znaménka. Protože operace hash funguje na nepodepsané hodnoty, zvažte strategie různých řazení Pokud není možné hodnoty hash bez znaménka.  
  
 Následující příklad porovnává výkon `sort`, `parallel_sort`, `parallel_buffered_sort`, a `parallel_radixsort` proti stejné velké sady náhodná data.  
  
 [!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_15.cpp)]  
  
 V tomto příkladu se předpokládá, že je přijatelné k přidělení místa O(N) při řazení, `parallel_radixsort` provede ideální pro tuto datovou sadu v této konfiguraci počítače.  
  
 [[Horní](#top)]  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Programování smyčky parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|Ukazuje, jak používat `parallel_for` algoritmus násobení matic.|  
|[Postupy: Programování smyčky parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|Ukazuje, jak používat `parallel_for_each` algoritmus vypočítat počet prvočísel v [std::array](../../standard-library/array-class-stl.md) objekt paralelně.|  
|[Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Ukazuje, jak používat `parallel_invoke` algoritmus ke zlepšení výkonu algoritmus bitonic řazení.|  
|[Postupy: Použití algoritmu parallel_invoke k provádění paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Ukazuje, jak používat `parallel_invoke` algoritmus ke zlepšení výkonu programu, který provádí víc operací na sdílený zdroj dat.|  
|[Postupy: Paralelní provádění operací mapování a redukce](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Ukazuje, jak používat `parallel_transform` a `parallel_reduce` algoritmy s cílem provést mapu a snížit počet výskytů slova v souborech operace.|  
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Popisuje PPL, která poskytuje imperativní programovací model, který zvýší úroveň škálovatelnost a snadné použití pro vývoj souběžných aplikací.|  
|[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)|Vysvětluje roli zrušení v knihovně PPL, jak zrušit paralelní práce a jak určit, kdy je zrušena skupinu úkolů.|  
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


