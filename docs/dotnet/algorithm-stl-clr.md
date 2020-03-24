---
title: algorithm (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/algorithm>
- cliext::adjacent_find
- cliext::binary_search
- cliext::copy
- cliext::copy_backward
- cliext::count
- cliext::count_if
- cliext::equal
- cliext::equal_range
- cliext::fill
- cliext::fill_n
- cliext::find
- cliext::find_end
- cliext::find_first_of
- cliext::find_if
- cliext::for_each
- cliext::generate
- cliext::generate_n
- cliext::includes
- cliext::inplace_merge
- cliext::iter_swap
- cliext::lexicographical_compare
- cliext::lower_bound
- cliext::make_heap
- cliext::max
- cliext::max_element
- cliext::merge
- cliext::min
- cliext::min_element
- cliext::mismatch
- cliext::next_permutation
- cliext::nth_element
- cliext::partial_sort
- cliext::partial_sort_copy
- cliext::partition
- cliext::pop_heap
- cliext::prev_permutation
- cliext::push_heap
- cliext::random_shuffle
- cliext::remove
- cliext::remove_copy
- cliext::remove_copy_if
- cliext::remove_if
- cliext::replace
- cliext::replace_copy
- cliext::replace_copy_if
- cliext::replace_if
- cliext::reverse
- cliext::reverse_copy
- cliext::rotate
- cliext::rotate_copy
- cliext::search
- cliext::search_n
- cliext::set_difference
- cliext::set_intersection
- cliext::set_symmetric_difference
- cliext::set_union
- cliext::sort
- cliext::sort_heap
- cliext::stable_partition
- cliext::stable_sort
- cliext::swap
- cliext::swap_ranges
- cliext::transform
- cliext::unique
- cliext::unique_copy
- cliext::upper_bound
helpviewer_keywords:
- algorithm functions [STL/CLR]
- <algorithm> header [STL/CLR]
- <cliext/algorithm> header [STL/CLR]
- adjacent_find function
- binary_search function [STL/CLR]
- copy function [STL/CLR]
- copy_backward function [STL/CLR]
- count function [STL/CLR]
- count_if function [STL/CLR]
- equal function [STL/CLR]
- equal_range function [STL/CLR]
- fill function
- fill_n function
- find function [STL/CLR]
- find_end function [STL/CLR]
- find_first_of function [STL/CLR]
- find_if function [STL/CLR]
- for_each function [STL/CLR]
- generate function [STL/CLR]
- generate_n function [STL/CLR]
- includes function [STL/CLR]
- inplace_merge function [STL/CLR]
- iter_swap function [STL/CLR]
- lexicographical_compare function [STL/CLR]
- lower_bound function [STL/CLR]
- make_heap function [STL/CLR]
- max function [STL/CLR]
- max_element function [STL/CLR]
- merge function [STL/CLR]
- min function [STL/CLR]
- min_element function [STL/CLR]
- mismatch function [STL/CLR]
- next_permutation function [STL/CLR]
- nth_element function [STL/CLR]
- partial_sort function [STL/CLR]
- partial_sort_copy function [STL/CLR]
- partition function [STL/CLR]
- pop_heap function [STL/CLR]
- prev_permutation function [STL/CLR]
- push_heap function [STL/CLR]
- random_shuffle function [STL/CLR]
- remove function [STL/CLR]
- remove_copy function [STL/CLR]
- remove_copy_if function [STL/CLR]
- remove_if function [STL/CLR]
- replace function [STL/CLR]
- replace_copy function [STL/CLR]
- replace_copy_if function [STL/CLR]
- replace_if function [STL/CLR]
- reverse function [STL/CLR]
- reverse_copy function [STL/CLR]
- rotate function [STL/CLR]
- rotate_copy function [STL/CLR]
- search function [STL/CLR]
- search_n function [STL/CLR]
- set_difference function [STL/CLR]
- set_intersection function [STL/CLR]
- set_symmetric_difference function [STL/CLR]
- set_union function [STL/CLR]
- sort function [STL/CLR]
- sort_heap function [STL/CLR]
- stable_partition function [STL/CLR]
- stable_sort function [STL/CLR]
- swap function [STL/CLR]
- swap_ranges function [STL/CLR]
- transform function [STL/CLR]
- unique function [STL/CLR]
- unique_copy function [STL/CLR]
- upper_bound function [STL/CLR]
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
ms.openlocfilehash: 4abd7eaa640bb89fd97c1787bf2fd692610212fb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208948"
---
# <a name="algorithm-stlclr"></a>algorithm (STL/CLR)

Definuje funkce šablony kontejneru STL/CLR, které provádějí algoritmy.

## <a name="syntax"></a>Syntaxe

```cpp
#include <cliext/algorithm>
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext –/Algorithm >

**Obor názvů:** cliext –

## <a name="declarations"></a>Deklarace

|Funkce|Popis|
|--------------|-----------------|
|[adjacent_find (STL/CLR)](#adjacent_find)|Vyhledá dva sousedící prvky, které jsou stejné.|
|[binary_search (STL/CLR)](#binary_search)|Testuje, zda seřazená sekvence obsahuje danou hodnotu.|
|[copy (STL/CLR)](#copy)|Zkopíruje hodnoty ze zdrojového rozsahu do cílového rozsahu a provede iteraci směrem směrem nahoru.|
|[copy_backward (STL/CLR)](#copy_backward)|Zkopíruje hodnoty ze zdrojového rozsahu do cílového rozsahu a provede iteraci v opačném směru.|
|[count (STL/CLR)](#count)|Vrátí počet prvků v rozsahu, jejichž hodnoty odpovídají zadané hodnotě.|
|[count_if (STL/CLR)](#count_if)|Vrátí počet prvků v rozsahu, jejichž hodnoty odpovídají zadané podmínce.|
|[equal (STL/CLR)](#equal)|Porovná dva rozsahy element po elementu.|
|[equal_range (STL/CLR)](#equal_range)|Vyhledá seřazenou sekvenci hodnot a vrátí dvě pozice, které vymezují dílčí sekvenci hodnot, které jsou rovny danému prvku.|
|[fill (STL/CLR)](#fill)|Každému prvku v zadaném rozsahu přiřadí stejnou novou hodnotu.|
|[fill_n (STL/CLR)](#fill_n)|Přiřadí novou hodnotu zadanému počtu prvků v rozsahu, který začíná konkrétním prvkem.|
|[find (STL/CLR)](#find)|Vrací pozici prvního výskytu zadané hodnoty.|
|[find_end (STL/CLR)](#find_end)|Vrátí poslední podsekvenci v rozsahu, který je totožný se zadaným pořadím.|
|[find_first_of (STL/CLR)](#find_first_of)|Vyhledá rozsah prvního výskytu některého z daných rozsahů prvků.|
|[find_if (STL/CLR)](#find_if)|Vrátí pozici prvního prvku v sekvenci hodnot, kde element splňuje zadanou podmínku.|
|[for_each (STL/CLR)](#for_each)|Aplikuje zadaný objekt funkce na každý prvek v sekvenci hodnot a vrátí objekt funkce.|
|[generate (STL/CLR)](#generate)|Přiřadí hodnoty generované objektem funkce každému prvku v posloupnosti hodnot.|
|[generate_n (STL/CLR)](#generate_n)|Přiřadí hodnoty generované objektem funkce na zadaný počet prvků.|
|[includes (STL/CLR)](#includes)|Testuje, zda jeden seřazený rozsah obsahuje všechny prvky ve druhém seřazeném rozsahu.|
|[inplace_merge (STL/CLR)](#inplace_merge)|Zkombinuje prvky ze dvou po sobě seřazených rozsahů do jednoho seřazeného rozsahu.|
|[iter_swap (STL/CLR)](#iter_swap)|Vymění dvě hodnoty odkazované dvojicí zadaných iterátorů.|
|[lexicographical_compare (STL/CLR)](#lexicographical_compare)|Porovná dva sekvence, element po prvku a určí, která sekvence je menší z těchto dvou.|
|[lower_bound (STL/CLR)](#lower_bound)|Vyhledá pozici prvního prvku v seřazené sekvenci hodnot, jejichž hodnota je větší než nebo rovna zadané hodnotě.|
|[make_heap (STL/CLR)](#make_heap)|Převede elementy ze zadaného rozsahu na haldu, kde je první prvek haldy největší.|
|[Max (STL/CLR)](#max))|Porovná dva objekty a vrátí větší z těchto dvou.|
|[max_element (STL/CLR)](#max_element)|Najde největší prvek v zadané sekvenci hodnot.|
|[merge (STL/CLR)](#merge))|Kombinuje všechny prvky ze dvou seřazených zdrojových rozsahů do jednoho seřazeného cílového rozsahu.|
|[min (STL/CLR)](#min)|Porovná dva objekty a vrátí menší z obou.|
|[min_element (STL/CLR)](#min_element)|Najde nejmenší prvek v zadané sekvenci hodnot.|
|[mismatch (STL/CLR)](#mismatch)|Porovná dva rozsahy element podle prvku a vrátí první pozici, kde dojde k rozdílu.|
|[next_permutation (STL/CLR)](#next_permutation)|Změní pořadí prvků v rozsahu tak, aby bylo původní řazení nahrazeno lexikograficky další permutací, pokud existuje.|
|[nth_element (STL/CLR)](#nth_element)|Rozdělí sekvenci prvků a správně vyhledá `n`element sekvence, aby všechny prvky před ním byly menší nebo rovny hodnotě a všechny prvky, které následují, jsou větší než nebo rovny.|
|[partial_sort (STL/CLR)](#partial_sort)|Uspořádá zadaný počet menších prvků v rozsahu do nesestupného pořadí.|
|[partial_sort_copy (STL/CLR)](#partial_sort_copy)|Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu tak, aby byly seřazené prvky ze zdrojového rozsahu.|
|[partition (STL/CLR)](#partition)|Uspořádá prvky v rozsahu tak, aby tyto prvky, které odpovídají unárnímu predikátu, předcházejí ty, které ji nevyhověly.|
|[pop_heap (STL/CLR)](#pop_heap)|Přesune největší prvek z přední části haldy na konec a následně vytvoří novou haldu ze zbývajících prvků.|
|[prev_permutation (STL/CLR)](#prev_permutation)|Přeuspořádat sekvenci prvků tak, aby původní řazení bylo nahrazeno lexikograficky předchozí větší permutací, pokud existuje.|
|[push_heap (STL/CLR)](#push_heap)|Přidá prvek, který je na konci rozsahu, do stávající haldy, která zahrnuje předchozí prvky daného rozsahu.|
|[random_shuffle (STL/CLR)](#random_shuffle)|Změní uspořádání sekvence `N` prvků v rozsahu na jednu z `N`! možné postupy vybrané náhodně.|
|[remove (STL/CLR)](#remove)|Odstraní zadanou hodnotu z daného rozsahu bez narušení pořadí zbývajících prvků a vrátí konec nového rozsahu, který je od zadané hodnoty volný.|
|[remove_copy (STL/CLR)](#remove_copy)|Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu s tím rozdílem, že prvky zadané hodnoty nejsou zkopírovány bez narušení pořadí zbývajících prvků.|
|[remove_copy_if (STL/CLR)](#remove_copy_if)|Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu s výjimkou těch, které odpovídají predikátu, bez narušení pořadí zbývajících prvků.|
|[remove_if (STL/CLR)](#remove_if)|Odstraní prvky, které odpovídají predikátu z daného rozsahu bez narušení pořadí zbývajících prvků. .|
|[replace (STL/CLR)](#replace)|Nahradí prvky v rozsahu, které odpovídají zadané hodnotě, novou hodnotou.|
|[replace_copy (STL/CLR)](#replace_copy)|Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu a nahradí prvky, které odpovídají zadané hodnotě, novou hodnotou.|
|[replace_copy_if (STL/CLR)](#replace_copy_if)|Zkontroluje každý prvek ve zdrojovém rozsahu a nahradí jej, pokud při kopírování výsledku do nového cílového rozsahu splňuje zadaný predikát.|
|[replace_if (STL/CLR)](#replace_if)|Zkontroluje každý prvek v rozsahu a nahradí jej, pokud splňuje zadaný predikát.|
|[reverse (STL/CLR)](#reverse)|Obrátí pořadí prvků v rozsahu.|
|[reverse_copy (STL/CLR)](#reverse_copy)|Obrátí pořadí prvků v rámci zdrojového rozsahu při kopírování do cílového rozsahu.|
|[rotate (STL/CLR)](#rotate)|Vymění prvky ve dvou sousedních rozsazích.|
|[rotate_copy (STL/CLR)](#rotate_copy)|Vymění prvky ve dvou sousedních rozsazích v rámci zdrojového rozsahu a zkopíruje výsledek do cílového rozsahu.|
|[search (STL/CLR)](#search_)|Vyhledá první výskyt sekvence v cílovém rozsahu, jejíž prvky jsou rovné prvkům v dané sekvenci prvků nebo jejíž prvky jsou ekvivalentní ve smyslu určeném binárním predikátem prvkům v dané sekvenci.|
|[search_n (STL/CLR)](#search_n)|Vyhledá první dílčí sekvenci v rozsahu zadaného počtu prvků s konkrétní hodnotou nebo vztahem k dané hodnotě podle binárního predikátu.|
|[set_difference (STL/CLR)](#set_difference)|Sjednotí všechny prvky, které patří do jednoho seřazeného zdrojového rozsahu, ale nikoli do druhého seřazeného zdrojového rozsahu, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[set_intersection (STL/CLR)](#set_intersection)|Sjednotí všechny prvky, které náleží do obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[set_symmetric_difference (STL/CLR)](#set_symmetric_difference)|Sjednotí všechny prvky, které náleží do jednoho, ale nikoli obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[set_union (STL/CLR)](#set_union))|Sjednotí všechny prvky, které náleží alespoň do jednoho ze dvou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[sort (STL/CLR)](#sort)|Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem.|
|[sort_heap (STL/CLR)](#sort_heap)|Převede haldu na seřazený rozsah.|
|[stable_partition (STL/CLR)](#stable_partition)|Rozdělí prvky v rozsahu do dvou oddělených sad. Prvky, které splňují unární predikát, jsou umístěny před těmi, které jej nesplňují. Relativní pořadí ekvivalentních prvků je zachováno.|
|[stable_sort (STL/CLR)](#stable_sort)|Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem a zachová relativní pořadí ekvivalentních prvků.|
|[swap (STL/CLR)](#swap)|Vymění hodnoty prvků mezi dvěma typy objektů, obsah prvního objektu přiřadí ke druhému objektu a obsah druhého k prvnímu objektu.|
|[swap_ranges (STL/CLR)](#swap_ranges)|Vymění prvky z jednoho rozsahu za prvky druhého rozsahu o stejné velikosti.|
|[transform (STL/CLR)](#transform)|Aplikuje zadaný objekt funkce na každý prvek ve zdrojovém rozsahu nebo na dvojici prvků ze dvou zdrojových rozsahů a zkopíruje vrácené hodnoty objektu funkce do cílového rozsahu.|
|[unique (STL/CLR)](#unique)|Odstraní duplicitní prvky, které v zadaném rozsahu sousedí.|
|[unique_copy (STL/CLR)](#unique_copy)|Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu s výjimkou sousedících duplicitních prvků.|
|[upper_bound (STL/CLR)](#upper_bound)|Najde pozici prvního prvku v seřazeném rozsahu, který má hodnotu větší než zadaná hodnota, kde kritérium pořadí může být určeno binárním predikátem.|

## <a name="members"></a>Členové

## <a name="adjacent_find-stlclr"></a><a name="adjacent_find"></a>adjacent_find (STL/CLR)

Vyhledá dva sousedící prvky, které jsou buď rovny, nebo splňují zadanou podmínku.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt> inline
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `adjacent_find`. Další informace najdete v tématu [adjacent_find](../standard-library/algorithm-functions.md#adjacent_find).

## <a name="binary_search-stlclr"></a><a name="binary_search"></a>binary_search (STL/CLR)

Ověřuje, zda v seřazeném rozsahu existuje prvek, který je roven zadané hodnotě nebo je jí ekvivalentní ve smyslu určeném binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Ty> inline
    bool binary_search(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    bool binary_search(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `binary_search`. Další informace najdete v tématu [binary_search](../standard-library/algorithm-functions.md#binary_search).

## <a name="copy-stlclr"></a><a name="copy"></a>Copy (STL/CLR)

Přiřadí hodnoty prvků ze zdrojového rozsahu do cílového rozsahu a provede iterace přes zdrojové sekvence prvků a přiřadí je novým pozicím směrem dopředu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt copy(_InIt _First, _InIt _Last, _OutIt _Dest);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `copy`. Další informace najdete v tématu [kopírování](../standard-library/algorithm-functions.md#copy).

## <a name="copy_backward-stlclr"></a><a name="copy_backward"></a>copy_backward (STL/CLR)

Přiřadí hodnoty prvků ze zdrojového rozsahu do cílového rozsahu a provede iterace přes zdrojové sekvence prvků a přiřadí je novým pozicím směrem dozadu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt1, class _BidIt2> inline
    _BidIt2 copy_backward(_BidIt1 _First, _BidIt1 _Last,
        _BidIt2 _Dest);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `copy_backward`. Další informace najdete v tématu [copy_backward](../standard-library/algorithm-functions.md#copy_backward).

## <a name="count-stlclr"></a><a name="count"></a>Count (STL/CLR)

Vrátí počet prvků v rozsahu, jejichž hodnoty odpovídají zadané hodnotě.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _Ty> inline
    typename iterator_traits<_InIt>::difference_type
        count(_InIt _First, _InIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `count`. Další informace najdete v tématu [Count](../standard-library/algorithm-functions.md#count).

## <a name="count_if-stlclr"></a><a name="count_if"></a>count_if (STL/CLR)

Vrátí počet prvků v rozsahu, jejichž hodnoty odpovídají zadané podmínce.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _Pr> inline
    typename iterator_traits<_InIt>::difference_type
        count_if(_InIt _First, _InIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `count_if`. Další informace najdete v tématu [count_if](../standard-library/algorithm-functions.md#count_if).

## <a name="equal-stlclr"></a><a name="equal"></a>EQUAL (STL/CLR)

Porovná dva rozsahy prvek podle prvku buď ke zjištění rovnosti, nebo ekvivalentnosti ve smyslu určeném binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2> inline
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `equal`. Další informace naleznete v tématu [EQUAL](../standard-library/algorithm-functions.md#equal).

## <a name="equal_range-stlclr"></a><a name="equal_range"></a>equal_range (STL/CLR)

Najde dvojici pozic v seřazeném rozsahu. První bude menší nebo rovna pozici zadaného prvku a druhá větší než pozice prvku, kde smysl ekvivalence nebo řazení použitý k určení pozic v sekvenci může být určen binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Ty> inline
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `equal_range`. Další informace najdete v tématu [equal_range](../standard-library/algorithm-functions.md#equal_range).

## <a name="fill-stlclr"></a><a name="fill"></a>Fill (STL/CLR)

Každému prvku v zadaném rozsahu přiřadí stejnou novou hodnotu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Ty> inline
    void fill(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `fill`. Další informace najdete v tématu [Fill](../standard-library/algorithm-functions.md#fill).

## <a name="fill_n-stlclr"></a><a name="fill_n"></a>fill_n (STL/CLR)

Přiřadí novou hodnotu zadanému počtu prvků v rozsahu, který začíná konkrétním prvkem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _OutIt, class _Diff, class _Ty> inline
    void fill_n(_OutIt _First, _Diff _Count, const _Ty% _Val);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `fill_n`. Další informace najdete v tématu [fill_n](../standard-library/algorithm-functions.md#fill_n).

## <a name="find-stlclr"></a><a name="find"></a>Find (STL/CLR)

Vyhledá pozici prvního výskytu prvku v rozsahu, který má zadanou hodnotu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _Ty> inline
    _InIt find(_InIt _First, _InIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `find`. Další informace najdete v tématu [Najít](../standard-library/algorithm-functions.md#find).

## <a name="find_end-stlclr"></a><a name="find_end"></a>find_end (STL/CLR)

Vyhledá v rozsahu poslední dílčí sekvenci, která je shodná se zadanou sekvencí nebo která je ekvivalentní ve smyslu určeném binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `find_end`. Další informace najdete v tématu [find_end](../standard-library/algorithm-functions.md#find_end).

## <a name="find_first_of-stlclr"></a><a name="find_first_of"></a>find_first_of (STL/CLR)

Vyhledá první výskyt jedné z několika hodnot v cílovém rozsahu nebo první výskyt jednoho z několika prvků, které jsou ekvivalentní ve smyslu určeném binárním predikátem zadané sadě prvků.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `find_first_of`. Další informace najdete v tématu [find_first_of](../standard-library/algorithm-functions.md#find_first_of).

## <a name="find_if-stlclr"></a><a name="find_if"></a>find_if (STL/CLR)

Vyhledá pozici prvního výskytu prvku v rozsahu, který splňuje zadanou podmínku.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _Pr> inline
    _InIt find_if(_InIt _First, _InIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `find_if`. Další informace najdete v tématu [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="for_each-stlclr"></a><a name="for_each"></a>for_each (STL/CLR)

Na každý prvek v pořadí dopředu v rozsahu použije zadaný objekt funkce a vrátí objekt funkce.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _Fn1> inline
    _Fn1 for_each(_InIt _First, _InIt _Last, _Fn1 _Func);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `for_each`. Další informace najdete v tématu [for_each](../standard-library/algorithm-functions.md#for_each).

## <a name="generate-stlclr"></a><a name="generate"></a>Generated (STL/CLR)

Přiřadí hodnoty generované objektem funkce každému prvku v rozsahu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Fn0> inline
    void generate(_FwdIt _First, _FwdIt _Last, _Fn0 _Func);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `generate`. Další informace naleznete v tématu [Generate](../standard-library/algorithm-functions.md#generate).

## <a name="generate_n-stlclr"></a><a name="generate_n"></a>generate_n (STL/CLR)

Přiřadí hodnoty generované objektem funkce zadanému počtu prvků v rozsahu a vrátí pozici prvku za poslední přiřazenou hodnotou.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _OutIt, class _Diff, class _Fn0> inline
    void generate_n(_OutIt _Dest, _Diff _Count, _Fn0 _Func);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `generate_n`. Další informace najdete v tématu [generate_n](../standard-library/algorithm-functions.md#generate_n).

## <a name="includes-stlclr"></a><a name="includes"></a>includes (STL/CLR)

Ověřuje, zda jeden seřazený rozsah obsahuje všechny prvky obsažené ve druhém seřazeném rozsahu, kde kritérium pořadí nebo ekvivalence mezi prvky může být určeno binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2> inline
    bool includes(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool includes(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `includes`. Další informace najdete v tématu [zahrnutí](../standard-library/algorithm-functions.md#includes).

## <a name="inplace_merge-stlclr"></a><a name="inplace_merge"></a>inplace_merge (STL/CLR)

Kombinuje prvky ze dvou po sobě následujících seřazených rozsahů do jednoho seřazeného rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt> inline
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako C++ standardní funkce knihovny `inplace_merge` Další informace naleznete v tématu [inplace_merge](../standard-library/algorithm-functions.md#inplace_merge).

## <a name="iter_swap-stlclr"></a><a name="iter_swap"></a>iter_swap (STL/CLR)

Vymění dvě hodnoty odkazované dvojicí zadaných iterátorů.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    void iter_swap(_FwdIt1 _Left, _FwdIt2 _Right);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `iter_swap`. Další informace najdete v tématu [iter_swap](../standard-library/algorithm-functions.md#iter_swap).

## <a name="lexicographical_compare-stlclr"></a><a name="lexicographical_compare"></a>lexicographical_compare (STL/CLR)

Porovná prvek po prvku mezi dvěma sekvencemi k určení, která z nich je menší.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2> inline
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `lexicographical_compare`. Další informace najdete v tématu [lexicographical_compare](../standard-library/algorithm-functions.md#lexicographical_compare).

## <a name="lower_bound-stlclr"></a><a name="lower_bound"></a>lower_bound (STL/CLR)

Vyhledá pozici prvního prvku v seřazeném rozsahu, jehož hodnota je menší než nebo rovna zadané hodnotě, kde kritérium pořadí může být určeno binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `lower_bound`. Další informace najdete v tématu [lower_bound](../standard-library/algorithm-functions.md#lower_bound).

## <a name="make_heap-stlclr"></a><a name="make_heap"></a>make_heap (STL/CLR)

Převede prvky ze zadaného rozsahu do haldy, ve které je první prvek největší a pro kterou může být kritérium řazení určeno binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void make_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void make_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `make_heap`. Další informace najdete v tématu [make_heap](../standard-library/algorithm-functions.md#make_heap).

## <a name="max-stlclr"></a><a name="max"></a>Max (STL/CLR)

Porovná dva objekty a vrátí větší z nich, kde kritérium pořadí může být určeno binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _Ty> inline
    const _Ty max(const _Ty% _Left, const _Ty% _Right);
template<class _Ty, class _Pr> inline
    const _Ty max(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `max`. Další informace najdete v tématu [Max](../standard-library/algorithm-functions.md#max).

## <a name="max_element-stlclr"></a><a name="max_element"></a>max_element (STL/CLR)

Vyhledá první výskyt největšího prvku v zadaném rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt> inline
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `max_element`. Další informace najdete v tématu [max_element](../standard-library/algorithm-functions.md#max_element).

## <a name="merge-stlclr"></a><a name="merge"></a>sloučení (STL/CLR)

Kombinuje všechny prvky ze dvou po sobě seřazených zdrojových rozsahů do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `merge`. Další informace najdete v tématu [sloučení](../standard-library/algorithm-functions.md#merge).

## <a name="min-stlclr"></a><a name="min"></a>min (STL/CLR)

Porovná dva objekty a vrátí menší z nich, kde kritérium pořadí může být určeno binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _Ty> inline
    const _Ty min(const _Ty% _Left, const _Ty% _Right);
template<class _Ty, class _Pr> inline
    const _Ty min(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `min`. Další informace najdete v tématu [min](../standard-library/algorithm-functions.md#min).

## <a name="min_element-stlclr"></a><a name="min_element"></a>min_element (STL/CLR)

Vyhledá první výskyt nejmenšího prvku v zadaném rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt> inline
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `min_element`. Další informace najdete v tématu [Min_element](../standard-library/algorithm-functions.md#min_element).

## <a name="mismatch-stlclr"></a><a name="mismatch"></a>Neshoda (STL/CLR)

Porovná dva rozsahy prvek po prvku buď ke zjištění rovnosti, nebo ekvivalence ve smyslu určeném binárním predikátem a vyhledá první pozici, kde existuje rozdíl.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2> inline
    _PAIR_TYPE(_InIt1)
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);
template<class _InIt1, class _InIt2, class _Pr> inline
    _PAIR_TYPE(_InIt1)
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
            _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `mismatch`. Další informace naleznete v tématu [neshoda](../standard-library/algorithm-functions.md#mismatch).

## <a name="next_permutation-stlclr"></a><a name="next_permutation"></a>next_permutation (STL/CLR)

Znovu uspořádá prvky v rozsahu tak, aby původní pořadí bylo nahrazeno lexikograficky následující větší permutací, pokud existuje, kde význam následujícího může být určen binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt> inline
    bool next_permutation(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    bool next_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `next_permutation`. Další informace najdete v tématu [next_permutation](../standard-library/algorithm-functions.md#next_permutation).

## <a name="nth_element-stlclr"></a><a name="nth_element"></a>nth_element (STL/CLR)

Rozdělí rozsah prvků na oddíly a správně vyhledá `n`element sekvence v rozsahu tak, aby všechny prvky před ním byly menší nebo rovny hodnotě a všechny prvky, které následují v sekvenci, jsou větší než nebo rovny.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `nth_element`. Další informace najdete v tématu [nth_element](../standard-library/algorithm-functions.md#nth_element).

## <a name="partial_sort-stlclr"></a><a name="partial_sort"></a>partial_sort (STL/CLR)

Uspořádá zadaný počet menších prvků v rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `partial_sort`. Další informace najdete v tématu [partial_sort](../standard-library/algorithm-functions.md#partial_sort).

## <a name="partial_sort_copy-stlclr"></a><a name="partial_sort_copy"></a>partial_sort_copy (STL/CLR)

Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu, kde zdrojové prvky jsou seřazeny buď podle binárního predikátu „menší než“ nebo jiného určeného binárního predikátu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _RanIt> inline
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,
        _RanIt _First2, _RanIt _Last2);
template<class _InIt, class _RanIt, class _Pr> inline
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,
        _RanIt _First2, _RanIt _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `partial_sort_copy`. Další informace najdete v tématu [partial_sort_copy](../standard-library/algorithm-functions.md#partial_sort_copy).

## <a name="partition-stlclr"></a><a name="partition"></a>Partition (STL/CLR)

Rozdělí prvky v rozsahu do dvou oddělených sad. Prvky, které splňují unární predikát, jsou umístěny před těmi, které jej nesplňují.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt, class _Pr> inline
    _BidIt partition(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `partition`. Další informace najdete v tématu [oddíl](../standard-library/algorithm-functions.md#partition).

## <a name="pop_heap-stlclr"></a><a name="pop_heap"></a>pop_heap (STL/CLR)

Odstraní největší prvek z přední části haldy až do předposlední pozice v rozsahu a ze zbývajících prvků vytvoří novou haldu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void pop_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void pop_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `pop_heap`. Další informace najdete v tématu [pop_heap](../standard-library/algorithm-functions.md#pop_heap).

## <a name="prev_permutation-stlclr"></a><a name="prev_permutation"></a>prev_permutation (STL/CLR)

Znovu uspořádá prvky v rozsahu tak, aby původní pořadí bylo nahrazeno lexikograficky následující větší permutací, pokud existuje, kde význam následujícího může být určen binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt> inline
    bool prev_permutation(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    bool prev_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `prev_permutation`. Další informace najdete v tématu [prev_permutation](../standard-library/algorithm-functions.md#prev_permutation).

## <a name="push_heap-stlclr"></a><a name="push_heap"></a>push_heap (STL/CLR)

Přidá prvek, který je na konci rozsahu, do stávající haldy, která zahrnuje předchozí prvky daného rozsahu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void push_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void push_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `push_heap`. Další informace najdete v tématu [push_heap](../standard-library/algorithm-functions.md#push_heap).

## <a name="random_shuffle-stlclr"></a><a name="random_shuffle"></a>random_shuffle (STL/CLR)

Změní uspořádání sekvence `N` prvků v rozsahu na jednu z `N`! možné postupy vybrané náhodně.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void random_shuffle(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Fn1> inline
    void random_shuffle(_RanIt _First, _RanIt _Last, _Fn1% _Func);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `random_shuffle`. Další informace najdete v tématu [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle).

## <a name="remove-stlclr"></a><a name="remove"></a>Remove (STL/CLR)

Odstraní zadanou hodnotu z daného rozsahu bez narušení pořadí zbývajících prvků a vrácení konce nového rozsahu, který neobsahuje zadanou hodnotu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt remove(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `remove`. Další informace najdete v tématu věnovaném [Odebrání](../standard-library/algorithm-functions.md#remove).

## <a name="remove_copy-stlclr"></a><a name="remove_copy"></a>remove_copy (STL/CLR)

Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu. Prvky zadané hodnoty zkopírovány nejsou. Nenaruší pořadí zbývajících prvků a nevrátí konec nového cílového rozsahu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt, class _Ty> inline
    _OutIt remove_copy(_InIt _First, _InIt _Last,
        _OutIt _Dest, const _Ty% _Val);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `remove_copy`. Další informace najdete v tématu [remove_copy](../standard-library/algorithm-functions.md#remove_copy).

## <a name="remove_copy_if-stlclr"></a><a name="remove_copy_if"></a>remove_copy_if (STL/CLR)

Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu. Prvky splňující predikát zkopírovány nejsou. Nenaruší pořadí zbývajících prvků a nevrátí konec nového cílového rozsahu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt, class _Pr> inline
    _OutIt remove_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `remove_copy_if`. Další informace najdete v tématu [remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if).

## <a name="remove_if-stlclr"></a><a name="remove_if"></a>remove_if (STL/CLR)

Odstraní prvky, které splňují predikát, z daného rozsahu bez narušení pořadí zbývajících prvků a vrácení konce nového rozsahu, který neobsahuje zadanou hodnotu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Pr> inline
    _FwdIt remove_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `remove_if`. Další informace najdete v tématu [remove_if](../standard-library/algorithm-functions.md#remove_if).

## <a name="replace-stlclr"></a><a name="replace"></a>Replace (STL/CLR)

Zkontroluje každý prvek v rozsahu a nahradí jej, pokud odpovídá zadané hodnotě.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Ty> inline
    void replace(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Oldval, const _Ty% _Newval);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `replace`. Další informace naleznete v tématu [Replace](../standard-library/algorithm-functions.md#replace).

## <a name="replace_copy-stlclr"></a><a name="replace_copy"></a>replace_copy (STL/CLR)

Zkontroluje každý prvek ve zdrojovém rozsahu a nahradí jej, pokud při kopírování výsledku do nového cílového rozsahu odpovídá zadané hodnotě.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt, class _Ty> inline
    _OutIt replace_copy(_InIt _First, _InIt _Last, _OutIt _Dest,
        const _Ty% _Oldval, const _Ty% _Newval);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `replace_copy`. Další informace najdete v tématu [replace_copy](../standard-library/algorithm-functions.md#replace_copy).

## <a name="replace_copy_if-stlclr"></a><a name="replace_copy_if"></a>replace_copy_if (STL/CLR)

Zkontroluje každý prvek ve zdrojovém rozsahu a nahradí jej, pokud při kopírování výsledku do nového cílového rozsahu splňuje zadaný predikát.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt, class _Pr, class _Ty> inline
    _OutIt replace_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred, const _Ty% _Val);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `replace_copy_if`. Další informace najdete v tématu [replace_copy_if](../standard-library/algorithm-functions.md#replace_copy_if).

## <a name="replace_if-stlclr"></a><a name="replace_if"></a>replace_if (STL/CLR)

Zkontroluje každý prvek v rozsahu a nahradí jej, pokud splňuje zadaný predikát.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Pr, class _Ty> inline
    void replace_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred,
        const _Ty% _Val);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `replace_if`. Další informace najdete v tématu [replace_if](../standard-library/algorithm-functions.md#replace_if).

## <a name="reverse-stlclr"></a><a name="reverse"></a>Reverse (STL/CLR)

Obrátí pořadí prvků v rozsahu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt> inline
    void reverse(_BidIt _First, _BidIt _Last);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `reverse`. Další informace najdete v tématu [reverzní](../standard-library/algorithm-functions.md#reverse).

## <a name="reverse_copy-stlclr"></a><a name="reverse_copy"></a>reverse_copy (STL/CLR)

Obrátí pořadí prvků v rámci zdrojového rozsahu při kopírování do cílového rozsahu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt, class _OutIt> inline
    _OutIt reverse_copy(_BidIt _First, _BidIt _Last, _OutIt _Dest);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `reverse_copy`. Další informace najdete v tématu [reverse_copy](../standard-library/algorithm-functions.md#reverse_copy).

## <a name="rotate-stlclr"></a><a name="rotate"></a>otočení (STL/CLR)

Vymění prvky ve dvou sousedních rozsazích.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt> inline
    void rotate(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `rotate`. Další informace najdete v tématu [otočení](../standard-library/algorithm-functions.md#rotate).

## <a name="rotate_copy-stlclr"></a><a name="rotate_copy"></a>rotate_copy (STL/CLR)

Vymění prvky ve dvou sousedních rozsazích v rámci zdrojového rozsahu a zkopíruje výsledek do cílového rozsahu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _OutIt> inline
    _OutIt rotate_copy(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last,
        _OutIt _Dest);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `rotate_copy`. Další informace najdete v tématu [rotate_copy](../standard-library/algorithm-functions.md#rotate_copy).

## <a name="search-stlclr"></a><a name="search_"></a>Search (STL/CLR)

Vyhledá první výskyt sekvence v cílovém rozsahu, jejíž prvky jsou rovné prvkům v dané sekvenci prvků nebo jejíž prvky jsou ekvivalentní ve smyslu určeném binárním predikátem prvkům v dané sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `search`. Další informace najdete v tématu [hledání](../standard-library/algorithm-functions.md#search).

## <a name="search_n-stlclr"></a><a name="search_n"></a>search_n (STL/CLR)

Vyhledá první dílčí sekvenci v rozsahu zadaného počtu prvků s konkrétní hodnotou nebo vztahem k dané hodnotě podle binárního predikátu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt1, class _Diff2, class _Ty> inline
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,
        _Diff2 _Count, const _Ty& _Val);
template<class _FwdIt1, class _Diff2, class _Ty, class _Pr> inline
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,
        _Diff2 _Count, const _Ty& _Val, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `search_n`. Další informace najdete v tématu [search_n](../standard-library/algorithm-functions.md#search_n).

## <a name="set_difference-stlclr"></a><a name="set_difference"></a>set_difference (STL/CLR)

Sjednotí všechny prvky, které patří do jednoho seřazeného zdrojového rozsahu, ale nikoli do druhého seřazeného zdrojového rozsahu, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2,_OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `set_difference`. Další informace najdete v tématu [set_difference](../standard-library/algorithm-functions.md#set_difference).

## <a name="set_intersection-stlclr"></a><a name="set_intersection"></a>set_intersection (STL/CLR)

Sjednotí všechny prvky, které náleží do obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `set_intersection`. Další informace najdete v tématu [set_intersection](../standard-library/algorithm-functions.md#set_intersection).

## <a name="set_symmetric_difference-stlclr"></a><a name="set_symmetric_difference"></a>set_symmetric_difference (STL/CLR)

Sjednotí všechny prvky, které náleží do jednoho, ale nikoli obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `set_symmetric_difference`. Další informace najdete v tématu [set_symmetric_difference](../standard-library/algorithm-functions.md#set_symmetric_difference).

## <a name="set_union-stlclr"></a><a name="set_union"></a>set_union (STL/CLR)

Sjednotí všechny prvky, které náleží alespoň do jednoho ze dvou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `set_union`. Další informace najdete v tématu [set_union](../standard-library/algorithm-functions.md#set_union).

## <a name="sort-stlclr"></a><a name="sort"></a>Sort (STL/CLR)

Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void sort(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void sort(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `sort`. Další informace najdete v tématu věnovaném [řazení](../mfc/reference/cmfclistctrl-class.md#sort).

## <a name="sort_heap-stlclr"></a><a name="sort_heap"></a>sort_heap (STL/CLR)

Převede haldu na seřazený rozsah.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void sort_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void sort_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `sort_heap`. Další informace najdete v tématu [sort_heap](../standard-library/algorithm-functions.md#sort_heap).

## <a name="stable_partition-stlclr"></a><a name="stable_partition"></a>stable_partition (STL/CLR)

Rozdělí prvky v rozsahu do dvou oddělených sad. Prvky, které splňují unární predikát, jsou umístěny před těmi, které jej nesplňují. Relativní pořadí ekvivalentních prvků je zachováno.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt, class _Pr> inline
    _BidIt stable_partition(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `stable_partition`. Další informace najdete v tématu [stable_partition](../standard-library/algorithm-functions.md#stable_partition).

## <a name="stable_sort-stlclr"></a><a name="stable_sort"></a>stable_sort (STL/CLR)

Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem a zachová relativní pořadí ekvivalentních prvků.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt> inline
    void stable_sort(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    void stable_sort(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `stable_sort`. Další informace najdete v tématu [stable_sort](../standard-library/algorithm-functions.md#stable_sort).

## <a name="swap-stlclr"></a><a name="swap"></a>swap (STL/CLR)

Vymění hodnoty prvků mezi dvěma typy objektů, obsah prvního objektu přiřadí ke druhému objektu a obsah druhého k prvnímu objektu.

### <a name="syntax"></a>Syntaxe

```cpp
<class _Ty> inline
    void swap(_Ty% _Left, _Ty% _Right);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `swap`. Další informace najdete v tématu [swap](../standard-library/algorithm-functions.md#swap).

## <a name="swap_ranges-stlclr"></a><a name="swap_ranges"></a>swap_ranges (STL/CLR)

Vymění prvky z jednoho rozsahu za prvky druhého rozsahu o stejné velikosti.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt2 swap_ranges(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `swap_ranges`. Další informace najdete v tématu [swap_ranges](../standard-library/algorithm-functions.md#swap_ranges).

## <a name="transform-stlclr"></a><a name="transform"></a>transformace (STL/CLR)

Aplikuje zadaný objekt funkce na každý prvek ve zdrojovém rozsahu nebo na dvojici prvků ze dvou zdrojových rozsahů a zkopíruje vrácené hodnoty objektu funkce do cílového rozsahu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt, class _Fn1> inline
    _OutIt transform(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Fn1 _Func);
template<class _InIt1, class _InIt2, class _OutIt, class _Fn2> inline
    _OutIt transform(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `transform`. Další informace najdete v tématu [transformace](../standard-library/algorithm-functions.md#transform).

## <a name="unique-stlclr"></a><a name="unique"></a>Unique (STL/CLR)

Odstraní duplicitní prvky, které v zadaném rozsahu sousedí.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt> inline
    _FwdIt unique(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt unique(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `unique`. Další informace najdete v tématu [Unique](../standard-library/algorithm-functions.md#unique).

## <a name="unique_copy-stlclr"></a><a name="unique_copy"></a>unique_copy (STL/CLR)

Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu s výjimkou sousedících duplicitních prvků.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest);
template<class _InIt, class _OutIt, class _Pr> inline
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `unique_copy`. Další informace najdete v tématu [unique_copy](../standard-library/algorithm-functions.md#unique_copy).

## <a name="upper_bound-stlclr"></a><a name="upper_bound"></a>upper_bound (STL/CLR)

Najde pozici prvního prvku v seřazeném rozsahu, který má hodnotu větší než zadaná hodnota, kde kritérium pořadí může být určeno binárním predikátem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako funkce C++ standardní knihovny `upper_bound`. Další informace najdete v tématu [Upper_bound](../standard-library/algorithm-functions.md#upper_bound).
